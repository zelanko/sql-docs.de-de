---
title: CursorImplicitConversion (Ereignisklasse) | Microsoft-Dokumentation
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
- CursorImplicitConversion event class
ms.assetid: 44d12e23-146a-42e6-bb38-1f2f6a035bad
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4bb7b67ebbe95181b1b25797051e639fb1b3e4b2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48187500"
---
# <a name="cursorimplicitconversion-event-class"></a>CursorImplicitConversion (Ereignisklasse)
  Die **CursorImplicitConversion** -Ereignisklasse beschreibt Ereignisse zu impliziten Cursorkonvertierungen, die bei API-Cursorn (Application Programming Interfaces, Schnittstellen für Anwendungsprogrammierung) oder [!INCLUDE[tsql](../../includes/tsql-md.md)] -Cursorn auftreten. Ereignisse zu impliziten Cursorkonvertierungen treten auf, wenn [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] eine Transact-SQL-Anweisung ausführt, die von Servercursorn des angeforderten Typs nicht unterstützt wird. [!INCLUDE[ssDE](../../includes/ssde-md.md)] gibt einen Fehler zurück, der anzeigt, dass sich der Cursortyp geändert hat.  
  
 Schließen Sie die **CursorImplicitConversion** -Ereignisklasse in Ablaufverfolgungen ein, die die Leistung von Cursorn aufzeichnen.  
  
 Wenn diese Ereignisklasse in eine Ablaufverfolgung eingeschlossen wird, hängt der Aufwand davon ab, wie oft Cursor, die die implizierte Konvertierung erfordern, für die Datenbank während der Ablaufverfolgung verwendet werden. Wenn Cursor sehr häufig verwendet werden, kann die Ablaufverfolgung die Leistung erheblich beeinträchtigen.  
  
## <a name="cursorimplicitconversion-event-class-data-columns"></a>Datenspalten der CursorImplicitConversion-Ereignisklasse  
  
|Datenspaltenname|Datentyp|Description|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Benutzerkontensteuerung|  
|**BinaryData**|**image**|Resultierender Cursortyp. Die Werte sind:<br /><br /> 1 = Keyset<br /><br /> 2 = Dynamisch<br /><br /> 4 = Vorwärtscursor<br /><br /> 8 = Statisch<br /><br /> 16 = Schneller Vorlauf|2|Benutzerkontensteuerung|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Benutzerkontensteuerung|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE *Datenbank* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *Datenbank*-Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Benutzerkontensteuerung|  
|**DatabaseName**|**nvarchar**|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Benutzerkontensteuerung|  
|**EventClass**|**int**|Typ des aufgezeichneten Ereignisses = 76.|27|nein|  
|**EventSequence**|**int**|Die Sequenz der **CursorClose** -Ereignisklasse im Stapel.|51|nein|  
|**GroupID**|**int**|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Benutzerkontensteuerung|  
|**Handle**|**int**|Das Handle des Objekts, auf das im Ereignis verwiesen wird.|33|Benutzerkontensteuerung|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Benutzerkontensteuerung|  
|**IntegerData**|**int**|Angeforderter Cursortyp. Die Werte sind:<br /><br /> 1 = Keyset<br /><br /> 2 = Dynamisch<br /><br /> 4 = Vorwärtscursor<br /><br /> 8 = Statisch<br /><br /> 16 = Schneller Vorlauf|25|nein|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Benutzerkontensteuerung|  
|**LoginName**|**nvarchar**|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Benutzerkontensteuerung|  
|**LoginSid**|**image**|Die Sicherheits-ID (Security Identifier, SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Benutzerkontensteuerung|  
|**NTDomainName**|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|Benutzerkontensteuerung|  
|**NTUserName**|**nvarchar**|Windows-Benutzername.|6|Benutzerkontensteuerung|  
|**RequestID**|**int**|Die Anforderungs-ID der impliziten Konvertierung.|49|Benutzerkontensteuerung|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|nein|  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Benutzerkontensteuerung|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Benutzerkontensteuerung|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Benutzerkontensteuerung|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Benutzerkontensteuerung|  
|**XactSequence**|**bigint**|Das Token, das die aktuelle Transaktion beschreibt.|50|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
