---
title: Verwenden von XSD-Schemas mit Anmerkungen in Abfragen (SQLXML)
description: Erfahren Sie, wie Sie XPath-Abfragen für ein XSD-Schema mit Anmerkungen in SQLXML 4,0 angeben, um Daten aus der Datenbank abzurufen.
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
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 030c1d04575c412c2cae9c69d0798e7d40e89450
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97467101"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>Verwenden von XSD-Schemas mit Anmerkungen in Abfragen (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Sie können Abfragen auf ein Schema mit Anmerkungen angeben, um Daten von der Datenbank abzurufen, indem Sie Xpath-Abfragen in einer Vorlage auf ein XSD-Schema festlegen.  
  
 Mit dem- **\<sql:xpath-query>** Element können Sie eine XPath-Abfrage für die XML-Sicht angeben, die durch das Schema mit Anmerkungen definiert wird. Das mit Anmerkungen versehene Schema, für das die XPath-Abfrage ausgeführt werden soll, wird mit dem **Mapping-Schema-** Attribut des- **\<sql:xpath-query>** Elements identifiziert.  
  
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
  
 Sie können dann das SQLXML 4.0-Testskript (Sqlxml4test.vbs) erstellen und es dazu verwenden, die Abfrage als Teil der Vorlagedatei auszuführen. Weitere Informationen finden Sie unter [mit Anmerkungen versehene XDR-Schemas &#40;in SQLXML 4,0&#41;veraltet ](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="using-inline-mapping-schemas"></a>Verwenden von Inlinezuordnungsschemas  
 Ein Schema mit Anmerkungen kann direkt in eine Vorlage eingefügt werden, und dann kann eine Xpath-Abfrage in der Vorlage auf das Inlineschema angegeben werden. Die Vorlage kann auch ein Updategram sein.  
  
 Eine Vorlage kann mehrere Inlineschemas einschließen. Wenn Sie ein Inline Schema verwenden möchten, das in einer Vorlage enthalten ist, geben Sie das **ID** -Attribut mit einem eindeutigen Wert für das **\<xsd:schema>** -Element an, und verwenden Sie dann **#idValue** , um auf das Inline Schema zu verweisen. Das **ID** -Attribut ist identisch mit der **SQL: ID** ({urn: Schemas-Microsoft-com: XML-SQL}-ID), die in XDR-Schemas verwendet wird.  
  
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
  
 Die Vorlage gibt auch zwei XPath-Abfragen an. Jedes der **\<xpath-query>** Elemente identifiziert das Zuordnungsschema eindeutig, indem das **Mapping-Schema-** Attribut angegeben wird.  
  
 Wenn Sie ein Inline Schema in der Vorlage angeben, muss die **SQL: is-Mapping-Schema-** Anmerkung auch für das-Element angegeben werden **\<xsd:schema>** . Das **SQL: is-Mapping-Schema** übernimmt einen booleschen Wert (0 = false, 1 = true). Ein Inline Schema mit **SQL: is-Mapping-Schema = "1"** wird als Inline Schema mit Anmerkungen behandelt und nicht im XML-Dokument zurückgegeben.  
  
 Die **SQL: is-Mapping-Schema-** Anmerkung gehört zum Vorlagen Namespace **urn: Schemas-Microsoft-com: XML-SQL**.  
  
 Speichern Sie zum Testen dieses Beispiels die Vorlage (InlineSchemaTemplate.xml) in einem lokalen Verzeichnis und erstellen und verwenden Sie dann das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen. Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Zusätzlich zur Angabe des **Mapping-Schema-** Attributs für das **\<sql:xpath-query>** Element in einer Vorlage (wenn eine XPath-Abfrage vorhanden ist) oder für **\<updg:sync>** ein Element in einem Update Gram können Sie folgende Schritte ausführen:  
  
-   Geben Sie das **Mapping-Schema-** Attribut für das- **\<ROOT>** Element (globale Deklaration) in der Vorlage an. Dieses Zuordnungsschema wird dann zum Standardschema, das von allen XPath-und Update Gram-Knoten verwendet wird, die keine explizite **Mapping-Schema-** Anmerkung aufweisen.  
  
-   Geben Sie das **Mapping-Schema** Attribut mithilfe des ADO- **Befehls** Objekts an.  
  
 Das **Mapping-Schema-** Attribut, das für das-Element oder das-Element angegeben wird, **\<xpath-query>** **\<updg:sync>** hat die höchste Rangfolge; das ADO- **Befehls** Objekt hat die niedrigste Priorität.  
  
 Beachten Sie Folgendes: Wenn Sie eine XPath-Abfrage in einer Vorlage angeben und kein Zuordnungsschema angeben, für das die XPath-Abfrage ausgeführt wird, wird die XPath-Abfrage als eine **dbobject** -typabfrage behandelt. Betrachten Sie z. B. die folgende Vorlage:  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 Die Vorlage gibt eine XPath-Abfrage, aber kein Zuordnungsschema an. Daher wird diese Abfrage als eine **dbobject** -typabfrage behandelt, bei der Production. ProductPhoto der Tabellenname und @ProductPhotoID = ' 100 ' ein Prädikat ist, das ein Produktfoto mit dem ID-Wert 100 findet. @LargePhoto die Spalte, aus der der Wert abgerufen werden soll.  
  
  
