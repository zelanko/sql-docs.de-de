---
title: SqlErrorLogEvent Class | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SqlErrorLogEvent class
- SqlErrorLogFile class
ms.assetid: bde6c467-38d0-4766-a7af-d6c9d6302b07
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 95588b82a36bb5d7d5d520a5f54ca968a9198112
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057118"
---
# <a name="sqlerrorlogevent-class"></a>SqlErrorLogEvent-Klasse
  Stellt Eigenschaften zum Anzeigen von Ereignissen in einer angegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Protokolldatei bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
class SQLErrorLogEvent   
{  
   stringFileName;  
   stringInstanceName;  
   datetimeLogDate;  
   stringMessage;  
   stringProcessInfo;  
};  
```  
  
## <a name="properties"></a>Eigenschaften  
 SQLErrorLogEvent-Klasse definiert die folgenden Eigenschaften.  
  
|||  
|-|-|  
|FileName|Datentyp: `string`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Der Name der Fehlerprotokolldatei.|  
|InstanceName|Datentyp: `string`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> Qualifizierer: Schlüssel<br /><br /> Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die die Protokolldatei enthält.|  
|LogDate|Datentyp: `datetime`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> Qualifizierer: Schlüssel<br /><br /> <br /><br /> Datum und Uhrzeit, zu denen das Ereignis in der Protokolldatei aufgezeichnet wurde.|  
|MessageBox|Datentyp: `string`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Die Ereignismeldung.|  
|ProcessInfo|Datentyp: `string`<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Informationen zur SPID (Source Server Process ID, Quellserverprozess-ID) für das Ereignis.|  
  
## <a name="remarks"></a>Hinweise  
  
|||  
|-|-|  
|MOF|Sqlmgmproviderxpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Namespace|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Werte für alle protokollierten Ereignisse in einer angegebenen Protokolldatei abgerufen werden. Ersetzen Sie zum Ausführen des Beispiels \< *Instance_Name*> durch den Namen der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], z. B. "Instance1", und Ersetzen Sie 'Dateiname' durch den Namen der Fehlerprotokolldatei, z. B. "ErrorLog. 1".  
  
```  
on error resume next  
strComputer = "."  
Set objWMIService = GetObject("winmgmts:" _  
    & "{impersonationLevel=impersonate}!\\" _  
    & strComputer & "\root\MICROSOFT\SqlServer\ComputerManagement10")  
set logEvents = objWmiService.ExecQuery("SELECT * FROM SqlErrorLogEvent WHERE InstanceName = '<Instance_Name>' AND FileName = 'File_Name'")  
  
For Each logEvent in logEvents  
WScript.Echo "Instance Name: " & logEvent.InstanceName & vbNewLine _  
    & "Log Date: " & logEvent.LogDate & vbNewLine _  
    & "Log File Name: " & logEvent.FileName & vbNewLine _  
    & "Process Info: " & logEvent.ProcessInfo & vbNewLine _  
    & "Message: " & logEvent.Message & vbNewLine _  
  
Next  
```  
  
## <a name="comments"></a>Kommentare  
 Wenn *InstanceName* oder *FileName* nicht finden Sie in der WQL-Anweisung, die Abfrage gibt Informationen für die Standardinstanz und der aktuelle zurück [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Protokolldatei. Die folgende WQL-Anweisung gibt z. B. alle Protokollereignisse aus der aktuellen Protokolldatei (ERRORLOG) auf der Standardinstanz (MSSQLSERVER) zurück.  
  
```  
"SELECT * FROM SqlErrorLogEvent"  
```  
  
## <a name="security"></a>Security  
 Verbindung mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Protokolldatei über WMI, benötigen Sie die folgenden Berechtigungen für die lokale und remote-Computer:  
  
-   Lesezugriff auf die **Root\Microsoft\SqlServer\ComputerManagement10** WMI-Namespace. Standardmäßig verfügt jeder Benutzer durch die Berechtigung Konto aktivieren über Lesezugriff.  
  
-   Leseberechtigung für den Ordner mit den Fehlerprotokollen. Standardmäßig werden Fehlerprotokolle unter dem folgenden Pfad (, in denen \< *Laufwerk >* steht für das Laufwerk, auf dem Sie installiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und \< *InstanceName*> ist der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):  
  
     **\<Laufwerk >: \Programme\Microsoft SQL Server\MSSQL12** **.\< InstanceName > \MSSQL\Log**  
  
 Wenn Sie eine Verbindung über eine Firewall herstellen, stellen Sie sicher, dass in der Firewall für WMI auf Remotezielcomputern eine Ausnahme festgelegt ist. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit WMI Remotely Starting with Windows Vista](http://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>Siehe auch  
 [SqlErrorLogFile-Klasse](sqlerrorlogfile-class.md)   
 [Anzeigen von Offlineprotokolldateien](../logs/view-offline-log-files.md)  
  
  