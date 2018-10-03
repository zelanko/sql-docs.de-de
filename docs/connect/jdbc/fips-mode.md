---
title: FIPS-Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: v-nisidh
ms.author: v-nisidh
manager: andrela
ms.openlocfilehash: cc13455e6f56950d6988909b53aa7664c7fd77f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47723828"
---
# <a name="fips-mode"></a>FIPS-Modus
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Der Microsoft JDBC-Treiber für SQL Server unterstützt *FIPS 140-kompatiblen Modus*. Für Oracle / Sun-JVM finden Sie in der [FIPS 140-kompatiblen Modus für SunJSSE](https://docs.oracle.com/javase/7/docs/technotes/guides/security/jsse/FIPS.html) Abschnitt bereitgestellt, die von Oracle so konfigurieren Sie FIPS aktivierte JVM. 

**Voraussetzungen:**
* FIPS konfiguriert JVM
* Entsprechende SSL-Zertifikat.
* Dateien der entsprechenden Richtlinie. 
* Entsprechende Konfigurationsparameter. 


## <a name="fips-configured-jvm"></a>FIPS konfiguriert JVM

Die genehmigten Module für die Konfiguration von FIPS, finden Sie in der [überprüft FIPS 140-1 und der kryptographischen Module FIPS 140-2](http://csrc.nist.gov/groups/STM/cmvp/documents/140-1/1401val2016.htm). 

Anbieter müssen möglicherweise einige zusätzliche Schritte zum Konfigurieren von JVM mit FIPS.

### <a name="ensure-your-jvm-is-in-fips-mode"></a>Stellen Sie sicher, dass Ihre JVM im FIPS-Modus ist
Um sicherzustellen, dass Ihre JVM FIPS aktiviert ist, führen Sie den folgenden Codeausschnitt ein: 

```java
public boolean isFIPS() throws Exception {
    Provider jsse = Security.getProvider("SunJSSE");
    return jsse != null && jsse.getInfo().contains("FIPS");
}
```

## <a name="appropriate-ssl-certificate"></a>Entsprechende SSL-Zertifikat
Um SQL Server im FIPS-Modus eine Verbindung herzustellen, ist ein gültiges SSL-Zertifikat erforderlich. Installieren Sie, oder importieren Sie es in den Store im Java-Schlüssel (JVM) auf dem Clientcomputer die, in denen FIPS aktiviert ist.

### <a name="importing-ssl-certificate-in-java-keystore"></a>SSL-Zertifikats in Java-KeyStore importieren
Für FIPS müssen in den meisten Fällen importieren Sie das Zertifikat (Cert) entweder PKCS oder in einem anbieterspezifischen Format. Verwenden Sie den folgenden Codeausschnitt, importieren Sie das SSL-Zertifikat, und speichern Sie sie in einem Arbeitsverzeichnis im passenden Format für den KeyStore ein. _TRUST_STORE_PASSWORD_ ist Ihr Kennwort für Java-KeyStore. 

```java
    public void saveGenericKeyStore(String provider, String trustStoreType, String certName, String certPath) throws KeyStoreException, CertificateException, NoSuchAlgorithmException, NoSuchProviderException, IOException {
        KeyStore ks = KeyStore.getInstance(trustStoreType, provider);
        FileOutputStream os = new FileOutputStream("./MyTrustStore_" + trustStoreType);
        ks.load(null, null);
        ks.setCertificateEntry(certName, getCertificate(certPath));
        ks.store(os, TRUST_STORE_PASSWORD.toCharArray());
        os.flush();
        os.close();
    }

    private Certificate getCertificate(String pathName) throws FileNotFoundException, CertificateException {
        FileInputStream fis = new FileInputStream(pathName);
        CertificateFactory cf = CertificateFactory.getInstance("X.509");
        return cf.generateCertificate(fis);
    }

```


Im folgende Beispiel wird ein Azure SSL-Zertifikat im PKCS12-Format mit BouncyCastle Anbieter importiert. Das Zertifikat wird importiert, in das Arbeitsverzeichnis, das mit dem Namen _MyTrustStore_PKCS12_ mit den folgenden Codeausschnitt:

` saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer"); `

## <a name="appropriate-policy-files"></a>Dateien der entsprechenden Richtlinie
Für einige Anbieter FIPS sind die uneingeschränkte Richtlinie-JAR-Dateien erforderlich. In solchen Fällen für Sun / Oracle, laden Sie die Java Cryptography Extension (JCE) Unlimited Stärke Rechtsprechung Richtliniendateien für [JRE 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) oder [JRE 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html). 

## <a name="appropriate-configuration-parameters"></a>Entsprechende Konfigurationsparameter
Führen Sie den JDBC-Treiber im FIPS-kompatiblen Modus konfigurieren Sie Verbindungseigenschaften, wie in der folgenden Tabelle dargestellt. 

**Eigenschaften:** 

|Eigenschaft|Typ|Default|und Beschreibung|Hinweise|
|---|---|---|---|---|
|encrypt|Boolesche Werte ["TRUE / FALSE"]|„FALSE“|Für FIPS aktivierte JVM Verschlüsseln von Eigenschaft sollte **"true"**||
|TrustServerCertificate|Boolesche Werte ["TRUE / FALSE"]|„FALSE“|Für FIPS, muss der Benutzer-Zertifikatskette zu überprüfen, damit der Benutzer verwenden sollten **"false"** Wert für diese Eigenschaft. ||
|trustStore|Zeichenfolge|NULL|Ihre Java-Keystore-Dateipfad, in dem Sie das Zertifikat importiert haben. Wenn Sie das Zertifikat auf Ihrem System und dann nicht erforderlich, übergeben Sie etwas installieren. Treiber verwendet die Cacerts oder Jssecacerts-Dateien.||
|trustStorePassword|Zeichenfolge|NULL|Das Kennwort, das zum Überprüfen der Integrität der trustStore-Daten verwendet wird.||
|fips|Boolesche Werte ["TRUE / FALSE"]|„FALSE“|Diese Eigenschaft sollte sein, für die FIPS JVM aktiviert **"true"**|In 6.1.4 hinzugefügt (Stable release 6.2.2)||
|fipsProvider|Zeichenfolge|NULL|FIPS-Anbieter in JVM konfiguriert. Z. B. BCFIPS oder SunPKCS11-NSS |6.1.2 hinzugefügt (Stable release 6.2.2), ausführliche Informationen finden Sie in 6.4.0: als veraltet markiert [hier](https://github.com/Microsoft/mssql-jdbc/pull/460).|
|trustStoreType|Zeichenfolge|JKS|FIPS-Modus Trust Store Mengentyp entweder PKCS12 Typ definiert, oder von FIPS-Anbieter |6.1.2 hinzugefügt (Stable release 6.2.2)||



  
