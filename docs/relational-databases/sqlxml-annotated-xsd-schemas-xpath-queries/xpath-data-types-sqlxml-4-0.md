---
title: XPath-Datentypen (SQLXML)
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
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
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 089b2b006d0159c63e480c8627762ac37dec98b8
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "75247089"
---
# <a name="xpath-data-types-sqlxml-40"></a>XPath-Datentypen (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XPath und XML Schema (XSD) haben sehr unterschiedliche Datentypen. Zum Beispiel verfügt XPath nicht über Ganzzahl- oder Datumsdatentypen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und XSD hingegen über mehrere. XSD gibt Zeitwerte auf die Nanosekunde genau an, während die Genauigkeit von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] höchstens 1/300 Sekunde beträgt. Einen Datentyp einem anderen zuzuordnen ist deshalb nicht immer möglich. Weitere Informationen zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Zuordnen von Datentypen zu XSD-Datentypen finden Sie unter [Datentyp-Coercions und den sql:datatype Annotation &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 XPath hat drei Datentypen: **string**, **number**und **boolean**. Der **Zahlendatentyp** ist immer ein GLEitkomma wert. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **float(53)-Datentyp** ist der XPath-Nummer am nächsten. **number** **Float(53)** ist jedoch nicht genau IEEE 754. Zum Beispiel wird weder NaN (Not-a-Number) noch Unendlichkeit verwendet. Der Versuch, eine nicht numerische Zeichenfolge in **zahlzuzahlen** und zu versuchen, durch Null zu dividieren, führt zu einem Fehler.  
  
## <a name="xpath-conversions"></a>XPath-Konvertierungen  
 Wenn Sie eine XPath-Abfrage wie `OrderDetail[@UnitPrice > "10.0"]` verwenden, können implizite und explizite Datentypkonvertierungen den Sinn der Abfrage leicht verändern. Deshalb sollte nachvollzogen werden können, wie XPath-Datentypen implementiert werden. Die XPath-Sprachspezifikation, XML Path Language (XPath) Version 1.0 W3C Proposed Recommendation 8 October 1999, finden Sie auf der W3C-Website unter http://www.w3.org/TR/1999/PR-xpath-19991008.html.  
  
 XPath-Operatoren werden in vier Kategorien unterteilt:  
  
-   Boolesche Operatoren (AND, OR)  
  
-   Relationale Operatoren\<( \<, >, =, >=)  
  
-   Gleichheitsoperatoren (=, !=)  
  
-   Arithmetische Operatoren (+, -, *, DIV, MOD)  
  
 Bei jeder Operatorkategorie werden die Operanden auf andere Art und Weise konvertiert. XPath-Operatoren konvertieren ihre Operanden gegebenenfalls implizit. Arithmetische Operatoren konvertieren ihre Operanden in **Zahl**und ergeben einen Zahlenwert. Boolesche Operatoren konvertieren ihre Operanden in **boolesche**und führen zu einem booleschen Wert. Relationale Operatoren und Gleichheitsoperatoren geben einen booleschen Wert aus. Allerdings verfügen sie, je nach dem ursprünglichen Datentyp ihrer Operanden, über unterschiedliche Konvertierungsregeln (siehe Tabelle).  
  
