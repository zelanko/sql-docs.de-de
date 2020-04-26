---
title: Showplan All-Ereignisklasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Showplan All event class
ms.assetid: ee341319-c34a-43e3-ad33-6bfb1f85e314
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 487aaee17be13727f2c23de42b95afcc27b0b939
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/25/2020
ms.locfileid: "62662194"
---
# <a name="showplan-all-event-class"></a>Showplan All-Ereignisklasse
  Die Ereignisklasse „Showplan All“ tritt auf, wenn [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine SQL-Anweisung ausführt. Die enthaltenen Informationen sind eine Teilmenge der in der Showplan XML Statistics Profile- oder Showplan XML-Ereignisklasse verfügbaren Informationen.  
  
 Die Showplan All-Ereignisklasse zeigt vollständige Kompilierungszeitdaten an, sodass Ablaufverfolgungen, die Showplan All enthalten, einen deutlichen Aufwand an Verarbeitungsleistung verursachen können. Um diesen zu minimieren, sollten Sie die Verwendung dieser Ereignisklasse auf Ablaufverfolgungen beschränken, die bestimmte Probleme für kurze Zeiträume überwachen.  
  
 Wenn die Showplan All-Ereignisklasse in eine Ablaufverfolgung aufgenommen wird, muss die BinaryData-Datenspalte ausgewählt sein. Ist dies nicht der Fall, werden Informationen zu dieser Ereignisklasse nicht in der Ablaufverfolgung angezeigt.  
  
## <a name="showplan-all-event-class-data-columns"></a>Datenspalten der Showplan All-Ereignisklasse  
  
|Datenspaltenname|Datentyp|BESCHREIBUNG|Column ID|Filterbar|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Name der Clientanwendung, die die Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]hergestellt hat. Diese Spalte wird mit den Werten aufgefüllt, die von der Anwendung übergeben werden, und nicht mit dem angezeigten Namen des Programms.|10|Ja|  
|BinaryData|`image`|Geschätzte Kosten des Showplan-Texts.|2|Nein|  
|ClientProcessID|`int`|Die ID, die der Hostcomputer dem Prozess zuweist, in dem die Clientanwendung ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn die Clientprozess-ID durch den Client bereitgestellt wird.|9|Ja|  
|DatabaseID|`Int`|Die ID der Datenbank, die durch die use *Database* -Anweisung angegeben wurde, oder die Standarddatenbank, wenn für eine bestimmte Instanz keine use *Database* -Anweisung ausgegeben wurde. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] zeigt den Namen der Datenbank an, wenn die ServerName-Datenspalte in der Ablaufverfolgung aufgezeichnet wird und der Server verfügbar ist. Der Wert für eine Datenbank kann mithilfe der DB_ID-Funktion ermittelt werden.|3|Ja|  
|DatabaseName|`nvarchar`|Name der Datenbank, in der die Benutzeranweisung ausgeführt wird.|35|Ja|  
|Ereignisklasse|`Int`|Ereignistyp = 97.|27|Nein|  
|EventSequence|`int`|Sequenz eines bestimmten Ereignisses innerhalb der Anforderung.|51|Nein|  
|GroupID|`int`|ID der Arbeitsauslastungsgruppe, in der das SQL-Ablaufverfolgungsereignis ausgelöst wird.|66|Ja|  
|HostName|`nvarchar`|Der Name des Computers, auf dem der Client ausgeführt wird. Diese Datenspalte wird aufgefüllt, wenn der Hostname durch den Client bereitgestellt wird. Der Hostname kann mithilfe der HOST_NAME-Funktion bestimmt werden.|8|Ja|  
|Ganzzahlige Daten|`Integer`|Geschätzte Anzahl der zurückgegebenen Zeilen.|25|Ja|  
|IsSystem|`int`|Gibt an, ob das Ereignis bei einem Systemprozess oder einem Benutzerprozess aufgetreten ist. 1 = System, 0 = Benutzer.|60|Ja|  
|LineNumber|`int`|Zeigt die Nummer der Zeile an, die den Fehler enthält|5|Ja|  
|LoginName|`nvarchar`|Anmeldename des Benutzers (Anmeldung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sicherheit oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anmeldeinformationen im Format DOMAIN\username).|11|Ja|  
|LoginSID|`image`|Sicherheits-ID (SID) des angemeldeten Benutzers. Diese Informationen finden Sie in der sys.server_principals-Katalogsicht. Die SID ist für jede Anmeldung beim Server eindeutig.|41|Nein|  
|NestLevel|`int`|Ganze Zahl, die die von @@NESTLEVEL zurückgegebenen Daten darstellt.|29|Ja|  
|NTDomainName|`nvarchar`|Windows-Domäne, zu der der Benutzer gehört.|7|Ja|  
|ObjectID|`int`|Vom System zugewiesene ID des Objekts.|22|Ja|  
|ObjectName|`nvarchar`|Name des Objekts, auf das verwiesen wird|34|Ja|  
|ObjektType|`int`|Der Wert, der den Typ des am Ereignis beteiligten Objekts darstellt. Dieser Wert entspricht der type-Spalte in sys.objects. Weitere Werte finden Sie unter [ObjectType (Spalte für Ablaufverfolgungsereignisse)](objecttype-trace-event-column.md).|28|Ja|  
|RequestID|`int`|Die ID der Anforderung, die die Anweisung enthält.|49|Ja|  
|ServerName|`nvarchar`|Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, für die eine Ablaufverfolgung ausgeführt wird.|26|Nein|  
|SessionLoginName|`nvarchar`|Der Anmeldename des Benutzers, der die Sitzung gestartet hat. Wenn Sie beispielsweise mithilfe von Login1 eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen und eine Anweisung als Login2 ausführen, zeigt SessionLoginName den Wert Login1 an und LoginName den Wert Login2. Diese Spalte zeigt sowohl den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - als auch den Windows-Anmeldenamen an.|64|Ja|  
|SPID|`int`|Die ID der Sitzung, in der das Ereignis aufgetreten ist.|12|Ja|  
|StartTime|`datetime`|Zeitpunkt, zu dem das Ereignis begonnen hat (falls vorhanden).|14|Ja|  
|TransactionID|`bigint`|Die vom System zugewiesene ID der Transaktion.|4|Ja|  
|XactSequence|`bigint`|Token zur Beschreibung der aktuellen Transaktion.|50|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [sp_trace_setevent &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Referenz zu logischen und physischen Showplan-Operatoren](../showplan-logical-and-physical-operators-reference.md)   
 [Showplan XML Statistics Profile (Ereignisklasse)](showplan-xml-statistics-profile-event-class.md)   
 [Showplan XML-Ereignisklasse](showplan-xml-event-class.md)  
  
  
