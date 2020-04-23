---
title: FPS-Modus in JDBC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: genemi
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 83ce3690d194b8b06fc79d58c2d7bc7efa996619
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293380"
---
# <a name="fips-mode"></a>FIPS-Modus

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Der Microsoft-JDBC-Treiber für SQL Server unterstützt die Ausführung in JVMs, die als *FIPS 140-konform* konfiguriert sind.

#### <a name="prerequisites"></a>Voraussetzungen

- Für FIPS konfigurierte JVM
- Geeignetes TSL/SSL-Zertifikat
- Geeignete Richtliniendateien
- Geeignete Konfigurationsparameter

## <a name="fips-configured-jvm"></a>Für FIPS konfigurierte JVM

Im Allgemeinen können Anwendungen die `java.security`-Datei für die Verwendung von FIPS-konformen Kryptografieanbietern konfigurieren. Informationen zur Konfiguration für die FIPS 140-Konformität finden Sie in der Dokumentation zu Ihrer JVM.

Die genehmigten Module für die FIPS-Konfiguration finden Sie unter [Validated Modules in the Cryptographic Module Validation Program](https://csrc.nist.gov/Projects/cryptographic-module-validation-program/Validated-Modules) (Validierte Module im Programm zur Validierung von Kryptografiemodulen).

Anbieter können zusätzliche Schritte zum Konfigurieren einer JVM mit FIPS eingerichtet haben.

## <a name="appropriate-ssl-certificate"></a>Geeignetes SSL-Zertifikat
Zum Herstellen einer Verbindung mit SQL Server im FIPS-Modus ist ein gültiges TLS/SSL-Zertifikat erforderlich. Installieren oder importieren Sie das Zertifikat in den Java-Keystore auf dem Clientcomputer (JVM), auf dem FIPS aktiviert ist.

### <a name="importing-ssl-certificate-in-java-keystore"></a>Importieren des SSL-Zertifikats in den Java-Keystore
Für FIPS müssen Sie das Zertifikat (CERT-Datei) wahrscheinlich als PKCS oder in einem anbieterspezifischen Format importieren.
Verwenden Sie den folgenden Codeausschnitt, um das TLS/SSL-Zertifikat zu importieren und im geeigneten Keystoreformat in einem Arbeitsverzeichnis zu speichern. _TRUST\_STORE\_PASSWORD_ ist Ihr Kennwort für den Java-Keystore.

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

Das folgende Beispiel importiert ein Azure-TLS/SSL-Zertifikat im PKCS12-Format mit dem Anbieter „BouncyCastle“. Das Zertifikat wird mit dem folgenden Codeausschnitt in das Arbeitsverzeichnis _MyTrustStore\_PKCS12_ importiert:

`saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer");`

## <a name="appropriate-policy-files"></a>Geeignete Richtliniendateien
Für einige FIPS-Anbieter sind uneingeschränkte Richtlinien-JAR-Dateien erforderlich. Laden Sie in solchen Fällen für Sun und Oracle die Richtliniendateien „Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction“ für [JRE 8](https://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) oder [JRE 7](https://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html) herunter. 

## <a name="appropriate-configuration-parameters"></a>Geeignete Konfigurationsparameter
Konfigurieren Sie Verbindungseigenschaften wie in der folgenden Tabelle gezeigt, um den JDBC-Treiber im FIPS-konformen Modus auszuführen. 

#### <a name="properties"></a>Eigenschaften 

|Eigenschaft|type|Standard|BESCHREIBUNG|Notizen|
|---|---|---|---|---|
|encrypt|Boolesche Werte ["TRUE / FALSE"]|„FALSE“|In einer JVM-Umgebung mit aktiviertem FIPS sollte die encrypt-Eigenschaft **true** lauten.||
|TrustServerCertificate|Boolesche Werte ["TRUE / FALSE"]|„FALSE“|Für FIPS muss der Benutzer die Zertifikatkette validieren, daher sollte der Wert **false** für diese Eigenschaft verwendet werden. ||
|trustStore|String|NULL|Der Dateipfad Ihres Java-Keystores, in den Sie das Zertifikat importiert haben. Wenn Sie das Zertifikat auf Ihrem System installieren, muss hier nichts übergeben werden. Der Treiber verwendet cacerts- oder jssecacerts-Dateien.||
|trustStorePassword|String|NULL|Das Kennwort, das zum Überprüfen der Integrität der trustStore-Daten verwendet wird.||
|fips|Boolesche Werte ["TRUE / FALSE"]|„FALSE“|In einer JVM-Umgebung mit aktiviertem FIPS sollte diese Eigenschaft **true** lauten.|Hinzugefügt in 6.1.4 (stabiles Release: 6.2.2)||
|fipsProvider|String|NULL|In JVM konfigurierter FIPS-Anbieter. Beispiele: BCFIPS oder SunPKCS11-NSS. |Hinzugefügt in 6.1.2 (stabiles Release: 6.2.2), veraltet in 6.4.0 – ausführliche Informationen finden Sie [hier](https://github.com/Microsoft/mssql-jdbc/pull/460).|
|trustStoreType|String|JKS|Legen Sie für den FIPS-Modus den Vertrauensspeichertyp auf PKCS12 oder auf einen vom FIPS-Anbieter definierten Typ fest. |Hinzugefügt in 6.1.2 (stabiles Release: 6.2.2)||
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
