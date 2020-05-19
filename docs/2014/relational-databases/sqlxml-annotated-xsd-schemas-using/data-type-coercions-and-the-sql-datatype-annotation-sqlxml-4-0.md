---
title: 'Datentyp Umwandlungen und die SQL: datatype-Anmerkung (SQLXML 4,0) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- type attribute
- sql:datatype
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- xsd:type
- datatype annotation
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XSD schemas [SQLXML], mapping data types
ms.assetid: db192105-e8aa-4392-b812-9d727918c005
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: aa2b5830ab0579fe0429357fea3275d4e14d1c47
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703634"
---
# <a name="data-type-coercions-and-the-sqldatatype-annotation-sqlxml-40"></a>Datentypumwandlungen und die sql:datatype-Anmerkung (SQLXML 4.0)
  In einem XSD-Schema gibt das `xsd:type`-Attribut den XSD-Datentyp eines Elements oder Attributs an. Wenn Daten anhand eines XSD-Schemas aus der Datenbank extrahiert werden, wird der angegebene Datentyp zur Formatierung der Daten verwendet.  
  
 Darüber hinaus können Sie neben dem XSD-Typ in einem Schema auch über die `sql:datatype`-Anmerkung einen Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp angeben. Die Attribute `xsd:type` und `sql:datatype` steuern die Zuordnung zwischen XSD-Datentypen und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen.  
  
## <a name="xsdtype-attribute"></a>xsd:type-Attribut  
 Sie können das `xsd:type`-Attribut verwenden, um den XML-Datentyp eines Attributs oder Elements anzugeben, das einer Spalte zugeordnet ist. `xsd:type` wirkt sich auf das vom Server zurückgegebene Dokument sowie auf die ausgeführte XPath-Abfrage aus. Wenn eine XPath-Abfrage für ein Zuordnungsschema ausgeführt wird, das `xsd:type` enthält, verwendet XPath den angegebenen Datentyp beim Verarbeiten der Abfrage. Weitere Informationen zur Verwendung von XPath `xsd:type` finden Sie unter [Mapping von XSD-Datentypen zu XPath-Datentypen &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md).  
  
 In einem zurückgegebenen Dokument werden alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen in Zeichenfolgendarstellungen konvertiert. Einige Datentypen erfordern zusätzliche Konvertierungen. In der folgenden Tabelle sind die Konvertierungen für verschiedene `xsd:type`-Werte aufgelistet.  
  
|XSD-Datentyp|SQL Server-Konvertierung|  
|-------------------|---------------------------|  
|Boolean|CONVERT(bit, COLUMN)|  
|Datum|LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)|  
|Decimal|CONVERT(money, COLUMN)|  
|id/idref/idrefs|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|nmtoken/nmtokens|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|Time|SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)|  
|Alle anderen|Keine zusätzliche Konvertierung|  
  
> [!NOTE]  
>  Einige von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurückgegebene Werte sind möglicherweise nicht mit den über `xsd:type` angegebenen XML-Datentypen kompatibel. Das liegt entweder daran, dass keine Konvertierung möglich ist (zum Beispiel die Konvertierung von XYZ in einen `decimal`-Datentyp) oder daran, dass der Wert den Bereich dieses Datentyps überschreitet (zum Beispiel bei der Konvertierung von -100000 in einen `UnsignedShort`-XSD-Typ). Inkompatible Typkonvertierungen führen möglicherweise zu ungültigen XML-Dokumenten oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlern.  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a>Zuordnen von SQL Server-Datentypen zu XSD-Datentypen  
 In der folgenden Tabelle wird eine offensichtliche Zuordnung zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen und XSD-Datentypen gezeigt. Wenn Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ kennen, können Sie dieser Tabelle den entsprechenden XSD-Typ für das XSD-Schema entnehmen.  
  
|SQL Server-Datentyp|XSD-Datentyp|  
|--------------------------|-------------------|  
|`bigint`|`long`|  
|`binary`|`base64Binary`|  
|`bit`|`boolean`|  
|`char`|`string`|  
|`datetime`|`dateTime`|  
|`decimal`|`decimal`|  
|`float`|`double`|  
|`image`|`base64Binary`|  
|`int`|`int`|  
|`money`|`decimal`|  
|`nchar`|`string`|  
|`ntext`|`string`|  
|`nvarchar`|`string`|  
|`numeric`|`decimal`|  
|`real`|`float`|  
|`smalldatetime`|`dateTime`|  
|`smallint`|`short`|  
|`smallmoney`|`decimal`|  
|`sql_variant`|`string`|  
|`sysname`|`string`|  
|`text`|`string`|  
|`timestamp`|`dateTime`|  
|`tinyint`|`unsignedByte`|  
|`varbinary`|`base64Binary`|  
|`varchar`|`string`|  
|`uniqueidentifier`|`string`|  
  
