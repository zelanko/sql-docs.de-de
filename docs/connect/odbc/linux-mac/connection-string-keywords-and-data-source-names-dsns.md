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
ms.openlocfilehash: 486d26dd3afeb91cb43181875e22592fb482af5f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68702806"
---
# <a name="connecting-to-sql-server"></a>Herstellen einer Verbindung mit SQL Server
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

In diesem Artikel wird beschrieben, wie Sie eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank herstellen können.  
  
## <a name="connection-properties"></a>Verbindungseigenschaften  

Weitere Informationen zu den Schlüsselwörtern und Attributen der Verbindungszeichenfolge, die unter Linux und Mac unterstützt werden, finden Sie unter [Schlüsselwörter und Attribute von DNS- und Verbindungszeichenfolgen](../../../connect/odbc/dsn-connection-string-attribute.md).

> [!IMPORTANT]  
> Geben Sie beim Herstellen einer Verbindung mit einer Datenbank, welche Datenbankspiegelung verwendet (oder einen Failoverpartner hat), nicht den Namen der Datenbank in der Verbindungszeichenfolge an. Senden Sie stattdessen den Befehl **use** _Datenbankname_, um eine Verbindung mit der Datenbank herzustellen, bevor Sie Ihre Abfragen ausführen.  
  
Einer der folgenden Werte kann an das **Driver**-Schlüsselwort übergeben werden:  
  
-   Der Name, den Sie verwendet haben, als Sie den Treiber installiert haben.

-   Der Pfad zur Treiberbibliothek, welcher in der Vorlagen-INI-Datei angegeben war, die wiederum verwendet wurde, um den Treiber zu installieren.  

Um einen DSN zu erstellen, erstellen Sie ggf. die Datei **~/.odbc.ini** (`.odbc.ini` in Ihrem Basisverzeichnis) für einen Benutzer-DSN, auf den nur der aktuelle Benutzer zugreifen kann, oder `/etc/odbc.ini` für einen System-DSN (Administratorrechte erforderlich). Hier folgt eine Beispieldatei, welche die mindestens erforderlichen Einträge für einen DSN zeigt:  

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

Sie können optional das Protokoll und den Port für die Verbindung mit dem Server angeben. Beispiel: **Server=tcp:**_Servername_**,12345**. Beachten Sie, dass das einzige von Linux- und macOS-Treibern unterstützte Protokoll `tcp` ist.

Um eine Verbindung mit einer benannten Instanz auf einem statischen Port herzustellen, verwenden Sie <b>Server=</b>*servername*,**port_number**. Das Herstellen einer Verbindung mit einem dynamischen Port wird vor Version 17.4 nicht unterstützt.

Alternativ können Sie die DSN-Informationen auch einer Vorlagendatei hinzufügen und den folgenden Befehl ausführen, um sie `~/.odbc.ini` hinzuzufügen:
 - **odbcinst -i -s -f** _Vorlagendatei_  
 
Sie können die Verbindung mit `isql` testen, um zu überprüfen, ob Ihr Treiber funktioniert, oder diesen Befehl verwenden:
 - **bcp master.INFORMATION_SCHEMA.TABLES out OutFile.dat -S <server> -U <name> -P <password>**  

## <a name="using-secure-sockets-layer-ssl"></a>Secure Sockets Layer (SSL) verwenden  
Sie können Secure Sockets Layer (SSL) verwenden, um Verbindungen mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zu verschlüsseln. SSL schützt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Benutzernamen und -Kennwörter über das Netzwerk. SSL überprüft auch die Identität des Servers, um Schutz vor „man-in-the-middle“-Attacken (MITM) zu bieten.  

Das Aktivieren der Verschlüsselung erhöht die Sicherheit auf Kosten der Leistung.

