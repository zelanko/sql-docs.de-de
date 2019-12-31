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
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75247089"
---
# <a name="xpath-data-types-sqlxml-40"></a>XPath-Datentypen (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XPath und XML-Schema (XSD) weisen sehr unterschiedliche Datentypen auf. Zum Beispiel verfügt XPath nicht über Ganzzahl- oder Datumsdatentypen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und XSD hingegen über mehrere. XSD gibt Zeitwerte auf die Nanosekunde genau an, während die Genauigkeit von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] höchstens 1/300 Sekunde beträgt. Einen Datentyp einem anderen zuzuordnen ist deshalb nicht immer möglich. Weitere Informationen zum Mapping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Datentypen zu XSD-Datentypen finden Sie unter Datentyp Umwandlungen [und die SQL: datatype-Anmerkung &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 XPath verfügt über drei Datentypen: **Zeichenfolge**, **Zahl**und **boolescher**Wert. Der **Number** -Datentyp ist immer ein IEEE 754-Gleit Komma Wert mit doppelter Genauigkeit. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]float-Datentyp **(53)** entspricht der XPath- **Nummer**. **Float (53)** ist jedoch nicht exakt IEEE 754. Zum Beispiel wird weder NaN (Not-a-Number) noch Unendlichkeit verwendet. Der Versuch, eine nicht numerische Zeichenfolge in eine **Zahl** zu konvertieren, und versucht, durch Null zu teilen, führt zu einem Fehler.  
  
## <a name="xpath-conversions"></a>XPath-Konvertierungen  
 Wenn Sie eine XPath-Abfrage wie `OrderDetail[@UnitPrice > "10.0"]` verwenden, können implizite und explizite Datentypkonvertierungen den Sinn der Abfrage leicht verändern. Deshalb sollte nachvollzogen werden können, wie XPath-Datentypen implementiert werden. Die XPath-Sprachspezifikation, XML Path Language (XPath), Version 1,0 W3C, vorgeschlagene Empfehlung 8. Oktober 1999, finden Sie auf der W3C http://www.w3.org/TR/1999/PR-xpath-19991008.html-Website unter.  
  
 XPath-Operatoren werden in vier Kategorien unterteilt:  
  
-   Boolesche Operatoren (AND, OR)  
  
