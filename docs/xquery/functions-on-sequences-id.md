---
title: ID-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:id function
- id function
ms.assetid: de99fc60-d0ad-4117-a17d-02bdde6512b4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 80bb427800f57ddaa07e5e53f21b03df9e8317d3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62933698"
---
# <a name="functions-on-sequences---id"></a>Funktionen für Sequenzen – id
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt die Sequenz der Elementknoten mit xs: ID-Werte, die die Werte eines oder mehrerer der xs: IDREF-Werte im angegebenen entsprechen *$arg*.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:id($arg as xs:IDREF*) as element()*  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Ein oder mehrere xs:IDREF-Werte.  
  
## <a name="remarks"></a>Hinweise  
 Das Ergebnis der Funktion ist eine Sequenz von Elementen in der XML-Instanz in der Dokumentreihenfolge, die einen xs:ID-Wert gleich einem oder mehreren xs:IDREF-Werten in der Liste der xs:IDREF-Kandidaten besitzt.  
  
 Wenn der xs:IDREF-Wert keinem Element entspricht, gibt die Funktion die leere Sequenz zurück.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen, die in verschiedenen gespeichert sind **Xml** -Typspalten in der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] Datenbank.  
  
### <a name="a-retrieving-elements-based-on-the-idref-attribute-value"></a>A. Abrufen von Elementen anhand des Werts des IDREF-Attributs  
 Im folgenden Beispiel wird die Fn: ID zum Abrufen der <`employee`> Elemente basierend auf dem IDREF-Manager-Attribut. In diesem Beispiel ist das Manager-Attribut ein Attribut vom Typ IDREF, und das eid-Attribut ist ein Attribut vom Typ ID.  
  
 Für einen bestimmten Manager Attribut-Wert der **id()** -Funktion sucht die <`employee`>-Element, dessen ID-typattributwert, den eingegebenen IDREF-Wert übereinstimmt. Das heißt, für einen bestimmten Mitarbeiter die **id()** Funktion gibt die Mitarbeiter-Manager zurück.  
  
 Im Beispiel geschieht Folgendes:  
  
-   Es wird eine XML-Schemaauflistung erstellt.  
  
-   Eine typisierte **Xml** Variable wird mithilfe der XML-schemaauflistung erstellt.  
  
-   Die Abfrage ruft das Element mit dem ID-Attributwert, der auf die verwiesen wird durch die **Manager** IDREF-Attribut von der <`employee`> Element.  
  
```  
-- If exists, drop the XML schema collection (SC).  
-- drop xml schema collection SC  
-- go  
  
create xml schema collection SC as  
'<schema xmlns="http://www.w3.org/2001/XMLSchema" xmlns:e="emp" targetNamespace="emp">  
            <element name="employees" type="e:EmployeesType"/>  
            <complexType name="EmployeesType">  
                 <sequence>  
                      <element name="employee" type="e:EmployeeType" minOccurs="0" maxOccurs="unbounded" />  
                 </sequence>  
            </complexType>    
  
            <complexType name="EmployeeType">  
                        <attribute name="eid" type="ID" />  
                        <attribute name="name" type="string" />  
                        <attribute name="manager" type="IDREF" />  
            </complexType>         
</schema>'  
go  
```  
  
```  
declare @x xml(SC)  
set @x='<e:employees xmlns:e="emp">  
<employee eid="e1" name="Joe" manager="e10" />  
<employee eid="e2" name="Bob" manager="e10" />  
<employee eid="e10" name="Dave" manager="e10" />  
</e:employees>'  
  
select @x.value(' declare namespace e="emp";   
 (fn:id(e:employees/employee[@name="Joe"]/@manager)/@name)[1]', 'varchar(50)')   
Go  
```  
  
 Die Abfrage gibt "Dave" als Wert zurück. Dies gibt an, dass Dave Joes Manager ist.  
  
