# Two-Way SSL Authentication in Java

## Overview
This project demonstrates a client-server model with mutual SSL/TLS authentication using Java.

## Prerequisites
- Java Development Kit (JDK)
- Keytool (included with JDK)

## Generating Keystores and Truststores

### 1. Create Server Keystore
```sh
keytool -genkey -alias server -keyalg RSA -keystore server.keystore -storepass password -validity 365
```

### 2. Export Server Certificate
```sh
keytool -export -alias server -keystore server.keystore -file server.cer -storepass password
```

### 3. Create Server Truststore and Import Client Certificate
```sh
keytool -import -alias client -file client.cer -keystore server.truststore -storepass password
```

### 4. Create Client Keystore
```sh
keytool -genkey -alias client -keyalg RSA -keystore client.keystore -storepass password -validity 365
```

### 5. Export Client Certificate
```sh
keytool -export -alias client -keystore client.keystore -file client.cer -storepass password
```

### 6. Create Client Truststore and Import Server Certificate
```sh
keytool -import -alias server -file server.cer -keystore client.truststore -storepass password
```

## Running the Project
1. Start the server:
```sh
java SSLServer
```
2. Run the client:
```sh
java SSLClient
```
*/
