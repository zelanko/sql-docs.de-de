---
title: SqlErrorLogFile-Klasse
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0dd923f17fe0267edf40d07da982d0856ec4ba06
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "73659054"
---
# <a name="sqlerrorlogfile-class"></a>SqlErrorLogFile-Klasse
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Stellt Eigenschaften zum Anzeigen von Informationen über eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Protokolldatei bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
class SQLErrorLogFile  
{  
   uint32ArchiveNumber;  
   stringInstanceName;  
   datetimeLastModified;  
   uint32LogFileSize;  
   stringName;  
  
};  
```  
  
## <a name="properties"></a>Eigenschaften  
 Die sqlerrorlogfile-Klasse definiert die folgenden Eigenschaften.  
  
|||  
|-|-|  
|Archivenreiber|Datentyp: **UInt32**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Die Archivnummer für die Protokolldatei.|  
|InstanceName|Datentyp: **Zeichenfolge**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> Qualifizierer: Schlüssel<br /><br /> <br /><br /> Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die die Protokolldatei enthält.|  
|LastModified|**Datentyp: DateTime**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Das Datum, an dem die Protokolldatei zuletzt geändert wurde.|  
|Logfile size|Datentyp: **UInt32**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Die Größe der Protokolldatei in Bytes.|  
|Name|Datentyp: **Zeichenfolge**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> Qualifizierer: Schlüssel<br /><br /> <br /><br /> Der Name der Protokolldatei.|  
  
## <a name="remarks"></a>Bemerkungen  
  
|||  
|-|-|  
|MOF|Sqlmgmprovider xpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Namespace|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden Informationen zu allen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Protokolldateien in einer angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abgerufen. Um das Beispiel auszuführen, ersetzen \<Sie *Instance_Name*> durch den Namen der Instanz, z. b. "instance1".  
  
```  
on error resume next  
set strComputer = "."  
set objWMIService = GetObject("winmgmts:\\.\root\Microsoft\SqlServer\ComputerManagement10")  
set LogFiles = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogFile WHERE InstanceName = '<Instance_Name>'")  
  
For Each logFile in LogFiles  
  
WScript.Echo "Instance Name:  " & logFile.InstanceName & vbNewLine _  
    & "Log File Name:  " & logFile.Name & vbNewLine _  
    & "Archive Number: " & logFile.ArchiveNumber & vbNewLine _  
    & "Log File Size:  " & logFile.LogFileSize & " bytes" & vbNewLine _  
    & "Last Modified:  " & logFile.LastModified & vbNewLine _  
  
Next   
```  
  
## <a name="comments"></a>Kommentare  
 Wenn *instanceName* nicht in der WQL-Anweisung angegeben wird, gibt die Abfrage Informationen für die Standard Instanz zurück. Die folgende WQL-Anweisung gibt z. B. Informationen zu allen Protokolldateien der Standardinstanz (MSSQLSERVER) zurück.  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a>Sicherheit  
 Zum Herstellen einer Verbindung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit einer Protokolldatei über WMI müssen Sie sowohl auf dem lokalen Computer als auch auf dem Remote Computer über die folgenden Berechtigungen verfügen:  
  
-   Lesen Sie den Zugriff auf den WMI-Namespace **root\Microsoft\SqlServer\ComputerManagement10** . Standardmäßig verfügt jeder Benutzer durch die Berechtigung Konto aktivieren über Lesezugriff.  
  
    > [!NOTE]  
    >  Weitere Informationen zum Überprüfen von WMI-Berechtigungen finden Sie im Abschnitt "Sicherheit" des Themas [Anzeigen von Offline Protokolldateien](../../relational-databases/logs/view-offline-log-files.md).  
  
-   Leseberechtigung für den Ordner mit den Fehlerprotokollen. Standardmäßig befinden sich die Fehlerprotokolle im folgenden Pfad (wobei \< *Laufwerk>* das Laufwerk darstellt, auf dem Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert \<haben, und *instanceName*> den Namen der Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von darstellt):  
  
     **Laufwerk>: \Programme\Microsoft SQL server\mssql11. \<** **\< InstanceName> \MSSQL\LOG**  
  
 Wenn Sie eine Verbindung über eine Firewall herstellen, stellen Sie sicher, dass in der Firewall für WMI auf Remotezielcomputern eine Ausnahme festgelegt ist. Weitere Informationen finden Sie unter [Herstellen einer Remote Verbindung mit WMI ab Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sqlerrorlogevent-Klasse](../../relational-databases/wmi-provider-configuration-classes/sqlerrorlogevent-class.md)   
 [Anzeigen von Offlineprotokolldateien](../../relational-databases/logs/view-offline-log-files.md)  
  
  
