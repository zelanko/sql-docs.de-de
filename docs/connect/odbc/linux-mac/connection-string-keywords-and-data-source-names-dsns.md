---
title: Herstellen einer Verbindung mit SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data source names
- connection string keywords
- DSNs
ms.assetid: f95cdbce-e7c2-4e56-a9f7-8fa3a920a125
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f1527b212385f280d16bf3f86ce753352b4fb744
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51603940"
---
# <a name="connecting-to-sql-server"></a>Herstellen einer Verbindung mit SQL Server
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

In diesem Artikel wird beschrieben, wie Sie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank herstellen können.  
  
## <a name="connection-properties"></a>Verbindungseigenschaften  

Finden Sie unter [DSN und Schlüsselwörter für Verbindungszeichenfolgen und Attribute](../../../connect/odbc/dsn-connection-string-attribute.md) für alle Schlüsselwörter für Verbindungszeichenfolgen und Attribute, die unter Linux und Mac unterstützt

> [!IMPORTANT]  
> Geben Sie beim Herstellen einer Verbindung mit einer Datenbank, welche Datenbankspiegelung verwendet (oder einen Failoverpartner hat), nicht den Namen der Datenbank in der Verbindungszeichenfolge an. Schicken Sie stattdessen den Befehl **use** *database_name*, um sich mit der Datenbank zu verbinden, bevor Sie Ihre Abfragen ausführen.  
  
Der an übergebene Wert den **Treiber** Schlüsselwort kann einen der folgenden sein:  
  
-   Der Name, den Sie verwendet haben, als Sie den Treiber installiert haben.

-   Der Pfad zur Treiberbibliothek, welcher in der Vorlagen-INI-Datei angegeben war, die wiederum verwendet wurde, um den Treiber zu installieren.  

Um ein DSN zu erstellen, erstellen Sie (falls erforderlich), und bearbeiten Sie die Datei **~/.odbc.ini** (`.odbc.ini` in Ihrem Basisverzeichnis) für einen Benutzer-DSN, der Zugriff nur für den aktuellen Benutzer oder `/etc/odbc.ini` für einen System-DSN (Administratorrechte erforderlich.) Hier folgt eine Beispieldatei, welche die erforderlichen Einträge für eine DSN zeigt:  

```  
[MSSQLTest]  
Driver = ODBC Driver 13 for SQL Server  
Server = [protocol:]server[,port]  
#   
# Note:  
# Port is not a valid keyword in the odbc.ini file  
# for the Microsoft ODBC driver on Linux or macOS
#  
```  

Sie können optional das Protokoll und den Port für die Verbindung mit dem Server angeben. Z. B. **Server = Tcp:***Servername***, 12345**. Beachten Sie, dass das einzige Protokoll unterstützt, indem Sie die Treiber für Linux und MacOS `tcp`.

Um eine Verbindung mit einer benannten Instanz auf einem statischen Port herzustellen, verwenden Sie <b>Server=</b>*servername*,**port_number**. Das Verbinden mit einem dynamischen Port wird nicht unterstützt.  

Alternativ können Sie die DSN-Informationen auch einer Vorlagendatei hinzufügen und den folgenden Befehl ausführen, um sie `~/.odbc.ini` hinzuzufügen:
 - **Odbcinst -i -s -f** *Template_file*  
 
Sie können überprüfen, ob Ihr Treiber funktioniert mit `isql` zum Testen der Verbindung, oder Sie können diesen Befehl verwenden:
 - **Bcp-master.INFORMATION_SCHEMA.TABLES out OutFile.dat -S <server> - U <name> - P <password>**  

## <a name="using-secure-sockets-layer-ssl"></a>Secure Sockets Layer (SSL) verwenden  
Sie können Secure Sockets Layer (SSL) verwenden, um Verbindungen mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]zu verschlüsseln. SSL schützt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Benutzernamen und -Kennwörter über das Netzwerk. SSL überprüft auch die Identität des Servers, um Schutz vor „man-in-the-middle“-Attacken (MITM) zu bieten.  

