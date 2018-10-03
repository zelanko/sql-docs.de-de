---
title: 'QN: Parameter Table (Ereignisklasse) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], QN:Parameter Table
ms.assetid: 292da1ed-4c7e-4bd2-9b84-b9ee09917724
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ae4921f764819ca0210fcd4c71cf57ebcb588f57
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48162310"
---
# <a name="qnparameter-table-event-class"></a>QN:Parameter Table (Ereignisklasse)
  Das QN:Parameter Table-Ereignis übermittelt Informationen zu Vorgängen, die notwendig sind, um interne Tabellen, in denen Parameterinformationen gespeichert sind, zu erstellen und abzulegen und den Verweiszähler zu erhalten. Dieses Ereignis übermittelt außerdem die interne Aktivität zum Zurücksetzen des Verwendungszählers für eine Parametertabelle.  
  
## <a name="qnparameter-table-event-class-data-columns"></a>Datenspalten der QN:Parameter Table-Ereignisklasse  
  
|Datenspalte|Typ|Description|Spaltennummer|Filterbar|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|`nvarchar`|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Benutzerkontensteuerung|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Benutzerkontensteuerung|  
|DatabaseID|`int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database*-Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die Server Name-Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|DatabaseName|`nvarchar`|Der Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Benutzerkontensteuerung|  
|EventClass|`Int`|Ereignistyp = 200.|27|nein|  
|EventSequence|`int`|Die Sequenznummer für dieses Ereignis.|51|nein|  
|EventSubClass|`nvarchar`|Der Typ der Ereignisunterklasse, der weitere Informationen zu jeder Ereignisklasse liefert. Diese Spalte kann die folgenden Werte enthalten:<br /><br /> Tabelle erstellt: Gibt an, in der Datenbank eine Parametertabelle erstellt wurde.<br /><br /> Tabelle Löschversuch: Gibt an, dass die Datenbank versucht hat, automatisch um Ressourcen freizugeben eine nicht verwendete Parametertabelle zu löschen.<br /><br /> Table Drop Versuch ist fehlgeschlagen: Gibt an, dass die Datenbank versucht, eine nicht verwendete Parametertabelle zu löschen. [!INCLUDE[ssDE](../../includes/ssde-md.md)] plant die Löschung der Parametertabelle automatisch neu, um Ressourcen frei zu geben.<br /><br /> Abgelegte Tabelle: Gibt an, dass die Datenbank erfolgreich eine Parametertabelle gelöscht.<br /><br /> Tabelle, die angeheftet: Gibt an, dass die Parametertabelle für die aktuelle Verwendung durch die interne Verarbeitung markiert ist.<br /><br /> Table unpinned: Gibt an, dass die Fixierung der Tabelle aufgehoben wurde. Die Tabelle wird von der internen Verarbeitung nicht mehr verwendet.<br /><br /> Anzahl von Benutzern, die inkrementiert: Gibt an, dass die Anzahl von Abfragebenachrichtigungsabonnements, die auf eine Parametertabelle verweisen erhöht hat.<br /><br /> Anzahl der Benutzer wieder um eins erniedrigt: Gibt an, dass die Anzahl von Abfragebenachrichtigungsabonnements, die auf eine Parametertabelle verweisen verringert hat.<br /><br /> LRU Counter Reset: Gibt an, dass der Verwendungszähler für die Parametertabelle zurückgesetzt wurde.<br /><br /> Task ' Verlaufscleanup ' gestartet: Gibt an, wann der Cleanupvorgang für alle Abonnements in dieser Parametertabelle begonnen wurde. Dieser Vorgang findet statt, wenn die Datenbank gestartet oder eine den Abonnements dieser Parametertabelle zugrunde liegende Tabelle gelöscht wird.<br /><br /> Task "Wartungscleanup" abgeschlossen: Gibt an, wann der Cleanupvorgang für alle Abonnements in dieser Parametertabelle beendet wurde.|21|Benutzerkontensteuerung|  
|GroupID|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Benutzerkontensteuerung|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Benutzerkontensteuerung|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist.<br /><br /> 0 = Benutzer<br /><br /> 1 = System|60|nein|  
|LoginName|`nvarchar`|Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder Windows-Anmeldeinformationen im Format *DOMAIN*\\*username*).|11|nein|  
|LoginSID|`image`|Die Sicherheits-ID (SID, Security Identification Number) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Benutzerkontensteuerung|  
|NTDomainName|`nvarchar`|Die Windows-Domäne, der der Benutzer angehört.|7|Benutzerkontensteuerung|  
|NTUserName|`nvarchar`|Der Name des Benutzers, der Besitzer der Verbindung ist, die dieses Ereignis generiert hat.|6|Benutzerkontensteuerung|  
|RequestID|`int`|Der Bezeichner der Anforderung, die die Anweisung enthält.|49|Benutzerkontensteuerung|  
|ServerName|`nvarchar`|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn beispielsweise eine Anwendung mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellt und eine Anweisung als Login2 ausführt, zeigt SessionLoginName "Login1" an, und LoginName zeigt "Login2" an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Benutzerkontensteuerung|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Benutzerkontensteuerung|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Benutzerkontensteuerung|  
|TextData|`ntext`|Gibt ein XML-Dokument mit spezifischen Informationen zu diesem Ereignis zurück. Dieses Dokument stimmt mit dem XML-Schema überein, das auf der Seite [SQL Server Query Notification Profiler Event Schema](http://go.microsoft.com/fwlink/?LinkId=63331) (in englischer Sprache) zur Verfügung gestellt wird.|1|Benutzerkontensteuerung|  
  
  
