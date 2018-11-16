---
title: "Anfordern von URL-verweisen auf BLOB-Daten mithilfe von Sql: encode ' (SQLXML 4.0) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a2893ff05a82ae647fa3194c2d1c7427827939c5
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51661739"
---
# <a name="requesting-url-references-to-blob-data-using-sqlencode-sqlxml-40"></a>Anfordern von URL-Verweisen auf BLOB-Daten mit 'sql:encode' (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Wenn in einem XSD-Schema mit Anmerkungen ein Attribut (oder Element) einer BLOB-Spalte in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugeordnet ist, werden die Daten im codierten Base-64-Format innerhalb von XML zurückgegeben.  
  
 Sollten Sie einen Verweis auf die Daten (URI) zurückgegeben werden später verwendet werden kann, die BLOB-Daten in einem binären Format abzurufen, geben Sie die **Sql: Codieren** Anmerkung. Sie können angeben, **Sql: Codieren** für ein Attribut oder Element des einfachen Typs.  
  
 Geben Sie die **Sql: Codieren** Anmerkung, um anzugeben, dass eine URL für das Feld nicht den Wert des Felds zurückgegeben werden sollen. **SQL: Codieren** hängt von den primären Schlüssel, um eine Singleton-Auswahl in der URL zu generieren. Der primäre Schlüssel kann angegeben werden, mithilfe der **SQL: Key-Felder** Anmerkung.  
  
 Die **Sql: Codieren** Anmerkung zugewiesen werden kann, "Url" oder den Wert "Default". Mit dem Wert "default" werden die Daten im codierten Base-64-Format zurückgegeben.  
  
 Die **Sql: Codieren** Anmerkung kann nicht verwendet werden, mit **SQL: use-Cdata** oder für die ID, IDREF, IDREFS, NMTOKEN oder NMTOKENS Attributtypen. Es kann auch nicht verwendet werden mit XSD **festen** Attribut.  
  
> [!NOTE]  
>  BLOB-Spalten können nicht als Teil eines Schlüssels oder Fremdschlüssels verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen für die Ausführung von SQLXML-Beispielen](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlencode-to-obtain-a-url-reference-to-blob-data"></a>A. Angeben von sql:encode zum Abrufen eines URL-Verweises auf BLOB-Daten  
 In diesem Beispiel gibt das Zuordnungsschema **Sql: Codieren** auf die **LargePhoto** abzurufenden URI-Verweis auf ein bestimmtes Produktfoto (statt der binären Daten in Base-64 - Attributs codierte Format).  
  
```  
<xsd:schema xmlns:xsd="https://www.w3.org/2001/XMLSchema"  
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
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine Beispiel-XPath-Abfrage anhand des Schemas  
  
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
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Dies ist das Ergebnis:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <ProductPhoto ProductPhotoID="100"  
                 LargePhoto="dbobject/Production.ProductPhoto[@ProductPhotoID="100"]/@LargePhoto" />   
</ROOT>  
```  
  
  
