---
title: Mapping-Schemas mit Anmerkungen für ein Update Gram (SQLXML)
description: Erfahren Sie, wie ein mit Anmerkungen versehene XSD-oder XDR-Mapping-Schema, das in einem SQLXML 4,0-Update Gram angegeben ist, zum Verarbeiten von Updates für eine Datenbank verwendet wird.
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, updategrams
- data types [SQLXML], mapping schema in updategrams
- updategrams [SQLXML], annotated mapping schemas
- annotated XDR schemas, updategrams
- inverse attribute
- parent-child relationships [SQLXML]
- mapping-schema attribute
- mapping schema [SQLXML], updategrams
- sql:inverse
ms.assetid: 2e266ed9-4cfb-434a-af55-d0839f64bb9a
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ed9225fad50f467dfcbc71068b46a6d822119ea9
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84882192"
---
# <a name="specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-40"></a>Angeben eines Zuordnungsschemas mit Anmerkungen in einem Updategram (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In diesem Thema wird erläutert, wie das in einem Updategram angegebene Zuordnungsschema (XSD oder XDR) zur Verarbeitung von Updates verwendet wird. In einem Update Gram können Sie den Namen eines Zuordnungsschemas bereitstellen, das bei der Zuordnung der Elemente und Attribute im Update Gram zu Tabellen und Spalten in verwendet werden soll [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Wenn in einem Updategram ein Zuordnungsschema angegeben ist, müssen die im Updategram festgelegten Element- und Attributnamen den Elementen und Attributen im Zuordnungsschema zugeordnet werden.  
  
 Um ein Zuordnungsschema anzugeben, verwenden Sie das **Mapping-Schema-** Attribut des- **\<sync>** Elements. Die folgenden Beispiele zeigen zwei Updategrams: ein Updategram, das ein einfaches Zuordnungsschema verwendet, und ein Updategram, das ein komplexeres Schema verwendet.  
  
> [!NOTE]  
>  Diese Dokumentation setzt voraus, dass Sie mit Vorlagen und der Unterstützung von Zuordnungsschemas in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vertraut sind. Weitere Informationen finden Sie unter [Einführung in XSD-Schemas mit Anmerkungen &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md). Informationen zu Legacy Anwendungen, die XDR verwenden, finden Sie unter mit Anmerkungen versehene [XDR-Schemas &#40;in SQLXML 4,0&#41;veraltet ](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="dealing-with-data-types"></a>Umgehen mit Datentypen  
 Wenn das Schema den **Image**-, **Binary**-oder **varbinary** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Datentyp (mithilfe von **SQL: datatype**) angibt und keinen XML-Datentyp angibt, geht das Update Gram davon aus, dass der XML-Datentyp die **binäre Basis 64**ist. Wenn es sich bei den Daten um den Typ **bin. Base** handelt, müssen Sie explizit den Typ angeben (**dt: Type = bin. Base** oder **Type = "xsd: hexBinary"**).  
  
 Wenn das Schema den **DateTime**-, **Date**-oder **time** -XSD-Datentyp angibt, müssen Sie auch den entsprechenden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datentyp mithilfe von **SQL: datatype = "DateTime"** angeben.  
  
 Bei der Behandlung von Parametern des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **Money** -Typs müssen Sie für den entsprechenden Knoten im Zuordnungsschema explizit **SQL: datatype = "Money"** angeben.  
  
## <a name="examples"></a>Beispiele  
 Wenn Sie in den folgenden Beispielen funktionierende Beispiele erstellen möchten, müssen Sie die unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)angegebenen Anforderungen erfüllen.  
  
### <a name="a-creating-an-updategram-with-a-simple-mapping-schema"></a>A. Erstellen eines Updategrams mit einem einfachen Zuordnungsschema  
 Das folgende XSD-Schema (SampleSchema.xml) ist ein Zuordnungs Schema, das das- **\<Customer>** Element der Sales. Customer-Tabelle zuordnet:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
        <xsd:attribute name="CustID"    
                       sql:field="CustomerID"   
                       type="xsd:string" />  
        <xsd:attribute name="RegionID"    
                       sql:field="TerritoryID"    
                       type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Das folgende Updategram fügt einen Datensatz in die Sales.Customer-Tabelle ein und ordnet diese Daten anhand des vorherigen Zuordnungsschemas der Tabelle ordnungsgemäß zu. Beachten Sie, dass für das Update Gram derselbe Elementname verwendet wird, der **\<Customer>** im Schema definiert ist. Dies ist obligatorisch, da das Updategram ein bestimmtes Schema angibt.  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen SampleUpdateSchema.xml.  
  