|Operand|Relationaler Operator|Gleichheitsoperator|  
|-------------|-------------------------|-----------------------|  
|Beide Operanden sind Knotensätze.|TRUE, wenn und nur wenn ein Knoten in einem Satz und ein Knoten im zweiten Satz vorhanden ist, so dass der Vergleich ihrer **Zeichenfolgenwerte** TRUE ist.|Identisch.|  
|Der eine ist ein Knotensatz, das andere eine **Zeichenfolge.**|TRUE wenn und nur wenn ein Knoten im Knotensatz vorhanden ist, so dass, wenn er in **zahl**konvertiert wird, der Vergleich mit der in **Zahl** konvertierten **Zeichenfolge** TRUE ist.|TRUE wenn und nur wenn ein Knoten im Knotensatz vorhanden ist, so dass der Vergleich mit der **Zeichenfolge** TRUE ist, wenn er in **string**konvertiert wird.|  
|Der eine ist ein Knotensatz, das andere eine **Zahl.**|TRUE, wenn und nur wenn ein Knoten im Knotensatz vorhanden ist, so dass der Vergleich mit der **Zahl** TRUE ist, wenn er in **zahl**konvertiert wird.|Identisch.|  
|Der eine ist ein Knotensatz, das andere ein **boolesches**.|TRUE wenn und nur wenn ein Knoten im Knotensatz vorhanden ist, so dass der Vergleich mit dem **booleschen,** in **Zahl** konvertierten Knoten, wenn er in **boolesche** und dann in **Zahl**konvertiert wird, TRUE ist.|TRUE, wenn und nur wenn ein Knoten im Knotensatz vorhanden ist, so dass der Vergleich mit dem **booleschen** Wert TRUE ist, wenn er in **boolesche**konvertiert wird.|  
|In beiden Fällen handelt es sich nicht um einen Knotensatz.|Konvertieren Sie beide Operanden in **Zahlen,** und vergleichen Sie sie dann.|Konvertieren Sie beide Operanden in einen gängigen Typ , und führen Sie dann einen Vergleich durch. Konvertieren Sie in **boolesche,** wenn entweder **boolesche**, **Zahl,** wenn entweder **nummer**ist ; Andernfalls konvertieren Sie in **String**.|  
  
> [!NOTE]  
>  Da relationale XPath-Operatoren ihre Operanden immer in **Anzahl**konvertieren, sind **Zeichenfolgenvergleiche** nicht möglich. Um Datumsvergleiche einzuschließen, bietet SQL Server 2000 diese Variation zur XPath-Spezifikation: Wenn ein relationaler Operator eine **Zeichenfolge** mit einer **Zeichenfolge,** einen Knotensatz mit einer **Zeichenfolge**oder einen Knotensatz mit Zeichenfolgenwert auf einen Knotensatz mit Zeichenfolgenwert vergleicht, wird ein **Zeichenfolgenvergleich** (kein **Zahlenvergleich)** durchgeführt.  
  
## <a name="node-set-conversions"></a>Konvertierungen von Knotensätzen  
 Konvertierungen von Knotensätzen sind nicht immer intuitiv. Ein Knotensatz wird in eine **Zeichenfolge** konvertiert, indem nur der Zeichenfolgenwert des ersten Knotens in der Gruppe verwendet wird. Ein Knotensatz wird in **Zahl** konvertiert, indem er in **string**konvertiert und dann **Zeichenfolge** in **Zahl**konvertiert wird. Ein Knotensatz wird durch Testen auf seine Existenz in **boolesch** konvertiert.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt bei Knotensätzen keine Positionalauswahl durch: Die XPath-Abfrage `Customer[3]` beispielsweise bezieht sich auf den dritten Kunden; eine solche Positionalauswahl wird in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht unterstützt. Daher werden die in der**string** XPath-Spezifikation beschriebenen Knoten-Set-to-String- oder Node-Set-to-Number-Konvertierungen nicht implementiert.**number** Die Semantik von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bezieht sich auf "ein" Vorkommnis, während die XPath-Spezifikation "das erste" Vorkommnis bezeichnet. Beispielsweise wählt die XPath-Abfrage `Order[OrderDetail/@UnitPrice > 10.0]` basierend auf der W3C XPath-Spezifikation die Aufträge mit dem ersten **OrderDetail** aus, das einen **UnitPrice** größer als 10,0 hat. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]wählt diese XPath-Abfrage die Aufträge mit **orderDetail** aus, die einen **UnitPrice** größer als 10,0 haben.  
  
 Die Konvertierung in **boolesch** generiert einen Existenztest. Daher entspricht die `Products[@Discontinued=true()]` XPath-Abfrage dem SQL-Ausdruck "Products.Discontinued is not null", nicht dem SQL-Ausdruck "Products.Discontinued = 1". Um die Abfrage dem letztgenannten SQL-Ausdruck zu entsprechen, konvertieren Sie zuerst den Knotensatz in einen nicht**booleschen** Typ, z. B. **number**. Beispiel: `Products[number(@Discontinued) = true()]`.  
  
 Da die meisten Operatoren gemäß Definition als TRUE gelten, wenn sie für einen beliebigen oder einen einzigen der Knoten im Knotensatz TRUE sind, ergeben diese Operationen stets FALSE, wenn der Knotensatz leer ist. Wenn also A leer ist, gilt sowohl für `A = B` als auch `A != B` FALSE, für `not(A=B)` und `not(A!=B)` hingegen gilt TRUE.  
  
 Normalerweise ist ein Attribut oder Element vorhanden, das einer Spalte zugeordnet ist, wenn der Wert dieser Spalte in der Datenbank nicht **null**ist. Elemente, die auf Zeilen verweisen, sind vorhanden, sobald untergeordnete Elemente vorhanden sind.  
  
