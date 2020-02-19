---
title: Behandlung von NULL-Werten
description: Veranschaulicht, wie Sie in SQL Server und .NET mit NULL-Werten arbeiten.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 861ed4395e6cf8f5e8df3a5cc41a0f6da597e5ad
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247749"
---
# <a name="handling-null-values"></a>Behandlung von NULL-Werten

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Ein NULL-Wert wird in einer relationalen Datenbank verwendet, wenn der Wert in einer Spalte unbekannt ist oder fehlt. Ein NULL-Wert ist weder eine leere Zeichenfolge (für Zeichen- oder datetime-Datentypen) noch der Wert 0 (für numerische Datentypen). Die ANSI-Spezifikation SQL-92 besagt, dass ein NULL-Wert für alle Datentypen gleich sein muss, damit alle NULL-Werte einheitlich behandelt werden. Der Namespace <xref:System.Data.SqlTypes> bietet Semantik für NULL-Werte, indem die Schnittstelle <xref:System.Data.SqlTypes.INullable> implementiert wird. Jeder der Datentypen in <xref:System.Data.SqlTypes> hat seine eigene `IsNull`-Eigenschaft und einen `Null`-Wert, der einer Instanz dieses Datentyps zugewiesen werden kann.  
  
> [!NOTE]
>  Mit .NET Framework-Version 2.0 und .NET Core-Version 1.0 wurde Unterstützung für NULL-Werte zulassende Typen eingeführt, die es Programmierern ermöglichen, einen Werttyp so zu erweitern, dass er alle Werte des zugrunde liegenden Typs darstellt. Diese CLR-Typen, die NULL-Werte zulassen, stellen eine Instanz der <xref:System.Nullable>-Struktur dar. Diese Fähigkeit ist besonders nützlich, wenn Werttypen geschachtelt oder ungeschachtelt sind, was eine verbesserte Kompatibilität mit Objekttypen ermöglicht. CLR-Typen, die NULL-Werte zulassen, sind nicht für die Speicherung von NULL-Werten in Datenbanken gedacht, da sich ein ANSI-SQL-NULL-Wert nicht so verhält wie ein `null`-Verweis (oder `Nothing` in Visual Basic). Verwenden Sie zum Arbeiten mit ANSI-SQL-NULL-Werten in Datenbanken NULL-Werte des Typs <xref:System.Data.SqlTypes> anstelle von <xref:System.Nullable>. Weitere Informationen zum Arbeiten mit CLR-Typen, die NULL-Werte zulassen, in C# finden Sie unter [Nullable-Werttypen](https://docs.microsoft.com/dotnet/csharp/programming-guide/nullable-types/). Informationen zu Visual Basic finden Sie unter [Auf NULL festlegbare Werttypen](https://docs.microsoft.com/dotnet/csharp/programming-guide/nullable-types/using-nullable-types/).  
  
## <a name="nulls-and-three-valued-logic"></a>NULL-Werte und dreiwertige Logik  
Durch das Zulassen von NULL-Werten in Spaltendefinitionen wird in Ihre Anwendung dreiwertige Logik eingeführt. Ein Vergleich kann anhand einer von drei Bedingungen ausgewertet werden:  
  
- True  
  
- False  
  
- Unknown  
  
Da NULL als unbekannt betrachtet wird, werden zwei miteinander verglichene NULL-Werte nicht als gleich angesehen. Wenn in Ausdrücken mit arithmetischen Operatoren einer der Operanden NULL ist, ist das Ergebnis ebenfalls NULL.  
  
## <a name="nulls-and-sqlboolean"></a>NULL-Werte und SqlBoolean  
Beim Vergleich zwischen beliebigen <xref:System.Data.SqlTypes> wird <xref:System.Data.SqlTypes.SqlBoolean> zurückgegeben. Die `IsNull`-Funktion für jeden `SqlType` gibt <xref:System.Data.SqlTypes.SqlBoolean> zurück und kann verwendet werden, um auf NULL-Werte zu prüfen. Die folgenden Wahrheitstabellen zeigen, wie die Operatoren AND, OR und NOT bei Vorhandensein eines NULL-Werts funktionieren. (T = TRUE, F = FALSE und U = Unbekannt oder NULL.)  
  
