---
title: 'Konvertieren von Datentypen mit SQL: datatype (SQLXML)'
description: 'Erfahren Sie, wie Sie das XSD: Type-Attribut und das SQL: DataType-Attribut in SQLXML 4,0 verwenden, um die Zuordnung zwischen XSD-Datentypen und SQL Server-Datentypen zu steuern.'
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0e457aa6c1d1e16e96682f19898e22813254e9ef
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97461801"
---
# <a name="data-type-conversions-and-the-sqldatatype-annotation-sqlxml-40"></a>Datentyp Konvertierungen und die SQL: datatype-Anmerkung (SQLXML 4,0)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  In einem XSD-Schema gibt das **xsd: Type** -Attribut den XSD-Datentyp eines Elements oder Attributs an. Wenn Daten anhand eines XSD-Schemas aus der Datenbank extrahiert werden, wird der angegebene Datentyp zur Formatierung der Daten verwendet.  
  
 Zusätzlich zur Angabe eines XSD-Typs in einem Schema können Sie auch einen Microsoft- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp mit der Anmerkung " **SQL: datatype** " angeben. Das **xsd: Type** -Attribut und das **SQL: datatype** -Attribut steuern die Zuordnung zwischen XSD-Datentypen und- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen.  
  
## <a name="xsdtype-attribute"></a>xsd:type-Attribut  
 Sie können das **xsd: Type** -Attribut verwenden, um den XML-Datentyp eines Attributs oder Elements anzugeben, das einer Spalte zugeordnet ist. Der **xsd: Type** wirkt sich auf das Dokument aus, das vom Server zurückgegeben wird, sowie auf die XPath-Abfrage, die ausgeführt wird. Wenn eine XPath-Abfrage für ein Zuordnungsschema ausgeführt wird, das **xsd: Type** enthält, verwendet XPath beim Verarbeiten der Abfrage den angegebenen Datentyp. Weitere Informationen zur Verwendung von **xsd: Type** in XPath finden [Sie unter Mapping von XSD-Datentypen zu XPath-Datentypen &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md).  
  
 In einem zurückgegebenen Dokument werden alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen in Zeichenfolgendarstellungen konvertiert. Einige Datentypen erfordern zusätzliche Konvertierungen. In der folgenden Tabelle sind die Konvertierungen aufgeführt, die für verschiedene **xsd: Type** -Werte verwendet werden.  
  
|XSD-Datentyp|SQL Server-Konvertierung|  
|-------------------|---------------------------|  
|Boolean|CONVERT(bit, COLUMN)|  
|Date|LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)|  
|Decimal|CONVERT(money, COLUMN)|  
|id/idref/idrefs|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|nmtoken/nmtokens|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|Time|SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)|  
|Alle anderen|Keine zusätzliche Konvertierung|  
  
