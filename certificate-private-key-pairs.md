---
copyright:
  years: 2025
lastupdated: "2025-11-21"

subcollection: dr-automation-powervs

keywords: private key, certificate

---

# GUI certificate and private-key pairs
{: #gui-certificates}


This topic describes steps to create and configure private-key pairs and certificates.

{{site.data.keyword.DR_full_notm}} and agent components. The GUI agents are enabled on all managed KSYS nodes. You can deploy the GUI server on a KSYS subsystem or on a separate AIX LPAR. The GUI server subsystem and the GUI agent subsystem communicate through the network using the secure sockets layer (SSL) protocol.

This communication requires both the GUI server subsystem and the GUI agent subsystem to have their own private-key pairs and certificates.  
- **server.key** and **server.cert** are used for secure communication between the GUI server and the web application.  
- **agent.key** and **agent.cert** are used for secure communication between the GUI server and the GUI agent.

By default, the GUI server and GUI agent use self-signed certificate–private-key pairs. These are exchanged automatically and require no additional configuration. If custom certificate–private-key pairs are used, you must configure them manually.


## Creating private-key pairs and certificates
{: #creating-pairs}

The following procedure explains how to create one private-key pair and one certificate. This example assumes one pair per workstation and uses `workstationname` as a placeholder.

### Steps to create a private-key pair and certificate
{: #create-steps}

1. Initialize the pseudorandom number generator (PRNG):

   **Windows:**
   ```
   openssl rand -out workstationname.rnd -rand ./openssl.exe 8192
   ```

   **UNIX/Linux:**
   ```
   openssl rand -out workstationname.rnd -rand ./openssl.cnf 8192
   ```

2. Create the private-key pair (with triple-DES encryption):

   ```
   openssl genrsa -des3 -out workstationname.key 2048
   ```

   Save the password in a file named `workstationname.pwd`.

   **Note:** Ensure the `workstationname.pwd` file contains only the password (no CR or LF characters).

3. Encode the password in Base64 format:

   ```
   openssl base64 -in workstationname.pwd -out workstationname.sth
   ```

   You can delete `workstationname.pwd` after this.

4. Create a certificate signing request (CSR):

   ```
   openssl req -new -key workstationname.key -out workstationname.csr -config ./openssl.cnf
   ```

5. Send the CSR to your Certificate Authority (CA).

The CA signs the CSR using its own key pair and creates the certificate:

   ```
   openssl x509 -req -CA ca.crt -CAkey ca.key -days 365 -in workstationname.csr -out workstationname.crt -CAcreateserial
   ```

6. Distribute the signed certificate (`workstationname.crt`) and the CA certificate (`ca.crt`) to the workstation.


### Files for local options
{: #local-files}

| Local option        | File                |
|---------------------|---------------------|
| SSL key             | workstationname.key |
| SSL certificate     | workstationname.crt |
| SSL key pwd         | workstationname.sth |
| SSL CA certificate  | ca.crt              |
| SSL random seed     | workstationname.rnd |
{: caption="Files for local options" caption-side="bottom"}

Files for local options {{site.data.keyword.DR_short}}

## Configuring private-key pairs and certificates on the GUI server
{: #configuring-pairs}

1. Go to the security folder:

   ```
   /opt/IBM/ksys/ui/security/
   ```

2. The folder contains the following files:

### Files in the security folder
{: #security-files}

| File name   | Description |
|-------------|-------------|
| ca.key      | Certification authority key |
| ca.cert     | CA certificate used to self-sign certificates |
| server.key  | Key for SSL communication between the GUI server and the web application |
| server.csr  | Certificate signing request |
| server.cert | Certificate signed by CA |
| agent.key   | Key for SSL communication between the GUI server and the GUI agent |
| agent.csr   | Certificate signing request for the agent |
| agent.cert  | Certificate signed by CA |
{: caption="Files in the security folder" caption-side="bottom"}

Files in the security folder {{site.data.keyword.DR_short}}

3. Stop the GUI server:

   ```
   stopsrc -s vmruiserver
   ```

4. Stop the GUI agent:

   ```
   stopsrc -s vmruiagent
   ```

5. Replace the default certificates and private-key pairs with your custom files.

6. Restart the GUI server:

   ```
   startsrc -s vmruiserver
   ```

7. Restart the GUI agent:

   ```
   startsrc -s vmruiagent
   ```
