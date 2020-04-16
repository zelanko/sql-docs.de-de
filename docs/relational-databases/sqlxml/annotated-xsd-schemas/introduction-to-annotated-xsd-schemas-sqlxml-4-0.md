---
title: Einführung in annotierte XSD-Schemas (SQLXML)
description: Erfahren Sie mehr über das Erstellen von XML-Ansichten relationaler Daten mithilfe der XML-Schemadefinitionssprache (XSD) (SQLXML 4.0).
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- mapping schema [SQLXML], about mapping schema
- views [SQLXML]
- valid XSD schemas [SQLXML]
- annotations [SQLXML]
- XSD schemas [SQLXML], creating XML views
- annotated XSD schemas, creating XML views
- minimum XSD schema
- annotated XSD schemas, examples
- XML views [SQLXML]
ms.assetid: 15282db1-65c4-43be-bdb7-e9ef49cb33a2
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c165ca271c3230399d54363f22d2b220e5427830
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388656"
---
# <a name="introduction-to-annotated-xsd-schemas-sqlxml-40"></a>Einführung in XSD-Schemas mit Anmerkungen (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Sie können mit der XML-Schemadefinitionssprache (XSD) XML-Sichten von relationalen Daten erstellen. Diese Sichten können dann mit XPath (XML Path)-Abfragen abgefragt werden. Dieser Vorgang gleicht prinzipiell dem Erstellen von Sichten mit CREATE VIEW-Anweisungen und dem Definieren von SQL-Abfragen für diese Sichten.  
  
 Ein XML-Schema beschreibt die Struktur eines XML-Dokuments und beschreibt auch die verschiedenen Einschränkungen für die Daten im Dokument. Wenn XQuery-Abfragen mit dem XSD-Schema angegeben werden, wird die Struktur des resultierenden XML-Dokuments durch das Schema bestimmt, mit dem die Abfrage ausgeführt wird.  
  
 In einem XSD-Schema umschließt das ** \<xsd:schema>-Element** das gesamte Schema. Alle Elementdeklarationen müssen im ** \<xsd:schema>-Element** enthalten sein. Sie können Attribute beschreiben, die den Namespace definieren, in dem sich das Schema befindet, und die Namespaces, die im Schema als Eigenschaften des ** \<xsd:schema>** Elements verwendet werden.  
  
 Ein gültiges XSD-Schema muss das ** \<xsd:schema>-Element** enthalten, das wie folgt definiert ist:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<!-- additional schema definitions here -->  
</xsd:schema>  
```  
  
 Das ** \<xsd:schema>-Element** wird von der http://www.w3.org/2001/XMLSchemaXML-Schema-Namespacespezifikation unter abgeleitet.  
  
## <a name="annotations-to-the-xsd-schema"></a>Anmerkungen zum XSD-Schema  
 Sie können ein XSD-Schema mit Anmerkungen angeben, welche die Zuordnung zu einer Datenbank beschreiben, die Datenbank abfragen und die Ergebnisse in Form eines XML-Dokuments zurückgeben. Anmerkungen werden bereitgestellt, um ein XSD-Schema Datenbanktabellen und -spalten zuzuordnen. XPath-Abfragen können für die XML-Sicht, die durch das XSD-Schema erstellt wird, angegeben werden, um die Datenbank abzufragen und die Ergebnisse als XML-Dokument zu erhalten.  
  
> [!NOTE]  
>  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 unterstützt die XSD-Schemasprache die Anmerkungen, die in der XDR-Schemasprache (XML-Data Reduced) mit Anmerkungen in [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] eingeführt wurden. XDR-Anmerkungen sind in SQLXML 4.0 veraltet.  
  
 Im Kontext relationaler Datenbanken ist es nützlich, das beliebige XSD-Schema einem relationalen Datenspeicher zuzuordnen. Dies lässt sich beispielsweise erreichen, indem das XSD-Schema mit Anmerkungen versehen wird. Ein XSD-Schema mit den Anmerkungen wird als *Zuordnungsschema*bezeichnet, das Informationen darüber bereitstellt, wie XML-Daten dem relationalen Speicher zugeordnet werden sollen. Ein Zuordnungsschema ist im Grunde eine XML-Sicht der relationalen Daten. Diese Zuordnungen können verwendet werden, um relationale Daten als XML-Dokument abzurufen.  
  
## <a name="namespace-for-annotations"></a>Namespace für Anmerkungen  
 In einem XSD-Schema werden Anmerkungen mithilfe des Namespace **urn:schemas-microsoft-com:mapping-schema**angegeben. Wie im folgenden Beispiel gezeigt, ist es am einfachsten, den Namespace im ** \<xsd:schema->-Tag** anzugeben.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
...  
</xsd:schema>  
```  
  
 Es kann ein beliebiges Namespacepräfix verwendet werden. In dieser Dokumentation **sql** wird das sql-Präfix verwendet, um den Annotationsnamespace zu bezeichnen und Anmerkungen in diesem Namespace von denen in anderen Namespaces zu unterscheiden.  
  
