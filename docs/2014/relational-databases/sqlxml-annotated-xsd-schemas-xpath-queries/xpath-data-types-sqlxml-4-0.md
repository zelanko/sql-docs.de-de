---
title: XPath-Datentypen (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping XDR types to XPath types [SQLXML]
- data types [XPath]
- arithmetic operators
- mapping data types [SQLXML]
- relational operators [SQLXML]
- node-set [SQLXML]
- data types [SQLXML], XPath
- XPath operators [SQLXML]
- XDR data type [SQLXML]
- equality operators [SQLXML]
- XPath conversions [SQLXML]
- converting data types [SQLXML]
- Boolean operators
- XPath queries [SQLXML], data types
- XPath data types [SQLXML]
- operators [SQLXML]
ms.assetid: a90374bf-406f-4384-ba81-59478017db68
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f38c8e12137ea2a906269b6cba7b86fefff5c508
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060458"
---
# <a name="xpath-data-types-sqlxml-40"></a>XPath-Datentypen (SQLXML 4.0)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-, XPath- und XML-Schemas (XSD) verfügen über sehr unterschiedliche Datentypen. Zum Beispiel verfügt XPath nicht über Ganzzahl- oder Datumsdatentypen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und XSD hingegen über mehrere. XSD gibt Zeitwerte auf die Nanosekunde genau an, während die Genauigkeit von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] höchstens 1/300 Sekunde beträgt. Einen Datentyp einem anderen zuzuordnen ist deshalb nicht immer möglich. Weitere Informationen zur Zuordnung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen und XSD-Datentypen, finden Sie unter [Datentypumwandlungen und die SQL: DataType-Anmerkung &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 XPath verfügt über drei Datentypen: `string`, `number` und `boolean`. Beim `number`-Datentyp handelt es sich stets um einen IEEE 754-Gleitkommawert mit doppelter Genauigkeit. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `float(53)` -Datentyp kommt XPath `number`. Allerdings entspricht `float(53)` IEEE 754 nicht genau. Zum Beispiel wird weder NaN (Not-a-Number) noch Unendlichkeit verwendet. Wenn man versucht, eine nicht numerische Zeichenfolge in `number` zu konvertieren und eine Division durch Null durchzuführen, tritt ein Fehler auf.  
  
## <a name="xpath-conversions"></a>XPath-Konvertierungen  
 Wenn Sie eine XPath-Abfrage wie `OrderDetail[@UnitPrice > "10.0"]` verwenden, können implizite und explizite Datentypkonvertierungen den Sinn der Abfrage leicht verändern. Deshalb sollte nachvollzogen werden können, wie XPath-Datentypen implementiert werden. Der XPath-Sprachspezifikation, XML Path Language (XPath) Version 1.0 W3C vorgeschlagenen Empfehlung 8. Oktober 1999, finden Sie unter der W3C-Website unter http://www.w3.org/TR/1999/PR-xpath-19991008.html.  
  
 XPath-Operatoren werden in vier Kategorien unterteilt:  
  
-   Boolesche Operatoren (AND, OR)  
  
-   Relationale Operatoren (\<, >, \<=, > =)  
  
-   Gleichheitsoperatoren (=, !=)  
  
-   Arithmetische Operatoren (+, -, *, DIV, MOD)  
  
 Bei jeder Operatorkategorie werden die Operanden auf andere Art und Weise konvertiert. XPath-Operatoren konvertieren ihre Operanden gegebenenfalls implizit. Arithmetische Operatoren konvertieren ihre Operanden in den Typ `number` und geben einen Zahlenwert aus. Boolesche Operatoren konvertieren ihre Operanden in den Typ `boolean` und geben einen booleschen Wert aus. Relationale Operatoren und Gleichheitsoperatoren geben einen booleschen Wert aus. Allerdings verfügen sie, je nach dem ursprünglichen Datentyp ihrer Operanden, über unterschiedliche Konvertierungsregeln (siehe Tabelle).  
  
|Operand|Relationaler Operator|Gleichheitsoperator|  
|-------------|-------------------------|-----------------------|  
|Beide Operanden sind Knotensätze.|TRUE ist nur dann gegeben, wenn sich der eine Knoten in einem Satz und der andere Knoten im zweiten Satz befindet, sodass der Vergleich ihrer `string`-Werte TRUE ergibt.|Identisch.|  
|Bei dem einen handelt sich um einen Knotensatz, bei dem anderen um den Typ `string`.|TRUE ist nur dann gegeben, wenn sich ein Knoten im Knotensatz befindet und bei der Konvertierung in `number` der Vergleich mit dem in `string` konvertierten Datentyp `number` TRUE ergibt.|TRUE ist nur dann gegeben, wenn sich ein Knoten im Knotensatz befindet und bei der Konvertierung in `string` der Vergleich mit dem Typ `string` TRUE ergibt.|  
|Bei dem einen handelt sich um einen Knotensatz, bei dem anderen um den Typ `number`.|TRUE ist nur dann gegeben, wenn sich ein Knoten im Knotensatz befindet und bei der Konvertierung in `number` der Vergleich mit dem Typ `number` TRUE ergibt.|Identisch.|  
|Bei dem einen handelt sich um einen Knotensatz, bei dem anderen um den Typ `boolean`.|TRUE ist nur dann gegeben, wenn sich ein Knoten im Knotensatz befindet und bei der Konvertierung in `boolean` und anschließend in `number` der Vergleich mit dem in `boolean` konvertierten Typ `number` TRUE ergibt.|TRUE ist nur dann gegeben, wenn sich ein Knoten im Knotensatz befindet und bei der Konvertierung in `boolean` der Vergleich mit dem Typ `boolean` TRUE ergibt.|  
|In beiden Fällen handelt es sich nicht um einen Knotensatz.|Konvertieren Sie beide Operanden in den Typ `number`, und führen Sie dann einen Vergleich durch.|Konvertieren Sie beide Operanden in einen gängigen Typ , und führen Sie dann einen Vergleich durch. Führen Sie eine Konvertierung in den Typ `boolean` durch, wenn es sich um den Typ `boolean` handelt, oder in den Typ `number`, wenn es sich um den Typ `number` handelt. Andernfalls führen Sie eine Konvertierung in den Typ `string` durch.|  
  
> [!NOTE]  
>  Da relationale XPath-Operatoren ihre Operanden stets in den Typ `number` konvertieren, sind `string`-Vergleiche nicht möglich. Um Datenvergleiche zu ermöglichen, bietet SQL Server 2000 bei der XPath-Spezifikation folgende Möglichkeit: Wenn ein relationaler Operator einen Typ `string` mit einem Typ `string`, einen Knotensatz mit einem Typ `string` oder einen als Zeichenkette angegebenen Knotensatz mit einem als Zeichenkette angegebenen Knotensatz vergleicht, erfolgt ein `string`-Vergleich (kein `number`-Vergleich).  
  
## <a name="node-set-conversions"></a>Konvertierungen von Knotensätzen  
 Konvertierungen von Knotensätzen sind nicht immer intuitiv. Die Konvertierung eines Knotensatzes in den Typ `string` erfolgt anhand des Zeichenkettenwerts des ersten Knotens des Satzes. Bei der Konvertierung eines Knotensatzes in den Typ `number` wird dieser zunächst in den Typ `string` und anschließend der Typ `string` in den Typ `number` konvertiert. Ein Knotensatz wird in den Typ `boolean` konvertiert, indem sein Vorhandensein überprüft wird.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt bei Knotensätzen keine Positionalauswahl durch: Die XPath-Abfrage `Customer[3]` beispielsweise bezieht sich auf den dritten Kunden; eine solche Positionalauswahl wird in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht unterstützt. Aus diesem Grund wurden die Konvertierungen, bei denen gemäß XPath-Spezifikation ein Knotensatz in den Typ `string` oder in den Typ `number` konvertiert wird, nicht implementiert. Die Semantik von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bezieht sich auf "ein" Vorkommnis, während die XPath-Spezifikation "das erste" Vorkommnis bezeichnet. Zum Beispiel basiert auf der W3C-XPath-Spezifikation die XPath-Abfrage `Order[OrderDetail/@UnitPrice > 10.0]` wählt diese Aufträge mit dem ersten **OrderDetail** , besitzt eine **UnitPrice** größer als 10.0. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], diese XPath-Abfrage wählt diese Aufträge mit **OrderDetail** , besitzt eine **UnitPrice** größer als 10.0.  
  
 Bei Konvertierungen in den Typ `boolean` wird das Vorhandensein überprüft; aus diesem Grund entspricht die XPath-Abfrage `Products[@Discontinued=true()]` dem SQL-Ausdruck "Products.Discontinued is not null", nicht dem SQL-Ausdruck "Products.Discontinued = 1". Damit die Abfrage dem letztgenannten SQL-Ausdruck entspricht, konvertierten Sie den Knotensatz zunächst in einen anderen Typ als `boolean`, etwa `number`. Beispiel: `Products[number(@Discontinued) = true()]`.  
  
 Da die meisten Operatoren gemäß Definition als TRUE gelten, wenn sie für einen beliebigen oder einen einzigen der Knoten im Knotensatz TRUE sind, ergeben diese Operationen stets FALSE, wenn der Knotensatz leer ist. Wenn also A leer ist, gilt sowohl für `A = B` als auch `A != B` FALSE, für `not(A=B)` und `not(A!=B)` hingegen gilt TRUE.  
  
 In der Regel ist ein Attribut oder ein Element, das auf eine Spalte verweist, vorhanden, sobald der Wert jener Spalte in der Datenbank ungleich `null` ist. Elemente, die auf Zeilen verweisen, sind vorhanden, sobald untergeordnete Elemente vorhanden sind.  
  