> [!NOTE]  
>  Elemente, die mit **is-constant** mit Anmerkungen benotet werden, sind immer vorhanden. Daher können XPath-Prädikate nicht für **is-konstante** Elemente verwendet werden.  
  
 Wenn ein Knotensatz in **Zeichenfolge** oder **Zahl**konvertiert wird, wird sein XDR-Typ (falls vorhanden) im mitAnmerkungsschema überprüft, und dieser Typ wird verwendet, um die erforderliche Konvertierung zu bestimmen.  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a>Zuordnung von XDR-Datentypen und XPath-Datentypen  
 Der XPath-Datentyp eines Knotens wird vom XDR-Datentyp im Schema abgeleitet, wie in der folgenden Tabelle dargestellt (der Knoten **EmployeeID** wird zur Veranschaulichung verwendet).  
  
|XDR-Datentyp|Entsprechung<br /><br /> XPath-Datentyp|Verwendete SQL Server-Konvertierung|  
|-------------------|------------------------------------|--------------------------------|  
|Nonebin.base64bin.hex|–|KeineEmployeeID|  
|boolean|boolean|CONVERT(bit, EmployeeID)|  
|number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8|number|CONVERT(float(53), EmployeeID)|  
|id, idref, idrefsentity, entities, enumerationnotation, nmtoken, nmtokens, chardate, Timedate, Time.tz, string, uri, uuid|Zeichenfolge|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|fixed14.4|– (es gibt keinen Datentyp in XPath, der dem fixed14.4 XDR-Datentyp entspricht)|CONVERT(money, EmployeeID)|  
|date|Zeichenfolge|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|time<br /><br /> time.tz|Zeichenfolge|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
 Die Datums- und Uhrzeitkonvertierungen sind so konzipiert, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dass unabhängig davon, ob der Wert mithilfe des **Datetime-Datentyps** oder einer **Zeichenfolge**in der Datenbank gespeichert wird. Beachten Sie, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]der **Datetime-Datentyp** keine **Zeitzone** verwendet und eine geringere Genauigkeit als der XML-Zeitdatentyp hat. **time** Um den **Zeitzonendatentyp** oder zusätzliche Genauigkeit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einzuschließen, speichern Sie die Daten mithilfe eines **Zeichenfolgentyps.**  
  
 Wenn ein Knoten vom XDR-Datentyp in den XPath-Datentyp konvertiert wird, müssen mitunter weitere Konvertierungen vorgenommen werden (von einem XPath-Datentyp in einen anderen XPath-Datentyp). Ein Beispiel ist die folgende XPath-Abfrage:  
  
```  
(@m + 3) = 4  
```  
  
 Wenn @m es sich um den **fixed14.4** XDR-Datentyp handelt, erfolgt die Konvertierung vom XDR-Datentyp in den XPath-Datentyp mit:  
  
