---
title: Daten Satz Generierungsprozess (SQLXML)
description: Erfahren Sie mehr über die Details des Generierungs Prozesses für den XML-Massen Ladevorgang in SQLXML 4,0.
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], record generation process
- node scopes [SQLXML]
- record subsets [SQLXML]
- scope [SQLXML]
- key ordering rules [SQLXML]
- record generation process for bulk loads [SQLXML]
- entering node scope [SQLXML]
- bulk load [SQLXML], record generation process
- leaving node scope [SQLXML]
- schema mapping [SQLXML]
ms.assetid: d8885bbe-6f15-4fb9-9684-ca7883cfe9ac
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 380698d9d164012f8e0be53f19be6cef8b7c56e8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773056"
---
# <a name="record-generation-process-sqlxml-40"></a>Datensatzgenerierungsprozess (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Beim XML-Massenladen werden die XML-Eingabedaten verarbeitet und Datensätze für die entsprechenden Tabellen in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vorbereitet. Die interne Logik beim XML-Massenladen entscheidet darüber, wann ein neuer Datensatz generiert wird, welche untergeordneten Elemente oder Attributwerte in die Datensatzfelder kopiert werden und wann der Datensatz vollständig ist und zum Einfügen an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gesendet werden kann.  
  
 Beim XML-Massenladen werden nicht alle XML-Eingabedaten in den Speicher geladen und keine vollständigen Datensätze erstellt, bevor Daten an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gesendet werden. Dies liegt daran, dass XML-Eingabedaten sehr große Dokumente bilden können und das Laden des gesamten Dokuments in den Speicher kostspielig sein kann. Stattdessen wird beim XML-Massenladen wie folgt vorgegangen:  
  
1.  Analysieren des Zuordnungsschemas und Vorbereiten des notwendigen Ausführungsplans.  
  
2.  Anwenden des Ausführungsplans auf die Daten im Eingabedatenstrom.  
  
 Aufgrund dieser sequenziellen Verarbeitung müssen die XML-Eingabedaten auf eine bestimmte Weise bereitgestellt werden. Es ist wichtig, zu verstehen, wie das Zuordnungsschema beim XML-Massenladen analysiert wird und wie der Datensatzgenerierungsprozess abläuft. Mit diesem Wissen können Sie ein Zuordnungsschema für XML-Massenladen bereitstellen, das die gewünschten Ergebnisse liefert.  
  
 Beim XML-Massenladen werden gängige Anmerkungen im Zuordnungsschema verarbeitet, darunter Spalten- und Tabellenzuordnungen (die explizit über Anmerkungen oder implizit über die Standardzuordnung angegeben werden), sowie Joinbeziehungen.  
  
