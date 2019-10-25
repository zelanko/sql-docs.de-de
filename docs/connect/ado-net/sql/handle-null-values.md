---
title: Behandlung von NULL-Werten
description: Veranschaulicht das Arbeiten mit GUID-und uniqueidentifier-Werten in SQL Server und .net.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 6ae2bc8d816dd2bc32572447483dacd76dd967f0
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452184"
---
# <a name="handling-null-values"></a>Behandlung von NULL-Werten

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Ein NULL-Wert in einer relationalen Datenbank wird verwendet, wenn der Wert in einer Spalte unbekannt oder nicht vorhanden ist. Ein NULL-Wert ist weder eine leere Zeichenfolge (für Zeichen-oder datetime-Datentypen) noch ein NULL-Wert (für numerische Datentypen). Die ANSI SQL-92-Spezifikation gibt an, dass ein NULL-Wert für alle Datentypen identisch sein muss, damit alle Nullen konsistent behandelt werden. Der <xref:System.Data.SqlTypes>-Namespace bietet eine NULL-Semantik durch Implementieren der <xref:System.Data.SqlTypes.INullable>-Schnittstelle. Jeder der Datentypen in <xref:System.Data.SqlTypes> verfügt über eine eigene `IsNull`-Eigenschaft und einen `Null` Wert, der einer Instanz dieses Datentyps zugewiesen werden kann.  
  
