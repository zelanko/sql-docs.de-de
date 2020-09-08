---
description: SqlErrorLogEvent-Klasse
title: SqlErrorLogEvent-Klasse
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- SqlErrorLogEvent class
- SqlErrorLogFile class
ms.assetid: bde6c467-38d0-4766-a7af-d6c9d6302b07
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ff086556b507c0d09750b7ab27671a7b1cfaf496
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89522148"
---
# <a name="sqlerrorlogevent-class"></a>SqlErrorLogEvent-Klasse
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]
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
 Die sqlerrorlogevent-Klasse definiert die folgenden Eigenschaften.  
  
| Eigenschaft | BESCHREIBUNG |
| -------- | ----------- |
|FileName|Datentyp: **Zeichenfolge**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Der Name der Fehlerprotokolldatei.|  
|InstanceName|Datentyp: **Zeichenfolge**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> Qualifizierer: Schlüssel<br /><br /> Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die die Protokolldatei enthält.|  
|LogDate|**Datentyp: DateTime**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> Qualifizierer: Schlüssel<br /><br /> <br /><br /> Datum und Uhrzeit, zu denen das Ereignis in der Protokolldatei aufgezeichnet wurde.|  
|Nachricht|Datentyp: **Zeichenfolge**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Die Ereignismeldung.|  
|ProcessInfo|Datentyp: **Zeichenfolge**<br /><br /> Zugriffstyp: Schreibgeschützt<br /><br /> <br /><br /> Informationen zur SPID (Source Server Process ID, Quellserverprozess-ID) für das Ereignis.|  
  
## <a name="remarks"></a>Hinweise  
  
| type | Name |
| ---- | ---- |
|MOF|Sqlmgmproviderxpsp2up.mof|  
|DLL|Sqlmgmprovider.dll|  
|Namespace|\root\Microsoft\SqlServer\ComputerManagement10|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Werte für alle protokollierten Ereignisse in einer angegebenen Protokolldatei abgerufen werden. Um das Beispiel auszuführen, ersetzen Sie \<*Instance_Name*> durch den Namen der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , z. b. "instance1", und ersetzen Sie "File_Name" durch den Namen der Fehlerprotokoll Datei (z. b. ' ErrorLog. 1 ').  
  
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
 Wenn *instanceName* oder *filename* nicht in der WQL-Anweisung angegeben wird, gibt die Abfrage Informationen für die Standard Instanz und die aktuelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Protokolldatei zurück. Die folgende WQL-Anweisung gibt z. B. alle Protokollereignisse aus der aktuellen Protokolldatei (ERRORLOG) für die Standardinstanz (MSSQLSERVER) zurück.  
  
```  
"SELECT * FROM SqlErrorLogEvent"  
```  
  
## <a name="security"></a>Sicherheit  
 Zum Herstellen einer Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Protokolldatei über WMI müssen Sie sowohl auf dem lokalen Computer als auch auf dem Remote Computer über die folgenden Berechtigungen verfügen:  
  
-   Lesen Sie den Zugriff auf den WMI-Namespace **root\Microsoft\SqlServer\ComputerManagement10** . Standardmäßig verfügt jeder Benutzer durch die Berechtigung Konto aktivieren über Lesezugriff.  
  
-   Leseberechtigung für den Ordner mit den Fehlerprotokollen. Standardmäßig befinden sich die Fehlerprotokolle unter dem folgenden Pfad (wobei \<*Drive> * das Laufwerk darstellt, auf dem Sie installiert haben, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und \<*InstanceName*> ist der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ):  
  
     ** \<Drive> : \Programme\Microsoft SQL server\mssql13** **. \<InstanceName> \MSSQL\LOG**  
  
 Wenn Sie eine Verbindung über eine Firewall herstellen, stellen Sie sicher, dass in der Firewall für WMI auf Remotezielcomputern eine Ausnahme festgelegt ist. Weitere Informationen finden Sie unter [Herstellen einer Remote Verbindung mit WMI ab Windows Vista](https://go.microsoft.com/fwlink/?LinkId=178848).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sqlerrorlogfile-Klasse](../../relational-databases/wmi-provider-configuration-classes/sqlerrorlogfile-class.md)   
 [Anzeigen von Offlineprotokolldateien](../../relational-databases/logs/view-offline-log-files.md)  
  
  
