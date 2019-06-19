---
title: CursorImplicitConversion (Ereignisklasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- CursorImplicitConversion event class
ms.assetid: 44d12e23-146a-42e6-bb38-1f2f6a035bad
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 28260dbc17ff506df50bf38d5b1f356995dc7235
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62686741"
---
# <a name="cursorimplicitconversion-event-class"></a>CursorImplicitConversion (Ereignisklasse)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Die **CursorImplicitConversion** -Ereignisklasse beschreibt Ereignisse zu impliziten Cursorkonvertierungen, die bei API-Cursorn (Application Programming Interfaces, Schnittstellen für Anwendungsprogrammierung) oder [!INCLUDE[tsql](../../includes/tsql-md.md)] -Cursorn auftreten. Ereignisse zu impliziten Cursorkonvertierungen treten auf, wenn [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] eine Transact-SQL-Anweisung ausführt, die von Servercursorn des angeforderten Typs nicht unterstützt wird. [!INCLUDE[ssDE](../../includes/ssde-md.md)] gibt einen Fehler zurück, der anzeigt, dass sich der Cursortyp geändert hat.  
  
 Schließen Sie die **CursorImplicitConversion** -Ereignisklasse in Ablaufverfolgungen ein, die die Leistung von Cursorn aufzeichnen.  
  
 Wenn diese Ereignisklasse in eine Ablaufverfolgung eingeschlossen wird, hängt der Aufwand davon ab, wie oft Cursor, die die implizierte Konvertierung erfordern, für die Datenbank während der Ablaufverfolgung verwendet werden. Wenn Cursor sehr häufig verwendet werden, kann die Ablaufverfolgung die Leistung erheblich beeinträchtigen.  
  
## <a name="cursorimplicitconversion-event-class-data-columns"></a>Datenspalten der CursorImplicitConversion-Ereignisklasse  
  
|Datenspaltenname|Datentyp|und Beschreibung|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|**BinaryData**|**image**|Resultierender Cursortyp. Die Werte sind:<br /><br /> 1 = Keyset<br /><br /> 2 = Dynamisch<br /><br /> 4 = Vorwärtscursor<br /><br /> 8 = Statisch<br /><br /> 16 = Schneller Vorlauf|2|Ja|  
|**ClientProcessID**|**ssNoversion**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Ja|  
|**DatabaseID**|**ssNoversion**|Die ID der Datenbank, die durch die USE *Datenbank* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *Datenbank*-Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|**DatabaseName**|**nvarchar**|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|**EventClass**|**ssNoversion**|Typ des aufgezeichneten Ereignisses = 76.|27|Nein|  
|**EventSequence**|**ssNoversion**|Die Sequenz der **CursorClose** -Ereignisklasse im Stapel.|51|Nein|  
|**GroupID**|**ssNoversion**|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Ja|  
|**Handle**|**ssNoversion**|Das Handle des Objekts, auf das im Ereignis verwiesen wird.|33|Ja|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|**IntegerData**|**ssNoversion**|Angeforderter Cursortyp. Die Werte sind:<br /><br /> 1 = Keyset<br /><br /> 2 = Dynamisch<br /><br /> 4 = Vorwärtscursor<br /><br /> 8 = Statisch<br /><br /> 16 = Schneller Vorlauf|25|Nein|  
|**IsSystem**|**ssNoversion**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|**LoginName**|**nvarchar**|Der Anmeldename des Benutzers ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheitsanmeldung oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|**LoginSid**|**image**|Die Sicherheits-ID (Security Identifier, SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der **sys.server_principals** -Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|**NTDomainName**|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|**NTUserName**|**nvarchar**|Windows-Benutzername.|6|Ja|  
|**RequestID**|**ssNoversion**|Die Anforderungs-ID der impliziten Konvertierung.|49|Ja|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung geöffnet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|**SPID**|**ssNoversion**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|**XactSequence**|**bigint**|Das Token, das die aktuelle Transaktion beschreibt.|50|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
