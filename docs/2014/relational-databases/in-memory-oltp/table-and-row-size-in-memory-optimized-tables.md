---
title: Tabellen- und Zeilengröße in speicheroptimierten Tabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b0a248a4-4488-4cc8-89fc-46906a8c24a1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d89fefdf575cdb7961df0ceae811184ca31fc51
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52822534"
---
# <a name="table-and-row-size-in-memory-optimized-tables"></a>Tabellen- und Zeilengröße in speicheroptimierten Tabellen
  Eine speicheroptimierte Tabelle besteht aus einer Auflistung von Zeilen und Indizes, die Zeiger auf die Zeilen enthalten. In einer speicheroptimierten Tabelle dürfen Zeilen eine maximale Länge von 8.060 Bytes aufweisen. Wenn Sie eine Vorstellung von der Größe einer speicheroptimierten Tabelle haben, können Sie besser einschätzen, ob Ihr Computer über genügend Arbeitsspeicher verfügt.  
  
 Es gibt zwei Gründe für das Berechnen der Tabellen- und Zeilengröße:  
  
-   Wie viel Arbeitsspeicher verwendet eine Tabelle?  
  
    -   Der Arbeitsspeicher, der für die Tabelle verwendet wird, kann nicht genau berechnet werden. Viele Faktoren beeinflussen den verwendeten Arbeitsspeicher. Faktoren wie seitenbasierte Speicherbelegung, Ort, Caching und Auffüllung. Darüber hinaus mehrere Versionen von Zeilen, denen entweder aktive Transaktionen zugeordnet sind oder die auf die Garbage Collection warten.  
  
    -   Die minimale Größe, die für die Daten und Indizes in der Tabelle erforderlich ist, wird durch die Berechnung von [table size] angegeben, wie unten erläutert.  
  
    -   Da die Berechnung der Arbeitsspeicherverwendung bestenfalls eine Näherung darstellt, ist es ratsam, auch eine Kapazitätsplanung in den Bereitstellungsplänen vorzusehen.  
  
-   Die Datengröße einer Zeile und die Frage, ob die maximale Zeilengröße von 8.060 Bytes eingehalten wird. Um diese Fragen zu beantworten, verwenden Sie die Berechnung von [row body size], wie unten erläutert.  
  
 Die folgende Abbildung zeigt eine Tabelle mit Indizes und Zeilen, die wiederum Zeilenüberschriften und Text enthalten:  
  
 ![Speicheroptimierte Tabelle](../../database-engine/media/hekaton-guide-1.gif "Speicheroptimierte Tabelle")  
Speicheroptimierte Tabelle, bestehend aus Indizes und Zeilen.  
  
 Die Größe einer Tabelle im Arbeitsspeicher in Bytes wird wie folgt berechnet:  
  
```  
[table size] = [size of index 1] + ... + [size of index n] + ([row size] * [row count])  
```  
  
 Die Größe eines Hashindexes wird bei Erstellung der Tabelle festgelegt und hängt von der tatsächlichen Bucketanzahl ab. Der bucket_count-Wert, der mit der Indexspezifikation angegeben wird, wird auf die nächste Zweierpotenz aufgerundet, um [actual bucket count] zu erhalten. Wenn der angegebene bucket_count-Wert beispielsweise 100000 ist, beträgt [actual bucket count] für den Index 131072.  
  
```  
[hash index size] = 8 * [actual bucket count]  
```  
  
 Die Zeilengröße wird berechnet, indem die Überschrift und der Text addiert werden:  
  
```  
[row size] = [row header size] + [actual row body size]  
[row header size] = 24 + 8 * [number of indices]  
```  
  
 **Zeilentextgröße**  
  
 Die Berechnung von [row body size] wird in der folgenden Tabelle erläutert.  
  
 Es gibt zwei verschiedene Berechnungen für die Zeilentextgröße: die berechnete Größe und die tatsächliche Größe:  
  
-   Die berechnete Größe, bezeichnet mit [computed row body size], wird verwendet, um festzustellen, ob die Zeilengrößeneinschränkung von 8.060 Bytes überschritten wird.  
  