![Wahrheitstabelle](../media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Grundlegendes zur Option ANSI_NULLS  
<xref:System.Data.SqlTypes> bietet die gleiche Semantik wie bei aktivierter Option ANSI_NULLS in SQL Server. Alle arithmetischen Operatoren (+, -, *, /, %), bitweisen Operatoren (~, &, &#124;) und die meisten Funktionen geben NULL zurück, wenn einer der Operanden oder Argumente NULL ist, außer für die Eigenschaft `IsNull`.  
  
Der ANSI SQL-92-Standard unterstützt *columnName* = NULL in einer WHERE-Klausel nicht. In SQL Server steuert die Option ANSI_NULLS sowohl die standardmäßige NULL-Zulässigkeit in der Datenbank als auch die Auswertung von Vergleichen mit NULL-Werten. Wenn ANSI_NULLS auf ON festgelegt ist (Standardeinstellung), muss in Ausdrücken bei Prüfen auf NULL-Werte der Operator IS NULL verwendet werden. Der folgende Vergleich gibt z. B. immer UNKNOWN zurück, wenn ANSI_NULLS auf ON festgelegt ist:  
  
```console
colname > NULL  
```  
  
Der Vergleich mit einer Variablen, die einen NULL-Wert enthält, ergibt ebenfalls „Unbekannt“:  
  
```console
colname > @MyVariable  
```  
  
Verwenden Sie die Prädikate IS NULL oder IS NOT NULL, um zu überprüfen, ob ein NULL-Wert vorliegt. Dadurch nimmt die Komplexität der WHERE-Klausel möglicherweise zu. Beispielsweise lässt die Spalte TerritoryID in der AdventureWorks-Tabelle „Customer“ NULL-Werte zu. Soll eine SELECT-Anweisung u. a. das Vorhandensein von NULL-Werten überprüfen, muss ein IS NULL-Prädikat eingefügt werden:  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
Wenn Sie ANSI_NULLS in SQL Server auf OFF festlegen, können Sie Ausdrücke erstellen, die den Gleichheitsoperator zum Vergleich mit NULL verwenden. Sie können jedoch nicht verhindern, dass verschiedene Verbindungen NULL-Optionen für diese Verbindung festlegen. Die Verwendung von IS NULL zum Testen auf NULL-Werte funktioniert immer, und zwar unabhängig von den ANSI_NULLS-Einstellungen für eine Verbindung.  
  
Das Deaktivieren von ANSI_NULLS wird in einem `DataSet` nicht unterstützt, das immer dem ANSI-Standard SQL-92 für die Behandlung von NULL-Werten in <xref:System.Data.SqlTypes> folgt.  
  
## <a name="assigning-null-values"></a>Zuweisen von NULL-Werten  
NULL-Werte sind etwas Besonderes, und ihre Speicher- und Zuordnungssemantik unterscheidet sich in verschiedenen Typen- und Speichersystemen. Ein `Dataset` ist für die Verwendung mit verschiedenen Typ- und Speichersystemen konzipiert.  
  
In diesem Abschnitt wird die NULL-Semantik für das Zuweisen von NULL-Werten zu einer <xref:System.Data.DataColumn> in einer <xref:System.Data.DataRow> in den verschiedenen Typensystemen beschrieben.  
  
`DBNull.Value`  
Diese Zuweisung ist gültig für eine `DataColumn` eines beliebigen Typs. Wenn der Typ `INullable` implementiert, wird `DBNull.Value` in den entsprechenden stark typisierten NULL-Wert gezwungen.  
  
`SqlType.Null`  
Alle <xref:System.Data.SqlTypes>-Datentypen implementieren `INullable`. Wenn der stark typisierte NULL-Wert mithilfe impliziter Umwandlungsoperatoren in den Datentyp der Spalte konvertiert werden kann, sollte die Zuweisung durchgeführt werden. Andernfalls wird eine Ausnahme aufgrund ungültiger Umwandlung ausgelöst.  
  
`null`  
Wenn 'null' ein zulässiger Wert für den angegebenen Datentyp `DataColumn` ist, wird er in den entsprechenden `DbNull.Value` oder `Null` gezwungen, der dem `INullable`-Typ (`SqlType.Null`) zugeordnet ist.  
  
`derivedUdt.Null`  
Bei UDT-Spalten werden NULL-Werte immer basierend auf dem Typ gespeichert, der `DataColumn` zugeordnet ist. Betrachten Sie den Fall einer UDT, die einer `DataColumn` zugeordnet ist, die nicht `INullable` implementiert, während ihre Unterklasse dies tut. Wenn in diesem Fall ein stark typisierter NULL-Wert der abgeleiteten Klasse zugewiesen ist, wird er als nicht typisierter `DbNull.Value` gespeichert, da die NULL-Speicherung immer im Einklang mit dem Datentyp von DataColumn ist.  
  
> [!NOTE]
>  Die Struktur von `Nullable<T>` oder <xref:System.Nullable> wird in `DataSet` derzeit nicht unterstützt.  
  
### <a name="multiple-column-row-assignment"></a>Zuweisung mehrerer Spalten (Zeilen)  
`DataTable.Add`, `DataTable.LoadDataRow` oder andere APIs, die ein <xref:System.Data.DataRow.ItemArray%2A> akzeptieren, das einer Zeile zugeordnet wird, ordnen 'null' dem Standardwert von DataColumn zu. Wenn ein Objekt im Array `DbNull.Value` oder sein stark typisiertes Pendant enthält, gelten die gleichen Regeln wie oben beschrieben.  
  
Außerdem gelten die folgenden Regeln für eine Instanz von NULL-Zuweisungen für `DataRow.["columnName"]`:  
  
- Für alle Spalten (mit Ausnahme der stark typisierten NULL-Spalten) lautet der *default*-Standardwert `DbNull.Value`. In den stark typisierten NULL-Spalten ist es der entsprechende stark typisierte NULL-Wert.  
  
- NULL-Werte werden niemals bei der Serialisierung in XML-Dateien geschrieben (wie in „xsi: nil“).  
  
- Alle Nicht-NULL-Werte, einschließlich der Standardwerte, werden bei der Serialisierung in XML immer geschrieben. Dies steht im Gegensatz zur XSD/XML-Semantik, bei der ein NULL-Wert (xsi:nil) explizit und der Standardwert implizit ist (wenn er in XML nicht vorhanden ist, kann ein validierender Parser ihn aus einem zugehörigen XSD-Schema abrufen). Das Gegenteil gilt für `DataTable`: Ein NULL-Wert ist implizit und der Standardwert ist explizit.  
  
- Allen fehlenden Spaltenwerten für aus der XML-Eingabe gelesene Zeilen wird NULL zugewiesen. Zeilen, die mit <xref:System.Data.DataTable.NewRow%2A> oder ähnlichen Methoden erstellt werden, wird der Standardwert von DataColumn zugewiesen.  
  
- Die <xref:System.Data.DataRow.IsNull%2A>-Methode gibt `true` sowohl für `DbNull.Value` als auch für `INullable.Null` zurück.  
  
## <a name="assigning-null-values"></a>Zuweisen von NULL-Werten  
Der Standardwert für jede <xref:System.Data.SqlTypes>-Instanz ist NULL.  
  
NULL-Werte in <xref:System.Data.SqlTypes> sind typspezifisch und können nicht durch einen einzelnen Wert, wie z. B. `DbNull`, dargestellt werden. Verwenden Sie die `IsNull`-Eigenschaft, um auf NULL-Werte zu prüfen.  
  
NULL-Werte können einem <xref:System.Data.DataColumn> zugewiesen werden, wie im folgenden Codebeispiel gezeigt. Sie können `SqlTypes`-Variablen direkt NULL-Werte zuweisen, ohne eine Ausnahme auszulösen.  
  
### <a name="example"></a>Beispiel  
Das folgende Codebeispiel erstellt eine <xref:System.Data.DataTable> mit zwei Spalten, die als <xref:System.Data.SqlTypes.SqlInt32> und <xref:System.Data.SqlTypes.SqlString> definiert sind. Der Code fügt eine Zeile mit bekannten Werten und eine Zeile mit NULL-Werten hinzu und iteriert dann durch die <xref:System.Data.DataTable>. Dabei werden die Werte den Variablen zugewiesen, und die Ausgabe wird im Konsolenfenster angezeigt.  
  
[!code-csharp[DataWorks SqlInt32_IsNull#1](~/../sqlclient/doc/samples/SqlInt32_IsNull.cs#1)]
  
In diesem Beispiel werden die folgenden Ergebnisse gezeigt:  
  
```console
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Vergleichen von NULL-Werten mit SqlTypes und CLR-Typen  
Beim Vergleich von NULL-Werten ist es wichtig, den Unterschied zwischen der Art und Weise zu verstehen, wie die `Equals`-Methode NULL-Werte in <xref:System.Data.SqlTypes> auswertet, im Vergleich dazu, wie sie mit CLR-Typen arbeitet. Alle <xref:System.Data.SqlTypes>`Equals`-Methoden verwenden Datenbanksemantik zur Auswertung von NULL-Werten. Wenn einer oder beide Werte NULL sind, ergibt der Vergleich NULL. Andererseits ergibt das Anwenden der CLR-Methode `Equals` auf zwei <xref:System.Data.SqlTypes> TRUE, wenn beide NULL sind. Dies spiegelt den Unterschied zwischen der Verwendung einer Instanzmethode wie der CLR-Methode `String.Equals` und der Verwendung der statischen/gemeinsamen Methode `SqlString.Equals` wider.  
  
Das folgende Beispiel veranschaulicht den Unterschied in den Ergebnissen zwischen der `SqlString.Equals`-Methode und der `String.Equals`-Methode, wenn jeweils ein Paar NULL-Werte und dann ein Paar leere Zeichenfolgen übergeben werden.  
  
[!code-csharp[DataWorks SqlString_Equals#1](~/../sqlclient/doc/samples/SqlString_Equals.cs#1)]
  
Der Code erzeugt folgende Ausgabe:  
  
```console
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True   
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Datentypen und ADO.NET](sql-server-data-types.md)