> [!NOTE]  
>  Einige der Werte, die von zurückgegeben werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sind möglicherweise nicht kompatibel mit den XML-Datentypen, die mit **xsd: Type** angegeben werden, weil die Konvertierung nicht möglich ist (z. b. die Konvertierung von "xyz" in einen **Decimal** 100000  -Datentyp) oder weil der Wert den Bereich dieses Datentyps überschreitet (z Inkompatible Typkonvertierungen führen möglicherweise zu ungültigen XML-Dokumenten oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlern.  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a>Zuordnen von SQL Server-Datentypen zu XSD-Datentypen  
 In der folgenden Tabelle wird eine offensichtliche Zuordnung zwischen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen und XSD-Datentypen gezeigt. Wenn Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ kennen, können Sie dieser Tabelle den entsprechenden XSD-Typ für das XSD-Schema entnehmen.  
  
|SQL Server-Datentyp|XSD-Datentyp|  
|--------------------------|-------------------|  
|**bigint**|**long**|  
|**binary**|**base64Binary**|  
|**bit**|**boolean**|  
|**char**|**string**|  
|**datetime**|**dateTime**|  
|**decimal**|**decimal**|  
|**float**|**double**|  
|**image**|**base64Binary**|  
|**int**|**int**|  
|**money**|**decimal**|  
|**nchar**|**string**|  
|**ntext**|**string**|  
|**nvarchar**|**string**|  
|**numeric**|**decimal**|  
|**real**|**float**|  
|**smalldatetime**|**dateTime**|  
|**smallint**|**short**|  
|**smallmoney**|**decimal**|  
|**sql_variant**|**string**|  
|**sysname**|**string**|  
|**text**|**string**|  
|**timestamp**|**dateTime**|  
|**tinyint**|**unsignedByte**|  
|**varbinary**|**base64Binary**|  
|**varchar**|**string**|  
|**uniqueidentifier**|**string**|  
  
## <a name="sqldatatype-annotation"></a>sql:datatype-Anmerkung  
 Die **SQL: datatype** -Anmerkung wird zum Angeben des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyps verwendet. diese Anmerkung muss angegeben werden, wenn:  
  
-   Sie werden per Massen Ladevorgang  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus einem XSD- **DateTime**-, **Date**-oder **time** -Typ in eine datetime-Spalte geladen. In diesem Fall müssen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp der Spalte mithilfe von **SQL: datatype = "DateTime"** identifizieren. Diese Regel gilt auch für Updategrams.  
  
-   Sie sind Massen laden in eine Spalte vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Typ " **uniqueidentifier** ", und der XSD-Wert ist eine GUID mit geschweiften Klammern ({und}). Wenn Sie **SQL: datatype = "uniqueidentifier"** angeben, werden die geschweiften Klammern aus dem Wert entfernt, bevor Sie in die Spalte eingefügt werden. Wenn **SQL: datatype** nicht angegeben wird, wird der Wert mit den geschweiften Klammern gesendet, und der INSERT-oder Update-Vorgang schlägt fehl.  
  
-   Der XML-Datentyp **base64Binary** wird verschiedenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentypen (**Binary**, **Image** oder **varbinary**) zugeordnet. Um den XML-Datentyp **base64Binary** einem bestimmten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp zuzuordnen, verwenden Sie die **SQL: datatype** -Anmerkung. Diese Anmerkung gibt den expliziten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp der Spalte an, der das Attribut zugeordnet ist. Dies ist nützlich, wenn Daten in der Datenbank gespeichert werden. Durch Angeben der **SQL: datatype** -Anmerkung können Sie den expliziten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp identifizieren.  
  
 Im Allgemeinen wird empfohlen, **SQL: datatype** im Schema anzugeben.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-xsdtype"></a>A. Angeben von "xsd:type"  
 Dieses Beispiel zeigt, wie ein XSD- **Datentyp** , der mit dem **xsd: Type** -Attribut im Schema angegeben wird, sich auf das resultierende XML-Dokument auswirkt. Das Schema stellt eine XML-Ansicht der Tabelle Sales.SalesOrderHeader in der AdventureWorks-Datenbank bereit.  
  
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
  
-   Gibt **xsd: Type = Date** für das **OrderDate** -Attribut an. der Datums Teil des Werts, der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für das **OrderDate** -Attribut zurückgegeben wird, wird angezeigt.  
  
-   Gibt **xsd: Type = Time** für das **ShipDate** -Attribut an. der Zeit Teil des Werts, der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für das **ShipDate** -Attribut zurückgegeben wird, wird angezeigt.  
  
-   Gibt keinen **xsd: Type** -Wert für das **DueDate** -Attribut an. der gleiche Wert, der von zurückgegeben wird, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird angezeigt.  
  
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

     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
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
 Ein funktionierendes Beispiel finden Sie unter Beispiel G in [XML Bulk Load examples &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md). In diesem Beispiel wird ein GUID-Wert, der "{" und "}" enthält, massengeladen. Das Schema in diesem Beispiel gibt den **SQL: datatype** -Wert an, um den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp als **uniqueidentifier** zu identifizieren. In diesem Beispiel wird veranschaulicht, wann **SQL: datatype** im Schema angegeben werden muss.  
  
  
