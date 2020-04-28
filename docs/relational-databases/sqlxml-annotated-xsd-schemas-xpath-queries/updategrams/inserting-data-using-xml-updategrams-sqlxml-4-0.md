---
title: Einfügen von Daten mit XML-Update grams (SQLXML)
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- xsi:nil attribute
- unique values
- <after> block
- id attribute
- data insertions [SQLXML]
- nil attribute
- <before> block
- updg:guid attribute
- multiple record insertions
- returnid attribute
- updategrams [SQLXML], inserting data
- updg:at-identity attribute
- invalid characters [SQLXML]
- updg:returnid attribute
- updg:id attribute
- namespaces [SQLXML], updategrams
- IDENTITY-type column
- guid attribute
- record insertion [SQLXML]
- null values [SQLXML]
- at-identity attribute
- xml data type [SQL Server], SQLXML
ms.assetid: 4dc48762-bc12-43fb-b356-ea1b9c1e287e
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 671dc9c8a0091a2fb14a4aa1c42ea8246b376c7a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "79112268"
---
# <a name="inserting-data-using-xml-updategrams-sqlxml-40"></a>Einfügen von Daten mit XML-Updategrams (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Ein Update Gram zeigt einen Einfügevorgang an, wenn eine Daten Satz Instanz im ** \<nach>** -Block, jedoch nicht im entsprechenden ** \<before>** -Block angezeigt wird. In diesem Fall fügt das Update Gram den Datensatz im ** \<nach>** Block in die Datenbank ein.  
  
 Dies ist das Updategramformat für einen Einfügevorgang:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   [<updg:before>  
   </updg:before>]  
    <updg:after [updg:returnid="x y ...] >  
       <ElementName [updg:id="value"]   
                   [updg:at-identity="x"]   
                   [updg:guid="y"]  
                   attribute="value"   
                   attribute="value"  
                   ...  
       />  
      [<ElementName .../>... ]  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
## <a name="before-block"></a>\<vor> Block  
 Der ** \<before>** -Block kann für einen Einfügevorgang ausgelassen werden. Wenn das optionale **Mapping-Schema-** Attribut nicht angegeben wird, wird der ** \<** im Update Gram angegebene Elementname->einer Datenbanktabelle zugeordnet, und die untergeordneten Elemente oder Attribute werden den Spalten in der Tabelle zugeordnet.  
  
## <a name="after-block"></a>\<nach>-Block  
 Sie können einen oder mehrere Datensätze im ** \<nach>** -Block angeben.  
  
 Wenn der ** \<after->** -Block keinen Wert für eine bestimmte Spalte bereitstellt, verwendet das Update Gram den Standardwert, der im Schema mit Anmerkungen angegeben ist (sofern ein Schema angegeben wurde). Wenn das Schema keinen Standardwert für die Spalte angibt, gibt das Update Gram keinen expliziten Wert für diese Spalte an und weist stattdessen der Spalte den [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Standardwert (falls angegeben) zu. Wenn kein [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Standardwert vorhanden ist, und die Spalte einen NULL-Wert akzeptiert, legt das Updategram den Spaltenwert auf NULL fest. Wenn die Spalte weder einen Standardwert besitzt, noch einen NULL-Wert akzeptiert, schlägt der Befehl fehl, und das Updategram gibt einen Fehler zurück. Das optionale **updg: returnid-** Attribut wird verwendet, um den Identitäts Wert zurückzugeben, der vom System generiert wird, wenn ein Datensatz in einer Tabelle mit einer Spalte vom Typ IDENTITY hinzugefügt wird.  
  
## <a name="updgid-attribute"></a>updg:id-Attribut  
 Wenn das Update Gram nur Datensätze einfügt, ist das **updg: ID** -Attribut für das Update Gram nicht erforderlich. Weitere Informationen zu **updg: ID**finden Sie unter [Aktualisieren von Daten mit XML-Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/updating-data-using-xml-updategrams-sqlxml-4-0.md).  
  
## <a name="updgat-identity-attribute"></a>updg:at-identity-Attribut  
 Wenn ein Update Gram einen Datensatz in einer Tabelle mit einer Spalte vom Typ Identity einfügt, kann das Update Gram den Wert des zugewiesenen Systems mithilfe des optionalen Attributs **updg: at-Identity** erfassen. Das Updategram kann dann diesen Wert in nachfolgenden Vorgängen verwenden. Bei der Ausführung des Update grams können Sie den Identitäts Wert zurückgeben, der generiert wird, indem Sie das **updg: returnid-** Attribut angeben.  
  
## <a name="updgguid-attribute"></a>updg:guid-Attribut  
 Das **updg: GUID** -Attribut ist ein optionales Attribut, das eine Globally Unique Identifier generiert. Dieser Wert verbleibt im Gültigkeitsbereich für den gesamten ** \<Synchronisierungs>** Block, in dem er angegeben ist. Sie können diesen Wert an beliebiger Stelle im ** \<Sync>** -Block verwenden. Das-Attribut ruft die **NewGuid ()** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Funktion auf, um den eindeutigen Bezeichner zu generieren.  
  
## <a name="examples"></a>Beispiele  
 Wenn Sie in den folgenden Beispielen funktionierende Beispiele erstellen möchten, müssen Sie die unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)angegebenen Anforderungen erfüllen.  
  
 Beachten Sie vor der Verwendung der Update Gram-Beispiele Folgendes:  
  
-   Die meisten der Beispiele verwenden die Standardzuordnung (d. h. es ist kein Zuordnungsschema im Updategram angegeben). Weitere Beispiele für Update grams, die Mapping-Schemas verwenden, finden Sie unter [Angeben eines Mappingschemas mit Anmerkungen in einem Update Gram &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
-   Die meisten Beispiele verwenden die [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]-Beispieldatenbank. Alle Updates werden für die Tabellen in dieser Datenbank übernommen.  
  
### <a name="a-inserting-a-record-by-using-an-updategram"></a>A. Einfügen eines Datensatzes mithilfe eines Updategrams  
 Dieses attributzentrierte Updategram fügt einen Datensatz in die HumanResources.Employee-Tabelle in der [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]-Datenbank ein.  
  
 In diesem Beispiel gibt das Updategram kein Zuordnungsschema an. Daher verwendet das Updategram die Standardzuordnung, in der der Elementname einem Tabellennamen und die untergeordneten Elemente oder Attribute den Spalten in dieser Tabelle zugeordnet werden.  
  
 Das [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]-Schema für die HumanResources.Department-Tabelle erzwingt eine NOT NULL-Einschränkung für alle Spalten. Daher muss das Updategram für alle Spalten angegebene Werte enthalten. DepartmentID ist eine Spalte vom Typ IDENTITY. Daher werden keine Werte dafür angegeben.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name="New Product Research"   
            GroupName="Research and Development"   
            ModifiedDate="2010-08-31"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
1.  Kopieren Sie das oben stehende Updategram, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen MyUpdategram.xml.  
  
2.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 In einer elementzentrierten Zuordnung sieht das Updategram aus wie folgt:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department>  
            <Name> New Product Research </Name>  
            <GroupName> Research and Development </GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Im gemischten Modus (elementzentriert und attributzentriert) kann ein Element sowohl Attribute als auch Unterelemente aufweisen, wie in diesem Updategram gezeigt:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name=" New Product Research "   
            <GroupName>Research and Development</GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="b-inserting-multiple-records-by-using-an-updategram"></a>B. Einfügen mehrerer Datensätze mithilfe eines Updategrams  
 Dieses Updategram fügt der HumanResources.Shift-Tabelle zwei neue Schichtdatensätze hinzu. Das Update Gram gibt den optionalen ** \<vor>** -Block nicht an.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
1.  Kopieren Sie das oben stehende Updategram, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen Updategram-AddShifts.xml.  
  
2.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Eine andere Version dieses Beispiels ist ein Update Gram, das zwei separate ** \<after->** -Blöcke anstelle eines Blocks verwendet, um die beiden Mitarbeiter einzufügen. Dies ist gültig und kann wie folgt codiert werden:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after >  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="c-working-with-valid-sql-server-characters-that-are-not-valid-in-xml"></a>C. Arbeiten mit gültigen SQL Server-Zeichen, die in XML nicht gültig sind  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] können Tabellennamen Leerzeichen enthalten, wie beispielsweise die Order Details-Tabelle in der Northwind-Datenbank. Dies gilt jedoch nicht für XML-Zeichen, die gültige [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Bezeichner sind, aber keine gültigen XML-IDs können mithilfe von "__xHHHH\_\_" als Codierungs Wert codiert werden, wobei "HHHH" für den vierstelligen hexadezimalen UCS-2-Code für das Zeichen in der signifikantesten bidirektionalen Reihenfolge steht.  
  
> [!NOTE]  
>  Für dieses Beispiel wird die Northwind-Datenbank verwendet. Sie können die Northwind-Datenbank mithilfe eines SQL-Skripts installieren, das von dieser [Microsoft](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)-Website heruntergeladen werden kann.  
  
 Der Elementname muss in Klammern ([ ]) stehen. Da die Zeichen [und] in XML nicht gültig sind, müssen Sie Sie als _x005B\_ bzw. _x005D\_codieren. (Falls Sie ein Zuordnungsschema verwenden, können Sie Elementnamen bereitstellen, die keine ungültigen Zeichen wie Leezeichen enthalten. Die erforderliche Zuordnung erfolgt über das Zuordnungsschema, daher müssen Sie diese Zeichen nicht codieren.)  
  
 Dieses Updategram fügt der Order Details-Tabelle der Northwind-Datenbank einen Datensatz hinzu:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <_x005B_Order_x0020_Details_x005D_ OrderID="1"  
            ProductID="11"  
            UnitPrice="$1.0"  
            Quantity="1"  
            Discount="0.0" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Die UnitPrice-Spalte in der Order Details-Tabelle weist den **Money** -Typ auf. Das Dollarzeichen ($) muss als Teil des Werts hinzugefügt werden, um die entsprechende Typkonvertierung (von einem **Zeichen** Folgentyp auf einen **Money** -Typ) anzuwenden. Wenn das Update Gram kein Mapping-Schema angibt, wird das erste Zeichen des **Zeichen** folgen Werts ausgewertet. Wenn das erste Zeichen ein Dollarzeichen ($) ist, wird die entsprechende Konvertierung angewendet.  
  
 Wenn das Update Gram für ein Zuordnungs Schema angegeben ist, in dem die Spalte entweder als **dt: Type = "Fixed. 14,4"** oder **SQL: datatype = "Money"** gekennzeichnet ist, ist das Dollarzeichen ($) nicht erforderlich, und die Konvertierung erfolgt durch die Zuordnung. Dies ist die empfohlene Methode, um sicherzustellen, dass die richtige Typkonvertierung stattfindet.  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
1.  Kopieren Sie das oben stehende Updategram, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen UpdategramSpacesInTableName.xml.  
  
2.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="d-using-the-at-identity-attribute-to-retrieve-the-value-that-has-been-inserted-in-the-identity-type-column"></a>D. Verwenden des at-identity-Attributs, um den in die Spalte vom Typ IDENTITY eingefügten Wert abzurufen  
 Das folgende Updategram fügt zwei Datensätze ein: einen in die Sales.SalesOrderHeader-Tabelle und einen in die Sales.SalesOrderDetail-Tabelle.  
  
 Zuerst fügt das Updategram der Sales.SalesOrderHeader-Tabelle einen Datensatz hinzu. In dieser Tabelle ist SalesOrderID eine Spalte vom Typ IDENTITY. Wenn Sie der Tabelle diesen Datensatz hinzufügen, verwendet das Update Gram das **at-Identity** -Attribut, um den zugewiesenen SalesOrderID-Wert als "x" (einen Platzhalter Wert) zu erfassen. Der Update Gram-Parameter gibt dann diese **at-Identity** -Variable als Wert des SalesOrderID- \<Attributs im Sales. SalesOrderDetail-> Element an.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
   <Sales.SalesOrderHeader updg:at-identity="x"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00001111-2222-3333-4444-556677889900"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
      <Sales.SalesOrderDetail SalesOrderID="x"  
                LineNumber="1"  
                OrderQty="1"  
                ProductID="776"  
                SpecialOfferID="1"  
                UnitPrice="2429.9928"  
                UnitPriceDiscount="0.00"  
                rowguid="aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee"  
                ModifiedDate="2001-07-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Wenn Sie den Identitäts Wert zurückgeben möchten, der vom **updg: at-Identity-** Attribut generiert wird, können Sie das **updg: returnid-** Attribut verwenden. Es folgt ein überarbeitetes Updategram, das diesen Identitätswert zurückgibt. (Dieses Updategram fügt zwei Order-Datensätze und zwei Order Detail-Datensätze hinzu, um das Beispiel ein bisschen zu komplizieren.)  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync>  
  <updg:before>  
  </updg:before>  
  <updg:after updg:returnid="x y" >  
       <HumanResources.Shift updg:at-identity="x" Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift updg:at-identity="y" Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:after>  
 </updg:sync>  
</ROOT>  
```  
  
 Wenn das Updategram ausgeführt wird, gibt es Ergebnisse wie die folgenden zurück, unter anderem den Identitätswert (den generierten Wert der für Tabellenidentität verwendeten ShiftID-Spalte):  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">   
  <returnid>   
    <x>4</x>   
    <y>5</y>   
  </returnid>   
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
1.  Kopieren Sie das oben stehende Updategram, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen Updategram-returnId.xml.  
  
2.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="e-using-the-updgguid-attribute-to-generate-a-unique-value"></a>E. Verwenden des updg:guid-Attributs, um einen eindeutigen Wert zu generieren  
 In diesem Beispiel fügt das Updategram einen Datensatz in die Tabellen Cust und CustOrder ein. Das Update Gram generiert außerdem einen eindeutigen Wert für das CustomerID-Attribut mithilfe des **updg: GUID** -Attributs.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after updg:returnid="x" >  
      <Cust updg:guid="x" >  
         <CustID>x</CustID>  
         <LastName>Fuller</LastName>  
      </Cust>  
      <CustOrder>  
         <CustID>x</CustID>  
         <OrderID>1</OrderID>  
      </CustOrder>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Das Update Gram gibt das **returnid-** Attribut an. Als Ergebnis wird der generierte GUID zurückgegeben:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <returnid>  
    <x>7111BD1A-7F0B-4CEE-B411-260DADFEFA2A</x>   
  </returnid>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Kopieren Sie das oben stehende Updategram, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen Updategram-GenerateGuid.xml.  
  
2.  Erstellen Sie die folgenden Tabellen:  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust (CustID uniqueidentifier, LastName varchar(20))  
    CREATE TABLE CustOrder (CustID uniqueidentifier, OrderID int)  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="f-specifying-a-schema-in-an-updategram"></a>F. Angeben eines Schemas in einem Updategram  
 Das Updategram in diesem Beispiel fügt einen Datensatz in die folgende Tabelle ein:  
  
```  
CustOrder(OrderID, EmployeeID, OrderType)  
```  
  
 In diesem Updategram wird ein XSD-Schema angegeben (d. h. es gibt keine Standardzuordnung von Updategramelementen und -attributen). Die erforderliche Zuordnung der Elemente und Attribute zu den Datenbanktabellen und -spalten erfolgt durch das Zuordnungsschema.  
  
 Das folgende Schema (CustOrderSchema. Xml) beschreibt ein ** \<CustOrder->** Element, das aus den Attributen **OrderID** und Mitarbeiter **Eid** besteht. Um das Schema interessanter zu machen, wird dem Mitarbeiter-ID **-Attribut ein** Standardwert zugewiesen. Ein Updategram verwendet den Standardwert eines Attributs nur bei Einfügevorgängen, und auch dann nur, wenn das Updategram kein anderes Attribut angibt.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="CustOrder" >  
   <xsd:complexType>  
        <xsd:attribute name="OrderID"     type="xsd:integer" />   
        <xsd:attribute name="EmployeeID"  type="xsd:integer" />  
        <xsd:attribute name="OrderType  " type="xsd:integer" default="1"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Dieses Updategram fügt einen Datensatz in die CustOrder-Tabelle ein. Das Updategram gibt nur die Attributwerte für OrderID und EmployeeID an. Der Attributwert für OrderType wird nicht angegeben. Daher verwendet das Updategram den Standardwert des EmployeeID-Attributs, das im vorhergehenden Schema angegeben ist.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
             xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync mapping-schema='CustOrderSchema.xml'>  
<updg:after>  
       <CustOrder OrderID="98000" EmployeeID="1" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 Weitere Beispiele für Update grams, die ein Mapping-Schema angeben, finden Sie unter [Angeben eines Mapping-Schemas mit Anmerkungen in einem Update Gram &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Erstellen Sie diese Tabelle in der **tempdb** -Datenbank:  
  
    ```  
    USE tempdb  
    CREATE TABLE CustOrder(  
                     OrderID int,   
                     EmployeeID int,   
                     OrderType int)  
    ```  
  
2.  Kopieren Sie das oben stehende Schema, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen CustOrderSchema.xml.  
  
3.  Kopieren Sie das oben stehende Updategram, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei als CustOrderUpdategram.xml in demselben Ordner, den Sie im vorherigen Schritt verwendet haben.  
  
4.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um das Updategram auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Dies ist das entsprechende XDR-Schema:  
  
```  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
 <ElementType name="CustOrder" >  
    <AttributeType name="OrderID" />  
    <AttributeType name="EmployeeID" />  
    <AttributeType name="OrderType" default="1" />  
    <attribute type="OrderID"  />  
    <attribute type="EmployeeID" />  
    <attribute type="OrderType" />  
  </ElementType>  
</Schema>  
```  
  
### <a name="g-using-the-xsinil-attribute-to-insert-null-values-in-a-column"></a>G. Verwenden des Attributs "xsi:nil", um NULL-Werte in eine Spalte einzufügen  
 Wenn Sie einen NULL-Wert in die entsprechende Spalte in der Tabelle einfügen möchten, können Sie das **xsi: Nil** -Attribut für ein Element in einem Update Gram angeben. Im entsprechenden XSD-Schema muss auch das XSD- **nillable** -Attribut angegeben werden.  
  
 Das folgende XSD-Schema ist ein Beispiel dafür:  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="Student" sql:relation="Students">  
  <xsd:complexType>  
    <xsd:all>  
      <xsd:element name="fname" sql:field="first_name"   
                                type="xsd:string"   
                                 nillable="true"/>  
    </xsd:all>  
    <xsd:attribute name="SID"   
                        sql:field="StudentID"  
                        type="xsd:ID"/>      
    <xsd:attribute name="lname"       
                        sql:field="last_name"  
                        type="xsd:string"/>  
    <xsd:attribute name="minitial"    
                        sql:field="middle_initial"   
                        type="xsd:string"/>  
    <xsd:attribute name="years"       
                         sql:field="no_of_years"  
                         type="xsd:integer"/>  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 Das XSD-Schema gibt **nillable = "true"** für das ** \<Name->** Element an. Das folgende Updategram verwendet dieses Schema:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
      xmlns:updg="urn:schemas-microsoft-com:xml-updategram"  
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  
<updg:sync mapping-schema='StudentSchema.xml'>  
  <updg:before/>  
  <updg:after>  
    <Student SID="S00004" lname="Elmaci" minitial="" years="2">  
      <fname xsi:nil="true">  
    </fname>  
    </Student>  
  </updg:after>  
</updg:sync>  
  
</ROOT>  
```  
  
 Das Update Gram gibt **xsi: Nil** für das ** \<fname->** Element im ** \<after>** -Block an. Daher wird beim Ausführen dieses Updategrams für die first_name-Spalte in der Tabelle der Wert NULL eingefügt.  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Erstellen Sie die folgende Tabelle in der **tempdb** -Datenbank:  
  
    ```  
    USE tempdb  
    CREATE TABLE Students (  
       StudentID char(6)NOT NULL ,  
       first_name varchar(50),  
       last_name varchar(50),  
       middle_initial char(1),  
       no_of_years int NULL)  
    GO  
    ```  
  
2.  Kopieren Sie das oben stehende Schema, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen StudentSchema.xml.  
  
3.  Kopieren Sie das oben stehende Updategram, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei als StudentUpdategram.xml in demselben Ordner, den Sie im vorherigen Schritt zum Speichern der Datei StudentSchema.xml verwendet haben.  
  
4.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um das Updategram auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="h-specifying-namespaces-in-an-updategram"></a>H. Angeben von Namespaces in einem Updategram  
 In einem Updategram können Elemente vorhanden sein, die zu einem in demselben Element im Updategram deklarierten Namespace gehören. In diesem Fall muss auch in dem entsprechenden Schema derselbe Namespace deklariert sein, und das Element muss diesem Zielnamespace angehören.  
  
 Im folgenden Update Gram (Updategram-ElementHavingNamespace. Xml) gehört das ** \<Order>** -Element z. b. zu einem Namespace, der im-Element deklariert ist.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema='XSD-ElementHavingNameSpace.xml'>  
    <updg:after>  
       <x:Order  xmlns:x="https://server/xyz/schemas/"  
             updg:at-identity="SalesOrderID"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00009999-8888-7777-6666-554433221100"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 In diesem Fall muss auch das Schema den Namespace deklarieren, wie in diesem Schema gezeigt:  
  
 Das folgende Schema (XSD-ElementHavingNamespace.xml) zeigt an, wie das entsprechende Element und die entsprechenden Attribute deklariert werden müssen.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
     xmlns:dt="urn:schemas-microsoft-com:datatypes"   
     xmlns:sql="urn:schemas-microsoft-com:mapping-schema"    
     xmlns:x="https://server/xyz/schemas/"   
     targetNamespace="https://server/xyz/schemas/" >  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" type="x:Order_type"/>  
  <xsd:complexType name="Order_type">  
    <xsd:attribute name="SalesOrderID"  type="xsd:ID"/>  
    <xsd:attribute name="RevisionNumber" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OrderDate" type="xsd:dateTime"/>  
    <xsd:attribute name="DueDate" type="xsd:dateTime"/>  
    <xsd:attribute name="ShipDate" type="xsd:dateTime"/>  
    <xsd:attribute name="Status" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OnlineOrderFlag" type="xsd:boolean"/>  
    <xsd:attribute name="SalesOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="PurchaseOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="AccountNumber" type="xsd:string"/>  
    <xsd:attribute name="CustomerID" type="xsd:int"/>  
    <xsd:attribute name="ContactID" type="xsd:int"/>  
    <xsd:attribute name="SalesPersonID" type="xsd:int"/>  
    <xsd:attribute name="TerritoryID" type="xsd:int"/>  
    <xsd:attribute name="BillToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipMethodID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardApprovalCode" type="xsd:string"/>  
    <xsd:attribute name="CurrencyRateID" type="xsd:int"/>  
    <xsd:attribute name="SubTotal" type="xsd:decimal"/>  
    <xsd:attribute name="TaxAmt" type="xsd:decimal"/>  
    <xsd:attribute name="Freight" type="xsd:decimal"/>  
    <xsd:attribute name="TotalDue" type="xsd:decimal"/>  
    <xsd:attribute name="Comment" type="xsd:string"/>  
    <xsd:attribute name="rowguid" type="xsd:string"/>  
    <xsd:attribute name="ModifiedDate" type="xsd:dateTime"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Kopieren Sie das oben stehende Schema, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen XSD-ElementHavingNamespace.xml.  
  
2.  Kopieren Sie das oben stehende Updategram, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei als Updategram-ElementHavingNamespace.xml in demselben Ordner, den Sie im vorherigen Schritt zum Speichern der Datei XSD-ElementHavingnamespace.xml verwendet haben.  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um das Updategram auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="i-inserting-data-into-an-xml-data-type-column"></a>I. Einfügen von Daten in eine XML-Datentypspalte  
 Der **XML** -Datentyp wurde in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]eingeführt. Mit Update grams können Sie in Spalten des **XML** -Datentyps gespeicherte Daten mit den folgenden bereit Stellungen einfügen und aktualisieren:  
  
-   Die **XML** -Spalte kann nicht zum Identifizieren einer vorhandenen Zeile verwendet werden. Daher kann er nicht in den **updg: Before** -Abschnitt eines Update grams eingefügt werden.  
  
-   Namespaces im Gültigkeitsbereich des XML-Fragments, die in die **XML** -Spalte eingefügt werden, werden beibehalten und deren Namespace Deklarationen werden dem obersten Element des eingefügten Fragments hinzugefügt.  
  
 Im folgenden Update Gram (SampleUpdateGram. Xml) aktualisiert beispielsweise das [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] ** \<Element>** -Element die ProductDescription-Spalte in der Production>ProductModel-Tabelle in der-Beispieldatenbank. Das Ergebnis dieses Update grams besteht darin, dass der XML-Inhalt der ProductDescription-Spalte mit dem XML-Inhalt des Elements ** \<** zum Entfernen von>aktualisiert wird.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
       <updg:before>  
<ProductModel ProductModelID="19">  
   <Name>Mountain-100</Name>  
</ProductModel>  
    </updg:before>  
    <updg:after>  
 <ProductModel>  
    <Name>Mountain-100</Name>  
    <Desc><?xml-stylesheet href="ProductDescription.xsl" type="text/xsl"?>  
        <p1:ProductDescription xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
              xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
              xmlns:wf="https://www.adventure-works.com/schemas/OtherFeatures"   
              xmlns:html="http://www.w3.org/1999/xhtml"   
              xmlns="">  
  <p1:Summary>  
     <html:p>Insert Example</html:p>  
  </p1:Summary>  
  <p1:Manufacturer>  
    <p1:Name>AdventureWorks</p1:Name>  
    <p1:Copyright>2002</p1:Copyright>  
    <p1:ProductURL>HTTP://www.Adventure-works.com</p1:ProductURL>  
  </p1:Manufacturer>  
  <p1:Features>These are the product highlights.   
    <wm:Warranty>  
       <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
       <wm:Description>parts and labor</wm:Description>  
    </wm:Warranty>  
    <wm:Maintenance>  
       <wm:NoOfYears>10 years</wm:NoOfYears>  
       <wm:Description>maintenance contract available through your dealer or any AdventureWorks retail store.</wm:Description>  
    </wm:Maintenance>  
    <wf:wheel>High performance wheels.</wf:wheel>  
    <wf:saddle>  
      <html:i>Anatomic design</html:i> and made from durable leather for a full-day of riding in comfort.</wf:saddle>  
    <wf:pedal>  
       <html:b>Top-of-the-line</html:b> clipless pedals with adjustable tension.</wf:pedal>  
    <wf:BikeFrame>Each frame is hand-crafted in our Bothell facility to the optimum diameter and wall-thickness required of a premium mountain frame. The heat-treated welded aluminum frame has a larger diameter tube that absorbs the bumps.</wf:BikeFrame>  
    <wf:crankset> Triple crankset; alumunim crank arm; flawless shifting. </wf:crankset>  
   </p1:Features>  
   <p1:Picture>  
      <p1:Angle>front</p1:Angle>  
      <p1:Size>small</p1:Size>  
      <p1:ProductPhotoID>118</p1:ProductPhotoID>  
   </p1:Picture>  
   <p1:Specifications> These are the product specifications.  
     <Material>Almuminum Alloy</Material>  
     <Color>Available in most colors</Color>  
     <ProductLine>Mountain bike</ProductLine>  
     <Style>Unisex</Style>  
     <RiderExperience>Advanced to Professional riders</RiderExperience>  
   </p1:Specifications>  
  </p1:ProductDescription>  
 </Desc>  
      </ProductModel>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Das Updategram verweist auf das folgende XSD-Schema mit Anmerkungen (SampleSchema.xml).  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
           xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">   
  <xsd:element name="ProductModel"  sql:relation="Production.ProductModel" >  
     <xsd:complexType>  
       <xsd:sequence>  
          <xsd:element name="Name" type="xsd:string"></xsd:element>  
          <xsd:element name="Desc" sql:field="CatalogDescription" sql:datatype="xml">  
           <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="ProductDescription">  
                 <xsd:complexType>  
                   <xsd:sequence>  
                     <xsd:element name="Summary" type="xsd:anyType">  
                     </xsd:element>  
                   </xsd:sequence>  
                 </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>   
       </xsd:sequence>  
       <xsd:attribute name="ProductModelID" sql:field="ProductModelID"/>  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Kopieren Sie das oben stehende Schema, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen XSD-SampleSchema.xml.  
  
    > [!NOTE]  
    >  Da Update grams die Standard Zuordnung unterstützen, gibt es keine Möglichkeit, den Anfang und das Beenden des **XML** -Datentyps zu identifizieren. Dies bedeutet, dass beim Einfügen oder Aktualisieren von Tabellen mit Spalten des **XML** -Datentyps ein Zuordnungsschema erforderlich ist. Wird kein Schema bereitgestellt, gibt SQLXML einen Fehler zurück und meldet, dass eine der Spalten in der Tabelle fehlt.  
  
2.  Kopieren Sie das oben stehende Updategram, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei als SampleUpdategram.xml in demselben Ordner, den Sie im vorherigen Schritt zum Speichern der Datei SampleSchema.xml verwendet haben.  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um das Updategram auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitsüberlegungen zu Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
