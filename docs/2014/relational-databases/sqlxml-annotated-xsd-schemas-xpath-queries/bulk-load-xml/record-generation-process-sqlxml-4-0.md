---
title: Datensatzgenerierungsprozess (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 2b43765b03ba42cede8c6879e749f1701f306d1f
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2019
ms.locfileid: "66013336"
---
# <a name="record-generation-process-sqlxml-40"></a>Datensatzgenerierungsprozess (SQLXML 4.0)
  Beim XML-Massenladen werden die XML-Eingabedaten verarbeitet und Datensätze für die entsprechenden Tabellen in Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vorbereitet. Die interne Logik beim XML-Massenladen entscheidet darüber, wann ein neuer Datensatz generiert wird, welche untergeordneten Elemente oder Attributwerte in die Datensatzfelder kopiert werden und wann der Datensatz vollständig ist und zum Einfügen an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gesendet werden kann.  
  
 Beim XML-Massenladen werden nicht alle XML-Eingabedaten in den Speicher geladen und keine vollständigen Datensätze erstellt, bevor Daten an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gesendet werden. Dies liegt daran, dass XML-Eingabedaten sehr große Dokumente bilden können und das Laden des gesamten Dokuments in den Speicher kostspielig sein kann. Stattdessen wird beim XML-Massenladen wie folgt vorgegangen:  
  
1.  Analysieren des Zuordnungsschemas und Vorbereiten des notwendigen Ausführungsplans.  
  
2.  Anwenden des Ausführungsplans auf die Daten im Eingabedatenstrom.  
  
 Aufgrund dieser sequenziellen Verarbeitung müssen die XML-Eingabedaten auf eine bestimmte Weise bereitgestellt werden. Es ist wichtig, zu verstehen, wie das Zuordnungsschema beim XML-Massenladen analysiert wird und wie der Datensatzgenerierungsprozess abläuft. Mit diesem Wissen können Sie ein Zuordnungsschema für XML-Massenladen bereitstellen, das die gewünschten Ergebnisse liefert.  
  
 Beim XML-Massenladen werden gängige Anmerkungen im Zuordnungsschema verarbeitet, darunter Spalten- und Tabellenzuordnungen (die explizit über Anmerkungen oder implizit über die Standardzuordnung angegeben werden), sowie Joinbeziehungen.  
  
> [!NOTE]  
>  Es wird davon ausgegangen, dass Sie mit XSD- oder XDR-Zuordnungsschemas mit Anmerkungen vertraut sind. Weitere Informationen zu Schemas finden Sie unter [Einführung in XSD-Schemas mit Anmerkungen versehen &#40;SQLXML 4.0&#41; ](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) oder [XDR-Schemas mit Anmerkungen versehen &#40;in SQLXML 4.0 veraltet&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
 Grundlage für das Verständnis der Datensatzgenerierung sind folgende Konzepte:  
  
-   Bereich eines Knotens  
  
-   Datensatzgenerierungsregel  
  
-   Datensatzteilmenge und Schlüsselsortierregel  
  
-   Ausnahmen von der Datensatzgenerierungsregel  
  
## <a name="scope-of-a-node"></a>Bereich eines Knotens  
 Ein Knoten (ein Element oder Attribut) in einem XML-Dokument *in den Bereich* beim XML-Massenladen tritt in der XML-Eingabedatenstrom. Bei Elementknoten bringt das Starttag des Elements das Element in den Bereich. Bei Attributknoten bringt der Attributname das Attribut in den Bereich.  
  
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
  
 Das Schema gibt ein  **\<Kunden >** -Element mit **"CustomerID"** und **CompanyName** Attribute. Die `sql:relation` -Anmerkung ordnet das  **\<Kunden >** Element zur Customers-Tabelle.  
  
 Betrachten Sie dieses Fragment eines XML-Dokuments:  
  
```  
<Customer CustomerID="1" CompanyName="xyz" />  
<Customer CustomerID="2" CompanyName="abc" />  
...  
```  
  
 Wenn für das XML-Massenladen das in den vorstehenden Absätzen erläuterte Schema und XML-Daten als Eingabe bereitgestellt werden, werden die (Element- und Attribut-) Knoten in den Quelldaten wie folgt verarbeitet:  
  
-   Das Starttag des ersten  **\<Kunden >** -Elements bringt dieses Element im Bereich. Dieser Knoten ist der Customers-Tabelle zugeordnet. Beim XML-Massenladen wird daher ein Datensatz für die Customers-Tabelle generiert.  
  
-   Im Schema alle Attribute der  **\<Kunden >** Spalten der Customers-Tabelle. Wenn diese Attribute in den Bereich gelangen, werden ihre Werte in den Kundendatensatz kopiert, der bereits vom übergeordneten Bereich generiert wurde.  
  
-   Bei Erreichen des XML-Massenladen das Endtag für das  **\<Kunden >** -Element, der das Element den Gültigkeitsbereich verlässt. Damit wird der Datensatz als vollständig betrachtet und an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gesendet.  
  
 XML-Massenladen nach diesem Prozess für jedes nachfolgende  **\<Kunden >** Element.  
  
> [!IMPORTANT]  
>  Da in diesem Modell ein Datensatz eingefügt wird, wenn das Endtag erreicht ist (oder der Knoten den Bereich verlässt), müssen Sie alle mit dem Datensatz verknüpften Daten innerhalb des Knotenbereichs definieren.  
  
## <a name="record-subset-and-the-key-ordering-rule"></a>Datensatzteilmenge und den Schlüssel, die Reihenfolge der Regel  
 Wenn Sie ein Zuordnungsschema angeben, das `<sql:relationship>` verwendet, werden diejenigen Datensätze als Teilmenge bezeichnet, die auf der Fremdschlüsselseite der Beziehung generiert werden. Im folgenden Beispiel sind die CustOrder-Datensätze auf der Fremdschlüsselseite, `<sql:relationship>`.  
  
 Nehmen Sie z. B. an, dass eine Datenbank die folgenden Tabellen enthält:  
  
-   Cust (CustomerID, CompanyName, City)  
  
-   CustOrder (CustomerID, OrderID)  
  
 Die CustomerID in der CustOrder-Tabelle ist ein Fremdschlüssel, der auf den CustomerID-Primärschlüssel in der Cust-Tabelle verweist.  
  
 Betrachten Sie jetzt die im folgenden XSD-Schema mit Anmerkungen angegebene XML-Sicht. Dieses Schema verwendet `<sql:relationship>`, um die Beziehung zwischen den Tabellen Cust und CustOrder anzugeben.  
  
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
  
-   Wenn eine  **\<Kunden >** Elementknoten in das XML-Datendatei in den Bereich gelangt, XML-Massenladen generiert einen Datensatz für die Cust-Tabelle. XML-Massenladen kopiert dann die erforderlichen Spaltenwerte (CustomerID, CompanyName und City) aus der  **\<"CustomerID" >**,  **\<CompanyName >**, und die  **\<City >** untergeordneten Elemente wie diese Elemente in den Bereich gelangen.  
  
-   Wenn ein  **\<Reihenfolge >** Elementknoten in den Bereich gelangt, XML-Massenladen generiert einen Datensatz für die CustOrder-Tabelle. XML-Massenladen kopiert den Wert der **"OrderID"** -Attributs in diesen Datensatz. Der erforderliche Wert für die Spalte "CustomerID" aus erfolgt die  **\<"CustomerID" >** untergeordnetes Element von der  **\<Kunden >** Element. XML-Massenladen verwendet die Informationen, die im angegebenen `<sql:relationship>` die CustomerID Fremdschlüsselwerts für diesen Datensatz abrufen, es sei denn, die **"CustomerID"** Attribut wurde angegeben, der  **\<Reihenfolge >** Element. Generell gilt, dass beim XML-Massenladen der explizit im untergeordneten Element als Fremdschlüsselattribut angegebene Wert verwendet wird (sofern vorhanden) und er nicht über `<sql:relationship>` aus dem übergeordneten Element abgerufen wird. Wie diese  **\<Reihenfolge >** Elementknoten den Gültigkeitsbereich verlässt, XML-Massenladen der Datensatz an gesendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und verarbeitet anschließend alle nachfolgenden  **\<Reihenfolge >** Elementknoten auf die gleiche Weise.  
  
-   Zum Schluss die  **\<Kunden >** Elementknoten den Gültigkeitsbereich verlässt. Der Kundendatensatz wird daraufhin an [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gesendet. Bei allen nachfolgenden Kunden im XML-Datenstrom wird nach demselben Prozess vorgegangen.  
  
 Zwei Beobachtungen zum Zuordnungsschema:  
  
-   Erfüllt das Schema die Regel "Aufnahme" (z. B. alle Daten, die die Kunden und dem Auftrag zugeordnet ist definiert wird, innerhalb des Bereichs des zugeordneten  **\<Kunden >** und  **\<Reihenfolge >** Elementknoten), das Massenladen erfolgreich.  
  
-   Bei der Beschreibung der  **\<Kunden >** -Elements werden seine untergeordneten Elemente in der richtigen Reihenfolge angegeben werden. In diesem Fall die  **\<"CustomerID" >** untergeordnetes Element angegeben ist, bevor Sie die  **\<Reihenfolge >** untergeordnetes Element. Dies bedeutet, dass in der XML-Eingabedatendatei der  **\<"CustomerID" >** Wert des Elements steht als Fremdschlüssel Wert fest, wenn die  **\<Reihenfolge >** Element in den Bereich gelangt. Die Schlüsselattribute werden gemäß der "Schlüsselsortierregel" zuerst angegeben.  
  
     Bei Angabe der  **\<"CustomerID" >** untergeordneten Element an, nach der  **\<Reihenfolge >** untergeordnetes Element der Wert ist nicht verfügbar, wenn die  **\< Reihenfolge >** Element in den Bereich gelangt. Wenn die  **\</Order >** Endtag wird dann gelesen, die der Datensatz für die CustOrder-Tabelle als vollständig angesehen und wird in die CustOrder-Tabelle mit einem Nullwert für die CustomerID-Spalte, die nicht das gewünschte Ergebnis ist.  
  
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
 Gelangt ein Knoten vom Typ IDREF oder IDREFS in den Bereich, wird kein Datensatz generiert. Stellen Sie sicher, dass an irgendeiner Stelle im Schema eine vollständige Beschreibung des Datensatzes vorhanden ist. Die `dt:type="nmtokens"`-Anmerkungen werden ebenso wie der IDREFS-Typ ignoriert.  
  
 Betrachten Sie beispielsweise die folgende XSD-Schema beschreibt  **\<Kunden >** und  **\<Reihenfolge >** Elemente. Die  **\<Kunden >** -Element enthält eine **OrderList** Attribut des IDREFS-Typs. Das `<sql:relationship>`-Tag gibt die 1:n-Beziehung zwischen dem Kunden und der Auftragsliste an.  
  
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
  
 Da das Massenladen Knoten vom IDREFS-Typ ignoriert, es wird kein Datensatz generiert bei der **OrderList** Attributknoten, die in den Bereich gelangt. Um die Auftragsdatensätze der Orders-Tabelle hinzuzufügen, müssen Sie demnach diese Aufträge irgendwo im Schema beschreiben. In diesem Schema angeben der  **\<Reihenfolge >** -Elements sicher, dass die XML-Massenladen die Auftragsdatensätze der Orders-Tabelle hinzugefügt. Die  **\<Reihenfolge >** -Element beschreibt alle Attribute, die zum Auffüllen des Datensatzes für die CustOrder-Tabelle erforderlich sind.  
  
 Müssen Sie sicherstellen, dass die **"CustomerID"** und **"OrderID"** Werte in der  **\<Kunden >** Element entsprechen den Werten in der  **\<Reihenfolge >** Element. Sie sind verantwortlich für die Wahrung der referenziellen Integrität.  
  
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
  
  