2.  Kopieren Sie die unten stehende Updategramvorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen SampleUpdategram.xml im gleichen Verzeichnis, in dem Sie SampleUpdateSchema.xml gespeichert haben.  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleUpdateSchema.xml">  
        <updg:before>  
          <Customer CustID="1" RegionID="1"  />  
        </updg:before>  
        <updg:after>  
          <Customer CustID="1" RegionID="2" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungschema (SampleUpdateSchema.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Dies ist das entsprechende XDR-Schema:  
  
```  
<?xml version="1.0" ?>  
   <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
         xmlns:dt="urn:schemas-microsoft-com:datatypes"   
         xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
     <ElementType name="Customer" sql:relation="Sales.Customer" >  
       <AttributeType name="CustID" />  
       <AttributeType name="RegionID" />  
  
       <attribute type="CustID" sql:field="CustomerID" />  
       <attribute type="RegionID" sql:field="TerritoryID" />  
     </ElementType>  
   </Schema>   
```  
  
### <a name="b-inserting-a-record-by-using-the-parent-child-relationship-specified-in-the-mapping-schema"></a>B. Einfügen eines Datensatzes durch Verwenden der im Zuordnungsschema angegebenen Über-/Unterordnungsbeziehung  
 Schemaelemente können in Beziehung gesetzt werden. Das **\<sql:relationship>** -Element gibt die über-/Unterordnungsbeziehung zwischen den Schema Elementen an. Mit diesen Informationen werden die entsprechenden Tabellen aktualisiert, die Primärschlüssel-Fremdschlüssel-Beziehungen aufweisen.  
  
 Das folgende Mapping-Schema (SampleSchema.xml) besteht aus zwei Elementen **\<Order>** **\<OD>** : und:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="OD"   
                     sql:relation="Sales.SalesOrderDetail"  
                     sql:relationship="OrderOD" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID"   type="xsd:integer" />  
              <xsd:attribute name="ProductID" type="xsd:integer" />  
             <xsd:attribute name="UnitPrice"  type="xsd:decimal" />  
             <xsd:attribute name="OrderQty"   type="xsd:integer" />  
             <xsd:attribute name="UnitPriceDiscount"   type="xsd:decimal" />  
  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesOrderID"  type="xsd:integer" />  
        <xsd:attribute name="OrderDate"  type="xsd:date" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Das folgende Update Gram verwendet dieses XSD-Schema, um einen neuen Bestell Detaildaten Satz (ein- **\<OD>** Element im- **\<after>** Block) für die Bestellung 43860 hinzuzufügen. Das **Mapping-Schema-** Attribut wird verwendet, um das Zuordnungsschema im Update Gram anzugeben.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43860" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43860" >  
           <OD ProductID="753" UnitPrice="$10.00"  
               Quantity="5" Discount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen SampleUpdateSchema.xml.  
  
2.  Kopieren Sie die oben stehende Updategramvorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen SampleUpdategram.xml im gleichen Verzeichnis, in dem Sie SampleUpdateSchema.xml gespeichert haben.  
  
     Der für das Zuordnungschema (SampleUpdateSchema.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Dies ist das entsprechende XDR-Schema:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="OD" sql:relation="Sales.SalesOrderDetail" >  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="ProductID" />  
    <AttributeType name="UnitPrice"  dt:type="fixed.14.4" />  
    <AttributeType name="OrderQty" />  
    <AttributeType name="UnitPriceDiscount" />  
  
    <attribute type="SalesOrderID" />  
    <attribute type="ProductID" />  
    <attribute type="UnitPrice" />  
    <attribute type="OrderQty" />  
    <attribute type="UnitPriceDiscount" />  
</ElementType>  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="OrderDate" />  
  
    <attribute type="CustomerID" />  
    <attribute type="SalesOrderID" />  
    <attribute type="OrderDate" />  
    <element type="OD" >  
             <sql:relationship   
                   key-relation="Sales.SalesOrderHeader"  
                   key="SalesOrderID"  
                   foreign-key="SalesOrderID"  
                   foreign-relation="Sales.SalesOrderDetail" />  
    </element>  
</ElementType>  
</Schema>  
```  
  
### <a name="c-inserting-a-record-by-using-the-parent-child-relationship-and-inverse-annotation-specified-in-the-xsd-schema"></a>C. Einfügen eines Datensatzes durch Verwenden der im XSD-Schema angegebenen Über-/Unterordnungsbeziehung und der inverse-Anmerkung  
 Dieses Beispiel veranschaulicht, wie die Update Gram Logik die über-/Unterordnungsbeziehung verwendet, die in der XSD für die Verarbeitung von Updates und die Verwendung der **umgekehrten** Anmerkung angegeben wird. Weitere Informationen zur **umgekehrten** Anmerkung finden Sie unter [angeben des SQL: inverse-Attributs für SQL: Relationship &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).  
  
 In diesem Beispiel wird davon ausgegangen, dass sich die folgenden Tabellen in der **tempdb** -Datenbank befinden:  
  
-   `Cust (CustomerID, CompanyName)`, wobei `CustomerID` der Primärschlüssel ist  
  
-   `Ord (OrderID, CustomerID)`, wobei `CustomerID` ein Fremdschlüssel ist, der auf den `CustomerID` Primärschlüssel in der `Cust`-Tabelle verweist.  
  
 Das Updategram verwendet das folgende XSD-Schema, um Datensätze in die Cust und Ord-Tabellen einzufügen:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
       <sql:relationship name="OrdCust" inverse="true"  
                  parent="Ord"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Cust"/>  
  </xsd:appinfo>  
</xsd:annotation>  
  
<xsd:element name="Order" sql:relation="Ord">  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element ref="Customer" sql:relationship="OrdCust"/>  
    </xsd:sequence>  
    <xsd:attribute name="OrderID"   type="xsd:int"/>  
    <xsd:attribute name="CustomerID" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
<xsd:element name="Customer" sql:relation="Cust">  
  <xsd:complexType>  
     <xsd:attribute name="CustomerID"  type="xsd:string"/>  
    <xsd:attribute name="CompanyName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
</xsd:schema>  
```  
  
 Das XSD-Schema in diesem Beispiel verfügt über die **\<Customer>** **\<Order>** Elemente und und gibt eine über-/Unterordnungsbeziehung zwischen den beiden Elementen an. Sie identifiziert **\<Order>** als übergeordnetes Element und **\<Customer>** als untergeordnetes Element.  
  
 Die Verarbeitungslogik des Updategrams bestimmt mit den Informationen über die Über-/Unterordnungsbeziehung die Reihenfolge, in der die Datensätze in die Tabellen eingefügt werden. In diesem Beispiel versucht die Update Gram Logik zuerst, einen Datensatz in die Ord-Tabelle einzufügen (da **\<Order>** das übergeordnete Element ist), und versucht dann, einen Datensatz in die Cust-Tabelle einzufügen (da **\<Customer>** das untergeordnete Element ist). Aufgrund der Primärschlüssel-Fremdschlüssel-Informationen, die im Datenbanktabellenschema enthalten sind, verursacht dieser Einfügevorgang jedoch eine Fremdschlüsselverletzung in der Datenbank und der Vorgang schlägt fehl.  
  
 Um die Update Gram Logik anzuweisen, die über-/Unterordnungsbeziehung während des Aktualisierungs Vorgangs umzukehren, wird die **umgekehrte** Anmerkung für das- **\<relationship>** Element angegeben. Als Folge werden die Datensätze zuerst in die Cust-Tabelle und anschließend in die Ord-Tabelle eingefügt, und der Vorgang wird erfolgreich ausgeführt.  
  
 Das folgende Updategram fügt mit dem angegebenen XSD-Schema einen Auftrag (OrderID=2) in die Ord-Tabelle ein und einen Kunden (CustomerID='AAAAA') in die Cust-Tabelle.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before/>  
    <updg:after>  
      <Order OrderID="2" CustomerID="AAAAA" >  
        <Customer CustomerID="AAAAA" CompanyName="AAAAA Company" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Erstellen Sie diese Tabellen in der **tempdb** -Datenbank:  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust(CustomerID varchar(5) primary key,   
                      CompanyName varchar(20))  
    GO  
    CREATE TABLE Ord (OrderID int primary key,   
                      CustomerID varchar(5) references Cust(CustomerID))  
    GO  
    ```  
  
2.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen SampleUpdateSchema.xml.  
  
3.  Kopieren Sie die oben stehende Updategramvorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen SampleUpdategram.xml im gleichen Verzeichnis, in dem Sie SampleUpdateSchema.xml gespeichert haben.  
  
     Der für das Zuordnungschema (SampleUpdateSchema.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
4.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitsüberlegungen zu Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
