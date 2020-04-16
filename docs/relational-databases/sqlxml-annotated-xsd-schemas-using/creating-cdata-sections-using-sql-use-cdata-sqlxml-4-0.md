---
title: Erstellen von CDATA-Abschnitten mit sql:use-cdata (SQLXML)
description: Erfahren Sie, wie Sie CDATA-Abschnitte in SQLXML 4.0 mithilfe der sql:use-cdata-Anmerkung erstellen, um Textblöcke zu entkommen, die Markupzeichen enthalten.
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- markup characters [SQLXML]
- special characters [SQLXML]
- use-cdata annotation
- plain text [SQLXML]
- CDATA sections
- escaping blocks of text [SQLXML]
- annotated XSD schemas, CDATA sections
- sql:use-cdata
ms.assetid: 26d2b9dc-f857-44ff-bcd4-aaf64ff809d0
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: aa359c1c1e855c3652d7c6486d3993f588bae46d
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388192"
---
# <a name="creating-cdata-sections-using-sqluse-cdata-sqlxml-40"></a>Erstellen von CDATA-Abschnitten mit sql:use-cdata (SQLXML 4.0)

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In XML werden Textblöcke, die Zeichen enthalten, die andernfalls als Markup erkannt würden, mit CDATA-Abschnitten in Escapezeichen umgewandelt.  
  
 Eine Datenbank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Microsoft kann manchmal Zeichen enthalten, die vom XML-Parser als Markupzeichen behandelt werden. Beispielsweise werden spitze Klammern (< und >), das Symbol mit geringer er- oder gleich-zu-Symbol (<=) und das bildende Und (&) als Markupzeichen behandelt. Sie können diese Sonderzeichen in einem CDATA-Abschnitt jedoch umschließen, um zu verhindern, dass sie als Markupzeichen behandelt werden. Der Text innerhalb des CDATA-Abschnitts wird vom XML-Parser als Nur-Text behandelt.  
  
 Die **sql:use-cdata-Anmerkung** wird verwendet, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzugeben, dass die von zurückgegebenen Daten in einen CDATA-Abschnitt eingeschlossen werden sollen (d. h., sie gibt an, ob der Wert aus einer Spalte, die von **sql:field** angegeben wird, in einen CDATA-Abschnitt eingeschlossen werden soll). Die **sql:use-cdata-Anmerkung** kann nur für Elemente angegeben werden, die einer Datenbankspalte zugeordnet sind.  
  
 Die **sql:use-cdata-Anmerkung** nimmt einen booleschen Wert an (0 = false, 1 = true). Zulässig sind die Werte 0, 1, true und false.  
  
 Diese Anmerkung kann nicht mit **sql:url-encode** oder mit den Attributtypen ID,IDREF, IDREFS, NMTOKEN und NMTOKENS verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen für die Ausführung von SQLXML-Beispielen](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqluse-cdata-on-an-element"></a>A. Angeben von sql:use-cdata für ein Element  
 Im folgenden Schema wird **sql:use-cdata** für die ** \<AddressLine1->** innerhalb des ** \<Address>-Elements** auf 1 (True) festgelegt. Daraufhin werden die Daten in einem CDATA-Abschnitt zurückgegeben.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Address"   
               sql:relation="Person.Address"   
               sql:key-fields="AddressID" >  
   <xsd:complexType>  
        <xsd:sequence>  
          <xsd:element name="AddressID"  type="xsd:string" />  
          <xsd:element name="AddressLine1" type="xsd:string"   
                       sql:use-cdata="1" />  
        </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispielabfrage anhand des Schemas  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen UseCData.xml.  
  
2.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen UseCDataT.xml im gleichen Verzeichnis, in dem Sie UseCData.xml gespeichert haben.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="UseCData.xml">  
            /Address[AddressID < 11]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungschema (UseCData.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\UseCData.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden wird ein Teil des Resultsets aufgeführt:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Address>   
    <AddressID>1</CustomerID>   
    <AddressLine1>   
      <![CDATA[ 1970 Napa Ct.  ]]>   
    </AddressLine1>   
  </Address>  
  <Address>  
    <AddressLine1>   
      <![CDATA[ 9833 Mt. Dias Blv. ]]>   
    </AddressLine1>   
  </Address>  
  ...  
</ROOT>  
```  
  
  
