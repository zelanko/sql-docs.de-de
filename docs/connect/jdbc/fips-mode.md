---
title: FPS-Modus in JDBC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/26/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: genemi
ms.technology: connectivity
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
manager: kenvh
ms.openlocfilehash: 482e820d17860b67f46d47f4bb8523e833d0cf5a
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68252214"
---
# <a name="fips-mode"></a>FIPS-Modus

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Der Microsoft JDBC-Treiber für SQL Server unterstützt das Ausführen von in JVMs, die für die Kompatibilität mit *PPS 140*konfiguriert sind.

#### <a name="prerequisites"></a>Voraussetzungen

- Konfigurierte JVM für PPS
- Entsprechendes SSL-Zertifikat
- Entsprechende Richtlinien Dateien
- Geeignete Konfigurationsparameter

## <a name="fips-configured-jvm"></a>Konfigurierte JVM für PPS

Im Allgemeinen können Anwendungen die Datei `java.security` so konfigurieren, dass Sie mit den kompatiblen Kryptografieanbietern von kompatibel sind. Informationen zum Konfigurieren der Konformität mit der Konfiguration von PPS 140 finden Sie in der Dokumentation zu Ihrer JVM.

Informationen zu den genehmigten Modulen für die Konfiguration von fps finden Sie unter [validierte Module im Überprüfungs Programm des kryptografiemoduls](https://csrc.nist.gov/Projects/cryptographic-module-validation-program/Validated-Modules).

Lieferanten können einige zusätzliche Schritte zum Konfigurieren einer JVM mit der Verwendung von PPS ausführen.

## <a name="appropriate-ssl-certificate"></a>Entsprechendes SSL-Zertifikat
Zum Herstellen einer Verbindung mit SQL Server im PPS-Modus ist ein gültiges SSL-Zertifikat erforderlich. Installieren oder importieren Sie es in den Java-Schlüsselspeicher auf dem Client Computer (JVM), auf dem die Aktivierung von "PPS" aktiviert ist.

### <a name="importing-ssl-certificate-in-java-keystore"></a>Importieren eines SSL-Zertifikats in den Java-KeyStore
Bei der Kenn Wort Formatierung müssen Sie das Zertifikat (. cert) höchstwahrscheinlich entweder in PKCS oder in einem anbieterspezifischen Format importieren.
Verwenden Sie den folgenden Code Ausschnitt, um das SSL-Zertifikat zu importieren, und speichern Sie es in einem Arbeitsverzeichnis mit dem entsprechenden Keystore-Format. _Trust\_Store\_Password_ ist Ihr Kennwort für den Java-KeyStore.

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

Das folgende Beispiel zeigt das Importieren eines Azure SSL-Zertifikats im PKCS12-Format mit dem bouncycastle-Anbieter. Das Zertifikat wird mit dem folgenden Code Ausschnitt in das Arbeitsverzeichnis namens _mytruststore\_PKCS12_ importiert:

`saveGenericKeyStore(BCFIPS, PKCS12, "SQLAzure SSL Certificate Name", "SQLAzure.cer");`

## <a name="appropriate-policy-files"></a>Entsprechende Richtlinien Dateien
Für einige-PPS-Anbieter sind uneingeschränkte Richtlinien für die Richtlinie erforderlich. Laden Sie in solchen Fällen für Sun/Oracle die Richtlinien Dateien für die Java-kryptografieerweiterung (JCE) unbegrenzt für [JRE 8](https://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html) oder [JRE 7](https://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html)herunter. 

## <a name="appropriate-configuration-parameters"></a>Geeignete Konfigurationsparameter
Konfigurieren Sie die Verbindungs Eigenschaften wie in der folgenden Tabelle gezeigt, um den JDBC-Treiber im fps-kompatiblen Modus auszuführen. 

#### <a name="properties"></a>Eigenschaften 

|Eigenschaft|Typ|Default|und Beschreibung|Hinweise|
|---|---|---|---|---|
|encrypt|Boolesche Werte ["TRUE / FALSE"]|„FALSE“|Für eine aktivierte JVM-Verschlüsselungs Eigenschaft sollte " **true** " lauten.||
|TrustServerCertificate|Boolesche Werte ["TRUE / FALSE"]|„FALSE“|Der Benutzer muss die Zertifikat Kette überprüfen, damit der Benutzer für diese Eigenschaft den Wert **"false"** verwenden kann. ||
|trustStore|Zeichenfolge|NULL|Ihr Java-KeyStore-Dateipfad, in den Sie Ihr Zertifikat importiert haben. Wenn Sie das Zertifikat auf Ihrem System installieren, müssen Sie nichts weiter passieren. Der Treiber verwendet cacerts oder jssecacerts-Dateien.||
|trustStorePassword|Zeichenfolge|NULL|Das Kennwort, das zum Überprüfen der Integrität der trustStore-Daten verwendet wird.||
|fips|Boolesche Werte ["TRUE / FALSE"]|„FALSE“|Für aktivierte JVM-JVM sollte diese Eigenschaft " **true** " lauten.|Hinzugefügt in 6.1.4 (stabile Version 6.2.2)||
|fipsProvider|Zeichenfolge|NULL|In JVM konfigurierter PPS-Anbieter. Beispielsweise bcfi oder SunPKCS11-NSS |Hinzugefügt in 6.1.2 (stabile Version 6.2.2), veraltet in 6.4.0. Weitere Informationen finden Sie [hier](https://github.com/Microsoft/mssql-jdbc/pull/460).|
|trustStoreType|Zeichenfolge|JKS|Legen Sie für den FPS-Modus den Vertrauens Speicher Typ "PKCS12" oder "Type" fest |Hinzugefügt in 6.1.2 (stabile Version 6.2.2)||
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
