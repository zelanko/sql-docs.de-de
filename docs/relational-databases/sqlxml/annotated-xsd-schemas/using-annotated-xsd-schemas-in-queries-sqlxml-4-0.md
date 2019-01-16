---
title: Mithilfe von Schemas mit Anmerkungen in XSD in Abfragen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7d6fd994c25acae6a27d5c66c18f1c2a7d7b3a77
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54256855"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>Verwenden von XSD-Schemas mit Anmerkungen in Abfragen (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Sie können Abfragen auf ein Schema mit Anmerkungen angeben, um Daten von der Datenbank abzurufen, indem Sie Xpath-Abfragen in einer Vorlage auf ein XSD-Schema festlegen.  
  
 Die  **\<XPath-Abfrage >** -Element können Sie eine XPath-Abfrage für die XML-Sicht angeben, die durch das Schema mit Anmerkungen definiert wird. Das Schema mit Anmerkungen für die die XPath-Abfrage ausgeführt werden, wird mithilfe von identifiziert die **Zuordnungsschema** Attribut der  **\<XPath-Abfrage >** Element.  
  
 Vorlagen sind gültige XML-Dokumente, die eine oder mehrere Abfragen enthalten. Die FOR XML- und XPath-Abfragen geben ein Dokumentfragment zurück. Vorlagen fungieren als Container für die Dokumentfragmente und bieten so eine Möglichkeit, ein einzelnes Element der obersten Ebene anzugeben.  
  
 In den Beispielen in diesem Thema werden Vorlagen dazu verwendet, eine XPath-Abfrage für ein Schema mit Anmerkungen auszuführen, um Daten von der Datenbank abzurufen.  
  
 Betrachten Sie beispielsweise die diesem Schema mit Anmerkungen:  
  
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
  
 Sie können dann das SQLXML 4.0-Testskript (Sqlxml4test.vbs) erstellen und es dazu verwenden, die Abfrage als Teil der Vorlagedatei auszuführen. Weitere Informationen finden Sie unter [XDR-Schemas mit Anmerkungen versehen &#40;in SQLXML 4.0 veraltet&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="using-inline-mapping-schemas"></a>Verwenden von Inlinezuordnungsschemas  
 Ein Schema mit Anmerkungen kann direkt in eine Vorlage eingefügt werden, und dann kann eine Xpath-Abfrage in der Vorlage auf das Inlineschema angegeben werden. Die Vorlage kann auch ein Updategram sein.  
  
 Eine Vorlage kann mehrere Inlineschemas einschließen. Um ein Inlineschema verwenden, die in einer Vorlage enthalten ist, geben die **Id** -Attribut mit einem eindeutigen Wert für die  **\<xsd: Schema >** -Element, und klicken Sie dann verwenden **#idvalue**auf das Inlineschema verweisen. Die **Id** -Attribut ist, verhält sich genauso die **SQL: ID** ({Urn: Schemas-Microsoft-com: XML-Sql} Id), die in XDR-Schemas verwendet.  
  
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
  
 Die Vorlage gibt auch zwei XPath-Abfragen an. Jede der  **\<Xpath-Abfrage >** -Elemente identifiziert eindeutig das Zuordnungsschema durch Angabe der **Zuordnungsschema** Attribut.  
  
 Wenn Sie ein Inlineschema in der Vorlage angeben der **Sql: is-Mapping-Schema** Anmerkung muss auch angegeben werden, auf die  **\<xsd: Schema >** Element. Die **Sql: is-Mapping-Schema** akzeptiert einen booleschen Wert (0 = False, 1 = True). Ein Inlineschema mit **Sql: is-Mapping-Schema = "1"** wird als Inlineschema mit Anmerkungen behandelt und in das XML-Dokument nicht zurückgegeben wird.  
  
 Die **Sql: is-Mapping-Schema** -Anmerkung gehört zum vorlagennamespace **Urn: Schemas-Microsoft-com: XML-Sql**.  
  
 Speichern Sie zum Testen dieses Beispiels die Vorlage (InlineSchemaTemplate.xml) in einem lokalen Verzeichnis und erstellen und verwenden Sie dann das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen. Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Zusätzlich zur Angabe der **Zuordnungsschema** -Attribut für die  **\<XPath-Abfrage >** Element in einer Vorlage (Wenn eine xpath_Abfrage vorhanden ist) oder auf  **\< updg: Sync >** Element in einem Updategram, können Sie Folgendes tun:  
  
-   Geben Sie die **Zuordnungsschema** -Attribut für die  **\<Stamm >** -Element (globale Deklaration) in der Vorlage. Dieses Zuordnungsschema wird das Standardschema an, die von allen XPath- und Updategram-Knoten verwendet werden, die keine explizite **Zuordnungsschema** Anmerkung.  
  
-   Geben Sie die **Zuordnungsschema** Attribut mit dem ADO **Befehl** Objekt.  
  
 Die **Zuordnungsschema** auf angegebene Attribut der  **\<Xpath-Abfrage >** oder  **\<updg: Sync >** Element hat die besten Rangfolge; Das ADO **Befehl** Objekt hat die niedrigste Priorität.  
  
 Beachten Sie, dass wenn Sie eine XPath-Abfrage in eine Vorlage angeben, und geben Sie ein Zuordnungsschema für die Ausführung die XPath-Abfrage nicht, die XPath-Abfrage so, als behandelt wird eine **Dbobject** Abfrage. Betrachten Sie z. B. die folgende Vorlage:  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 Die Vorlage gibt eine XPath-Abfrage, aber kein Zuordnungsschema an. Aus diesem Grund wird diese Abfrage als behandelt eine **Dbobject** Typabfrage, in dem Production.ProductPhoto der Tabellenname ist, und @ProductPhotoID='100 ' ist ein Prädikat, das ein produktphoto mit dem ID-Wert von 100 sucht. @LargePhoto ist die Spalte aus der den Wert abgerufen werden soll.  
  
  
