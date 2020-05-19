---
title: Angeben von Achsen in XPath-Abfragen (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- context node [SQLXML]
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- axes [SQLXML]
ms.assetid: d17b8278-da58-4576-95b4-7a92772566d8
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8adf10727478344216da05ea982a466daa0eba63
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717828"
---
# <a name="specifying-axes-in-xpath-queries-sqlxml-40"></a>Angeben von Achsen in XPath-Abfragen (SQLXML 4.0)
  In den folgenden Beispielen wird gezeigt, wie Achsen in XPath-Abfragen angegeben werden.  
  
 Die XPath-Abfragen in diesen Beispielen werden für das in SampleSchema1.xml enthaltene Zuordnungsschema angegeben. Weitere Informationen zu diesem Beispiel Schema finden Sie unter [Beispiel: XSD-Schema mit Anmerkungen für XPath-Beispiele &#40;SQLXML 4,0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-retrieve-child-elements-of-the-context-node"></a>A. Abrufen von untergeordneten Elementen des Kontextknotens  
 Die folgende XPath-Abfrage wählt alle ** \< Kontakte>** untergeordneten Elementen des Kontext Knotens aus:  
  
```  
/child::Contact  
```  
  
 In der Abfrage `child` ist die Achse und `Contact` ist der Knoten Test (true, wenn `Contact` ein ** \< Element>** Knoten ist, da \< Element> der primäre Knotentyp ist, der der Achse zugeordnet ist `child` ).  
  
 Die `child`-Achse ist die Standardachse. Daher kann die Abfrage wie folgt geschrieben werden:  
  
```  
/Contact  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>So testen Sie die XPath-Abfrage mit dem Zuordnungsschema  
  
1.  Kopieren Sie den [Beispiel Schema Code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) , und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen SampleSchema1.xml.  
  
2.  Erstellen Sie die folgende Vorlage (XPathAxesSampleA.xml), und speichern Sie sie in dem Verzeichnis, in dem SampleSchema1.xml gespeichert wurde.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (SampleSchema1.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden finden Sie einen Auszug aus dem Resultset der Vorlagenausführung:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Contact ContactID="1" LastName="Achong" FirstName="Gustavo" Title="Mr." />   
  <Contact ContactID="2" LastName="Abel" FirstName="Catherine" Title="Ms." />   
  <Contact ContactID="3" LastName="Abercrombie" FirstName="Kim" Title="Ms." />   
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />  
  ...  
</ROOT>  
```  
  
### <a name="b-retrieve-grandchildren-of-the-context-node"></a>B. Abrufen von untergeordneten Elementen zweiter Ordnung des Kontextknotens  
 Die folgende XPath-Abfrage wählt alle untergeordneten Elemente der ** \< Reihenfolge>** der untergeordneten Elemente des ** \< Customer->** Elements des Kontext Knotens aus:  
  
```  
/child::Customer/child::Order  
```  
  
 In der Abfrage `child` ist die Achse und `Customer` und `Order` sind die Knoten Tests (diese Knoten Tests sind true, wenn Customer und Order ein ** \< Element>** Knoten sind, da das ** \< Element>** Knoten der primäre Knoten für die `child` Achse ist). Für jeden Knoten, der dem ** \< Kunden>** entspricht, werden die Knoten, die mit ** \< Bestellungen** übereinstimmen>dem Ergebnis hinzugefügt Im Resultset wird nur die ** \< Reihenfolge>** zurückgegeben.  
  
 Die `child`-Achse ist die Standardachse. Daher kann die Abfrage wie folgt angegeben werden:  
  
```  
/Customer/Order  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>So testen Sie die XPath-Abfrage mit dem Zuordnungsschema  
  
1.  Kopieren Sie den [Beispiel Schema Code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) , und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen SampleSchema1.xml.  
  
2.  Erstellen Sie die folgende Vorlage (XPathAxesSampleB.xml), und speichern Sie sie im folgenden Verzeichnis:  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer/Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (SampleSchema1.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden finden Sie einen Auszug aus dem Resultset der Vorlagenausführung:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
         OrderDate="2001-08-01T00:00:00"   
         DueDate="2001-08-13T00:00:00"   
         ShipDate="2001-08-08T00:00:00">  
  <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-761" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-762" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-765" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-768" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-770" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
   ...  
</ROOT>  
```  
  
 Wenn die XPath-Abfrage als angegeben wird `Customer/Order/OrderDetail` , navigiert die Abfrage von allen Knoten, die mit Customer übereinstimmen ** \<>** die ** \< Reihenfolge>** Elementen. Und für jeden Knoten, der mit ** \< Order>** übereinstimmt, fügt die Abfrage dem Ergebnis die ** \< Order Detail** -Knoten>hinzu. Im Resultset wird nur die ** \< OrderDetail->** zurückgegeben.  
  
### <a name="c-use--to-specify-the-parent-axis"></a>C. Verwenden Sie.. Angeben der übergeordneten Achse  
 Die folgende Abfrage ruft alle ** \< Order>** -Elemente mit einem übergeordneten ** \< Customer->** -Element mit einem **CustomerID-** Attribut Wert von 1 ab. Die Abfrage verwendet die- `child` Achse im Prädikat, um das übergeordnete Element des ** \< Order>** -Elements zu finden.  
  
```  
/child::Customer/child::Order[../@CustomerID="1"]  
```  
  
 Die `child` Achse ist die Standard Achse. Daher kann die Abfrage wie folgt angegeben werden:  
  
```  
/Customer/Order[../@CustomerID="1"]  
```  
  
 Die XPath-Abfrage hat die folgende Entsprechung:  
  
```  
/Customer[@CustomerID="1"]/Order.  
```  
  
> [!NOTE]  
>  Die XPath-Abfrage `/Order[../@CustomerID="1"]` gibt einen Fehler zurück, da es kein übergeordnetes Element von ** \< Order>** gibt. Obwohl möglicherweise Elemente im Zuordnungs Schema vorhanden sind, die die ** \< Reihenfolge>** enthalten, konnte der XPath nicht mit einem der beiden Elemente beginnen. Folglich wird ** \< Order>** als Elementtyp der obersten Ebene im Dokument betrachtet.  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>So testen Sie die XPath-Abfrage mit dem Zuordnungsschema  
  
1.  Kopieren Sie den [Beispiel Schema Code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) , und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen SampleSchema1.xml.  
  
2.  Erstellen Sie die folgende Vorlage (XPathAxesSampleC.xml), und speichern Sie sie im folgenden Verzeichnis:  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer/Order[../@CustomerID="1"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (SampleSchema1.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden finden Sie einen Auszug aus dem Resultset der Vorlagenausführung:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
         OrderDate="2001-08-01T00:00:00"   
         DueDate="2001-08-13T00:00:00"   
         ShipDate="2001-08-08T00:00:00">  
  <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-761" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-762" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-765" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-768" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-770" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
   ...  
</Order>  
</ROOT>  
```  
  
### <a name="d-specify-the-attribute-axis"></a>D: Angeben der Attributachse  
 Die folgende XPath-Abfrage wählt alle untergeordneten Elemente des ** \< Kunden>** des Kontext Knotens mit dem **CustomerID-** Attribut Wert 1 aus:  
  
```  
/child::Customer[attribute::CustomerID="1"]  
```  
  
 Im Prädikat `attribute::CustomerID` `attribute` ist die Achse und `CustomerID` der Knoten Test. (wenn `CustomerID` ein Attribut ist, ist der Knoten Test true, da das ** \< Attribut>** Knoten der primäre Knoten für die Achse ist `attribute` ).  
  
 Es kann eine Verknüpfung mit der `attribute`-Achse (@) angegeben werden, und da `child` die Standardachse ist, muss sie in der Abfrage nicht angegeben werden:  
  
```  
/Customer[@CustomerID="1"]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>So testen Sie die XPath-Abfrage mit dem Zuordnungsschema  
  
1.  Kopieren Sie den [Beispiel Schema Code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) , und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen SampleSchema1.xml.  
  
2.  Erstellen Sie die folgende Vorlage (XPathAxesSampleD.xml), und speichern Sie sie in dem Verzeichnis, in dem SampleSchema1.xml gespeichert wird.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        child::Customer[attribute::CustomerID="1"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (SampleSchema1.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden finden Sie einen Auszug aus dem Resultset der Vorlagenausführung:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" SalesPersonID="280"   
            TerritoryID="1" AccountNumber="1"   
            CustomerType="S" Orders="Ord-43860 Ord-44501 Ord-45283 Ord-46042">  
    <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
           OrderDate="2001-08-01T00:00:00"   
           DueDate="2001-08-13T00:00:00"   
           ShipDate="2001-08-08T00:00:00">  
       <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
                    OrderQty="1" UnitPriceDiscount="0" />   
       <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
                    OrderQty="1" UnitPriceDiscount="0" />   
       <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
                    OrderQty="1" UnitPriceDiscount="0" />   
      ...   
    </Order>  
   ...  
  </Customer>  
</ROOT>  
```  
  
  
