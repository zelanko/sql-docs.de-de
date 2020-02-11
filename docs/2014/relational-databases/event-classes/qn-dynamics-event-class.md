---
title: QN:Dynamics-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], QN:Dynamics
ms.assetid: 3c1ffa0c-c9e5-40a6-a26b-28339f60ebc3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eb59abed8be5649d9258bce0f279222e4498b547
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63035702"
---
# <a name="qndynamics-event-class"></a>QN:Dynamics (Ereignisklasse)
  Die QN:Dynamics-Ereignisklasse übermittelt Informationen zu Hintergrundaktivitäten, die von [!INCLUDE[ssDE](../../includes/ssde-md.md)] zur Unterstützung von Abfragebenachrichtigungen durchgeführt werden. In [!INCLUDE[ssDE](../../includes/ssde-md.md)]werden Abonnementtimeouts, auszulösende ausstehende Abonnements und das Löschen von Parametertabellen in einem Hintergrundthread überwacht.  
  
## <a name="qndynamics-event-class-data-columns"></a>Datenspalten der QN:Dynamics-Ereignisklasse  
  
|Datenspalte|type|BESCHREIBUNG|Spaltennummer|Filterbar|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|`nvarchar`|Der Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Ja|  
|DatabaseID|`int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database*-Anweisung ausgegeben wurde. 
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die Server Name-Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|DatabaseName|`nvarchar`|Der Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|EventClass|`int`|Ereignistyp = 202|27|Nein|  
|EventSequence|`int`|Die Sequenznummer für dieses Ereignis.|51|Nein|  
|EventSubClass|`nvarchar`|Der Typ der Ereignisunterklasse, der weitere Informationen zu jeder Ereignisklasse liefert. Diese Spalte kann die folgenden Werte enthalten:<br /><br /> Clock Run Started: gibt an, dass der Hintergrund Thread [!INCLUDE[ssDE](../../includes/ssde-md.md)] in, der abgelaufene Parameter Tabellen für den Bereinigung plant, gestartet wurde.<br /><br /> Uhr ausführen abgeschlossen: gibt an, dass der Hintergrund Thread [!INCLUDE[ssDE](../../includes/ssde-md.md)] in, der abgelaufene Parameter Tabellen für den Bereinigung plant, abgeschlossen ist.<br /><br /> Master cleanup task started: Gibt an, wann der Cleanup (Garbage Collection) zum Entfernen abgelaufener Abfragebenachrichtigungsabonnements beginnt.<br /><br /> Master cleanup task finished: Gibt an, wann der Cleanup (Garbage Collection) zum Entfernen abgelaufener Abfragebenachrichtigungsabonnements endet.<br /><br /> Master Bereinigung Task übersprungen: gibt an, [!INCLUDE[ssDE](../../includes/ssde-md.md)] dass keine Bereinigung (Garbage Collection) zum Entfernen abgelaufener Abfrage Benachrichtigungs Abonnement Daten durchgeführt hat.|21|Ja|  
|GroupID|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Ja|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist.<br /><br /> 0 = Benutzer<br /><br /> 1 = System|60|Nein|  
|LoginName|`nvarchar`|Der Anmelde Name des Benutzers (Anmeldung der- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sicherheit oder Windows-Anmelde Informationen im Format *DOMAIN\username*).|11|Nein|  
|LoginSID|`image`|Die Sicherheits-ID (SID, Security Identification Number) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|NTDomainName|`nvarchar`|Die Windows-Domäne, der der Benutzer angehört.|7|Ja|  
|NTUserName|`nvarchar`|Der Name des Benutzers, der Besitzer der Verbindung ist, die dieses Ereignis generiert hat.|6|Ja|  
|RequestID|`int`|Der Bezeichner der Anforderung, die die Anweisung enthält.|49|Ja|  
|Servername|`nvarchar`|Der Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn beispielsweise eine Anwendung mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellt und eine Anweisung als Login2 ausführt, zeigt SessionLoginName "Login1" an, und LoginName zeigt "Login2" an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|TextData|`ntext`|Gibt ein XML-Dokument mit spezifischen Informationen zu diesem Ereignis zurück. Dieses Dokument stimmt mit dem XML-Schema überein, das auf der Seite [SQL Server Query Notification Profiler Event Schema](https://go.microsoft.com/fwlink/?LinkId=63331) (in englischer Sprache) zur Verfügung gestellt wird.|1|Ja|  
  
  
