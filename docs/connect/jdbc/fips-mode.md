---
title: FIPS-Modus auf JDBC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/26/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: craigg
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
manager: kenvh
ms.openlocfilehash: d710bb6e83d6f9761f7926afac3280a2c33d2bec
ms.sourcegitcommit: 96090bb369ca8aba364c2e7f60b37165e5af28fc
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2019
ms.locfileid: "66822236"
---
# <a name="fips-mode"></a>FIPS-Modus

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Der Microsoft JDBC-Treiber für SQL Server unterstützt die Ausführung in JVMs konfiguriert *FIPS 140-konformen*.

#### <a name="prerequisites"></a>Voraussetzungen

- FIPS konfiguriert JVM
- Entsprechende SSL-Zertifikat
- Dateien der entsprechenden Richtlinie
- Entsprechende Konfigurationsparameter

## <a name="fips-configured-jvm"></a>FIPS konfiguriert JVM

Anwendungen können konfigurieren, in der Regel die `java.security` Datei, die FIPS-konformen Crypto-Provider verwendet. Informieren Sie sich die Informationen zum Konfigurieren der FIPS 140-Kompatibilität JVM bereit.

Die genehmigten Module für die Konfiguration von FIPS, finden Sie in [überprüft Module in der kryptografischen Modul-Validierungsprogramm](https://csrc.nist.gov/Projects/cryptographic-module-validation-program/Validated-Modules).

Anbieter müssen möglicherweise einige zusätzliche Schritte zum Konfigurieren einer JVM mit FIPS.

## <a name="appropriate-ssl-certificate"></a>Entsprechende SSL-Zertifikat
Um die Verbindung mit SQL Server im FIPS-Modus ist ein gültiges SSL-Zertifikat erforderlich. Installieren Sie, oder importieren Sie es in den Store im Java-Schlüssel (JVM) auf dem Clientcomputer die, in denen FIPS aktiviert ist.

### <a name="importing-ssl-certificate-in-java-keystore"></a>SSL-Zertifikats in Java-KeyStore importieren
Für FIPS müssen in den meisten Fällen importieren Sie das Zertifikat (Cert) im PKCS oder einem anbieterspezifischen Format.
Verwenden Sie den folgenden Codeausschnitt, importieren Sie das SSL-Zertifikat, und speichern Sie sie in einem Arbeitsverzeichnis im passenden Format für den KeyStore ein. _VERTRAUEN\_STORE\_Kennwort_ ist Ihr Kennwort für Java-KeyStore.

```java
public void saveGenericKeyStore(
        String provider,
        String trustStoreType,
        String certName,
        String certPath
        ) throws KeyStoreException, CertificateException,
            NoSuchAlgorithmException, NoSuchProviderException,
            IOException
{
    KeyStore ks = KeyStore.getInstance(trustStoreType, provider);
    FileOutputStream os = new FileOutputStream("./MyTrustStore_" + trustStoreType);
    ks.load(null, null);
    ks.setCertificateEntry(certName, getCertificate(certPath));
    ks.store(os, TRUST_STORE_PASSWORD.toCharArray());
    os.flush();
    os.close();
}

private Certificate getCertificate(String pathName)
        throws FileNotFoundException, CertificateException
{
    FileInputStream fis = new FileInputStream(pathName);
    CertificateFactory cf = CertificateFactory.getInstance("X.509");
    return cf.generateCertificate(fis);
}
```

Im folgende Beispiel wird ein Azure SSL-Zertifikat im PKCS12-Formats mit dem Anbieter BouncyCastle importieren. Das Zertifikat wird importiert, in das Arbeitsverzeichnis, das mit dem Namen _MyTrustStore\_PKCS12_ mit den folgenden Codeausschnitt:

`saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer");`

## <a name="appropriate-policy-files"></a>Dateien der entsprechenden Richtlinie
Für einige Anbieter FIPS sind die uneingeschränkte Richtlinie-JAR-Dateien erforderlich. In solchen Fällen für Sun / Oracle, laden Sie die Java Cryptography Extension (JCE) Unlimited Stärke Rechtsprechung Richtliniendateien für [JRE 8](https://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) oder [JRE 7](https://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html). 

## <a name="appropriate-configuration-parameters"></a>Entsprechende Konfigurationsparameter
Führen Sie den JDBC-Treiber im FIPS-kompatiblen Modus konfigurieren Sie Verbindungseigenschaften, wie in der folgenden Tabelle dargestellt. 

#### <a name="properties"></a>Eigenschaften 

|Eigenschaft|Typ|Default|und Beschreibung|Hinweise|
|---|---|---|---|---|
|encrypt|Boolesche Werte ["TRUE / FALSE"]|„FALSE“|Für FIPS aktivierte JVM Verschlüsseln von Eigenschaft sollte **"true"**||
|TrustServerCertificate|Boolesche Werte ["TRUE / FALSE"]|„FALSE“|Für FIPS, muss der Benutzer-Zertifikatskette zu überprüfen, damit der Benutzer verwenden sollten **"false"** Wert für diese Eigenschaft. ||
|trustStore|Zeichenfolge|NULL|Ihre Java-Keystore-Dateipfad, in dem Sie das Zertifikat importiert haben. Wenn Sie das Zertifikat auf Ihrem System und dann nicht erforderlich, übergeben Sie etwas installieren. Treiber verwendet die Cacerts oder Jssecacerts-Dateien.||
|trustStorePassword|Zeichenfolge|NULL|Das Kennwort, das zum Überprüfen der Integrität der trustStore-Daten verwendet wird.||
|fips|Boolesche Werte ["TRUE / FALSE"]|„FALSE“|Diese Eigenschaft sollte sein, für die FIPS JVM aktiviert **"true"**|In 6.1.4 hinzugefügt (Stable release 6.2.2)||
|fipsProvider|Zeichenfolge|NULL|FIPS-Anbieter in JVM konfiguriert. Z. B. BCFIPS oder SunPKCS11-NSS |6\.1.2 hinzugefügt (Stable release 6.2.2), ausführliche Informationen finden Sie in 6.4.0: als veraltet markiert [hier](https://github.com/Microsoft/mssql-jdbc/pull/460).|
|trustStoreType|Zeichenfolge|JKS|FIPS-Modus Trust Store Mengentyp entweder PKCS12 Typ definiert, oder von FIPS-Anbieter |6\.1.2 hinzugefügt (Stable release 6.2.2)||
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