-   Relationale Operatoren (\<, \<#a0, =, >=)  
  
-   Gleichheitsoperatoren (=, !=)  
  
-   Arithmetische Operatoren (+, -, *, DIV, MOD)  
  
 Bei jeder Operatorkategorie werden die Operanden auf andere Art und Weise konvertiert. XPath-Operatoren konvertieren ihre Operanden gegebenenfalls implizit. Arithmetische Operatoren konvertieren ihre Operanden in **Number**und führen zu einem Zahlenwert. Boolesche Operatoren konvertieren ihre Operanden in einen **booleschen**Wert und führen zu einem booleschen Wert. Relationale Operatoren und Gleichheitsoperatoren geben einen booleschen Wert aus. Allerdings verfügen sie, je nach dem ursprünglichen Datentyp ihrer Operanden, über unterschiedliche Konvertierungsregeln (siehe Tabelle).  
  
|Operand|Relationaler Operator|Gleichheitsoperator|  
|-------------|-------------------------|-----------------------|  
|Beide Operanden sind Knotensätze.|True, wenn es sich um einen Knoten in einer Gruppe und einen Knoten in der zweiten Menge handelt, sodass der Vergleich der **Zeichen** folgen Werte true ist.|Identisch.|  
|Eine ist eine Knotengruppe, die andere eine **Zeichen**Folge.|True ist nur dann, wenn ein Knoten in der Knotengruppe vorhanden ist, sodass bei der Konvertierung in eine **Zahl**der Vergleich mit der **Zeichenfolge** , die in **Number** konvertiert wurde, den Wert true hat.|True, wenn ein Knoten im Knoten Satz vorhanden ist, der bei der Konvertierung in eine **Zeichen** **Folge den** Wert true hat.|  
|Eine ist eine Knotengruppe, die andere eine **Zahl**.|True **ist nur** dann, wenn ein Knoten im Knoten Satz vorhanden ist, der bei der Konvertierung in eine **Zahl**den Wert true hat.|Identisch.|  
|Eine ist eine Knotengruppe, die andere ein **boolescher**Wert.|True **ist nur** dann, wenn ein Knoten im Knoten Satz vorhanden ist, der bei der Konvertierung in einen **booleschen** Wert und dann in eine **Zahl**den Wert "true" mit dem **booleschen** Wert "true" hat.|True ist nur dann, wenn ein Knoten im Knoten Satz vorhanden ist, der bei der Konvertierung in einen **booleschen**Wert mit dem **booleschen** Wert true ist.|  
|In beiden Fällen handelt es sich nicht um einen Knotensatz.|Konvertieren Sie beide Operanden in **Number** , und vergleichen Sie dann.|Konvertieren Sie beide Operanden in einen gängigen Typ , und führen Sie dann einen Vergleich durch. Konvertieren in einen **booleschen** Wert, wenn einer der beiden Werte " **booleschen** **" ist,**" **Number** " Andernfalls konvertieren Sie in eine **Zeichenfolge**.|  
  
> [!NOTE]  
>  Da relationale XPath-Operatoren ihre Operanden immer in **Number**konvertieren, sind **Zeichen** folgen Vergleiche nicht möglich. Um Datums Vergleiche einzuschließen, bietet SQL Server 2000 diese Abweichung der XPath-Spezifikation: Wenn ein relationaler Operator eine **Zeichen** Folge mit einer **Zeichen**Folge vergleicht, eine Knotengruppe auf eine **Zeichen**Folge oder ein Knoten mit Zeichen folgen Wert auf einen Knoten Satz mit Zeichen folgen Wert festgelegt ist, wird ein **Zeichen** folgen Vergleich (kein **Zahlen** Vergleich) durchgeführt.  
  
## <a name="node-set-conversions"></a>Konvertierungen von Knotensätzen  
 Konvertierungen von Knotensätzen sind nicht immer intuitiv. Eine Knotengruppe wird in eine **Zeichenfolge** konvertiert, indem der Zeichen folgen Wert des ersten Knotens im Satz übernommen wird. Eine Knotengruppe wird in eine **Zahl** konvertiert, indem Sie in eine **Zeichenfolge**konvertiert und anschließend eine **Zeichenfolge** in eine **Zahl**konvertiert wird. Eine Knotengruppe wird in einen **booleschen** Wert konvertiert, indem überprüft wird, ob Sie vorhanden ist.  
  
> [!NOTE]  
>  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt bei Knotensätzen keine Positionalauswahl durch: Die XPath-Abfrage `Customer[3]` beispielsweise bezieht sich auf den dritten Kunden; eine solche Positionalauswahl wird in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht unterstützt. Aus diesem Grund werden die in der XPath-Spezifikation beschriebenen Konvertierungen von Knoten Satz zu**Zeichen** folgen oder Knoten Satz-zu-**Zahlen** nicht implementiert. Die Semantik von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bezieht sich auf "ein" Vorkommnis, während die XPath-Spezifikation "das erste" Vorkommnis bezeichnet. Beispielsweise wählt die XPath-Abfrage `Order[OrderDetail/@UnitPrice > 10.0]` basierend auf der W3C-XPath-Spezifikation diese Bestellungen mit dem ersten **OrderDetail** aus, das einen **UnitPrice** größer als 10,0 hat. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]wählt diese XPath-Abfrage diese Bestellungen mit allen **OrderDetails** aus, deren **UnitPrice** größer als 10,0 ist.  
  
 Die Konvertierung in einen **booleschen** Wert generiert einen Existenz Test. Daher entspricht die XPath- `Products[@Discontinued=true()]` Abfrage dem SQL-Ausdruck "Products. nicht eingestellt is not NULL", nicht dem SQL-Ausdruck "Products. nicht eingestellt = 1". Um die Abfrage dem letzteren SQL-Ausdruck entsprechend zu entsprechen, konvertieren Sie zunächst den Knoten Satz in einen nicht**booleschen** Typ, wie z. b. **Number**. Beispiel: `Products[number(@Discontinued) = true()]`.  
  
 Da die meisten Operatoren gemäß Definition als TRUE gelten, wenn sie für einen beliebigen oder einen einzigen der Knoten im Knotensatz TRUE sind, ergeben diese Operationen stets FALSE, wenn der Knotensatz leer ist. Wenn also A leer ist, gilt sowohl für `A = B` als auch `A != B` FALSE, für `not(A=B)` und `not(A!=B)` hingegen gilt TRUE.  
  
 Normalerweise ist ein Attribut oder Element, das einer Spalte zugeordnet ist, vorhanden, wenn der Wert dieser Spalte in der Datenbank nicht **null**ist. Elemente, die auf Zeilen verweisen, sind vorhanden, sobald untergeordnete Elemente vorhanden sind.  
  