-   Die tatsächliche Größe, bezeichnet mit [actual row body size], ist die tatsächliche Speichergröße des Zeilentexts im Arbeitsspeicher und in den Prüfpunktdateien.  
  
 [computed row body size] und [actual row body size] werden ähnlich berechnet. Der einzige Unterschied ist die Berechnung der Größe von (n)varchar(i)- und varbinary(i)-Spalten, wie unten in der folgenden Tabelle dargestellt. Bei der berechneten Zeilentextgröße wird die deklarierte Größe *i* als Größe der Spalte verwendet, während für die tatsächliche Zeilentextgröße die tatsächliche Größe der Daten verwendet wird.  
  
 In der folgenden Tabelle wird die Berechnung der Zeilentextgröße beschrieben, die wie folgt angegeben wird: [actual row body size] = SUM([size of shallow types]) + 2 + 2 * [number of deep type columns].  
  
|Abschnitt|Größe|Kommentare|  
|-------------|----------|--------------|  
|Spalten flacher Typen|SUM([size of shallow types])<br /><br /> **Größe der einzelnen Typen lautet wie folgt aus:**<br /><br /> Bit: 1<br /><br /> Tinyint: 1<br /><br /> Smallint: 2<br /><br /> Int: 4<br /><br /> Real: 4<br /><br /> Smalldatetime: 4<br /><br /> Smallmoney: 4<br /><br /> Bigint: 8<br /><br /> Datetime: 8<br /><br /> Datetime2: 8<br /><br /> Float: 8<br /><br /> Money: 8<br /><br /> Numeric (Genauigkeit < = 18) &#124; 8<br /><br /> Time: 8<br /><br /> Numeric(Precision>18) &#124; 16<br /><br /> Uniqueidentifier: 16||  
|Auffüllung flacher Spalten|Dabei sind folgende Werte möglich:<br /><br /> 1, wenn Spalten tiefer Typen vorhanden sind und die gesamte Datengröße der flachen Spalten eine ungerade Zahl darstellt.<br /><br /> 0 andernfalls|Tiefe Typen sind die Typen (var)binary und (n)(var)char.|  
|Offsetarray für Spalten tiefer Typen|Dabei sind folgende Werte möglich:<br /><br /> 0, wenn keine Spalten tiefer Typen vorhanden sind<br /><br /> 2 + 2 * [number of deep type columns] andernfalls|Tiefe Typen sind die Typen (var)binary und (n)(var)char.|  
|NULL-Array|[number of nullable columns] / 8, aufgerundet auf vollständige Bytes.|Das Array verfügt über ein Bit pro Spalte, die NULL zulässt. Dies wird auf vollständige Bytes aufgerundet.|  
|NULL-Arrayauffüllung|Dabei sind folgende Werte möglich:<br /><br /> 1, wenn Spalten tiefer Typen vorhanden sind und die Größe des NULL-Arrays eine ungerade Anzahl von Bytes darstellt.<br /><br /> 0 andernfalls|Tiefe Typen sind die Typen (var)binary und (n)(var)char.|  
|Auffüllung|Wenn keine Spalten tiefer Typen vorhanden sind: 0<br /><br /> Wenn Spalten tiefer Typen vorhanden sind, wird eine 0-7-Byte-Auffüllung hinzugefügt, basierend auf der größten Ausrichtung, die für eine flache Spalte erforderlich ist. Jede flache Spalte erfordert eine Ausrichtung gleich ihrer Größe, wie oben beschrieben. Nur GUID-Spalten erfordern eine Ausrichtung von einem Byte (nicht 16) und numerische Spalten immer eine Ausrichtung von 8 Bytes (nie 16). Die größte Ausrichtungsanforderung unter allen flachen Spalten wird verwendet, und eine 0-7-Byte-Auffüllung wird so hinzugefügt, dass die bisherige Gesamtgröße (ohne die Spalten tiefer Typen) ein Vielfaches der erforderlichen Ausrichtung ergibt.|Tiefe Typen sind die Typen (var)binary und (n)(var)char.|  
|Spalten tiefer Typen mit fester Länge|SUM([size of fixed length deep type columns])<br /><br /> Die Größe jeder Spalte lautet wie folgt:<br /><br /> i für char(i) und binary(i).<br /><br /> 2 * i für nchar(i)|Spalten tiefer Typen mit fester Länge sind Spalten des Typs char(i), nchar(i) oder binary(i).|  
|Spalten tiefer Typen mit variabler Länge [computed size]|SUM([computed size of variable length deep type columns])<br /><br /> Die berechnete Größe jeder Spalte lautet wie folgt:<br /><br /> i für varchar(i) und varbinary(i)<br /><br /> 2 * i für nvarchar(i)|Diese Zeile wird nur auf [computed row body size] angewendet.<br /><br /> Spalten tiefer Typen mit variabler Länge sind Spalten des Typs varchar(i), nvarchar(i) oder varbinary(i). Die berechnete Größe wird durch die maximale Länge (i) der Spalte bestimmt.|  
|Spalten tiefer Typen mit variabler Länge [actual size]|SUM([actual size of variable length deep type columns])<br /><br /> Die tatsächliche Größe jeder Spalte lautet wie folgt:<br /><br /> n, wobei n der Anzahl der in der Spalte gespeicherten Zeichen entspricht; für varchar(i).<br /><br /> 2 * n, wobei n der Anzahl der in der Spalte gespeicherten Zeichen entspricht; für nvarchar(i).<br /><br /> n, wobei n der Anzahl der in der Spalte gespeicherten Bytes ist; für varbinary(i).|Diese Zeile wird nur auf [actual row body size] angewendet.<br /><br /> Die tatsächliche Größe wird durch die Daten bestimmt, die in den Spalten der Zeile gespeichert werden.|  
  
