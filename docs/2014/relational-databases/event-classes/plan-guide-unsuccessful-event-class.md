---
title: Plan Guide Unsuccessful (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Plan Guide Unsuccessful event class
ms.assetid: ef9759f8-5613-4884-9257-86b609313f69
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1f5355fc73acb76a65d81c142d57a826535b05ae
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075720"
---
# <a name="plan-guide-unsuccessful-event-class"></a>Plan Guide Unsuccessful (Ereignisklasse)
  Die Plan Guide Unsuccessful-Ereignisklasse zeigt an, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für eine Abfrage oder einen Batch mit Planhinweisliste keinen Ausführungsplan erzeugen konnte. Der Plan wurde stattdessen ohne die Planhinweisliste kompiliert. Dieses Ereignis wird ausgelöst, wenn die folgenden Voraussetzungen erfüllt sind:  
  
-   Der Batch/das Modul in der Planhinweislisten-Definition stimmt mit dem ausgeführten Batch überein.  
  
-   Die Abfrage in der Planhinweislisten-Definition stimmt mit der ausgeführten Abfrage überein.  
  
-   Die Hinweise in der Planhinweislisten-Definition, einschließlich des USE PLAN-Hinweises, konnten nicht auf die Abfrage bzw. den Batch angewendet werden. Das heißt, dass der kompilierte Abfrageplan die angegebenen Hinweise ignoriert hat und der Plan ohne die Planhinweisliste kompiliert wurde.  
  
 Dieses Ereignis kann auch durch eine ungültige Planhinweisliste ausgelöst werden. Überprüfen Sie die von der Abfrage bzw. dem Batch verwendete Planhinweisliste mit der [sys.fn_validate_plan_guide](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql) -Funktion, und berichtigen Sie den von der Funktion gemeldeten Fehler.  
  
 Dieses Ereignis ist in der Optimierungsvorlage von [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] enthalten.  
  
## <a name="plan-guide-unsuccessful-event-class-data-columns"></a>Datenspalten der Plan Guide Unsuccessful-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten gefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Benutzerkontensteuerung|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Benutzerkontensteuerung|  
|DatabaseID|`int`|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine angegebene Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die ServerName-Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|DatabaseName|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Benutzerkontensteuerung|  
|EventClass|`int`|Ereignistyp = 218.|27|nein|  
|EventSequence|`int`|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung|51|nein|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Benutzerkontensteuerung|  
|IsSystem|`int`|Gibt an, ob das Ereignis in einem Systemprozess oder einem Benutzerprozess aufgetreten ist: 1 = System, 0 = Benutzer.|60|Benutzerkontensteuerung|  
|LoginName|`nvarchar`|Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\\*Benutzername*).|11|Benutzerkontensteuerung|  
|LoginSid|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Sie finden diese Informationen in der [sys.server_principals](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql) -Katalogsicht bzw. in der [sys.sql_logins](/sql/relational-databases/system-catalog-views/sys-sql-logins-transact-sql) -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Benutzerkontensteuerung|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Benutzerkontensteuerung|  
|NTUserName|`nvarchar`|Windows-Benutzername.|6|Benutzerkontensteuerung|  
|ObjectID|`int`|Objekt-ID des Moduls, das kompiliert wurde, als die Planhinweisliste angewendet wurde. Falls die Planhinweisliste auf kein Modul angewendet wurde, wird diese Spalte auf NULL festgelegt.|22|Benutzerkontensteuerung|  
|RequestID|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|Benutzerkontensteuerung|  
|ServerName|`nvarchar`|Name der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Benutzerkontensteuerung|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Benutzerkontensteuerung|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Benutzerkontensteuerung|  
|TextData|`ntext`|Name der Planhinweisliste.|1|Benutzerkontensteuerung|  
|TransactionID|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Benutzerkontensteuerung|  
|XactSequence|`bigint`|Das Token, das die aktuelle Transaktion beschreibt.|50|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Siehe auch  
 [Plan Guide Successful (Ereignisklasse)](plan-guide-successful-event-class.md)   
 [Erweiterte Ereignisse](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sys.fn_validate_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
