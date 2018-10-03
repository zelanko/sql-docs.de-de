---
title: SqlErrorLogFile-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 1cd24b1717bca086bf1419a2df3b44b57104d1f7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48226610"
---
# <a name="sqlerrorlogfile-class"></a>SqlErrorLogFile-Klasse
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
 SQLErrorLogFile-Klasse definiert die folgenden Eigenschaften an.  
  
|||  
|-|-|  
|ArchiveNumber|Datentyp: `uint32`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Die Archivnummer für die Protokolldatei.|  
|InstanceName|Datentyp: `string`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> Qualifizierer: Schlüssel<br /><br /> <br /><br /> Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die die Protokolldatei enthält.|  
|LastModified|Datentyp: `datetime`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Das Datum, an dem die Protokolldatei zuletzt geändert wurde.|  
|LogFileSize|Datentyp: `uint32`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Die Größe der Protokolldatei in Bytes.|  
|Name|Datentyp: `string`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> Qualifizierer: Schlüssel<br /><br /> <br /><br /> Der Name der Protokolldatei.|  
  
## <a name="remarks"></a>Hinweise  
  
|||  
|-|-|  
|MOF|Sqlmgmprovider xpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Namespace|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden Informationen zu allen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Protokolldateien in einer angegebenen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abgerufen. Um das Beispiel auszuführen, ersetzen \< *Instance_Name*> durch den Namen der Instanz ein, z. B. 'Instanz1'.  
  
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
 Wenn *InstanceName* wurde nicht angegeben in der WQL-Anweisung, die Abfrage gibt Informationen für die Standardinstanz zurück. Die folgende WQL-Anweisung gibt z. B. Informationen zu allen Protokolldateien der Standardinstanz (MSSQLSERVER) zurück.  
  
```  
"SELECT * FROM SqlErrorLogFile"  
```  
  
## <a name="security"></a>Security  
 Zum Herstellen einer Verbindung mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Protokolldatei über WMI, benötigen Sie die folgenden Berechtigungen für die lokale und remote-Computer:  
  
-   Lesezugriff auf die **Root\Microsoft\SqlServer\ComputerManagement10** WMI-Namespace. Standardmäßig verfügt jeder Benutzer durch die Berechtigung Konto aktivieren über Lesezugriff.  
  
    > [!NOTE]  
    >  Informationen zum Überprüfen von WMI-Berechtigungen finden Sie unter Abschnitt "Sicherheit" des Themas [Anzeigen von Offlineprotokolldateien](../logs/view-offline-log-files.md).  
  
-   Leseberechtigung für den Ordner mit den Fehlerprotokollen. Standardmäßig ist der Fehler Protokolle unter folgendem Pfad befinden (, in denen \< *Laufwerk >* stellt dar, das Laufwerk, auf dem Sie installiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und \< *InstanceName*> ist der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):  
  
     **\<Laufwerk >: \Programme\Microsoft SQL Server\MSSQL11** **.\< Instanzname > \MSSQL\Log**  
  
 Wenn Sie eine Verbindung über eine Firewall herstellen, stellen Sie sicher, dass in der Firewall für WMI auf Remotezielcomputern eine Ausnahme festgelegt ist. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit WMI Remotely Starting with Windows Vista](http://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>Siehe auch  
 [SqlErrorLogEvent-Klasse](sqlerrorlogevent-class.md)   
 [Anzeigen von Offlineprotokolldateien](../logs/view-offline-log-files.md)  
  
  