> [!NOTE]  
>  Es wird davon ausgegangen, dass Sie mit XSD- oder XDR-Zuordnungsschemas mit Anmerkungen vertraut sind. Weitere Informationen zu Schemas finden Sie unter [Einführung in XSD-Schemas mit Anmerkungen &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) oder [mit Anmerkungen versehene XDR-Schemas &#40;in SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
 Grundlage für das Verständnis der Datensatzgenerierung sind folgende Konzepte:  
  
-   Bereich eines Knotens  
  
-   Datensatzgenerierungsregel  
  
-   Datensatzteilmenge und Schlüsselsortierregel  
  
-   Ausnahmen von der Datensatzgenerierungsregel  
  
## <a name="scope-of-a-node"></a>Bereich eines Knotens  
 Ein Knoten (ein Element oder Attribut) in einem XML-Dokument wird in den Gültigkeits *Bereich* eingegeben, wenn der XML-Massen Ladevorgang im XML-Eingabedaten Strom auftritt. Bei Elementknoten bringt das Starttag des Elements das Element in den Bereich. Bei Attributknoten bringt der Attributname das Attribut in den Bereich.  
  
 Ein Knoten verlässt den Bereich, wenn keine Daten mehr dafür vorliegen, das heißt entweder am Endtag (im Fall eines Elementknotens) oder am Ende eines Attributwerts (im Fall eines Attributknotens).  
  
## <a name="record-generation-rule"></a>Datensatzgenerierungsregel  
 Gelangt ein (Element- oder Attribut-) Knoten in den Bereich, kann daraus ein Datensatz generiert werden. Der Datensatz besteht weiter, solange der zugeordnete Knoten im Bereich ist. Verlässt der Knoten den Bereich, wird der generierte Datensatz als vollständig (mit Daten) betrachtet und zum Einfügen an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gesendet.  
  
 Betrachten Sie beispielsweise das folgende XSD-Schemafragment:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Customer" sql:relation="Customers" >  
   <xsd:complexType>  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
     <xsd:attribute name="CompanyName" type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Das Schema gibt ein **\<Customer>** -Element mit den Attributen **CustomerID** und **CompanyName** an. Die **SQL: Relation** -Anmerkung ordnet das- **\<Customer>** Element der Customers-Tabelle zu.  
  
 Betrachten Sie dieses Fragment eines XML-Dokuments:  
  
```  
<Customer CustomerID="1" CompanyName="xyz" />  
<Customer CustomerID="2" CompanyName="abc" />  
...  
```  
  
 Wenn für das XML-Massenladen das in den vorstehenden Absätzen erläuterte Schema und XML-Daten als Eingabe bereitgestellt werden, werden die (Element- und Attribut-) Knoten in den Quelldaten wie folgt verarbeitet:  
  
-   Das Starttag des ersten **\<Customer>** Elements bringt dieses Element in den Gültigkeitsbereich. Dieser Knoten ist der Customers-Tabelle zugeordnet. Beim XML-Massenladen wird daher ein Datensatz für die Customers-Tabelle generiert.  
  
-   Im Schema sind alle Attribute des- **\<Customer>** Elements Spalten der Customers-Tabelle zugeordnet. Wenn diese Attribute in den Bereich gelangen, werden ihre Werte in den Kundendatensatz kopiert, der bereits vom übergeordneten Bereich generiert wurde.  
  
-   Wenn das XML-Massen laden das Endtag für das-Element erreicht, verlässt das-Element den Gültigkeits **\<Customer>** Bereich. Damit wird der Datensatz als vollständig betrachtet und an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gesendet.  
  
 Das XML-Massen laden folgt diesem Prozess für jedes nachfolgende **\<Customer>** Element.  
  
> [!IMPORTANT]  
>  Da in diesem Modell ein Datensatz eingefügt wird, wenn das Endtag erreicht ist (oder der Knoten den Bereich verlässt), müssen Sie alle mit dem Datensatz verknüpften Daten innerhalb des Knotenbereichs definieren.  
  
## <a name="record-subset-and-the-key-ordering-rule"></a>Daten Satz Teilmenge und Schlüssel Bestellungs Regel  
 Wenn Sie ein Zuordnungsschema angeben **\<sql:relationship>** , das verwendet, bezieht sich der untergeordnete Begriff auf den Satz von Datensätzen, der auf der fremd Seite der Beziehung generiert wird. Im folgenden Beispiel befinden sich die CustOrder-Datensätze auf der fremd Seite **\<sql:relationship>** .  
  
 Nehmen Sie z. B. an, dass eine Datenbank die folgenden Tabellen enthält:  
  
-   Cust (CustomerID, CompanyName, City)  
  
-   CustOrder (CustomerID, OrderID)  
  
 Die CustomerID in der CustOrder-Tabelle ist ein Fremdschlüssel, der auf den CustomerID-Primärschlüssel in der Cust-Tabelle verweist.  
  
 Betrachten Sie jetzt die im folgenden XSD-Schema mit Anmerkungen angegebene XML-Sicht. Dieses Schema verwendet **\<sql:relationship>** , um die Beziehung zwischen den Tabellen Cust und CustOrder anzugeben.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Die XML-Beispieldaten und die Schritte zum Erstellen eines funktionierenden Beispiels sind unten aufgeführt.  
  
-   Wenn ein **\<Customer>** Elementknoten in der XML-Datendatei in den Gültigkeitsbereich eintritt, generiert XML-Massen laden einen Datensatz für die Cust-Tabelle. Beim XML-Massen laden werden dann die erforderlichen Spaltenwerte (CustomerID, CompanyName und City) aus den untergeordneten **\<CustomerID>** Elementen, und kopiert, **\<CompanyName>** **\<City>** Wenn diese Elemente in den Gültigkeitsbereich gelangen.  
  
-   Wenn ein **\<Order>** Elementknoten in den Bereich gelangt, generiert das XML-Massen laden einen Datensatz für die CustOrder-Tabelle. XML-Massen laden kopiert den Wert des **OrderID** -Attributs in diesen Datensatz. Der erforderliche Wert für die CustomerID-Spalte wird aus dem untergeordneten- **\<CustomerID>** Element des- **\<Customer>** Elements abgerufen. Beim XML-Massen laden werden die in angegebenen Informationen verwendet, **\<sql:relationship>** um den CustomerID-Fremdschlüssel Wert für diesen Datensatz abzurufen, es sei denn, das **CustomerID-** Attribut wurde im- **\<Order>** Element angegeben. Die allgemeine Regel ist, dass das XML-Massen laden diesen Wert verwendet, wenn das untergeordnete Element explizit einen Wert für das Fremdschlüssel Attribut angibt und den Wert aus dem übergeordneten Element nicht unter Verwendung des angegebenen-Objekts abruft **\<sql:relationship>** . Wenn dieser **\<Order>** Elementknoten den Gültigkeitsbereich verlässt, sendet XML-Massen laden den Datensatz an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und verarbeitet dann alle nachfolgenden **\<Order>** Elementknoten auf die gleiche Weise.  
  
-   Schließlich verlässt der **\<Customer>** Elementknoten den Gültigkeitsbereich. Der Kundendatensatz wird daraufhin an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gesendet. Bei allen nachfolgenden Kunden im XML-Datenstrom wird nach demselben Prozess vorgegangen.  
  
 Zwei Beobachtungen zum Zuordnungsschema:  
  
-   Wenn das Schema der "Containment"-Regel entspricht (z. b. werden alle Daten, die dem Kunden und der Bestellung zugeordnet sind, innerhalb des Bereichs der zugeordneten **\<Customer>** -und- **\<Order>** Elementknoten definiert), ist das Massen Laden erfolgreich.  
  
-   Beim Beschreiben des- **\<Customer>** Elements werden seine untergeordneten Elemente in der entsprechenden Reihenfolge angegeben. In diesem Fall wird das untergeordnete- **\<CustomerID>** Element vor dem untergeordneten- **\<Order>** Element angegeben. Dies bedeutet, dass der Elementwert in der XML-Eingabe Datendatei **\<CustomerID>** als Fremdschlüssel Wert verfügbar ist, wenn das Element in den Gültigkeits **\<Order>** Bereich gelangt. Die Schlüsselattribute werden gemäß der "Schlüsselsortierregel" zuerst angegeben.  
  
     Wenn Sie das untergeordnete- **\<CustomerID>** Element nach dem untergeordneten- **\<Order>** Element angeben, ist der Wert nicht verfügbar, wenn das Element in den Gültigkeits **\<Order>** Bereich eintritt. Wenn das **\</Order>** Endtag dann gelesen wird, gilt der Datensatz für die CustOrder-Tabelle als abgeschlossen und wird in die CustOrder-Tabelle mit einem NULL-Wert für die CustomerID-Spalte eingefügt, was nicht das gewünschte Ergebnis ist.  
  
#### <a name="to-create-a-working-sample"></a>So erstellen Sie ein funktionierendes Beispiel  
  
1.  Speichern Sie das in diesem Beispiel bereitgestellte Schema unter dem Dateinamen SampleSchema.xml.  
  
2.  Erstellen Sie die folgenden Tabellen:  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int         PRIMARY KEY,  
                  CompanyName    varchar(20) NOT NULL,  
                  City           varchar(20) DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                 OrderID        int         PRIMARY KEY,  
                 CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID))  
    GO  
    ```  
  
3.  Speichern Sie die folgenden XML-Eingabedaten unter dem Dateinamen SampleXMLData.xml:  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>   
        <Order OrderID="1" />  
        <Order OrderID="2" />  
      </Customers>  
  
      <Customers>  
        <CustomerID>1112</CustomerID>  
        <CompanyName>Toms Spezialitten</CompanyName>  
        <City>LA</City>  
        <Order OrderID="3" />  
      </Customers>  
      <Customers>  
        <CustomerID>1113</CustomerID>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
    </Customers>  
    </ROOT>  
    ```  
  
