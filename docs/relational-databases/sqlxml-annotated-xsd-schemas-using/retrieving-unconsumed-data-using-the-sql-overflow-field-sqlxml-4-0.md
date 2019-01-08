---
title: 'Abrufen nicht verbrauchter Daten mithilfe der SQL: Overflow-Feld (SQLXML 4.0) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- unconsumed data
- storing unconsumed data
- retrieving unconsumed data
- annotated XSD schemas, unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: 8526998d-b47d-4a32-8dc2-7f50a8d11097
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4193f98f4431ae5d73cfeadb1ef9898bd330a078
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52522183"
---
# <a name="retrieving-unconsumed-data-using-the-sqloverflow-field-sqlxml-40"></a>Abrufen von nicht verbrauchten Daten mithilfe von 'sql:overflow-field' (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Wenn Datensätze mithilfe der [!INCLUDE[tsql](../../includes/tsql-md.md)] OPENXML-Funktion aus einem XML-Dokument in eine Datenbank eingefügt werden, können alle nicht verbrauchten Daten aus dem XML-Quelldokument in einer Spalte gespeichert werden. Wenn Sie Daten mit kommentierte Schemas aus einer Datenbank abrufen, können Sie die **SQL: Overflow-Feld** Attribut zu Spalte in der Tabelle, in der die Überlaufdaten gespeichert. Die **SQL: Overflow-Feld** Attribut kann angegeben werden, auf  **\<Element >**.  
  
 Anschließend gibt es folgende Möglichkeiten, diese Daten abzurufen:  
  
-   In der Überlaufspalte gespeicherte Attribute hinzugefügt Element mit der **SQL: Overflow-Feld** Anmerkung.  
  
-   Die untergeordneten Elemente und ihre Nachfolger, die in der Überlaufspalte der Datenbank gespeichert sind, werden nach dem im Schema explizit angegebenen Inhalt als untergeordnete Elemente hinzugefügt. (Die Reihenfolge wird nicht beibehalten.)  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen für die Ausführung von SQLXML-Beispielen](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqloverflow-field-for-an-element"></a>A. Angeben von "sql:overflow-field" für ein Element  
 Im folgenden Beispiel wird vorausgesetzt, dass das folgende Skript ausgeführt wurde, damit eine Tabelle mit dem Namen Customers2 in der tempdb-Datenbank vorhanden ist:  
  
```  
USE tempdb  
CREATE TABLE Customers2 (  
CustomerID       VARCHAR(10),   
ContactName    VARCHAR(30),   
AddressOverflow    NVARCHAR(500))  
  
GO  
INSERT INTO Customers2 VALUES (  
'ALFKI',   
'Joe',  
'<Address>  
  <Address1>Maple St.</Address1>  
  <Address2>Apt. E105</Address2>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98147</Zip>  
 </Address>')  
GO  
```  
  
 Darüber hinaus müssen Sie ein virtuelles Verzeichnis für die Tempdb-Datenbank erstellen – und einen virtuellen Vorlagennamen vom **Vorlage** Typ mit dem Namen "Template".  
  
 Im folgenden Beispiel ruft das Zuordnungsschema die nicht verbrauchten Daten ab, die in der Spalte AddressOverflow der Tabelle Customers2 gespeichert sind.  
  
```  
<xsd:schema xmlns:xsd="https://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customers2" sql:overflow-field="AddressOverflow" >  
    <xsd:complexType>  
      <xsd:attribute name="CustomerID"  type="xsd:integer"/>  
      <xsd:attribute name="ContactName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine Beispiel-XPath-Abfrage anhand des Schemas  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen Overflow.xml.  
  
2.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen OverflowT.xml im gleichen Verzeichnis, in dem Sie Overflow.xml gespeichert haben. Die Abfrage in der Vorlage wählt die Datensätze in der Customers2-Tabelle aus.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Overflow.xml">  
            /Customers2  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (Overflow.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert ist. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\Overflow.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden wird das Resultset aufgeführt:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers2 CustomerID="ALFKI" ContactName="Joe">  
    <Address1>Maple St.</Address1>   
    <Address2>Apt. E105</Address2>   
    <City>Seattle</City>   
    <State>WA</State>   
    <Zip>98147</Zip>   
  </Customers2>  
</ROOT>  
```  
  
  