> [!NOTE]  
>  Elemente, die mit **is-constant** kommentiert werden, sind immer vorhanden. Folglich können XPath-Prädikate nicht für **is-constant-** Elemente verwendet werden.  
  
 Wenn eine Knotengruppe in eine **Zeichenfolge** oder eine **Zahl**konvertiert wird, wird der zugehörige XDR-Typ (sofern vorhanden) im Schema mit Anmerkungen überprüft. dieser Typ wird verwendet, um die erforderliche Konvertierung zu bestimmen.  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a>Zuordnung von XDR-Datentypen und XPath-Datentypen  
 Der XPath-Datentyp eines Knotens wird vom XDR-Datentyp im Schema abgeleitet, wie in der folgenden Tabelle dargestellt ( **die Knoten Mitarbeiter** -ID wird zur Veranschaulichung verwendet).  
  
|XDR-Datentyp|Entsprechung<br /><br /> XPath-Datentyp|Verwendete SQL Server-Konvertierung|  
|-------------------|------------------------------------|--------------------------------|  
|Nonebin.base64bin.hex|Nicht zutreffend|KeineEmployeeID|  
|boolean|boolean|CONVERT(bit, EmployeeID)|  
|number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8|number|CONVERT(float(53), EmployeeID)|  
|id, idref, idrefsentity, entities, enumerationnotation, nmtoken, nmtokens, chardate, Timedate, Time.tz, string, uri, uuid|string|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|fixed14.4|– (es gibt keinen Datentyp in XPath, der dem fixed14.4 XDR-Datentyp entspricht)|CONVERT(money, EmployeeID)|  
|date|string|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|in<br /><br /> time.tz|string|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
 Die Datums-und Uhrzeit Konvertierungen sind so konzipiert, dass Sie funktionieren, ob der Wert in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]der Datenbank mit dem **DateTime-Datentyp** oder einer **Zeichenfolge**gespeichert wird. Beachten Sie, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dass der **DateTime-Datentyp** keine **Zeitzone** verwendet und eine geringere Genauigkeit aufweist als der XML- **Zeit** Datentyp. Wenn Sie den **Zeitzone** -Datentyp oder die zusätzliche Genauigkeit einschließen möchten, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] speichern Sie die Daten in mithilfe eines **Zeichen** folgen Typs.  
  
 Wenn ein Knoten vom XDR-Datentyp in den XPath-Datentyp konvertiert wird, müssen mitunter weitere Konvertierungen vorgenommen werden (von einem XPath-Datentyp in einen anderen XPath-Datentyp). Ein Beispiel ist die folgende XPath-Abfrage:  
  
```  
(@m + 3) = 4  
```  
  
 Wenn @m den Fixed-XDR-Datentyp " **14,4** " hat, wird die Konvertierung vom XDR-Datentyp in den XPath-Datentyp mit folgenden Aktionen durchgeführt:  
  