4.  Speichern Sie folgendes [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript)-Beispiel unter dem Dateinamen BulkLoad.vbs, und führen Sie es aus, um das XML-Massenladen auszuführen:  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
## <a name="exceptions-to-the-record-generation-rule"></a>Ausnahmen von der Datensatzgenerierungsregel  
 Gelangt ein Knoten vom Typ IDREF oder IDREFS in den Bereich, wird kein Datensatz generiert. Stellen Sie sicher, dass an irgendeiner Stelle im Schema eine vollständige Beschreibung des Datensatzes vorhanden ist. Die **dt: Type = "nmtokens"** -Anmerkungen werden ignoriert, wenn der IDREFS-Typ ignoriert wird.  
  
 Sehen Sie sich beispielsweise das folgende XSD-Schema an, das die **\<Customer>** Elemente und beschreibt **\<Order>** . Das- **\<Customer>** Element enthält ein **OrderList** -Attribut des IDREFS-Typs. Das **\<sql:relationship>** -Tag gibt die 1: n-Beziehung zwischen dem Kunden und der Liste der Bestellungen an.  
  
 Das ist das Schema:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
                 parent="Cust"  
                 parent-key="CustomerID"  
                 child="CustOrder"  
                 child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
    <xsd:attribute name="CustomerID" type="xsd:integer" />  
    <xsd:attribute name="CompanyName" type="xsd:string" />  
    <xsd:attribute name="City" type="xsd:string" />  
    <xsd:attribute name="OrderList"   
                       type="xsd:IDREFS"   
                       sql:relation="CustOrder"   
                       sql:field="OrderID"  
                       sql:relationship="CustCustOrder" >  
    </xsd:attribute>  
  </xsd:complexType>  
 </xsd:element>  
  
  <xsd:element name="Order" sql:relation="CustOrder" >  
   <xsd:complexType>  
    <xsd:attribute name="OrderID" type="xsd:string" />  
    <xsd:attribute name="CustomerID" type="xsd:integer" />  
    <xsd:attribute name="OrderDate" type="xsd:date" />  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 Da der Massen Ladevorgang die Knoten des IDREFS-Typs ignoriert, gibt es keine Daten Satz Generierung, wenn der **OrderList** -Attribut Knoten in den Gültigkeitsbereich gelangt. Um die Auftragsdatensätze der Orders-Tabelle hinzuzufügen, müssen Sie demnach diese Aufträge irgendwo im Schema beschreiben. In diesem Schema wird durch das Angeben des- **\<Order>** Elements sichergestellt, dass das XML-Massen laden die Auftragsdaten Sätze der Orders-Tabelle hinzufügt. Das- **\<Order>** Element beschreibt alle Attribute, die zum Auffüllen des Datensatzes für die CustOrder-Tabelle erforderlich sind.  
  
 Sie müssen sicherstellen, dass die Werte **CustomerID** und **OrderID** im- **\<Customer>** Element den Werten im- **\<Order>** Element entsprechen. Sie sind verantwortlich für die Wahrung der referenziellen Integrität.  
  