## <a name="sqldatatype-annotation"></a>sql:datatype-Anmerkung  
 Die `sql:datatype`-Anmerkung wird verwendet, um den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp anzugeben. Diese Anmerkung ist obligatorisch, wenn:  
  
-   Sie sind Massen laden in eine `dateTime` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Spalte aus einem XSD- `dateTime` ,- `date` oder- `time` Typ. In diesem Fall müssen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Spaltendatentyp mit `sql:datatype="dateTime"` angeben. Diese Regel gilt auch für Updategrams.  
  
-   Sie sind Massen laden in eine Spalte vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `uniqueidentifier` Typ, und der XSD-Wert ist eine GUID mit geschweiften Klammern ({und}). Wenn Sie `sql:datatype="uniqueidentifier"` angeben, werden die Klammern vor dem Einfügen in die Spalte aus dem Wert entfernt. Wird `sql:datatype` nicht angegeben, wird der Wert einschließlich Klammern gesendet, und der Einfüge- oder Updatevorgang erzeugt einen Fehler.  
  
-   Der XML-Datentyp `base64Binary` ist verschiedenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen (`binary`, `image` oder `varbinary`) zugeordnet. Um den XML-Datentyp `base64Binary`einem bestimmten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp zuzuordnen, verwenden Sie die `sql:datatype`-Anmerkung. Diese Anmerkung gibt den expliziten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp der Spalte an, der das Attribut zugeordnet ist. Dies ist nützlich, wenn Daten in der Datenbank gespeichert werden. Durch Angeben der `sql:datatype`-Anmerkung können Sie den expliziten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp identifizieren.  
  
 Es wird im Allgemeinen empfohlen, `sql:datatype` im Schema anzugeben.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-xsdtype"></a>A. Angeben von "xsd:type"  
 Dieses Beispiel zeigt, wie sich ein über das `date`-Attribut im Schema angegebener `xsd:type` XSD-Typ auf das daraus resultierende XML-Dokument auswirkt. Das Schema stellt eine XML-Ansicht der Tabelle Sales.SalesOrderHeader in der AdventureWorks-Datenbank bereit.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader">  
     <xsd:complexType>  
       <xsd:attribute name="SalesOrderID" type="xsd:string" />   
       <xsd:attribute name="CustomerID"   type="xsd:string" />   
       <xsd:attribute name="OrderDate"    type="xsd:date" />   
       <xsd:attribute name="DueDate"  />   
       <xsd:attribute name="ShipDate"  type="xsd:time" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 In diesem XSD-Schema gibt es drei Attribute, die einen Datumswert von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zurückgeben. Wenn das Schema:  
  
-   Gibt `xsd:type=date` für das **OrderDate** -Attribut an, dass der Datums Teil des Werts, der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für das **OrderDate** -Attribut zurückgegeben wird, angezeigt wird.  
  
-   Gibt für `xsd:type=time` das **ShipDate** -Attribut an, dass der Uhrzeit Teil des Werts, der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für das **ShipDate** -Attribut zurückgegeben wird, angezeigt wird.  
  
-   Gibt `xsd:type` für das **DueDate** -Attribut nicht an, dass derselbe Wert, der von zurückgegeben wird, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angezeigt wird.  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen xsdType.xml.  
  
2.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen xsdTypeT.xml im gleichen Verzeichnis wie sdType.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="xsdType.xml">  
        /Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (xsdType.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert ist. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\xsdType.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden wird ein Teil des Resultsets aufgeführt:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43659"   
         CustomerID="676"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
  <Order SalesOrderID="43660"   
         CustomerID="117"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
 ...  
</ROOT>  
```  
  
 Dies ist das entsprechende XDR-Schema:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader">  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="CustomerID"  />  
    <AttributeType name="OrderDate" dt:type="date" />  
    <AttributeType name="DueDate" />  
    <AttributeType name="ShipDate" dt:type="time" />  
  
    <attribute type="SalesOrderID" sql:field="OrderID" />  
    <attribute type="CustomerID" sql:field="CustomerID" />  
    <attribute type="OrderDate" sql:field="OrderDate" />  
    <attribute type="DueDate" sql:field="DueDate" />  
    <attribute type="ShipDate" sql:field="ShipDate" />  
</ElementType>  
</Schema>  
```  
  
### <a name="b-specifying-sql-data-type-using-sqldatatype"></a>B. Angeben des SQL-Datentyps mit "sql:datatype"  
 Ein funktionierendes Beispiel finden Sie unter Beispiel G in [XML Bulk Load examples &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md). In diesem Beispiel wird ein GUID-Wert, der "{" und "}" enthält, massengeladen. Das Schema in diesem Beispiel gibt `sql:datatype` an, um den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp als `uniqueidentifier` zu identifizieren. Dieses Beispiel veranschaulicht, wann `sql:datatype` im Schema angegeben werden muss.  
  
  
