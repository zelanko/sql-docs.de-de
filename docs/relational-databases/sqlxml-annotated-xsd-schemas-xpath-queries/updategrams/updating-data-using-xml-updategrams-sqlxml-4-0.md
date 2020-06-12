---
title: Aktualisieren von Daten mit XML-Update grams (SQLXML)
description: Erfahren Sie, wie Sie vorhandene Daten mithilfe eines XML-Update Grams in SQLXML 4,0 aktualisieren.
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREF type attribute [SQLXML]
- before attribute
- <sync> block
- <after> block
- id attribute
- <before> block
- updg:after attribute
- mapping-schema attribute
- IDREFS type attribute [SQLXML]
- updg:id attribute
- multiple record updates
- after attribute
- updategrams [SQLXML], updating data
- updg:before attribute
- record updates [SQLXML]
ms.assetid: 90ef8a33-5ae3-4984-8259-608d2f1d727f
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2e4cfa5ef312bc9048a53405a6c1083183b10054
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529779"
---
# <a name="updating-data-using-xml-updategrams-sqlxml-40"></a>Aktualisieren von Daten mit XML-Updategrams (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Wenn Sie vorhandene Daten aktualisieren, müssen Sie sowohl den **\<before>** -als auch den- **\<after>** Block angeben. Die in den **\<before>** Blöcken und angegebenen Elemente **\<after>** beschreiben die gewünschte Änderung. Das Update Gram verwendet die im-Block angegebenen Elemente, **\<before>** um die vorhandenen Datensätze in der Datenbank zu identifizieren. Die entsprechenden Elemente im- **\<after>** Block geben an, wie die Datensätze nach dem Ausführen des Aktualisierungs Vorgangs aussehen sollen. Aus diesen Informationen erstellt das Update Gram eine SQL-Anweisung, die mit dem-Block übereinstimmt **\<after>** . Das Updategram verwendet dann diese Anweisung, um die Datenbank zu aktualisieren.  
  
 Dies ist das Updategramformat für einen Updatevorgang:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
      <ElementName [updg:id="value"] .../>  
      [<ElementName [updg:id="value"] .../> ... ]  
   </updg:before>  
   <updg:after>  
      <ElementName [updg:id="value"] ... />  
      [<ElementName [updg:id="value"] .../> ...]  
   </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 **\<updg:before>**  
 Die Elemente im- **\<before>** Block identifizieren vorhandene Datensätze in den Datenbanktabellen.  
  
 **\<updg:after>**  
 Die Elemente im- **\<after>** Block beschreiben, wie die im-Block angegebenen Datensätze **\<before>** nach dem Anwenden der Updates aussehen sollten.  
  
 Das **Mapping-Schema-** Attribut identifiziert das Zuordnungsschema, das vom Update Gram verwendet werden soll. Wenn das Update Gram ein Zuordnungsschema angibt, müssen die in den Blöcken und angegebenen Element-und Attributnamen **\<before>** **\<after>** mit den Namen im Schema identisch sein. Das Zuordnungsschema ordnet diese Element- oder Attributnamen der Datenbanktabelle und den Spaltennamen zu.  
  
 Wenn ein Updategram kein Schema angibt, verwendet das Updategram die Standardzuordnung. Bei der Standard Zuordnung wird die, die **\<ElementName>** im Update Gram angegeben ist, der Datenbanktabelle zugeordnet, und die untergeordneten Elemente oder Attribute werden den Daten Bank Spalten zugeordnet.  
  
 Ein Element im- **\<before>** Block muss mit nur einer Tabellenzeile in der Datenbank identisch sein. Wenn das-Element entweder mit mehreren Tabellenzeilen übereinstimmt oder mit keiner Tabellenzeile übereinstimmt, gibt das Update Gram einen Fehler zurück und bricht den gesamten- **\<sync>** Block ab.  
  
 Ein Update Gram kann mehrere Blöcke enthalten **\<sync>** . Jeder **\<sync>** Block wird als Transaktion behandelt. Jeder **\<sync>** Block kann über mehrere **\<before>** -und- **\<after>** Blöcke verfügen. Wenn Sie z. b. zwei der vorhandenen Datensätze aktualisieren, können Sie zwei **\<before>** -und- **\<after>** Paare angeben, eine für jeden zu aktualisierenden Datensatz.  
  