#### <a name="to-test-a-working-sample"></a>So testen Sie ein funktionstüchtiges Beispiel  
  
1.  Erstellen Sie die folgenden Tabellen:  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int          PRIMARY KEY,  
                  CompanyName    varchar(20)  NOT NULL,  
                  City           varchar(20)  DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID        varchar(10) PRIMARY KEY,  
                  CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID),  
                  OrderDate      datetime DEFAULT '2000-01-01')  
    GO  
    ```  
  
2.  Speichern Sie das in diesem Beispiel bereitgestellte Zuordnungsschema unter dem Dateinamen SampleSchema.xml.  
  
3.  Speichern Sie die folgenden XML-Daten unter dem Dateinamen SampleXMLData.xml:  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1111" CompanyName="Sean Chai" City="NY"  
                 OrderList="Ord1 Ord2" />  
      <Customers CustomerID="1112" CompanyName="Dont Know" City="LA"  
                 OrderList="Ord3 Ord4" />  
      <Order OrderID="Ord1" CustomerID="1111" OrderDate="1999-01-01" />  
      <Order OrderID="Ord2" CustomerID="1111" OrderDate="1999-02-01" />  
      <Order OrderID="Ord3" CustomerID="1112" OrderDate="1999-03-01" />  
      <Order OrderID="Ord4" CustomerID="1112" OrderDate="1999-04-01" />  
    </ROOT>  
    ```  
  
4.  Speichern Sie dieses VBScript-Beispiel (SampleVB.vbs), und führen Sie es aus, um das XML-Massenladen auszuführen:  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
  
