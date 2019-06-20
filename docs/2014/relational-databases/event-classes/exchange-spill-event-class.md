---
title: Exchange Spill-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Exchange Spill event class
ms.assetid: fb876cec-f88d-4975-b3fd-0fb85dc0a7ff
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0220e81325345e84524ec0218dbaff7d6143bdd8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62663675"
---
# <a name="exchange-spill-event-class"></a>Exchange Spill-Ereignisklasse
  Die **Exchange Spill** -Ereignisklasse gibt an, dass die Kommunikationspuffer in einem parallelen Abfrageplan vorübergehend in die **tempdb** -Datenbank geschrieben wurden. Dies tritt nur selten auf, und auch nur, wenn ein Abfrageplan mehrere Bereichsscans hat.  
  
 Normalerweise verfügt die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfrage, die diese Bereichsscans generiert, über viele BETWEEN-Operatoren, wobei jeder dieser Operatoren einen Zeilenbereich aus einer Tabelle oder aus einem Index auswählt. Alternativ können Sie mehrere Bereiche, die mit Ausdrücken wie abrufen (T.a > 10 AND T.a \< 20) oder (T.a > 100 AND T.a \< 120). Darüber hinaus müssen die Abfragepläne erfordern, dass diese Bereiche der Reihenfolge nach gescannt werden. Dies geschieht aufgrund einer ORDER BY-Klausel für T.a oder weil ein Iterator im Plan erfordert, dass die Tupel in einer bestimmten Reihenfolge verwendet werden.  
  
 Wenn ein Abfrageplan für eine solche Abfrage mehrere **Parallelism** -Operatoren aufweist, werden die von den **Parallelism** -Operatoren verwendeten Speicherkommunikationspuffer vollständig gefüllt. Das kann dazu führen, dass der Ausführungsfortschritt der Abfrage beendet wird. In dieser Situation schreibt einer der **Parallelism** -Operatoren seinen Ausgabepuffer in **tempdb** (dieser Vorgang wird *Austauschüberlauf*genannt), damit Zeilen aus einigen seiner Eingabepuffer verwendet werden können. Letztendlich werden die übergelaufenen Zeilen wieder an den Consumer zurückgegeben, wenn dieser in der Lage ist, sie zu verarbeiten.  
  
 In seltenen Fällen können mehrere Austauschüberläufe innerhalb desselben Ausführungsplans auftreten, wodurch die Abfrage verlangsamt ausgeführt wird. Wenn Sie mehr als fünf Überläufe in der Ausführung desselben Abfrageplans feststellen, wenden Sie sich an einen Supportmitarbeiter.  
  
 Austauschüberläufe sind mitunter vorübergehend und sind möglicherweise nach geänderter Datenverteilung nicht mehr vorhanden.  
  
 Es gibt mehrere Möglichkeiten, Austauschüberläufe zu vermeiden:  
  
-   Geben Sie die ORDER BY-Klausel nicht an, wenn das Resultset nicht sortiert vorliegen muss.  
  
-   Wenn ORDER BY erforderlich ist, entfernen Sie die Spalte, die an mehreren Bereichsscans teilnimmt (T.a im oben angeführten Beispiel), aus der ORDER BY-Klausel.  
  
-   Durch das Verwenden eines Indexhinweises wird der Optimierer gezwungen, für die betreffende Tabelle eine andere Zugriffsmethode zu verwenden.  
  
-   Schreiben Sie die Abfrage neu, um einen anderen Abfrageausführungsplan zu erstellen.  
  
-   Erzwingen Sie die serielle Ausführung der Abfrage, indem Sie die Option MAXDOP = 1 am Ende der Abfrage oder des Indexvorgangs hinzufügen. Weitere Informationen finden Sie unter [Konfigurieren der Serverkonfigurationsoption Max. Grad an Parallelität](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) und [Konfigurieren von Parallelindexvorgängen](../indexes/configure-parallel-index-operations.md).  
  
> [!IMPORTANT]  
>  Zur Bestimmung der Stelle, an der das **Exchange Spill** -Ereignis auftritt, wenn der Abfrageoptimierer einen Ausführungsplan generiert, sollte Sie außerdem eine Showplan-Ereignisklasse in der Ablaufverfolgung sammeln. Abgesehen von den Ereignisklassen **Showplan Text** und **Showplan Text (Unencoded)** , die keine Knoten-ID zurückgeben, können Sie jede der Showplan-Ereignisklassen auswählen. Knoten-IDs in Showplans identifizieren jeden Vorgang, den der Abfrageoptimierer beim Generieren eines Abfrageausführungsplans ausführt. Diese Vorgänge werden als Operatoren bezeichnet. Jeder Operator in einem Showplan verfügt über eine Knoten-ID. Die Spalte **ObjectID** für **Exchange Spill** -Ereignisse entspricht der Knoten-ID in Showplans, sodass Sie den Operator bzw. den Vorgang ermitteln können, der den Fehler verursacht.  
  
## <a name="exchange-spill-event-class-data-columns"></a>Datenspalten für Exchange Spill-Ereignisklassen  
  
|Datenspaltenname|Datentyp|Beschreibung|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|**ClientProcessID**|**int**|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Client die Clientprozess-ID angibt.|9|Ja|  
|**DatabaseID**|**int**|Die ID der Datenbank, die durch die USE *database* -Anweisung angegeben wurde, bzw. die ID der Standarddatenbank, wenn für eine bestimmte Instanz keine USE *database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die **ServerName** -Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|**DatabaseName**|**nvarchar**|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|**EventClass**|**int**|Ereignistyp = 127.|27|Nein|  
|**EventSequence**|**int**|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|**EventSubClass**|**int**|Der Typ der Ereignisunterklasse.<br /><br /> 1=Beginn des Überlaufs<br /><br /> 2=Ende des Überlaufs|21|Ja|  
|**GroupID**|**int**|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Ja|  
|**HostName**|**nvarchar**|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname vom Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|**IsSystem**|**int**|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|**LoginName**|**nvarchar**|Anmeldename des Benutzers (Entweder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherheitsanmeldung oder Windows-Anmeldeinformationen im Format *\<DOMAIN>\\<username\>* ).|11|Ja|  
|**LoginSid**|**image**|Sicherheits-ID (SID) des angemeldeten Benutzers. Sie finden diese Informationen in der **syslogins** -Tabelle der **master** -Datenbank. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Ja|  
|**NTDomainName**|**nvarchar**|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|**NTUserName**|**nvarchar**|Windows-Benutzername.|6|Ja|  
|**ObjectID**|**int**|Vom System zugewiesene ID des Objekts. Entspricht der Knoten-ID in Showplans.|22|Ja|  
|**RequestID**|**int**|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|**ServerName**|**nvarchar**|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|**SessionLoginName**|**nvarchar**|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie z. B. mit Login1 eine Verbindung zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und mit Login2 eine Anweisung ausführen, zeigt **SessionLoginName** Login1 an, und **LoginName** zeigt Login2 an. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|**SPID**|**int**|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|**StartTime**|**datetime**|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|**TransactionID**|**bigint**|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|**XactSequence**|**bigint**|Das Token, das die aktuelle Transaktion beschreibt.|50|Ja|  
  
## <a name="see-also"></a>Siehe auch  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Festlegen von Indexoptionen](../indexes/set-index-options.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)  
  
  
