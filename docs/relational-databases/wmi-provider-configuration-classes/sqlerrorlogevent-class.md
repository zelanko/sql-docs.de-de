---
title: SqlErrorLogEvent-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
helpviewer_keywords:
- SqlErrorLogEvent class
- SqlErrorLogFile class
ms.assetid: bde6c467-38d0-4766-a7af-d6c9d6302b07
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 02bf982b6b154d99c5f3f153550c8531f23afa72
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47669658"
---
# <a name="sqlerrorlogevent-class"></a>SqlErrorLogEvent-Klasse
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
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
 SQLErrorLogEvent-Klasse definiert die folgenden Eigenschaften an.  
  
|||  
|-|-|  
|FileName|Datentyp: **Zeichenfolge**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Der Name der Fehlerprotokolldatei.|  
|InstanceName|Datentyp: **Zeichenfolge**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> Qualifizierer: Schlüssel<br /><br /> Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die die Protokolldatei enthält.|  
|LogDate|Datentyp: **"DateTime"**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> Qualifizierer: Schlüssel<br /><br /> <br /><br /> Datum und Uhrzeit, zu denen das Ereignis in der Protokolldatei aufgezeichnet wurde.|  
|MessageBox|Datentyp: **Zeichenfolge**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Die Ereignismeldung.|  
|ProcessInfo|Datentyp: **Zeichenfolge**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Informationen zur SPID (Source Server Process ID, Quellserverprozess-ID) für das Ereignis.|  
  
## <a name="remarks"></a>Hinweise  
  
|||  
|-|-|  
|MOF|Sqlmgmproviderxpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Namespace|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Werte für alle protokollierten Ereignisse in einer angegebenen Protokolldatei abgerufen werden. Um das Beispiel auszuführen, ersetzen \< *Instance_Name*> durch den Namen der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], z. B. 'Instanz1', und Ersetzen Sie 'Dateiname' durch den Namen der Fehlerprotokolldatei, beispielsweise "ErrorLog. 1".  
  
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
 Wenn *InstanceName* oder *FileName* nicht finden Sie in der WQL-Anweisung, die Abfrage gibt Informationen für die Standardinstanz und der aktuelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Protokolldatei. Beispielsweise gibt die folgende WQL-Anweisung alle Protokollereignisse aus der aktuellen Protokolldatei (ERRORLOG) für die Standardinstanz (MSSQLSERVER) zurück.  
  
```  
"SELECT * FROM SqlErrorLogEvent"  
```  
  
## <a name="security"></a>Security  
 Zum Herstellen einer Verbindung mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Protokolldatei über WMI, benötigen Sie die folgenden Berechtigungen für die lokale und remote-Computer:  
  
-   Lesezugriff auf die **Root\Microsoft\SqlServer\ComputerManagement10** WMI-Namespace. Standardmäßig verfügt jeder Benutzer durch die Berechtigung Konto aktivieren über Lesezugriff.  
  
-   Leseberechtigung für den Ordner mit den Fehlerprotokollen. Standardmäßig ist der Fehler Protokolle unter folgendem Pfad befinden (, in denen \< *Laufwerk >* stellt dar, das Laufwerk, auf dem Sie installiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und \< *InstanceName*> ist der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]):  
  
     **\<Laufwerk >: \Programme\Microsoft SQL Server\MSSQL13** **.\< Instanzname > \MSSQL\Log**  
  
 Wenn Sie eine Verbindung über eine Firewall herstellen, stellen Sie sicher, dass in der Firewall für WMI auf Remotezielcomputern eine Ausnahme festgelegt ist. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit WMI Remotely Starting with Windows Vista](http://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>Siehe auch  
 [SqlErrorLogFile-Klasse](../../relational-databases/wmi-provider-configuration-classes/sqlerrorlogfile-class.md)   
 [Anzeigen von Offlineprotokolldateien](../../relational-databases/logs/view-offline-log-files.md)  
  
  
