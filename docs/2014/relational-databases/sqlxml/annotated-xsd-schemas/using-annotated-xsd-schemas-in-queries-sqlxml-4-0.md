---
title: Verwenden von XSD-Schemas mit Anmerkungen in Abfragen (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: c435ff3bacecb101784695fe42b8b2158625e058
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66014467"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>Verwenden von XSD-Schemas mit Anmerkungen in Abfragen (SQLXML 4.0)
  Sie können Abfragen auf ein Schema mit Anmerkungen angeben, um Daten von der Datenbank abzurufen, indem Sie Xpath-Abfragen in einer Vorlage auf ein XSD-Schema festlegen.  
  
 Mit dem ** \<SQL: XPath-Query->-** Element können Sie eine XPath-Abfrage für die XML-Sicht angeben, die durch das Schema mit Anmerkungen definiert wird. Das mit Anmerkungen versehene Schema, für das die XPath-Abfrage ausgeführt werden soll, wird mithilfe `mapping-schema` des-Attributs des ** \<SQL: XPath-Query->** Elements identifiziert.  
  
 Vorlagen sind gültige XML-Dokumente, die eine oder mehrere Abfragen enthalten. Die FOR XML- und XPath-Abfragen geben ein Dokumentfragment zurück. Vorlagen fungieren als Container für die Dokumentfragmente und bieten so eine Möglichkeit, ein einzelnes Element der obersten Ebene anzugeben.  
  
 In den Beispielen in diesem Thema werden Vorlagen dazu verwendet, eine XPath-Abfrage für ein Schema mit Anmerkungen auszuführen, um Daten von der Datenbank abzurufen.  
  
 Beachten Sie z. b. das Schema mit Anmerkungen:  
  
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
  
 Sie können dann das SQLXML 4.0-Testskript (Sqlxml4test.vbs) erstellen und es dazu verwenden, die Abfrage als Teil der Vorlagedatei auszuführen. Weitere Informationen finden Sie unter [mit Anmerkungen versehene XDR-Schemas &#40;in SQLXML 4,0&#41;veraltet ](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="using-inline-mapping-schemas"></a>Verwenden von Inlinezuordnungsschemas  
 Ein Schema mit Anmerkungen kann direkt in eine Vorlage eingefügt werden, und dann kann eine Xpath-Abfrage in der Vorlage auf das Inlineschema angegeben werden. Die Vorlage kann auch ein Updategram sein.  
  
 Eine Vorlage kann mehrere Inlineschemas einschließen. Wenn Sie ein Inline Schema verwenden möchten, das in einer Vorlage enthalten ist, geben Sie das **ID** -Attribut mit einem eindeutigen Wert für das ** \<XSD: Schema->** Element an, und verwenden Sie dann **#idValue** , um auf das Inline Schema zu verweisen. Das **ID** -Attribut ist identisch mit der **SQL: ID** ({urn: Schemas-Microsoft-com: XML-SQL}-ID), die in XDR-Schemas verwendet wird.  
  
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
  
 Die Vorlage gibt auch zwei XPath-Abfragen an. Alle ** \<XPath-Query->** Elemente identifizieren das Zuordnungsschema eindeutig, indem `mapping-schema` Sie das-Attribut angeben.  
  
 Wenn Sie ein Inline Schema in der Vorlage angeben, muss `sql:is-mapping-schema` die-Anmerkung auch für das ** \<XSD: Schema>** -Element angegeben werden. Die `sql:is-mapping-schema`-Anmerkung akzeptiert einen booleschen Wert (0 =false, 1 = true). Ein Inline Schema mit **SQL: is-Mapping-Schema = "1"** wird als Inline Schema mit Anmerkungen behandelt und nicht im XML-Dokument zurückgegeben.  
  
 Die `sql:is-mapping-schema`-Anmerkung gehört zum Vorlagennamespace `urn:schemas-microsoft-com:xml-sql`.  
  
 Speichern Sie zum Testen dieses Beispiels die Vorlage (InlineSchemaTemplate.xml) in einem lokalen Verzeichnis und erstellen und verwenden Sie dann das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen. Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Zusätzlich zum Angeben des `mapping-schema` -Attributs für das ** \<SQL: XPath-Query>-** Element in einer Vorlage (wenn eine XPath-Abfrage vorhanden ist) oder für ** \<das Element updg: Sync>** in einem Update Gram können Sie folgende Schritte ausführen:  
  
-   Geben Sie `mapping-schema` das-Attribut für das ** \<root>** -Element (globale Deklaration) in der Vorlage an. Dieses Zuordnungsschema wird dann zum Standardschema, das von allen Xpath- und Updategram-Knoten verwendet wird, die keine explizite `mapping-schema`-Anmerkung aufweisen.  
  
-   Geben Sie das `mapping schema`-Attribut mithilfe des `Command`-Objekts in ADO an.  
  
 Das `mapping-schema` Attribut, das für das ** \<XPath-Query->** oder ** \<das updg: Sync>** -Element angegeben ist, hat die höchste Rangfolge. das ADO `Command` -Objekt hat die niedrigste Priorität.  
  
 Beachten Sie Folgendes: Wenn Sie eine XPath-Abfrage in einer Vorlage angeben und kein Zuordnungsschema angeben, für das die XPath-Abfrage ausgeführt wird, wird die XPath-Abfrage als eine **dbobject** -typabfrage behandelt. Betrachten Sie z. B. die folgende Vorlage:  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 Die Vorlage gibt eine XPath-Abfrage, aber kein Zuordnungsschema an. Daher wird diese Abfrage als eine **dbobject** -typabfrage behandelt, bei der Production. ProductPhoto der Tabellenname und @ProductPhotoID= ' 100 ' ein Prädikat ist, das ein Produktfoto mit dem ID-Wert 100 findet. @LargePhotodie Spalte, aus der der Wert abgerufen werden soll.  
  
  
