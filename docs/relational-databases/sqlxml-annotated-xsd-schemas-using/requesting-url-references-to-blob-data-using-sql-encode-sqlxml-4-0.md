---
title: 'Erhalten von URL-verweisen auf BLOB-Daten mit SQL: encode (SQLXML)'
description: 'Erfahren Sie, wie Sie einen URL-Verweis auf BLOB-Daten anfordern, indem Sie die SQL: encode-Anmerkung in SQLXML 4,0 angeben.'
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:encode
- encode annotation
- URL references to BLOB data [SQLXML]
- references to BLOB data [SQLXML]
- annotated XSD schemas, URL references to BLOB data
- requesting URL references to BLOB data
- BLOBs, URL references
- Base 64-encoded format
ms.assetid: 2f8cd93b-c636-462b-8291-167197233ee0
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 487ed2bbee997db22739bdeecd7e024b817ace80
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81388118"
---
# <a name="requesting-url-references-to-blob-data-using-sqlencode-sqlxml-40"></a>Anfordern von URL-Verweisen auf BLOB-Daten mit 'sql:encode' (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Wenn in einem XSD-Schema mit Anmerkungen ein Attribut (oder Element) einer BLOB-Spalte in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugeordnet ist, werden die Daten im codierten Base-64-Format innerhalb von XML zurückgegeben.  
  
 Wenn ein Verweis auf die Daten (ein URI) zurückgegeben werden soll, der später zum Abrufen der BLOB-Daten in einem binären Format verwendet werden kann, geben Sie die **SQL: encode** -Anmerkung an. Sie können **SQL: encode** für ein Attribut oder Element des einfachen Typs angeben.  
  
 Geben Sie die **SQL: encode** -Anmerkung an, um anzugeben, dass anstelle des Werts des Felds eine URL zum Feld zurückgegeben werden soll. **SQL: Codieren** hängt vom Primärschlüssel ab, um eine Singleton-Auswahl in der URL zu generieren. Der Primärschlüssel kann mithilfe der **SQL: key-fields-** Anmerkung angegeben werden.  
  
 Der **SQL: encode** -Anmerkung kann der Wert "URL" oder "Default" zugewiesen werden. Mit dem Wert "default" werden die Daten im codierten Base-64-Format zurückgegeben.  
  
 Die **SQL: encode** -Anmerkung kann nicht mit **SQL: use-cdata** oder den Attributtypen ID, IDREF, IDREFS, NMTOKEN oder NMTOKENS verwendet werden. Sie kann auch nicht mit dem XSD-Attribut **Fixed** verwendet werden.  
  
> [!NOTE]  
>  BLOB-Spalten können nicht als Teil eines Schlüssels oder Fremdschlüssels verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlencode-to-obtain-a-url-reference-to-blob-data"></a>A. Angeben von sql:encode zum Abrufen eines URL-Verweises auf BLOB-Daten  
 In diesem Beispiel gibt das Zuordnungsschema **SQL: encode** für das **LargePhoto** -Attribut an, um den URI-Verweis auf ein bestimmtes Produktfoto abzurufen (anstatt die Binärdaten 64 im Base64-codierten Format abzurufen).  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="ProductPhoto" sql:relation="Production.ProductPhoto"   
               sql:key-fields="ProductPhotoID" >  
   <xsd:complexType>  
      <xsd:attribute name="ProductPhotoID"  type="xsd:int"  />  
     <xsd:attribute name="LargePhoto" type="xsd:string" sql:encode="url" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen sqlEncode.xml.  
  
2.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen sqlEncodeT.xml im gleichen Verzeichnis, in dem Sie sqlEncode.xml gespeichert haben.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sqlEncode.xml">  
            /ProductPhoto[@ProductPhotoID=100]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungschema (sqlEncode.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlEncode.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Dies ist das Ergebnis:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <ProductPhoto ProductPhotoID="100"  
                 LargePhoto="dbobject/Production.ProductPhoto[@ProductPhotoID="100"]/@LargePhoto" />   
</ROOT>  
```  
  
  
