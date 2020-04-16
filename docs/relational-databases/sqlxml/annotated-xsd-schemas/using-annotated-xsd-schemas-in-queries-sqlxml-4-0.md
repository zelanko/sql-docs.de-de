---
title: Verwenden von annotierten XSD-Schemas in Abfragen (SQLXML)
description: Erfahren Sie, wie Sie XPath-Abfragen für ein mit Anmerkungen bezeichnetes XSD-Schema in SQLXML 4.0 angeben, um Daten aus der Datenbank abzurufen.
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML]
- inline schemas [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- queries [SQLXML], annotated XSD schemas
- retrieving data
- mapping schema [SQLXML], queries
- multiple inline schemas
- annotated XSD schemas, queries
- XSD schemas [SQLXML], queries
- templates [SQLXML], annotated XSD schemas in queries
ms.assetid: 927a30a2-eae8-420d-851d-551c5f884f3c
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e9ecd9d65d0f70f7c25328c15bb886ca52122de2
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388683"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>Verwenden von XSD-Schemas mit Anmerkungen in Abfragen (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Sie können Abfragen auf ein Schema mit Anmerkungen angeben, um Daten von der Datenbank abzurufen, indem Sie Xpath-Abfragen in einer Vorlage auf ein XSD-Schema festlegen.  
  
 Mit dem ** \<sql:xpath-query->-Element** können Sie eine XPath-Abfrage für die XML-Ansicht angeben, die durch das mit Anmerkungen bezeichnete Schema definiert ist. Das mit Anmerkungen versehene Schema, für das die XPath-Abfrage ausgeführt werden soll, wird mithilfe des **Attributs mapping-schema** des ** \<sql:xpath-query-elements>** identifiziert.  
  
 Vorlagen sind gültige XML-Dokumente, die eine oder mehrere Abfragen enthalten. Die FOR XML- und XPath-Abfragen geben ein Dokumentfragment zurück. Vorlagen fungieren als Container für die Dokumentfragmente und bieten so eine Möglichkeit, ein einzelnes Element der obersten Ebene anzugeben.  
  
 In den Beispielen in diesem Thema werden Vorlagen dazu verwendet, eine XPath-Abfrage für ein Schema mit Anmerkungen auszuführen, um Daten von der Datenbank abzurufen.  
  
 Betrachten Sie z. B. dieses annotierte Schema:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID" type="xsd:string" />   
       <xsd:attribute name="FirstName" type="xsd:string" />   
       <xsd:attribute name="LastName"  type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Zur Veranschaulichung wird dieses XSD-Schema in einer Datei mit dem Namen Schema2.xml gespeichert. Sie können dann eine Xpath-Abfrage auf das in der folgenden Vorlagendatei angegebene Schema mit Anmerkungen (Schema2.xml) ausführen:  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql"  
     >  
          Person.Contact[@ContactID="1"]  
</sql:xpath-query>  
```  
  
 Sie können dann das SQLXML 4.0-Testskript (Sqlxml4test.vbs) erstellen und es dazu verwenden, die Abfrage als Teil der Vorlagedatei auszuführen. Weitere Informationen finden Sie unter [Annotierte XDR-Schemas &#40;veraltet in SQLXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="using-inline-mapping-schemas"></a>Verwenden von Inlinezuordnungsschemas  
 Ein Schema mit Anmerkungen kann direkt in eine Vorlage eingefügt werden, und dann kann eine Xpath-Abfrage in der Vorlage auf das Inlineschema angegeben werden. Die Vorlage kann auch ein Updategram sein.  
  
 Eine Vorlage kann mehrere Inlineschemas einschließen. Um ein Inlineschema zu verwenden, das in einer Vorlage enthalten ist, geben Sie das **id-Attribut** mit einem eindeutigen Wert für das ** \<xsd:schema->-Element** an, und verwenden Sie dann **#idvalue,** um auf das Inlineschema zu verweisen. Das **id-Attribut** ist im Verhalten identisch mit dem sql:id('urn:schemas-microsoft-com:xml-sql'id),' verwendet in XDR-Schemas. **sql:id**  
  
 Die folgende Vorlage gibt beispielsweise zwei Inlineschemas mit Anmerkungen an:  
  
```  
<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema1' sql:is-mapping-schema='1'>  
  <xsd:element name='Employees' ms:relation='HumanResources.Employee'>  
    <xsd:complexType>  
      <xsd:attribute name='LoginID'   
                     type='xsd:string'/>  
      <xsd:attribute name='Title'   
                     type='xsd:string'/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema2' sql:is-mapping-schema='1'>  
  <xsd:element name='Contacts' ms:relation='Person.Contact'>  
    <xsd:complexType>  
  
      <xsd:attribute name='ContactID'   
                     type='xsd:string' />  
      <xsd:attribute name='FirstName'   
                     type='xsd:string' />  
      <xsd:attribute name='LastName'   
                     type='xsd:string' />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema1'>  
    /Employees[@LoginID='adventure-works\guy1']  
</sql:xpath-query>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema2'>  
    /Contacts[@ContactID='1']  
</sql:xpath-query>  
</ROOT>  
```  
  
 Die Vorlage gibt auch zwei XPath-Abfragen an. Jedes der ** \<xpath-query->-Elemente** identifiziert das Zuordnungsschema eindeutig, indem das **Attribut -Schema-Attribut** angegeben wird.  
  
 Wenn Sie ein Inlineschema in der Vorlage angeben, muss die **sql:is-mapping-schema-Anmerkung** auch für das ** \<xsd:schema>-Element** angegeben werden. Das **sql:is-mapping-schema** nimmt einen booleschen Wert an (0=false, 1=true). Ein Inlineschema mit **sql:is-mapping-schema="1"** wird als inline annotiertes Schema behandelt und nicht im XML-Dokument zurückgegeben.  
  
 Die **sql:is-mapping-schema-Anmerkung** gehört zur Vorlage namespace **urn:schemas-microsoft-com:xml-sql**.  
  
 Speichern Sie zum Testen dieses Beispiels die Vorlage (InlineSchemaTemplate.xml) in einem lokalen Verzeichnis und erstellen und verwenden Sie dann das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen. Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Zusätzlich zur Angabe des **Mapping-schema-Attributs** für das ** \<sql:xpath-query->-Element** in einer Vorlage (wenn eine XPath-Abfrage vorhanden ist) oder auf ** \<updg:sync>-Element** in einem Updategram können Sie Folgendes tun:  
  
-   Geben Sie das **Mapping-Schema-Attribut** für das ** \<ROOT->-Element** (globale Deklaration) in der Vorlage an. Dieses Zuordnungsschema wird dann zum Standardschema, das von allen XPath- und Updategram-Knoten ohne explizite **Zuordnungsschemaanmerkung** verwendet wird.  
  
-   Geben Sie das **Zuordnungsschemaattribut** mithilfe des ADO **Command-Objekts** an.  
  
 Das **Mapping-Schema-Attribut,** das auf der ** \<xpath-query>** oder ** \<updg:sync->-Element** angegeben wird, hat die höchste Priorität. Das ADO **Command-Objekt** hat die niedrigste Priorität.  
  
 Wenn Sie eine XPath-Abfrage in einer Vorlage angeben und kein Zuordnungsschema angeben, für das die XPath-Abfrage ausgeführt wird, wird die XPath-Abfrage als **dbobject-Typabfrage** behandelt. Betrachten Sie z. B. die folgende Vorlage:  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 Die Vorlage gibt eine XPath-Abfrage, aber kein Zuordnungsschema an. Daher wird diese Abfrage als **dbobject-Typabfrage** behandelt, in der @ProductPhotoIDProduction.ProductPhoto der Tabellenname und ='100' ein Prädikat ist, das ein Produktfoto mit dem ID-Wert 100 findet. @LargePhotoist die Spalte, aus der der Wert abgerufen werden soll.  
  
  