```  
CONVERT(money, m)  
```  
  
 Bei dieser Konvertierung `m` wird der Knoten von **fixed14.4** in **money**konvertiert. Um den Wert 3 hinzuzufügen, ist jedoch eine zusätzliche Konvertierung erforderlich:  
  
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
||X ist unbekannt|X ist **String**|X ist **die Zahl**|X ist **boolesch**|  
|string(X)|CONVERT (nvarchar(4000), X, 126)|-|CONVERT (nvarchar(4000), X, 126)|CASE WHEN X THEN N'true' ELSE N'false' END|  
|number(X)|CONVERT (float(53), X)|CONVERT (float(53), X)|-|CASE WHEN X THEN 1 ELSE 0 END|  
|boolean(X)|-|LEN(X) > 0|X != 0|-|  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a>A. Konvertieren Sie einen Datentyp in einer XPath-Abfrage  
 In der folgenden XPath-Abfrage, die für ein mit Anmerkungen versehenes XSD-Schema angegeben wurde, wählt die Abfrage alle **Employee-Knoten** mit dem **EmployeeID-Attributwert** Von E-1 aus, wobei "E-" das Präfix ist, das mit der anderkten **sql:id-prefix** angegeben wird.  
  
 `Employee[@EmployeeID="E-1"]`  
  
 Das Prädikat in der Abfrage entspricht dem folgenden SQL-Ausdruck:  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 Da **EmployeeID** einer der **Datentypwerte id** (**idref**, **idrefs**, **nmtokens**usw.) im XSD-Schema ist, wird **EmployeeID** mithilfe der zuvor beschriebenen Konvertierungsregeln in den **Zeichenfolgen-XPath-Datentyp** konvertiert. **nmtokens**  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 Der Zeichenfolge wird das Präfix "E-" hinzugefügt, und das Ergebnis wird dann mit `N'E-1'` verglichen.  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a>B. Führen Sie mehrere Datentypkonvertierungen in einer XPath-Abfrage aus  
 Betrachten Sie die folgende, für ein mit Anmerkungen versehenes XSD-Schema angegebene XPath-Abfrage: `OrderDetail[@UnitPrice * @OrderQty > 98]`  
  
 Diese XPath-Abfrage gibt alle ** \<OrderDetail->** `@UnitPrice * @OrderQty > 98`Elemente zurück, die das Prädikat erfüllen. Wenn der **UnitPrice** mit einem **fixed14.4-Datentyp** im annotierten Schema mit Anmerkungen mit Anmerkungen bezeichnet wird, entspricht dieses Prädikat dem SQL-Ausdruck:  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 Beim Konvertieren der Werte in der XPath-Abfrage wird zunächst der XDR-Datentyp in den XPath-Datentyp konvertiert. Da der XSD-Datentyp von **UnitPrice** **festist14.4**, wie in der vorherigen Tabelle beschrieben, ist dies die erste Konvertierung, die verwendet wird:  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 Da die arithmetischen Operatoren ihre Operanden in die **Nummer** XPath-Datentyp konvertieren, wird die zweite Konvertierung (von einem XPath-Datentyp in einen anderen XPath-Datentyp) angewendet, bei der der Wert in **float(53)** **(float(53)** in der Nähe des XPath-Zahlendatentyps konvertiert wird: **number**  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 Unter der Annahme, dass das **OrderQty-Attribut** keinen XSD-Datentyp hat, wird **OrderQty** in einer einzigen Konvertierung in eine **Zahl** xPath-Datentyp konvertiert:  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 Ebenso wird der Wert 98 in die **Nummer** XPath-Datentyp konvertiert:  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  Wenn der im Schema verwendete XSD-Datentyp mit dem in der Datenbank zugrunde gelegten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp inkompatibel ist oder eine nicht mögliche XPath-Datentypkonvertierung durchgeführt werden soll, sollte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Fehler melden. Wenn das **EmployeeID-Attribut** z. B. mit der Anmerkung mit **id-prefix-Anmerkungen** versehen `Employee[@EmployeeID=1]` wird, generiert XPath einen Fehler, da **EmployeeID** über die **Annotation id-prefix** verfügt und nicht in die **Zahl**konvertiert werden kann.  
  
  