```  
CONVERT(money, m)  
```  
  
 Bei dieser Konvertierung wird der Knoten `m` von **Fixed 14,4** in **Money**konvertiert. Um den Wert 3 hinzuzufügen, ist jedoch eine zusätzliche Konvertierung erforderlich:  
  
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
||X ist unbekannt|X ist **Zeichenfolge**|X ist **Zahl**|X ist ein **boolescher** Wert.|  
|string(X)|CONVERT (nvarchar(4000), X, 126)|-|CONVERT (nvarchar(4000), X, 126)|CASE WHEN X THEN N'true' ELSE N'false' END|  
|number(X)|CONVERT (float(53), X)|CONVERT (float(53), X)|-|CASE WHEN X THEN 1 ELSE 0 END|  
|boolean(X)|-|LEN (X) #a0 0|X != 0|-|  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a>A. Konvertieren Sie einen Datentyp in einer XPath-Abfrage  
 In der folgenden XPath-Abfrage, die für ein mit Anmerkungen versehene XSD-Schema angegeben ist, wählt die Abfrage alle Employee-Knoten mit dem **Employee** **Eid** -Attribut Wert "e-1" aus, wobei "e-" das Präfix ist, das mit der **SQL: id-prefix-** Anmerkung angegeben wird.  
  
 `Employee[@EmployeeID="E-1"]`  
  
 Das Prädikat in der Abfrage entspricht dem folgenden SQL-Ausdruck:  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 Da Mitarbeiter **Eid** einer der ID-Werte (**IDREF**, **IDREFS**, **NMTOKEN**, **NMTOKENS**usw.) im XSD-Schema **ist, wird** die Mitarbeiter- **ID** mithilfe der zuvor beschriebenen Konvertierungsregeln in den XPath-Datentyp **String** konvertiert.  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 Der Zeichenfolge wird das Präfix "E-" hinzugefügt, und das Ergebnis wird dann mit `N'E-1'` verglichen.  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a>B: Führen Sie mehrere Datentypkonvertierungen in einer XPath-Abfrage aus  
 Betrachten Sie die folgende, für ein mit Anmerkungen versehenes XSD-Schema angegebene XPath-Abfrage: `OrderDetail[@UnitPrice * @OrderQty > 98]`  
  
 Diese XPath-Abfrage gibt alle ** \<OrderDetail->** Elemente zurück, die `@UnitPrice * @OrderQty > 98`das Prädikat erfüllen. Wenn der **UnitPrice** mit einem **festgelegten 14,4** -Datentyp im Schema mit Anmerkungen versehen wird, entspricht dieses Prädikat dem SQL-Ausdruck:  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 Beim Konvertieren der Werte in der XPath-Abfrage wird zunächst der XDR-Datentyp in den XPath-Datentyp konvertiert. Da der XSD-Datentyp von **UnitPrice** **festgelegt**ist, wie in der vorherigen Tabelle beschrieben, ist dies die erste verwendete Konvertierung:  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 Da die arithmetischen Operatoren ihre Operanden in den **Number** XPath-Datentyp konvertieren, wird die zweite Konvertierung (von einem XPath-Datentyp in einen anderen XPath-Datentyp) angewendet, in der der Wert in **float (53)** konvertiert wird (**float (53)** entspricht dem Datentyp "XPath **Number** "):  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 Wenn das **OrderQty** -Attribut keinen XSD-Datentyp aufweist, wird **OrderQty** in einer einzelnen Konvertierung in einen **Number** -XPath-Datentyp konvertiert:  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 Entsprechend wird der Wert 98 in den Datentyp **Number** XPath konvertiert:  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  Wenn der im Schema verwendete XSD-Datentyp mit dem in der Datenbank zugrunde gelegten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp inkompatibel ist oder eine nicht mögliche XPath-Datentypkonvertierung durchgeführt werden soll, sollte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Fehler melden. Wenn das Mitarbeiter-ID- **Attribut z** . b. mit der **ID-Präfix** Anmerkung versehen ist, generiert `Employee[@EmployeeID=1]` XPath einen Fehler, **da die** Mitarbeiter-ID über die **ID-Präfix-** Anmerkung verfügt und nicht in **Number**konvertiert werden kann.  
  
  