## <a name="example-of-an-annotated-xsd-schema"></a>Beispiel eines XSD-Schemas mit Anmerkungen  
 Im folgenden Beispiel besteht das XSD-Schema aus einem ** \<Person.Contact**>-Element. Das ** \<Employee>-Element** verfügt über ein **ContactID-Attribut** und ** \<FirstName>** und ** \<LastName>** untergeordneteelemente Elemente:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <xsd:element name="Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     type="xsd:string" />   
        <xsd:element name="LName"  
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Diesem XSD-Schema werden Anmerkungen hinzugefügt, um die darin enthaltenen Elemente und Attribute den entsprechenden Datenbanktabellen und –spalten zuzuordnen.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID"   
                       sql:field="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Im Zuordnungsschema ** \<** wird das Contact>-Element der Tabelle Person.Contact in der AdventureWorks-Beispieldatenbank mithilfe der **sql:relation-Anmerkung** zugeordnet. Die Attribute ConID, FName und LName werden den Spalten ContactID, FirstName und LastName in der Tabelle Person.Contact mithilfe der **sql:field-Anmerkungen** zugeordnet.  
  
 Dieses XSD-Schema mit Anmerkungen stellt die XML-Sicht der relationalen Daten bereit. Diese XML-Sicht kann mit der XPath-Sprache abgefragt werden. Xpath-Abfragen geben als Ergebnis ein XML-Dokument zurück statt eines Rowsets, das von SQL-Abfragen zurückgegeben wird.  
  
> [!NOTE]  
>  Ob im Zuordnungsschema bei relationalen Werten, z. B. Tabellenname und Spaltenname, zwischen Groß-und Kleinschreibung unterschieden wird, hängt davon ab, ob in den Sortiereinstellungen auf dem SQL Server die Groß-/Kleinschreibung beachtet wird. Weitere Informationen finden Sie unter [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="other-resources"></a>Weitere Ressourcen  
 Weitere Informationen zu XSD (XML Schema Definition Language), XPath (XML Path Language) und XSLT (Extensible Stylesheet Language Transformations) finden Sie auf den folgenden Websites:  
  
-   XML-Schema Teil 0: Primer, W3C-Empfehlung (https://www.w3.org/TR/xmlschema-0/)  
  
-   XML-Schema Teil 1: Strukturen, W3C-Empfehlung (https://www.w3.org/TR/xmlschema-1/)  
  
-   XML-Schema Teil 2:Datentypen, W3C-Empfehlung (https://www.w3.org/TR/xmlschema-2/)  
  
-   XML-Pfadsprache (XPath) (https://www.w3.org/TR/xpath)  
  
-   XSL-Transformationen (XSLT) (https://www.w3.org/TR/xslt)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Annotierte Schemasicherheitsüberlegungen &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)   
 [Annotierte XDR-Schemas &#40;in SQLXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)  
  
  