##  <a name="bkmk_RowStructure"></a> Zeilenstruktur  
 Die Zeilen in einer speicheroptimierten Tabelle verfügen über folgende Komponenten:  
  
-   Die Zeilenüberschrift enthält den Zeitstempel, der erforderlich ist, um Zeilenversionsverwaltung zu implementieren. Die Zeilenüberschrift enthält auch den Indexzeiger, um die Zeilenverkettung in den Hashbuckets zu implementieren (oben beschrieben).  
  
-   Der Zeilentext enthält die tatsächlichen Spaltendaten, darunter einige zusätzliche Informationen wie das NULL-Array für Spalten, die NULL-Werte zulassen, und das Offsetarray für Datentypen variabler Länge.  
  
 Die folgende Abbildung veranschaulicht die Zeilenstruktur für eine Tabelle mit zwei Indizes:  
  
 ![Zeilenstruktur für eine Tabelle mit zwei Indizes.](../../database-engine/media/hekaton-tables-4.gif "Row structure for a table that has two indexes.")  
  
 Die Zeitstempel für Beginn und Ende geben den Zeitraum an, in dem eine bestimmte Zeilenversion gültig ist. Für Transaktionen, die in diesem Intervall beginnen, ist diese Zeilenversion sichtbar. Weitere Informationen finden Sie unter [Transaktionen in speicheroptimierten Tabellen](memory-optimized-tables.md).  
  
 Die Indexzeiger zeigen auf die nächste Zeile in der Kette, die dem Hashbucket angehört. Die folgende Abbildung veranschaulicht die Struktur einer Tabelle mit zwei Spalten (Name, Ort) und mit zwei Indizes: einem für den Spaltennamen und einen für den Spaltenort.  
  
 ![Die Struktur einer Tabelle mit zwei Spalten und Indizes.](../../database-engine/media/hekaton-tables-5.gif "Structure of a table with two columns and indexes.")  
  
 In dieser Abbildung werden die Namen John und Jane zum ersten Hashbucket hinzugefügt. Susan wird dem zweiten Hashbucket hinzugefügt. Die Städte Beijing (Peking) und Bogota werden dem ersten Hashbucket hinzugefügt. Paris und Prag werden dem zweiten Hashbucket hinzugefügt.  
  
 Somit ergeben sie folgende Ketten für den Hashindex für Namen:  
  
-   Erste Bucket: (John, Beijing (Peking)); (John, Paris); (Jane, Prag)  
  
-   Zweiter Bucket: (Susan, Bogota)  
  
 Die Ketten für den Index für die Stadt lauten wie folgt:  
  
-   Erste Bucket: (John, Beijing (Peking)), (Susan, Bogota)  
  
-   Zweiter Bucket: (John, Paris), (Jane, Prag)  
  
 Einen endzeitstempel??? (Unendlichkeit) gibt an, dass es sich um die aktuell gültige Version der Zeile handelt. Die Zeile wurde nicht aktualisiert oder gelöscht, seitdem diese Zeilenversion geschrieben wurde.  
  
 Eine Zeit, die größer als 200 ist, enthält die Tabelle die folgenden Zeilen:  
  
|Name|Ort|  
|----------|----------|  
|John|Beijing (Peking)|  
|Jane|Prag|  
  
 Allerdings wird jeder aktiven Transaktion mit Anfangszeit 100 die folgende Version der Tabelle angezeigt:  
  
|Name|Ort|  
|----------|----------|  
|John|Paris|  
|Jane|Prag|  
|Susan|Bogota|  
  