> [!NOTE]
>  Der .NET Framework Version 2,0 und die .net Core-Version 1,0 haben Unterstützung für Typen mit Nullwert eingeführt, die es Programmierern ermöglichen, einen Werttyp zu erweitern, um alle Werte des zugrunde liegenden Typs darzustellen. Diese CLR-Typen, die NULL-Werte zulassen, stellen eine Instanz der <xref:System.Nullable> Struktur dar. Diese Funktion ist besonders nützlich, wenn Werttypen mittels Boxing und Unboxing versehen werden, um die Kompatibilität mit Objekttypen zu verbessern. CLR-Typen, die NULL-Werte zulassen, sind nicht für die Speicherung von Daten Bank Nullen gedacht, da sich ein ANSI-SQL-NULL-Wert nicht auf dieselbe Weise verhält wie ein `null` Verweis (oder `Nothing` in Visual Basic Verwenden Sie zum Arbeiten mit Datenbank-ANSI-SQL-NULL-Werten <xref:System.Data.SqlTypes> Nullen anstelle von <xref:System.Nullable>. Weitere Informationen zum Arbeiten mit CLR-Typen, die NULL C# -Werte zulassen, finden [Sie](https://docs.microsoft.com/dotnet/csharp/programming-guide/nullable-types/using-nullable-types/)unter C# Typen, [die NULL-](https://docs.microsoft.com/dotnet/csharp/programming-guide/nullable-types/)Werte zulassen.  
  
## <a name="nulls-and-three-valued-logic"></a>Nullen und dreiwertige Logik  
Durch das Zulassen von NULL-Werten in Spaltendefinitionen wird eine dreiwertige Logik in Ihre Anwendung eingeführt. Ein Vergleich kann eine von drei Bedingungen auswerten:  
  
- Wahr  
  
- False  
  
- Unknown  
  
Da NULL als unbekannt angesehen wird, werden zwei NULL-Werte im Vergleich zueinander nicht als gleich betrachtet. In Ausdrücken, die arithmetische Operatoren verwenden, ist das Ergebnis ebenfalls NULL, wenn einer der Operanden NULL ist.  
  
## <a name="nulls-and-sqlboolean"></a>Nullen und SqlBoolean  
Beim Vergleich zwischen allen <xref:System.Data.SqlTypes> wird ein <xref:System.Data.SqlTypes.SqlBoolean> zurückgegeben. Die `IsNull`-Funktion für jede `SqlType` gibt eine <xref:System.Data.SqlTypes.SqlBoolean> zurück und kann verwendet werden, um nach NULL-Werten zu suchen. Die folgenden Wahrheitstabellen zeigen, wie die Operatoren and, or und Not im vorhanden sein eines NULL-Werts funktionieren. (T = true, F = false und U = unknown oder NULL.)  
  
![Wahrheitstabelle](../media/truthtable-bpuedev11.gif "|::ref1::|")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Grundlegendes zur ANSI_NULLS-Option  
<xref:System.Data.SqlTypes> bietet die gleiche Semantik wie bei Festlegung der ANSI_NULLS-Option in SQL Server. Alle arithmetischen Operatoren (+, -, *, /, %), bitweisen Operatoren (~, &, &#124;) und die meisten Funktionen geben NULL zurück, wenn einer der Operanden oder Argumente NULL ist, außer für die Eigenschaft `IsNull`.  
  
Der ANSI SQL-92-Standard unterstützt *columnName* = NULL in einer WHERE-Klausel nicht. In SQL Server steuert die ANSI_NULLS-Option sowohl die standardmäßige NULL-Zulässigkeit in der Datenbank als auch die Auswertung von vergleichen mit NULL-Werten. Wenn ANSI_NULLS aktiviert ist (Standardeinstellung), muss der is NULL-Operator beim Testen auf NULL-Werte in Ausdrücken verwendet werden. Der folgende Vergleich gibt z. B. immer UNKNOWN zurück, wenn ANSI_NULLS auf ON festgelegt ist:  
  
```console
colname > NULL  
```  
  
Der Vergleich mit einer Variablen, die einen NULL-Wert enthält, ergibt ebenfalls unbekanntes Ergebnis:  
  
```console
colname > @MyVariable  
```  
  
Verwenden Sie die Prädikate IS NULL oder IS NOT NULL, um zu überprüfen, ob ein NULL-Wert vorliegt. Dadurch nimmt die Komplexität der WHERE-Klausel möglicherweise zu. Beispielsweise lässt die Territor-ID-Spalte in der AdventureWorks Customer-Tabelle NULL-Werte zu. Soll eine SELECT-Anweisung u. a. das Vorhandensein von NULL-Werten überprüfen, muss ein IS NULL-Prädikat eingefügt werden:  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
Wenn Sie in SQL Server ANSI_NULLS Off festlegen, können Sie Ausdrücke erstellen, die den Gleichheits Operator verwenden, um mit NULL zu vergleichen. Sie können jedoch nicht verhindern, dass unterschiedliche Verbindungen NULL-Optionen für diese Verbindung festlegen. Das Verwenden von is NULL zum Testen auf NULL-Werte funktioniert immer, unabhängig von den ANSI_NULLS-Einstellungen für eine Verbindung.  
  
Das Festlegen von ANSI_NULLS off wird in einem `DataSet` nicht unterstützt, das immer dem ANSI SQL-92-Standard für die Behandlung von NULL-Werten in <xref:System.Data.SqlTypes> folgt.  
  
## <a name="assigning-null-values"></a>Zuweisen von NULL-Werten  
NULL-Werte sind Sonderzeichen, und ihre Speicher-und Zuweisungs Semantik unterscheidet sich in verschiedenen Typsystemen und Speichersystemen. Ein `Dataset` ist für die Verwendung mit verschiedenen Typen und Speichersystemen konzipiert.  
  
In diesem Abschnitt wird die NULL-Semantik zum Zuweisen von NULL-Werten zu einem <xref:System.Data.DataColumn> in einem <xref:System.Data.DataRow> über die verschiedenen Typsysteme beschrieben.  
  
`DBNull.Value`  
Diese Zuweisung ist gültig für eine `DataColumn` eines beliebigen Typs. Wenn der Typ `INullable` implementiert, wird `DBNull.Value` in den entsprechenden stark typisierten NULL-Wert umgewandelt.  
  
`SqlType.Null`  
Alle <xref:System.Data.SqlTypes>-Datentypen implementieren `INullable`. Wenn der stark typisierte NULL-Wert mithilfe impliziter Umwandlungs Operatoren in den Datentyp der Spalte konvertiert werden kann, sollte die Zuweisung durchlaufen werden. Andernfalls wird eine ungültige Umwandlungs Ausnahme ausgelöst.  
  
`null`  
Wenn ' NULL ' ein gültiger Wert für den angegebenen `DataColumn` Datentyp ist, wird er in die entsprechende `DbNull.Value` oder `Null` umgewandelt, die dem `INullable` Typ zugeordnet ist (`SqlType.Null`).  
  
`derivedUdt.Null`  
Bei UDT-Spalten werden Nullen immer basierend auf dem Typ gespeichert, der dem `DataColumn` zugeordnet ist. Beachten Sie die Groß-/Kleinschreibung eines UDT, der einem `DataColumn` zugeordnet ist, der `INullable` nicht implementiert, während seine Unterklasse dies tut. Wenn in diesem Fall ein stark typisierter NULL-Wert zugewiesen wird, der der abgeleiteten Klasse zugeordnet ist, wird er als nicht typisiertes `DbNull.Value` gespeichert, da der NULL-Speicher immer mit dem Datentyp der datacolenumn konsistent ist.  
  
> [!NOTE]
>  Die `Nullable<T>`-oder <xref:System.Nullable> Struktur wird im `DataSet` derzeit nicht unterstützt.  
  
### <a name="multiple-column-row-assignment"></a>Zuweisung mehrerer Spalten (Zeilen)  
`DataTable.Add`, `DataTable.LoadDataRow` oder andere APIs, die ein <xref:System.Data.DataRow.ItemArray%2A> akzeptieren, das einer Zeile zugeordnet wird, ordnen Sie "Null" dem Standardwert von datacolenn zu. Wenn ein Objekt im Array `DbNull.Value` oder seine stark typisierte Entsprechung enthält, werden dieselben Regeln angewendet wie oben beschrieben.  
  
Außerdem gelten die folgenden Regeln für eine Instanz von `DataRow.["columnName"]` NULL-Zuweisungen:  
  
- Für alle Spalten (mit Ausnahme der stark typisierten NULL-Spalten) lautet der *default*-Standardwert `DbNull.Value`. In den stark typisierten NULL-Spalten ist es der entsprechende stark typisierte NULL-Wert.  
  
- NULL-Werte werden niemals bei der Serialisierung in XML-Dateien geschrieben (wie in "xsi: nil").  
  
- Alle nicht-NULL-Werte, einschließlich der Standardwerte, werden bei der Serialisierung in XML immer geschrieben. Dies ist anders als die XSD/XML-Semantik, bei der ein NULL-Wert (xsi: nil) explizit ist und der Standardwert implizit ist (wenn er nicht in XML vorhanden ist, kann ein Validierungs Parser ihn aus einem zugeordneten XSD-Schema erhalten). Das Gegenteil gilt für eine `DataTable`: ein NULL-Wert ist implizit, und der Standardwert ist explizit.  
  
- Allen fehlenden Spaltenwerten für aus der XML-Eingabe gelesene Zeilen wird NULL zugewiesen. Zeilen, die mit <xref:System.Data.DataTable.NewRow%2A> oder ähnlichen Methoden erstellt werden, wird der Standardwert von datacolenumn zugewiesen.  
  
- Die <xref:System.Data.DataRow.IsNull%2A>-Methode gibt `true` sowohl für `DbNull.Value` als auch für `INullable.Null` zurück.  
  
## <a name="assigning-null-values"></a>Zuweisen von NULL-Werten  
Der Standardwert für jede <xref:System.Data.SqlTypes> Instanz ist NULL.  
  
NULL-Werte in <xref:System.Data.SqlTypes> sind typspezifisch und können nicht durch einen einzelnen Wert dargestellt werden, z. b. `DbNull`. Verwenden Sie die `IsNull`-Eigenschaft, um nach NULL-Werten zu suchen.  
  
NULL-Werte können einem <xref:System.Data.DataColumn> zugewiesen werden, wie im folgenden Codebeispiel gezeigt. Sie können `SqlTypes` Variablen direkt NULL-Werte zuweisen, ohne eine Ausnahme auszulösen.  
  
### <a name="example"></a>Beispiel  
Im folgenden Codebeispiel wird eine <xref:System.Data.DataTable> mit zwei Spalten erstellt, die als <xref:System.Data.SqlTypes.SqlInt32> und <xref:System.Data.SqlTypes.SqlString> definiert sind. Der Code fügt eine Zeile bekannter Werte, eine Zeile mit NULL-Werten, ein und durchläuft dann die <xref:System.Data.DataTable>, wobei die Werte den Variablen zugewiesen und die Ausgabe im Konsolenfenster angezeigt wird.  
  
[!code-csharp[DataWorks SqlInt32_IsNull#1](~/../sqlclient/doc/samples/SqlInt32_IsNull.cs#1)]
  
In diesem Beispiel werden die folgenden Ergebnisse angezeigt:  
  
```console
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Vergleichen von NULL-Werten mit SqlTypes und CLR-Typen  
Beim Vergleichen von NULL-Werten ist es wichtig, den Unterschied zwischen der Auswertung der NULL-Werte durch die `Equals`-Methode in <xref:System.Data.SqlTypes> im Vergleich zur Funktionsweise von CLR-Typen zu verstehen. Alle <xref:System.Data.SqlTypes> `Equals` Methoden verwenden Daten Bank Semantik zum Auswerten von NULL-Werten: Wenn mindestens einer der Werte NULL ist, ergibt der Vergleich Null. Andererseits ergibt die Verwendung der CLR-`Equals` Methode auf zwei <xref:System.Data.SqlTypes> true, wenn beide NULL sind. Dies spiegelt den Unterschied zwischen der Verwendung einer Instanzmethode, z. b. der CLR-`String.Equals` Methode, und der Verwendung der static/Shared-Methode `SqlString.Equals`.  
  
Im folgenden Beispiel werden die Unterschiede in den Ergebnissen zwischen der `SqlString.Equals`-Methode und der `String.Equals`-Methode veranschaulicht, wenn jeweils ein paar von NULL-Werten und dann ein paar leerer Zeichen folgen an Sie weitergeleitet wird.  
  
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
