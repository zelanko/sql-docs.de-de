---
title: Ereignisdateiziel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- event file target
- file target [SQL Server extended events]
- targets [SQL Server extended events], file target
ms.assetid: 4f0ee6ec-a0a8-4c38-aa61-8293ab6ac7fd
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 66777a5db1812d1a63e100d4a02522bc1ac3b43a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48092852"
---
# <a name="event-file-target"></a>Event File Target
  Das Ereignisdateiziel ist ein Ziel, das vollständige Puffer auf Datenträger schreibt.  
  
 In der folgenden Tabelle werden die verfügbaren Optionen zum Konfigurieren des Ereignisdateiziels beschrieben.  
  
|Option|Zulässige Werte|Description|  
|------------|--------------------|-----------------|  
|filename|Eine beliebige Zeichenfolge mit bis zu 260&nbsp;Zeichen. Dieser Wert ist erforderlich.|Der Speicherort und der Dateiname.<br /><br /> Sie können eine beliebige Dateinamenerweiterung verwenden.|  
|max_file_size|Eine beliebige 64-Bit-Ganzzahl. Dieser Wert ist optional.|Die maximale Dateigröße in Megabyte (MB). Wenn max_file_size nicht angegeben ist, kann die Datei so lange anwachsen, bis der Speicherplatz auf dem Datenträger erschöpft ist. Die Standarddateigröße ist 1&nbsp;GB.<br /><br /> Der Wert für max_file_size muss größer als die aktuelle Größe der Sitzungspuffer sein. Andernfalls wird zurückgegeben, dass max_file_size ungültig ist, und das Dateiziel kann nicht initialisiert werden. Fragen Sie zum Anzeigen der aktuellen Puffergröße die Spalte „buffer_size“ in der dynamischen Verwaltungssicht [sys.dm_xe_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql) ab.<br /><br /> Wenn die Standardgröße geringer als die Sitzungspuffergröße ist, sollten Sie für „max_file_size“ den in der Spalte „max_memory“ der Katalogsicht [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) angegebenen Wert festlegen.<br /><br /> Wenn für max_file_size ein höherer Wert als für die Sitzungspuffer definiert ist, wird dieses möglicherweise auf das nächstkleinere Vielfache der Sitzungspuffergröße abgerundet. Hierdurch wird eine Zieldatei erzeugt, die kleiner als der für max_file_size angegebene Wert ist. Beispiel: Wenn die Puffergröße 100 MB beträgt und für &lt;legacyBold&gt;max_file_size&lt;/legacyBold&gt; 150 MB festgelegt ist, wird die resultierende Dateigröße auf 100 MB abgerundet, da in die verbleibenden 50 MB kein zweiter Puffer passen würde.<br /><br /> Wenn die Standarddateigröße kleiner als die Sitzungspuffergröße ist, sollten Sie für „max_file_size“ den Wert in der Spalte „max_memory“ der Katalogsicht [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) festlegen.|  
|max_rollover_files|Eine beliebige 32-Bit-Ganzzahl. Dieser Wert ist optional.|Die maximale Anzahl von Dateien, die im Dateisystem beibehalten werden. Der Standardwert ist 5.|  
|increment|Eine beliebige 32-Bit-Ganzzahl. Dieser Wert ist optional.|Die inkrementelle Zunahme für die Datei in Megabyte (MB). Falls der Wert für <legacyBold>increment</legacyBold> nicht angegeben wurde, wird als Standardwert das Doppelte der Sitzungspuffergröße verwendet.|  
  
 Wenn ein Ereignisdateiziel zum ersten Mal erstellt wird, wird an den Dateinamen „_0\_ “ und ein langer ganzzahliger Wert angefügt. Der ganzzahlige Wert entspricht der Anzahl von Millisekunden zwischen dem 1.&nbsp;Januar&nbsp;1600 und dem Datum sowie der Uhrzeit der Dateierstellung. Nachfolgende Rolloverdateien verwenden ebenfalls dieses Format. Anhand des langen ganzzahligen Werts können Sie die neueste Datei ermitteln. Das folgende Beispiel veranschaulicht, wie Dateien in einem Szenario benannt werden, in dem die Option für den Dateinamen als C:\OutputFiles\MyOutput.xel angegeben wird:  
  
-   Erste erstellte Datei: C:\OutputFiles\MyOutput_0_128500310259380000.xel  
  
-   Erste Rolloverdatei: C:\OutputFiles\MyOutput_0_128505831770890000.xel  
  
-   Zweite Rolloverdatei: C:\OutputFiles\MyOutput_0_132410772966237000.xel  
  
## <a name="adding-the-target-to-a-session"></a>Hinzufügen des Ziels zu einer Sitzung  
 Schließen Sie beim Erstellen oder Ändern einer Ereignissitzung die folgenden Anweisungen ein, wobei Sie *Dateiname* durch den gewünschten Dateinamen mit Pfad ersetzen, um das Ereignisdateiziel einer Sitzung für erweiterte Ereignisse hinzuzufügen:  
  
```  
ADD TARGET package0.event_file(  
   SET filename='file_name.xel')  
```  
  
## <a name="reviewing-the-target-output"></a>Überprüfen der Zielausgabe  
 Verwenden Sie zum Überprüfen der Funktion „sys.fn_xe_file_target_read_file“ die Ausgabe des Dateiziels. Es empfiehlt sich, die Daten in XML umzuwandeln. Sie können die folgende Syntax verwenden, wobei Sie *Dateiname* durch den Dateinamen mit Pfad ersetzen, die Sie beim Hinzufügen des Ziels angegeben haben:  
  
```  
SELECT *, CAST(event_data AS XML) AS 'event_data_XML'  
FROM sys.fn_xe_file_target_read_file('file_name*.xel', NULL, NULL, NULL)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Ziele für erweiterte Ereignisse von SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [Sys. fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)   
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
