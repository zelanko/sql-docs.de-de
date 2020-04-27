---
title: Sqlerrorlogfile-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
ms.assetid: 2b83ae4a-c0d4-414c-b6e5-a41ec7c13159
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 8c5c6f1998cffc268a57318e0124f74d3411a3b4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63249317"
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
 Die sqlerrorlogfile-Klasse definiert die folgenden Eigenschaften.  
  
|||  
|-|-|  
|Archivenreiber|Datentyp: `uint32`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Die Archivnummer für die Protokolldatei.|  
|InstanceName|Datentyp: `string`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> Qualifizierer: Schlüssel<br /><br /> <br /><br /> Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die die Protokolldatei enthält.|  
|LastModified|Datentyp: `datetime`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Das Datum, an dem die Protokolldatei zuletzt geändert wurde.|  
|Logfile size|Datentyp: `uint32`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Die Größe der Protokolldatei in Bytes.|  
|name|Datentyp: `string`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> Qualifizierer: Schlüssel<br /><br /> <br /><br /> Der Name der Protokolldatei.|  
  
## <a name="remarks"></a>Hinweise  
  
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
    >  Weitere Informationen zum Überprüfen von WMI-Berechtigungen finden Sie im Abschnitt "Sicherheit" des Themas [Anzeigen von Offline Protokolldateien](../logs/view-offline-log-files.md).  
  
-   Leseberechtigung für den Ordner mit den Fehlerprotokollen. Standardmäßig befinden sich die Fehlerprotokolle im folgenden Pfad (wobei \< *Laufwerk>* das Laufwerk darstellt, auf dem Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert \<haben, und *instanceName*> den Namen der Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von darstellt):  
  
     **Laufwerk>: \Programme\Microsoft SQL server\mssql11. \<** **\< InstanceName> \MSSQL\LOG**  
  
 Wenn Sie eine Verbindung über eine Firewall herstellen, stellen Sie sicher, dass in der Firewall für WMI auf Remotezielcomputern eine Ausnahme festgelegt ist. Weitere Informationen finden Sie unter [Herstellen einer Remote Verbindung mit WMI ab Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sqlerrorlogevent-Klasse](sqlerrorlogevent-class.md)   
 [Anzeigen von Offlineprotokolldateien](../logs/view-offline-log-files.md)  
  
  
