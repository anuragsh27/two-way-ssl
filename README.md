# two-way-ssl

This APi contains the code for two way ssl.

use this url (http://localhost:8081/clientApp) to call the client API (i.e  my-ssl-twoway-apiFlow1). which will call the server flow (i.e my-ssl-twoway-apiFlow)

- the commands used to create Client (keystore and truststore) and Server (keystore and truststore)

      Generate Server Keystore
-keytool -genkey -alias mule-server -keysize 2048 -keyalg RSA -keystore server-keystore.jks

    Export the Public Certificate From Server Keystore
-keytool -export -alias mule-server -keystore server-keystore.jks -file server_public.crt

    Import Server Public Certificate Into Client Truststore
-keytool -import -alias mule-client-public -keystore client-truststore.jks -file server_public.crt

    Generate Client Keystore
-keytool -genkey -alias mule-client -keysize 2048 -keyalg RSA -keystore client-keystore.jks

    Export the Public Certificate From Client Keystore
-keytool -export -alias mule-client -keystore client-keystore.jks -file client_public.crt

    Import Client Public Certificate Into Server truststore
-keytool -import -alias mule-server-public -keystore server-truststore.jks -file client_public.crt