> [!NOTE]  
>  Mit der `is-constant`-Anmerkung versehene Elemente sind immer vorhanden. Infolgedessen können XPath-Prädikate nicht für `is-constant`-Elemente verwendet werden.  
  
 Wenn ein Knotensatz in den Typ `string` oder `number` konvertiert wird, wird sein XDR-Typ (sofern vorhanden) im mit Anmerkungen versehenen Schema überprüft. Dieser Typ wird dann verwendet, um die erforderliche Konvertierung zu ermitteln.  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a>Zuordnung von XDR-Datentypen und XPath-Datentypen  
 Der XPath-Datentyp eines Knotens wird vom XDR-Datentyp im Schema abgeleitet, wie in der folgenden Tabelle dargestellt (der Knoten **EmployeeID** wird zur Veranschaulichung verwendet).  
  
|XDR-Datentyp|Entsprechung<br /><br /> XPath-Datentyp|Verwendete SQL Server-Konvertierung|  
|-------------------|------------------------------------|--------------------------------|  
|Nonebin.base64bin.hex|–|NoneEmployeeID|  
|boolean|boolean|CONVERT(bit, EmployeeID)|  
|number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8|number|CONVERT(float(53), EmployeeID)|  
|id, idref, idrefsentity, entities, enumerationnotation, nmtoken, nmtokens, chardate, Timedate, Time.tz, string, uri, uuid|Zeichenfolge|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|fixed14.4|– (es gibt keinen Datentyp in XPath, der dem fixed14.4 XDR-Datentyp entspricht)|CONVERT(money, EmployeeID)|  
|date|Zeichenfolge|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|Uhrzeit<br /><br /> time.tz|Zeichenfolge|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
 Das Datum und Uhrzeit-Konvertierungen sind für die Verwendung konzipiert, ob der Wert in der Datenbank gespeichert ist die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` -Datentyp oder einen `string`. Beachten Sie, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` -Datentyp verwendet keine `timezone` und eine geringere Genauigkeit als der XML-Code hat `time` -Datentyp. Um den `timezone`-Datentyp aufzunehmen oder eine höhere Genauigkeit zu gewährleisten, speichern Sie die Daten mithilfe eines `string`-Typs in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Wenn ein Knoten vom XDR-Datentyp in den XPath-Datentyp konvertiert wird, müssen mitunter weitere Konvertierungen vorgenommen werden (von einem XPath-Datentyp in einen anderen XPath-Datentyp). Ein Beispiel ist die folgende XPath-Abfrage:  
  
