---
title: Herstellen einer Verbindung mit einer Azure SQL-Datenbank
description: In diesem Artikel werden Probleme behandelt, die bei der Verwendung des Microsoft JDBC-Treibers für SQL Server zum Herstellen einer Verbindung mit einer Azure SQL-Datenbankinstanz auftreten.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 49645b1f-39b1-4757-bda1-c51ebc375c34
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bda9c33588c8248d0aff62f555ec46451d0e9e78
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725491"
---
# <a name="connecting-to-an-azure-sql-database"></a>Herstellen einer Verbindung mit einer Azure SQL-Datenbank

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

In diesem Artikel werden Probleme behandelt, die auftreten können, wenn mit dem [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] eine Verbindung mit einer [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] hergestellt wird. Weitere Informationen zur Verbindung mit einer [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] finden Sie unter:  
  
- [Azure SQL-Datenbank](/azure/sql-database/sql-database-technical-overview)  
  
- [Vorgehensweise: Herstellen einer Verbindung mit Azure SQL über JDBC](/azure/sql-database/sql-database-connect-query-java)  

- [Connecting using Azure Active Directory Authentication (Herstellen einer Verbindung mithilfe der Azure Active Directory-Authentifizierung)](connecting-using-azure-active-directory-authentication.md)  
  
## <a name="details"></a>Details

Wenn Sie eine Verbindung mit einer [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]-Instanz herstellen, sollten Sie die Masterdatenbank auswählen, um **SQLServerDatabaseMetaData.getCatalogs** aufzurufen.  
Die Rückgabe sämtlicher Kataloge aus einer Benutzerdatenbank wird von [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] nicht unterstützt. **SQLServerDatabaseMetaData.getCatalogs** verwendet die Ansicht „sys.databases“, um Kataloge abzurufen. Eine Erläuterung zum Verhalten von **SQLServerDatabaseMetaData.getCatalogs** in einer [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]-Instanz finden Sie im Abschnitt „Berechtigungen“ des Artikels [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
## <a name="connections-dropped"></a>Getrennte Verbindungen

Bei der Verbindung mit einer [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] können Verbindungen im Leerlauf nach einer Phase ohne Aktivität durch eine Netzwerkkomponente (z. B. eine Firewall) getrennt werden. In diesem Kontext werden zwei Arten von inaktiven Verbindungen behandelt:  

- Inaktive Verbindungen auf der TCP-Ebene, wobei Verbindungen von einer beliebigen Anzahl von Netzwerkgeräten gelöscht werden können.  

- Durch das Azure SQL-Gateway ermittelte, inaktive Verbindungen. Dabei kann TCP **KeepAlive**-Meldungen ausgeben (wodurch sie aus TCP-Sicht nicht inaktiv sind), über die jedoch in den letzten 30 Minuten keine aktive Abfrage ausgeführt wurde. In diesem Szenario wird durch das Gateway ermittelt, ob die TDS-Verbindung 30 Minuten inaktiv war, und die Verbindung wird beendet.  
  
Um zu vermeiden, dass Verbindungen im Leerlauf durch eineNetzwerkkomponente getrennt werden, sollten die folgenden Registrierungseinstellungen(bzw. deren Nicht-Windows-Äquivalente) für das Betriebssystem festgelegt werden, unter dem der Treiber geladen wurde:  
  
|Registrierungseinstellung|Empfohlener Wert|  
|----------------------|-----------------------|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ Parameters \ KeepAliveTime|30.000|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ Parameters \ KeepAliveInterval|1000|  
|HKEY_LOCAL_MACHINE \ SYSTEM \ CurrentControlSet \ Services \ Tcpip \ Parameters \ TcpMaxDataRetransmissions|10|  
  
Starten Sie den Computer neu, damit die Registrierungseinstellungen wirksam werden.  

Um diesen Vorgang in Azure auszuführen, erstellen Sie einen Starttask, durch den die Registrierungsschlüssel hinzugefügt werden.  Fügen Sie der Dienstdefinitionsdatei beispielsweise folgenden Starttask hinzu:  

```xml
<Startup>  
    <Task commandLine="AddKeepAlive.cmd" executionContext="elevated" taskType="simple">  
    </Task>  
</Startup>  
```

Fügen Sie dem Projekt anschließend die Datei „AddKeepAlive.cmd“ hinzu. Legen Sie die Einstellung In Ausgabeverzeichnis kopieren auf Immer kopieren fest. Das folgende Beispiel veranschaulicht eine Datei AddKeepAlive.cmd:  

```bat
if exist keepalive.txt goto done  
time /t > keepalive.txt  
REM Workaround for JDBC keep alive on Azure SQL  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveTime /t REG_DWORD /d 30000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v KeepAliveInterval /t REG_DWORD /d 1000 >> keepalive.txt  
REG ADD HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters /v TcpMaxDataRetransmissions /t REG_DWORD /d 10 >> keepalive.txt  
shutdown /r /t 1  
:done  
```

## <a name="appending-the-server-name-to-the-userid-in-the-connection-string"></a>Anfügen des Servernamens an die UserId in der Verbindungszeichenfolge  

Vor Version 4.0 von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] war es bei der Verbindung mit einer [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] erforderlich, den Servernamen an die UserID in der Verbindungszeichenfolge anzufügen. Beispiel: user@servername. Ab Version 4.0 von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] muss @servername nicht mehr an die UserID in der Verbindungszeichenfolge angefügt werden.  

## <a name="using-encryption-requires-setting-hostnameincertificate"></a>Einstellung „hostNameInCertificate“ zur Verwendung der Verschlüsselung erforderlich

Wenn Sie eine Vorgängerversion von Version 7.2 des [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] verwenden, sollten Sie beim Herstellen einer Verbindung mit einer [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]-Instanz **hostNameInCertificate** angeben, wenn Sie **encrypt=true** angeben. Wenn der Servername in der Verbindungszeichenfolge *shortName*.*domainName* lautet, legen Sie die Eigenschaft **hostNameInCertificate** auf \*.*domainName* fest. Diese Eigenschaft ist ab Version 7.2 des Treibers optional.

Beispiel:

```java
jdbc:sqlserver://abcd.int.mscds.com;databaseName=myDatabase;user=myName;password=myPassword;encrypt=true;hostNameInCertificate=*.int.mscds.com;
```

## <a name="see-also"></a>Weitere Informationen

[Verbinden mit SQL Server mit dem JDBC-Treiber](connecting-to-sql-server-with-the-jdbc-driver.md)