---
title: Angeben von Achsen in XPath-Abfragen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 820542c25947157b9e062608f1134e4bdeaa702a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62737690"
---
# <a name="specifying-axes-in-xpath-queries-sqlxml-40"></a>Angeben von Achsen in XPath-Abfragen (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In den folgenden Beispielen wird gezeigt, wie Achsen in XPath-Abfragen angegeben werden.  
  
 Die XPath-Abfragen in diesen Beispielen werden für das in SampleSchema1.xml enthaltene Zuordnungsschema angegeben. Weitere Informationen zu diesem Beispielschema finden Sie unter [Annotated XSD-Beispielschema für XPath-Beispiele &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-retrieve-child-elements-of-the-context-node"></a>A. Abrufen von untergeordneten Elementen des Kontextknotens  
 Der folgende XPath-Abfrage wählt alle dem  **\<wenden Sie sich an >** untergeordnete Elemente des Kontextknotens aus:  
  
```  
/child::Contact  
```  
  
 In der Abfrage `child` ist die Achse und `Contact` ist der Knotentest (TRUE, wenn `Contact` ist ein  **\<Element >** Knoten, da \<Element > der primäre Knotentyp zugewiesen ist die `child` Achse).  
  
 Die `child`-Achse ist die Standardachse. Daher kann die Abfrage wie folgt geschrieben werden:  
  
```  
/Contact  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>So testen Sie die XPath-Abfrage mit dem Zuordnungsschema  
  
1.  Kopieren der [Schema Beispielcode](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) und fügen Sie ihn in eine Textdatei. Speichern Sie die Datei unter dem Dateinamen SampleSchema1.xml.  
  
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
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
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
 Der folgende XPath-Abfrage wählt alle dem  **\<Reihenfolge >** untergeordnete Elemente des der  **\<Kunden >** untergeordneten-Elemente des Kontextknotens aus:  
  
```  
/child::Customer/child::Order  
```  
  
 In der Abfrage `child` ist die Achse und `Customer` und `Order` sind die Knotentests (diese Knotentests sind TRUE, wenn Customer und Order sind  **\<Element >** Knoten, da die  **\<Element >** Knoten ist der primäre Knoten für die **untergeordneten** Achse). Für jeden Knoten übereinstimmende  **\<Kunden >** , die übereinstimmenden Knoten  **\<Bestellungen >** zum Ergebnis hinzugefügt werden. Nur  **\<Reihenfolge >** wird im Resultset zurückgegeben.  
  
 Die **untergeordneten** -Achse die Standardachse ist. Daher kann die Abfrage wie folgt angegeben werden:  
  
```  
/Customer/Order  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>So testen Sie die XPath-Abfrage mit dem Zuordnungsschema  
  
1.  Kopieren der [Schema Beispielcode](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) und fügen Sie ihn in eine Textdatei. Speichern Sie die Datei unter dem Dateinamen SampleSchema1.xml.  
  
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
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
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
  
 Wenn die XPath-Abfrage als angegeben wird `Customer/Order/OrderDetail`, von einem einzelnen Knoten Abgleich  **\<Kunden >** Abfrage navigiert zu der  **\<Reihenfolge >** Elemente. Und für den Abgleich von einzelnen Knoten  **\<Reihenfolge >** , die Abfrage fügt die Knoten  **\<OrderDetail >** auf das Ergebnis. Nur  **\<OrderDetail >** wird im Resultset zurückgegeben.  
  
### <a name="c-use--to-specify-the-parent-axis"></a>C. Verwenden... Angeben der übergeordneten Achse  
 Die folgende Abfrage ruft alle der  **\<Reihenfolge >** -Elemente mit einem übergeordneten  **\<Kunden >** -Element mit einem **"CustomerID"** Attribut der Wert 1. Die Abfrage verwendet die **untergeordneten** -Achse im Prädikat, um das übergeordnete Element des finden die  **\<Reihenfolge >** Element.  
  
```  
/child::Customer/child::Order[../@CustomerID="1"]  
```  
  
 Die **untergeordneten** -Achse ist die Standardachse. Daher kann die Abfrage wie folgt angegeben werden:  
  
```  
/Customer/Order[../@CustomerID="1"]  
```  
  
 Die XPath-Abfrage hat die folgende Entsprechung:  
  
```  
/Customer[@CustomerID="1"]/Order.  
```  
  
> [!NOTE]  
>  Die XPath-Abfrage `/Order[../@CustomerID="1"]` wird ein Fehler zurückgegeben, da es kein übergeordnetes Element des ist  **\<Reihenfolge >** . Es kann jedoch auch Elementen im Zuordnungsschema mit  **\<Reihenfolge >** , XPath beginnt bei keinem dieser Elemente; daher  **\<Reihenfolge >** gilt die Typ der Element der obersten Ebene im Dokument.  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>So testen Sie die XPath-Abfrage mit dem Zuordnungsschema  
  
1.  Kopieren der [Schema Beispielcode](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) und fügen Sie ihn in eine Textdatei. Speichern Sie die Datei unter dem Dateinamen SampleSchema1.xml.  
  
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
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
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
  
### <a name="d-specify-the-attribute-axis"></a>D. Angeben der Attributachse  
 Der folgende XPath-Abfrage wählt alle dem  **\<Kunden >** untergeordnete Elemente des Kontextknotens eine **"CustomerID"** -Attributwert 1 beträgt:  
  
```  
/child::Customer[attribute::CustomerID="1"]  
```  
  
 Im Prädikat `attribute::CustomerID`, `attribute` ist die Achse und `CustomerID` ist der Knotentest (Wenn `CustomerID` ist ein Attribut der Knotentest "true ist", da die  **\<Attribut >** Knoten ist der primäre Knoten für die `attribute` Achse).  
  
 Es kann eine Verknüpfung mit der `attribute`-Achse (@) angegeben werden, und da `child` die Standardachse ist, muss sie in der Abfrage nicht angegeben werden:  
  
```  
/Customer[@CustomerID="1"]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>So testen Sie die XPath-Abfrage mit dem Zuordnungsschema  
  
1.  Kopieren der [Schema Beispielcode](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) und fügen Sie ihn in eine Textdatei. Speichern Sie die Datei unter dem Dateinamen SampleSchema1.xml.  
  
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
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
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
  
  