Weitere Informationen dazu finden Sie unter [Verschlüsseln von Verbindungen zu SQL Server](https://go.microsoft.com/fwlink/?LinkId=220900) und [Verwenden von Verschlüsselung ohne Überprüfung](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation).

Unabhängig von den Einstellungen für **Encrypt** und **TrustServerCertificate**werden die Serveranmeldeinformationen (Benutzername und Kennwort) immer verschlüsselt. Die folgende Tabelle zeigt den Effekt der Einstellungen für **Encrypt** und **TrustServerCertificate** .  

||**TrustServerCertificate=no**|**TrustServerCertificate=yes**|  
|-|-------------------------------------|------------------------------------|  
|**Encrypt=no**|Das Serverzertifikat wird nicht überprüft.<br /><br />Zwischen dem Client und dem Server verschickte Daten sind nicht verschlüsselt.|Das Serverzertifikat wird nicht überprüft.<br /><br />Zwischen dem Client und dem Server verschickte Daten sind nicht verschlüsselt.|  
|**Encrypt=yes**|Serverzertifikat wird überprüft.<br /><br />Zwischen dem Client und dem Server verschickte Daten sind verschlüsselt.<br /><br />Der Name (oder die IP-Adresse) in einem allgemeinen Namen (Common Name (CN)) oder alternativen Antragsstellernamen (Subject Alternative Name (SAN)) in einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-SSL-Zertifikat sollte genau mit dem Servernamen (oder der IP-Adresse), der in der Verbindungszeichenfolge angegeben wurde, übereinstimmen.|Das Serverzertifikat wird nicht überprüft.<br /><br />Zwischen dem Client und dem Server verschickte Daten sind verschlüsselt.|  

Standardmäßig überprüfen verschlüsselte Verbindungen immer das Zertifikat des Servers. Wenn Sie jedoch eine Verbindung mit einem Server herstellen, der über ein selbstsigniertes Zertifikat verfügt, müssen Sie auch die Option `TrustServerCertificate` hinzufügen, um die Überprüfung des Zertifikats anhand der Liste der vertrauenswürdigen Zertifizierungsstellen zu umgehen:  

```  
Driver={ODBC Driver 13 for SQL Server};Server=ServerNameHere;Encrypt=YES;TrustServerCertificate=YES  
```  
  
SSL verwendet die OpenSSL-Bibliothek. Die folgende Tabelle zeigt die minimalen unterstützten Versionen von OpenSSL und die Zertifikatsvertrauensspeicherorte für jede Plattform:

|Plattform|Minimale OpenSSL-Version|Standard-Zertifikatsvertrauensspeicherort|  
|------------|---------------------------|--------------------------------------------|
|Debian 10|1.1.1|/etc/ssl/certs|
|Debian 9|1.1.0|/etc/ssl/certs|
|Debian 8.71|1.0.1|/etc/ssl/certs|
|OS X 10.11, macOS 10.12, 10.13, 10.14|1.0.2|/usr/local/etc/openssl/certs|
|Red Hat Enterprise Linux 8|1.1.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 7|1.0.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 6|1.0.0-10|/etc/pki/tls/cert.pem|
|SuSE Linux Enterprise 15|1.1.0|/etc/ssl/certs|
|SuSE Linux Enterprise 11, 12|1.0.1|/etc/ssl/certs|
|Ubuntu 18.10, 19.04|1.1.1|/etc/ssl/certs|
|Ubuntu 18.04|1.1.0|/etc/ssl/certs|
|Ubuntu 16.04, 16.10, 17.10|1.0.2|/etc/ssl/certs|
|Ubuntu 14.04|1.0.1|/etc/ssl/certs|

Sie können die Verschlüsselung auch in der Verbindungszeichenfolge angeben, indem Sie die Option `Encrypt` verwenden, wenn Sie **SQLDriverConnect** zum Herstellen der Verbindung verwenden.

## <a name="adjusting-the-tcp-keep-alive-settings"></a>Anpassen der TCP-Keep-Alive-Einstellungen

Ab ODBC-Treiber 17.4 ist konfigurierbar, wie oft der Treiber Keep-Alive-Pakete sendet und erneut überträgt, wenn er keine Antwort empfängt.
Fügen Sie entweder dem Abschnitt des Treibers in `odbcinst.ini` oder dem Abschnitt des DSN in `odbc.ini` die folgenden Einstellungen zum Konfigurieren hinzu. Beim Herstellen einer Verbindung mit einem DSN verwendet der Treiber die Einstellungen im Abschnitt des DSN, sofern vorhanden. Andernfalls werden, wenn nur eine Verbindung mit einer Verbindungszeichenfolge hergestellt wird, die Einstellungen im Abschnitt des Treibers in `odbcinst.ini` verwendet. Wenn die Einstellung an keinem der Speicherorte vorhanden ist, verwendet der Treiber den Standardwert.

- `KeepAlive=<integer>` steuert, wie häufig TCP ein Keep-Alive-Paket sendet, um zu überprüfen, ob eine Verbindung im Leerlauf noch reagiert. Der Standardwert ist **30** Sekunden.

- `KeepAliveInterval=<integer>` bestimmt das Intervall, das zwischen den erneuten Keep-Alive-Übertragungen liegt, bis eine Antwort empfangen wird.  Der Standardwert beträgt **1** Sekunde.


## <a name="see-also"></a>Weitere Informationen  
[Installieren des Microsoft ODBC Driver for SQL Server unter Linux und macOS](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)  
[Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md)
