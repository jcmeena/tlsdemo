command to generate the certificate from a command prompt.

keytool -genkeypair -alias samplekey -keyalg RSA -keysize 2048 -storetype PKCS12 -keystore samplekey.p12 -validity 3650

command to create a JKS keystore:
keytool -genkeypair -alias springboot -keyalg RSA -keysize 4096 -storetype JKS -keystore springboot.jks -validity 3650 -storepass password

To create a PKCS12 keystore, and we should, the command is the following:
keytool -genkeypair -alias springboot -keyalg RSA -keysize 4096 -storetype PKCS12 -key

description of the things in the command
genkeypair: generates a key pair;
alias: the alias name for the item we are generating;
keyalg: the cryptographic algorithm to generate the key pair;
keysize: the size of the key;
storetype: the type of keystore;
keystore: the name of the keystore;
validity: validity number of days;
storepass: a password for the keystore.

To check the content of the keystore following the JKS format, we can use keytool again:

keytool -list -v -keystore springboot.jks


To test the content of a keystore following the PKCS12 format:

keytool -list -v -keystore springboot.p12

Convert a JKS keystore into PKCS12 :Should we have already a JKS keystore, 
we have the option to migrate it to PKCS12; keytool has a convenient command for that:

keytool -importkeystore -srckeystore springboot.jks -destkeystore springboot.p12 -deststoretype pkcs12