### <a name="b-retrieving-elements-based-on-the-orderlist-idrefs-attribute-value"></a>B. Abrufen von Elementen anhand des Werts des IDREFS-Attributs von OrderList  
 Im folgenden Beispiel ist das OrderList-Attribut von der <`Customer`>-Element ist ein Attribut des IDREFS-Typ. Es listet die Bestellungs-IDs für diesen bestimmten Kunden auf. Für jede ORDER_ID ist ein <`Order`> untergeordneten Elements unter dem <`Customer`> mit dem entsprechenden Wert.  
  
 Der Abfrageausdruck `data(CustOrders:Customers/Customer[1]/@OrderList)[1]` ruft den ersten Wert aus der IDRES-Liste für den ersten Kunden ab. Dieser Wert wird dann zum Übergeben der **id()** Funktion. Die Funktion sucht dann nach dem <`Order`> Element, dessen OrderID-Attributwert der Eingabe, um entspricht, die **id()** Funktion.  
  
```  
drop xml schema collection SC  
go  
create xml schema collection SC as  
'<schema xmlns="http://www.w3.org/2001/XMLSchema" xmlns:Customers="Customers" targetNamespace="Customers">  
            <element name="Customers" type="Customers:CustomersType"/>  
            <complexType name="CustomersType">  
                        <sequence>  
                            <element name="Customer" type="Customers:CustomerType" minOccurs="0" maxOccurs="unbounded" />  
                        </sequence>  
            </complexType>  
             <complexType name="OrderType">  
                <sequence minOccurs="0" maxOccurs="unbounded">  
                            <choice>  
                                <element name="OrderValue" type="integer" minOccurs="0" maxOccurs="unbounded"/>  
                            </choice>  
                </sequence>                                             
                <attribute name="OrderID" type="ID" />  
            </complexType>  
  
            <complexType name="CustomerType">  
                <sequence minOccurs="0" maxOccurs="unbounded">  
                            <choice>  
                                <element name="spouse" type="string" minOccurs="0" maxOccurs="unbounded"/>  
                                <element name="Order" type="Customers:OrderType" minOccurs="0" maxOccurs="unbounded"/>  
                            </choice>  
                </sequence>                                             
                <attribute name="CustomerID" type="string" />  
                <attribute name="OrderList" type="IDREFS" />  
            </complexType>  
 </schema>'  
go  
declare @x xml(SC)  
set @x='<CustOrders:Customers xmlns:CustOrders="Customers">  
                <Customer CustomerID="C1" OrderList="OrderA OrderB"  >  
                              <spouse>Jenny</spouse>  
                                <Order OrderID="OrderA"><OrderValue>11</OrderValue></Order>  
                                <Order OrderID="OrderB"><OrderValue>22</OrderValue></Order>  
  
                </Customer>  
                <Customer CustomerID="C2" OrderList="OrderC OrderD" >  
                                <spouse>John</spouse>  
                                <Order OrderID="OrderC"><OrderValue>33</OrderValue></Order>  
                                <Order OrderID="OrderD"><OrderValue>44</OrderValue></Order>  
  
                        </Customer>  
                <Customer CustomerID="C3"  OrderList="OrderE OrderF" >  
                                <spouse>Jane</spouse>  
                                <Order OrderID="OrderE"><OrderValue>55</OrderValue></Order>  
                                <Order OrderID="OrderF"><OrderValue>55</OrderValue></Order>  
                </Customer>  
                <Customer CustomerID="C4"  OrderList="OrderG"  >  
                                <spouse>Tim</spouse>  
                                <Order OrderID="OrderG"><OrderValue>66</OrderValue></Order>  
                        </Customer>  
                <Customer CustomerID="C5"  >  
                </Customer>  
                <Customer CustomerID="C6" >  
                </Customer>  
                <Customer CustomerID="C7"  >  
                </Customer>  
</CustOrders:Customers>'  
select @x.query('declare namespace CustOrders="Customers";  
  id(data(CustOrders:Customers/Customer[1]/@OrderList)[1])')  
  
-- result  
<Order OrderID="OrderA">  
  <OrderValue>11</OrderValue>  
</Order>  
```  
  
### <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unterstützt nicht die zwei Argumenten-Version des **id()**.  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] muss dem Argumenttyp der **id()** ein Untertyp von xs: IDREF * sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen für Sequenzen](https://msdn.microsoft.com/library/672d2795-53ab-49c2-bf24-bc81a47ecd3f)  
  
  