Das Aktivieren der Verschlüsselung erhöht die Sicherheit auf Kosten der Leistung.

Weitere Informationen finden Sie unter [Verschlüsseln von Verbindungen zu SQL Server](https://go.microsoft.com/fwlink/?LinkId=220900) und [mithilfe von Verschlüsselung ohne Überprüfung](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation).

Unabhängig von den Einstellungen für **Encrypt** und **TrustServerCertificate**werden die Serveranmeldeinformationen (Benutzername und Kennwort) immer verschlüsselt. Die folgende Tabelle zeigt den Effekt der Einstellungen für **Encrypt** und **TrustServerCertificate** .  

||**TrustServerCertificate = Nein**|**TrustServerCertificate = Yes**|  
|-|-------------------------------------|------------------------------------|  
|**Encrypt=no**|Das Serverzertifikat wird nicht überprüft.<br /><br />Zwischen dem Client und dem Server verschickte Daten sind nicht verschlüsselt.|Das Serverzertifikat wird nicht überprüft.<br /><br />Zwischen dem Client und dem Server verschickte Daten sind nicht verschlüsselt.|  
|**Encrypt=yes**|Serverzertifikat wird überprüft.<br /><br />Zwischen dem Client und dem Server verschickte Daten sind verschlüsselt.<br /><br />Der Name (oder die IP-Adresse) in einem allgemeinen Namen (Common Name (CN)) oder alternativen Antragsstellernamen (Subject Alternative Name (SAN)) in einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -SSL-Zertifikat sollte genau mit dem Servernamen (oder der IP-Adresse), der in der Verbindungszeichenfolge angegeben wurde, übereinstimmen.|Das Serverzertifikat wird nicht überprüft.<br /><br />Zwischen dem Client und dem Server verschickte Daten sind verschlüsselt.|  

Standardmäßig überprüfen verschlüsselte Verbindungen immer das Zertifikat des Servers. Jedoch auch hinzufügen, wenn Sie eine Verbindung mit einem Server, die über ein selbst signiertes Zertifikat verfügt herstellen, die `TrustServerCertificate` Option aus, um die Überprüfung des Zertifikats mit der Liste der vertrauenswürdigen Zertifizierungsstelle herausgegebenes Zertifikat:  

```  
Driver={ODBC Driver 13 for SQL Server};Server=ServerNameHere;Encrypt=YES;TrustServerCertificate=YES  
```  
  
SSL verwendet die OpenSSL-Bibliothek. Die folgende Tabelle zeigt die minimalen unterstützten Versionen von OpenSSL und die Zertifikatsvertrauensspeicherorte für jede Plattform:

|Platform|Minimale OpenSSL-Version|Standard-Zertifikatsvertrauensspeicherort|  
|------------|---------------------------|--------------------------------------------|
|Debian 9|1.1.0|/etc/ssl/certs|
|Debian 8.71 |1.0.1|/etc/ssl/certs|
|macOS 10.13|1.0.2|/usr/local/etc/OpenSSL/certs|
|macOS 10.12|1.0.2|/usr/local/etc/OpenSSL/certs|
|OS X 10.11|1.0.2|/usr/local/etc/OpenSSL/certs|
|Red Hat Enterprise Linux 7|1.0.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 6|1.0.0-10|/etc/pki/tls/cert.pem|
|SuSE Linux Enterprise 12 |1.0.1|/etc/ssl/certs|
|SuSE Linux Enterprise 11 |0.9.8|/etc/ssl/certs|
|Ubuntu 17.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.04 |1.0.2|/etc/ssl/certs|
  
Sie können die Verschlüsselung auch angeben, in die Verbindungszeichenfolge mithilfe der `Encrypt` option bei Verwendung **SQLDriverConnect** eine Verbindung herstellen.

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Installieren des Microsoft ODBC Driver for SQL Server unter Linux und macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)  
[Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md)