##  <a name="bkmk_ExampleComputation"></a> Beispiel: Tabellen- und Zeilengrößenberechnung  
 Für Hashindizes wird die tatsächliche Bucketanzahl auf die nächste Zweierpotenz aufgerundet. Wenn der angegebene bucket_count-Wert beispielsweise 100000 ist, beträgt die tatsächliche Bucketanzahl für den Index 131072.  
  
 Betrachten Sie eine Orders-Tabelle mit folgender Definition:  
  
```tsql  
CREATE TABLE dbo.Orders (  
     OrderID int NOT NULL   
           PRIMARY KEY NONCLUSTERED,  
     CustomerID int NOT NULL   
           INDEX IX_CustomerID HASH WITH (BUCKET_COUNT=10000),  
     OrderDate datetime NOT NULL,  
     OrderDescription nvarchar(1000)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
```  
  
 Beachten Sie, dass diese Tabelle einen Hashindex und einen nicht gruppierten Index (den Primärschlüssel) aufweist. Darüber hinaus weist sie drei Spalten fester Länge und eine Spalte variabler Länge auf, wobei eine der Spalten NULL-Werte zulässt (OrderDescription). Nehmen wir an, die Orders-Tabelle hat 8379 Zeilen, und die durchschnittliche Länge der Werte in der OrderDescription-Spalte beträgt 78 Zeichen.  
  
 Um die Tabellengröße zu ermitteln, ermitteln Sie zuerst die Größe der Indizes. Der bucket_count-Wert für beide Indizes wird mit 10000 angegeben. Dies wird auf die nächste Potenz von 2 aufgerundet: 16384. Daher ergibt sich die Gesamtgröße der Indizes für die Orders-Tabelle wie folgt:  
  
```  
8 * 16384 = 131072 bytes  
```  
  
 Was bleibt, ist die Tabellendatengröße:  
  
```  
[row size] * [row count] = [row size] * 8379  
```  
  
 (Die Beispieltabelle enthält 8379 Zeilen.) Jetzt haben wir:  
  
```  
[row size] = [row header size] + [actual row body size]  
[row header size] = 24 + 8 * [number of indices] = 24 + 8 * 1 = 32 bytes  
```  
  
 Als Nächstes berechnen wir [actual row body size]:  
  
-   Spalten flacher Typen:  
  
    ```  
    SUM([size of shallow types]) = 4 [int] + 4 [int] + 8 [datetime] = 16  
    ```  
  
-   Die Auffüllung flacher Spalten ist 0, da die Gesamtgröße der flachen Spalten einem geraden Wert entspricht.  
  
-   Offsetarray für Spalten tiefer Typen:  
  
    ```  
    2 + 2 * [number of deep type columns] = 2 + 2 * 1 = 4  
    ```  
  
-   NULL-Array = 1  
  
-   NULL-Arrayauffüllung = 1, da die NULL-Arraygröße ungerade ist und eine Spalte tiefen Typs vorhanden ist.  
  
-   Auffüllung  
  
    -   8 ist die größte Ausrichtungsanforderung.  
  
    -   Die bisherige Größe ist 16 + 0 + 4 + 1 + 1 = 22.  
  
    -   Das nächste Vielfache von 8 ist 24.  
  
    -   Die Gesamtauffüllung beträgt 24 - 22 = 2 Bytes.  
  
-   Es wurden keine Spalten tiefer Typen fester Länge (Spalten tiefer Typen mit fester Länge: 0.).  
  
-   Die tatsächliche Größe der Spalte tiefen Typs ist 2 * 78 = 156. Die einzelne Spalte tiefen Typs OrderDescription hat den Typ nvarchar.  
  
```  
[actual row body size] = 24 + 156 = 180 bytes  
```  
  
 Um die Berechnung abzuschließen:  
  
```  
[row size] = 32 + 180 = 212 bytes  
[table size] = 8 * 16384 + 212 * 8379 = 131072 + 1776348 = 1907420  
```  
  
 Die gesamte Tabellengröße im Arbeitsspeicher entspricht daher ungefähr 2 MB. Dabei wird weder der mögliche Mehraufwand durch die Speicherbelegung noch die Zeilenversionsverwaltung berücksichtigt, die für die Transaktionen benötigt wird, die auf diese Tabelle zugreifen.  
  
 Der tatsächliche Arbeitsspeicher, der dieser Tabelle zugeordnet ist und von ihr und den zugehörigen Indizes verwendet wird, kann über die folgende Abfrage abgerufen werden:  
  
```tsql  
select * from sys.dm_db_xtp_table_memory_stats  
where object_id = object_id('dbo.Orders')  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Speicheroptimierte Tabellen](memory-optimized-tables.md)  
  
  