## <a name="using-the-updgid-attribute"></a>Verwenden des updg:id-Attributs  
 Wenn mehrere-Elemente in den **\<before>** -und-Blöcken angegeben werden **\<after>** , verwenden Sie das **updg: ID** -Attribut, um Zeilen in den **\<before>** -und-Blöcken zu markieren **\<after>** . Die Verarbeitungslogik verwendet diese Informationen, um zu bestimmen, welcher Datensatz in den **\<before>** Block Paaren mit welchem Datensatz im Block verwendet wird **\<after>** .  
  
 Das **updg: ID** -Attribut ist nicht erforderlich (obwohl empfohlen), wenn eine der folgenden Optionen vorhanden ist:  
  
-   Für die Elemente im angegebenen Zuordnungsschema ist das **SQL: key-fields-** Attribut definiert.  
  
-   Ein oder mehrere bestimmte Werte sind für das Schlüsselfeld oder die Schlüsselfelder im Updategram angegeben.  
  
 Wenn dies der Fall ist, verwendet das Update Gram die Schlüssel Spalten, die in den **SQL: key-fields** angegeben sind, um die Elemente in den **\<before>** Blöcken und zu koppeln **\<after>** .  
  
 Wenn das Zuordnungsschema keine Schlüssel Spalten (mithilfe von **SQL: key-fields**) identifiziert oder wenn das Update Gram einen Schlüssel Spaltenwert aktualisiert, müssen Sie **updg: ID**angeben.  
  
 Die Datensätze, die in den **\<before>** -und-Blöcken identifiziert werden, **\<after>** müssen sich nicht in derselben Reihenfolge befinden. Das **updg: ID** -Attribut erzwingt die Zuordnung zwischen den Elementen, die in den **\<before>** Blöcken und angegeben sind **\<after>** .  
  
 Wenn Sie ein Element im **\<before>** -Block und nur ein entsprechendes Element im- **\<after>** Block angeben, ist die Verwendung von **updg: ID** nicht erforderlich. Es wird jedoch empfohlen, **updg: ID** trotzdem anzugeben, um Mehrdeutigkeit zu vermeiden.  
  
## <a name="examples"></a>Beispiele  
 Bevor Sie die Updategrambeispiele verwenden, beachten Sie Folgendes:  
  
