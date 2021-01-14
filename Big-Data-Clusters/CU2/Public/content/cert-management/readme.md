# A set of notebooks used for Certificate Management

The notebooks in this chapter can be used to create a self-signed root certificate authority (or allow for one to be uploaded), and then use that root CA to create and sign certificates for each external endpoint in a Big Data Cluster.

After running the notebook in this chapter, and installing the Root CA certificate locally, all connections to the Big Data Cluster can be made securely (i.e. the internet browser will indicate "This Connection is Secure").  The following notebook can be used to install the Root CA certificate locally on this machine.

- [CER010]()

## Run the notebooks in a sequence

These two notebooks run the required notebooks in this chapter in a sequence in a single 'run all cells' button press.

- [CER100]()
- [CER101]()

The first notebook (CER100) will first generate a Root CA certificate.  The 2nd notebook (CER101) will use an already existing Root CA downloaded and upload using:

- [CER002]()
- [CER003]()

## Details

- By default, the Big Data Cluster cluster generates its own Root CA certificate and all the certificates used inside the cluster are signed with this Root CA certificate. External clients connecting to cluster endpoints will not have this internal Root CA installed and this leads to the certificate verification related warnings on clients (internet browsers etc.) and the need to use the --insecure option with tools like CURL.

- It is better if the certificates for the external endpoints in the Big Data Cluster can be provided and installed in the containers hosting the endpoint services, most preferably using your own trusted CA to sign these certificates and then install the CA chain inside the cluster.  The notebooks in this chapter aid in this process by creating a self-signed Root CA certificate and then creating certificates for each external endpoint signed by the self-signed Root CA certificate.

- The openssl certificate tracking database is created in the `controller` in the `/var/opt/secrets/test-certificates` folder.  Here a record is maintained of each certificate that has been issued for tracking purposes.

[Home](../readme.md)

## Notebooks in this Chapter
- [CER001 - Generate a Root CA certificate

- [CER002 - Download existing Root CA certificate

- [CER003 - Upload existing Root CA certificate

- [CER010 - Install generated Root CA locally

- [CER020 - Create Management Proxy certificate

- [CER021 - Create Knox certificate

- [CER022 - Create App Proxy certificate

- [CER023 - Create Controller certificate

- [CER030 - Sign Management Proxy certificate with generated CA

- [CER031 - Sign Knox certificate with generated CA

- [CER032 - Sign App-Proxy certificate with generated CA

- [CER033 - Sign Controller certificate with cluster Root CA

- [CER040 - Install signed Management Proxy certificate

- [CER041 - Install signed Knox certificate

- [CER042 - Install signed App-Proxy certificate

- [CER043 - Install signed Controller certificate

- [CER050 - Wait for BDC to be Healthy

- [CER100 - Configure Cluster with Self Signed Certificates

- [CER101 - Configure Cluster with Self Signed Certificates using existing Root CA