```  
(@m + 3) = 4  
```  
  
 Wenn @m wird von der `fixed14.4` XDR-Datentyp, die Konvertierung von XDR-Datentyp in XPath-Datentyp erfolgt über:  
  
```  
CONVERT(money, m)  
```  
  
 Bei dieser Konvertierung wird der Knoten `m` von `fixed14.4` in `money` konvertiert. Um den Wert 3 hinzuzufügen, ist jedoch eine zusätzliche Konvertierung erforderlich:  
  
```  
CONVERT(float(CONVERT(money, m))  
```  
  
 Der XPath-Ausdruck wird wie folgt ausgewertet:  
  
```  
CONVERT(float(CONVERT(money, m)) + CONVERT(float(53), 3) = CONVERT(float(53), 3)  
```  
  
 Wie in der folgenden Tabelle dargestellt, handelt es sich hierbei um die gleiche Konvertierung wie bei anderen XPath-Ausdrücken (etwa Literalausdrücken oder zusammengesetzten Ausdrücken).  
  
||||||  
|-|-|-|-|-|  
||X ist unbekannt|X ist vom Datentyp `string`|X ist vom Datentyp `number`|X ist vom Datentyp `boolean`|  
|string(X)|CONVERT (nvarchar(4000), X, 126)|-|CONVERT (nvarchar(4000), X, 126)|CASE WHEN X THEN N'true' ELSE N'false' END|  
|number(X)|CONVERT (float(53), X)|CONVERT (float(53), X)|-|CASE WHEN X THEN 1 ELSE 0 END|  
|boolean(X)|-|LEN(X) > 0|X != 0|-|  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a>A. Konvertieren Sie einen Datentyp in einer XPath-Abfrage  
 In der folgenden XPath-Abfrage für ein mit Anmerkungen versehene XSD-Schema angegeben, die Abfrage wählt alle **Mitarbeiter** Knoten mit der **EmployeeID** -Attributwert E-1, wobei "E-" das Präfix angegeben ist, mit der `sql:id-prefix` Anmerkung.  
  
 `Employee[@EmployeeID="E-1"]`  
  
 Das Prädikat in der Abfrage entspricht dem folgenden SQL-Ausdruck:  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 Da **EmployeeID** ist eine von der `id` (`idref`, `idrefs`, `nmtoken`, `nmtokens`usw.) Datentyp der Werte in der XSD-Schema **EmployeeID** ist Konvertiert die `string` XPath-Datentyp mithilfe der zuvor beschriebenen Konvertierungsregeln.  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 Der Zeichenfolge wird das Präfix "E-" hinzugefügt, und das Ergebnis wird dann mit `N'E-1'` verglichen.  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a>B. Führen Sie mehrere Datentypkonvertierungen in einer XPath-Abfrage aus  
 Betrachten Sie die folgende, für ein mit Anmerkungen versehenes XSD-Schema angegebene XPath-Abfrage: `OrderDetail[@UnitPrice * @OrderQty > 98]`  
  
 Diese XPath-Abfrage gibt alle dem  **\<OrderDetail >** Elemente das Prädikat erfüllen `@UnitPrice * @OrderQty > 98`. Wenn die **UnitPrice** mit versehen ist eine `fixed14.4` -Datentyp, in dem Schema mit Anmerkungen dieses Prädikat ist gleichbedeutend mit der SQL-Ausdruck:  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 Beim Konvertieren der Werte in der XPath-Abfrage wird zunächst der XDR-Datentyp in den XPath-Datentyp konvertiert. Da der XSD-Datentyp **UnitPrice** ist `fixed14.4`, wie in der obigen Tabelle beschrieben wird, ist dies die erste Konvertierung, die verwendet wird:  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 Da die arithmetischen Operatoren ihre Operanden in den `number`-XPath-Datentyp konvertieren, erfolgt eine zweite Konvertierung (von einem XPath-Datentyp in einen anderen XPath-Datentyp), bei der der Wert in `float(53)` konvertiert wird (`float(53)` ist nahe am `number`-XPath-Datentyp):  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 Vorausgesetzt, die **OrderQty** Attribut hat keine XSD-Datentyp **OrderQty** konvertiert eine `number` XPath-Datentyp in einer einzelkonvertierung:  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 Parallel dazu wird der Wert 98 in den `number`-XPath-Datentyp konvertiert:  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  Wenn der im Schema verwendete XSD-Datentyp mit dem in der Datenbank zugrunde gelegten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp inkompatibel ist oder eine nicht mögliche XPath-Datentypkonvertierung durchgeführt werden soll, sollte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Fehler melden. Z. B. wenn die **EmployeeID** mit dem Attribut versehen ist `id-prefix` Anmerkung XPath `Employee[@EmployeeID=1]` generiert einen Fehler, da **EmployeeID** hat die `id-prefix` Anmerkung und kann nicht konvertiert werden, um `number`.  
  
  