-   Die meisten der Beispiele verwenden die Standardzuordnung (d. h. es ist kein Zuordnungsschema im Updategram angegeben). Weitere Beispiele für Update grams, die Mapping-Schemas verwenden, finden Sie unter [Angeben eines Mappingschemas mit Anmerkungen in einem Update Gram &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
-   Die meisten der Beispiele verwenden die AdventureWorks-Beispieldatenbank. Alle Updates werden für die Tabellen in dieser Datenbank übernommen. Sie können die AdventureWorks-Datenbank wiederherstellen.  
  
### <a name="a-updating-a-record"></a>A. Aktualisieren eines Datensatzes  
 Das folgende Updategram aktualisiert den Nachnamen des Mitarbeiters in der Person.Contact-Tabelle in der AdventureWorks-Datenbank zu "Fuller". Das Updategram gibt kein Zuordnungsschema an, deswegen verwendet das Updategram die Standardzuordnung.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" />  
</updg:before>  
<updg:after>  
   <Person.Contact LastName="Abel-Achong" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 Der Datensatz, der im-Block beschrieben wird, **\<before>** stellt den aktuellen Datensatz in der Datenbank dar. Das Update Gram verwendet alle Spaltenwerte, die im-Block angegeben sind **\<before>** , um nach dem Datensatz zu suchen. In diesem Update Gram bietet der- **\<before>** Block nur die ContactID-Spalte. Daher verwendet das Update Gram nur den Wert, um nach dem Datensatz zu suchen. Wenn Sie diesem Block den LastName-Wert hinzufügen würden, würde das Updategram sowohl den ContactID- als auch den LastName-Wert für die Suche verwenden.  
  
 In diesem Update Gram bietet der- **\<after>** Block nur den LastName-Spaltenwert, da dies der einzige Wert ist, der geändert wird.  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Kopieren Sie die oben stehende Updategramvorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen UpdateLastName.xml.  
  
2.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um das Updategram auszuführen.  

     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="b-updating-multiple-records-by-using-the-updgid-attribute"></a>B. Aktualisieren von mehreren Datensätzen mit dem Attribut "updg:id"  
 In diesem Beispiel führt das Updategram zwei Updates auf die HumanResources.Shift-Tabelle in der AdventureWorks-Datenbank aus:  
  
-   Es ändert den Namen der ursprünglichen Tagschicht, die um 7.00 Uhr beginnt, von "Day" in "Early Morning".  
  
-   Es fügt eine neue Schicht namens "Late Morning" ein, die um 10.00 Uhr beginnt.  
  
 Im Update Gram erstellt das **updg: ID** -Attribut Zuordnungen zwischen Elementen in den **\<before>** -und- **\<after>** Blöcken.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift updg:id="x" Name="Day" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift updg:id="y" Name="Late Morning"   
                            StartTime="1900-01-01 10:00:00.000"  
                            EndTime="1900-01-01 18:00:00.000"  
                            ModifiedDate="2004-06-01 00:00:00.000"/>  
      <HumanResources.Shift updg:id="x" Name="Early Morning" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Beachten Sie, dass das **updg: ID** -Attribut die erste Instanz des- \<HumanResources.Shift> Elements im- **\<before>** Block mit der zweiten Instanz des- \<HumanResources.Shift> Elements im- **\<after>** Block verbindet.  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Kopieren Sie die oben stehende Updategramvorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen UpdateMultipleRecords.xml.  
  
2.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um das Updategram auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="c-specifying-multiple-before-and-after-blocks"></a>C. Angeben von mehreren \<before> -und- \<after> Blöcken  
 Um Mehrdeutigkeit zu vermeiden, können Sie das Update Gram in Beispiel B mithilfe mehrerer **\<before>** -und- **\<after>** Block Paare schreiben. Das Angeben von **\<before>** -Paaren und- **\<after>** Paaren ist eine Möglichkeit, mehrere Updates mit einer minimalen Verwirrung anzugeben. Außerdem **\<before>** **\<after>** müssen Sie das **updg: ID** -Attribut nicht verwenden, wenn jeder der-und-Blöcke höchstens ein Element angibt.  
  
> [!NOTE]  
>  Um ein paar zu bilden, **\<after>** muss das Tag direkt auf das entsprechende **\<before>** Tag folgen.  
  
 Im folgenden Update Gram aktualisiert das erste und das **\<before>** **\<after>** Paar den Verschiebungs Namen für die Tagesschicht. Das zweite Paar fügt einen neuen Schichtdatensatz ein.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="1" Name="Day" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="Early Morning" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="Late Morning"   
                            StartTime="1900-01-01 10:00:00.000"  
                            EndTime="1900-01-01 18:00:00.000"  
                            ModifiedDate="2004-06-01 00:00:00.000"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Kopieren Sie die oben stehende Updategramvorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen UpdateMultipleBeforeAfter.xml.  
  
2.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um das Updategram auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="d-specifying-multiple-sync-blocks"></a>D: Angeben mehrerer \<sync> Blöcke  
 Sie können mehrere- **\<sync>** Blöcke in einem Update Gram angeben. Jeder **\<sync>** angegebene Block ist eine unabhängige Transaktion.  
  
 Im folgenden Update Gram aktualisiert der erste **\<sync>** Block einen Datensatz in der Sales. Customer-Tabelle. Der Einfachheit halber gibt das Updategram nur die erforderlichen Spaltenwerte an, nämlich den Identitätswert (CustomerID) und den zu aktualisierenden Wert (SalesPersonID).  
  
 Der zweite **\<sync>** Block fügt der Sales. SalesOrderHeader-Tabelle zwei Datensätze hinzu. Für diese Tabelle ist SalesOrderID eine Spalte vom Typ IDENTITY. Daher gibt das Update Gram den Wert von SalesOrderID nicht in jedem der \<Sales.SalesOrderHeader> Elemente an.  
  
 Das Angeben mehrerer **\<sync>** Blöcke ist nützlich, da der zweite Block **\<sync>** (eine Transaktion) der Sales. SalesOrderHeader-Tabelle keine Datensätze hinzufügen kann. der erste **\<sync>** Block kann weiterhin den Kundendaten Satz in der Sales. Customer-Tabelle aktualisieren.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
      <Sales.Customer CustomerID="1" SalesPersonID="280" />  
    </updg:before>  
    <updg:after>  
      <Sales.Customer CustomerID="1" SalesPersonID="283" />  
    </updg:after>  
  </updg:sync>  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
   <Sales.SalesOrderHeader   
             CustomerID="1"  
             RevisionNumber="1"  
             OrderDate="2004-07-01 00:00:00.000"  
             DueDate="2004-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="01010101-2222-3333-4444-556677889900"  
             ModifiedDate="2004-07-08 00:00:00.000" />  
   <Sales.SalesOrderHeader  
             CustomerID="1"  
             RevisionNumber="1"  
             OrderDate="2004-07-01 00:00:00.000"  
             DueDate="2004-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="1000.0000"  
             TaxAmt="0.0000"  
             Freight="0.0000"  
             rowguid="10101010-2222-3333-4444-556677889900"  
             ModifiedDate="2004-07-09 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Kopieren Sie die oben stehende Updategramvorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen UpdateMultipleSyncs.xml.  
  
2.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um das Updategram auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="e-using-a-mapping-schema"></a>E. Verwenden eines Zuordnungsschemas  
 In diesem Beispiel gibt das Update Gram ein Zuordnungsschema mit dem **Mapping-Schema-** Attribut an. (Es gibt keine Standardzuordnung, d. h. das Zuordnungsschema bietet die erforderliche Zuordnung der Elemente und Attribute im Updategram zu den Datenbanktabellen und -spalten.)  
  
 Die im Updategram angegebenen Elemente und Attribute verweisen auf die Elemente und Attribute im Zuordnungsschema.  
  
 Das folgende XSD-Zuordnungs Schema enthält die **\<Customer>** Elemente, und, die **\<Order>** **\<OD>** den Tabellen Sales. Customer, Sales. SalesOrderHeader und Sales. SalesOrderDetail in der-Datenbank zugeordnet sind.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustomerOrder"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustomerOrder" >  
           <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OD"   
                             sql:relation="Sales.SalesOrderDetail"  
                             sql:relationship="OrderOD" >  
                 <xsd:complexType>  
                  <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                  <xsd:attribute name="ProductID" type="xsd:integer" />  
                  <xsd:attribute name="UnitPrice" type="xsd:decimal" />  
                  <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  <xsd:attribute name="UnitPriceDiscount" type="xsd:decimal" />   
                 </xsd:complexType>  
                </xsd:element>  
              </xsd:sequence>  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="OrderDate" type="xsd:date" />  
           </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Dieses Zuordnungsschema (UpdategramMappingSchema.xml) wird im folgenden Updategram angegeben. Das Updategram fügt in der Sales.SalesOrderDetail-Tabelle ein Auftragselement für einen bestimmten Auftrag hinzu. Das Update Gram enthält geschachtelte Elemente: ein **\<OD>** Element, das in einem-Element geschachtelt ist **\<Order>** . Die Primärschlüssel-Fremdschlüssel-Beziehung zwischen diesen beiden Elementen wird im Zuordnungsschema angegeben.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="UpdategramMappingSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43659" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43659" >  
          <OD ProductID="776" UnitPrice="2329.0000"  
              OrderQty="2" UnitPriceDiscount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Kopieren Sie das oben stehende Zuordnungsschema, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen UpdategramMappingSchema.xml.  
  
2.  Kopieren Sie die oben stehende Updategramvorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen UpdateWithMappingSchema.xml im selben Ordner, indem Sie das Zuordnungsschema (UpdategramMappingSchema.xml) gespeichert haben.  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um das Updategram auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Weitere Beispiele für Update grams, die Mapping-Schemas verwenden, finden Sie unter [Angeben eines Mappingschemas mit Anmerkungen in einem Update Gram &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
### <a name="f-using-a-mapping-schema-with-idrefs-attributes"></a>F. Verwenden eines Zuordnungsschemas mit IDREFS-Attributen  
 Dieses Beispiel veranschaulicht, wie Updategrams die IDREFS-Attribute im Zuordnungsschema verwenden, um Datensätze in mehreren Tabellen zu aktualisieren. Nehmen Sie für dieses Beispiel an, dass die Datenbank aus den folgenden Tabellen besteht:  
  
-   Student(StudentID, LastName)  
  
-   Course(CourseID, CourseName)  
  
-   Enrollment(StudentID, CourseID)  
  
 Da ein Student sich in viele Kurse einschreiben kann und an einem Kurs zahlreiche Studenten teilnehmen können, wird die dritte Tabelle, die Enrollment-Tabelle, benötigt, um diese m:n-Beziehung darzustellen.  
  
 Das folgende XSD-Mapping-Schema stellt mithilfe der **\<Student>** Elemente, und eine XML-Ansicht der Tabellen bereit **\<Course>** **\<Enrollment>** . Die **IDREFS** -Attribute im Zuordnungsschema geben die Beziehung zwischen diesen Elementen an. Das **StudentIDList** -Attribut des- **\<Course>** Elements ist ein Attribut vom Typ **IDREFS** , das auf die StudentID-Spalte in der Registrierungs Tabelle verweist. Entsprechend ist das Attribut " **attribuledin** " für das- **\<Student>** Element ein Attribut vom Typ **IDREFS** , das auf die CourseID-Spalte in der Registrierungs Tabelle verweist.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="StudentEnrollment"  
          parent="Student"  
          parent-key="StudentID"  
          child="Enrollment"  
          child-key="StudentID" />  
  
    <sql:relationship name="CourseEnrollment"  
          parent="Course"  
          parent-key="CourseID"  
          child="Enrollment"  
          child-key="CourseID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Course" sql:relation="Course"   
                             sql:key-fields="CourseID" >  
    <xsd:complexType>  
    <xsd:attribute name="CourseID"  type="xsd:string" />   
    <xsd:attribute name="CourseName"   type="xsd:string" />   
    <xsd:attribute name="StudentIDList" sql:relation="Enrollment"  
                 sql:field="StudentID"  
                 sql:relationship="CourseEnrollment"   
                                     type="xsd:IDREFS" />  
  
    </xsd:complexType>  
  </xsd:element>  
  <xsd:element name="Student" sql:relation="Student" >  
    <xsd:complexType>  
    <xsd:attribute name="StudentID"  type="xsd:string" />   
    <xsd:attribute name="LastName"   type="xsd:string" />   
    <xsd:attribute name="EnrolledIn" sql:relation="Enrollment"  
                 sql:field="CourseID"  
                 sql:relationship="StudentEnrollment"   
                                     type="xsd:IDREFS" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Jedes Mal, wenn Sie dieses Schema in einem Updategram angeben und einen Datensatz in die Course-Tabelle einfügen, fügt das Updategram einen neuen Kursdatensatz in die Course-Tabelle ein. Wenn Sie eine oder mehrere neue StudentIDs für das StudentIDList-Attribut angeben, fügt das Updategram ebenfalls einen Datensatz für jeden neuen Studenten in die Enrollment-Tabelle ein. Das Updategram stellt sicher, dass der Enrollment-Tabelle keine Duplikate hinzugefügt werden.  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Erstellen Sie diese Tabellen in der Datenbank, die im virtuellen Stammverzeichnis angegeben wird:  
  
    ```  
    CREATE TABLE Student(StudentID varchar(10) primary key,   
                         LastName varchar(25))  
    CREATE TABLE Course(CourseID varchar(10) primary key,   
                        CourseName varchar(25))  
    CREATE TABLE Enrollment(StudentID varchar(10)   
                                      references Student(StudentID),  
                           CourseID varchar(10)   
                                      references Course(CourseID))  
    ```  
  
2.  Fügen Sie diese Beispieldaten hinzu:  
  
    ```  
    INSERT INTO Student VALUES ('S1','Davoli')  
    INSERT INTO Student VALUES ('S2','Fuller')  
  
    INSERT INTO Course VALUES  ('CS101', 'C Programming')  
    INSERT INTO Course VALUES  ('CS102', 'Understanding XML')  
  
    INSERT INTO Enrollment VALUES ('S1', 'CS101')  
    INSERT INTO Enrollment VALUES ('S1', 'CS102')  
    ```  
  
3.  Kopieren Sie das oben stehende Zuordnungsschema, und fügen Sie es in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen SampleSchema.xml.  
  
4.  Speichern Sie das Updategram (SampleUpdategram) im selben Ordner, indem Sie das Zuordnungsschema im vorherigen Schritt gespeichert haben. (Dieses Updategram löscht einen Studenten mit StudentID="1" aus dem Kurs CS102.)  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101 CS102" />  
        </updg:before>  
        <updg:after >  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
5.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um das Updategram auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
6.  Speichern Sie das Updategram wie in den vorherigen Schritten beschrieben und führen Sie es aus. Das Updategram fügt den Studenten mit StudentID="1" wieder dem Kurs CS102 hinzu, indem der Enrollment-Tabelle ein Datensatz hinzugefügt wird.  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101" />  
        </updg:before>  
        <updg:after >  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101 CS102" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
7.  Speichern Sie das nächste Updategram wie in den vorherigen Schritten beschrieben und führen Sie es aus. Dieses Updategram fügt drei neue Studenten ein und schreibt Sie in den Kurs CS101 ein. Wieder fügt die IDREFS-Beziehung Datensätze in der Enrollment-Tabelle ein.  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
           <Course updg:id="y" CourseID="CS101"   
                               CourseName="C Programming" />  
        </updg:before>  
        <updg:after >  
           <Student updg:id="x1" StudentID="S3" LastName="Leverling" />  
           <Student updg:id="x2" StudentID="S4" LastName="Pecock" />  
           <Student updg:id="x3" StudentID="S5" LastName="Buchanan" />  
           <Course updg:id="y" CourseID="CS101"  
                               CourseName="C Programming"  
                               StudentIDList="S3 S4 S5" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
 Dies ist das entsprechende XDR-Schema:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ElementType name="Enrollment" sql:relation="Enrollment" sql:key-fields="StudentID CourseID">  
    <AttributeType name="StudentID" dt:type="id" />  
    <AttributeType name="CourseID" dt:type="id" />  
  
    <attribute type="StudentID" />  
    <attribute type="CourseID" />  
  </ElementType>  
  <ElementType name="Course" sql:relation="Course" sql:key-fields="CourseID">  
    <AttributeType name="CourseID" dt:type="id" />  
    <AttributeType name="CourseName" />  
  
    <attribute type="CourseID" />  
    <attribute type="CourseName" />  
  
    <AttributeType name="StudentIDList" dt:type="idrefs" />  
    <attribute type="StudentIDList" sql:relation="Enrollment" sql:field="StudentID" >  
        <sql:relationship  
                key-relation="Course"  
                key="CourseID"  
                foreign-relation="Enrollment"  
                foreign-key="CourseID" />  
    </attribute>  
  
  </ElementType>  
  <ElementType name="Student" sql:relation="Student">  
    <AttributeType name="StudentID" dt:type="id" />  
     <AttributeType name="LastName" />  
  
    <attribute type="StudentID" />  
    <attribute type="LastName" />  
  
    <AttributeType name="EnrolledIn" dt:type="idrefs" />  
    <attribute type="EnrolledIn" sql:relation="Enrollment" sql:field="CourseID" >  
        <sql:relationship  
                key-relation="Student"  
                key="StudentID"  
                foreign-relation="Enrollment"  
                foreign-key="StudentID" />  
    </attribute>  
  
    <element type="Enrollment" sql:relation="Enrollment" >  
        <sql:relationship key-relation="Student"  
                          key="StudentID"  
                          foreign-relation="Enrollment"  
                          foreign-key="StudentID" />  
    </element>  
  </ElementType>  
  
</Schema>  
```  
  
 Weitere Beispiele für Update grams, die Mapping-Schemas verwenden, finden Sie unter [Angeben eines Mappingschemas mit Anmerkungen in einem Update Gram &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitsüberlegungen zu Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
