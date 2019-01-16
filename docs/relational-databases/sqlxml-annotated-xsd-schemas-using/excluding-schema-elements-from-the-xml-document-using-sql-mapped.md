---
title: 'Ausschließen von Schemaelementen aus dem XML-Dokument mit Sql: zugeordnet | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- annotated XSD schemas, excluding schema elements
- mapped annotation
- table mapping [SQLXML], excluding schema elements
- sql:mapped
- excluding schema elements
- element mapping [SQLXML], excluding schema elements
- column mapping [SQLXML]
- XSD schemas [SQLXML], excluding schema elements
- attribute mapping [SQLXML], excluding schema elements
- table/view mapping [SQLXML], excluding schema elements
ms.assetid: 7d2649dd-0038-4a2c-b16d-f80f7c306966
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a93d62917efb4bb53c1d5a699109844e1d358bb6
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2019
ms.locfileid: "54256035"
---
# <a name="excluding-schema-elements-from-the-xml-document-using-sqlmapped"></a>Ausschließen von Schemaelementen aus dem XML-Dokument mithilfe von „sql:mapped“
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Aufgrund der Standardzuordnung werden alle Elemente und Attribute im XSD-Schema einer Datenbanktabelle/-sicht und -spalte zugeordnet. Wenn ein Element im XSD-Schema erstellen, auf Sie keiner Datenbanktabelle (Sicht) oder – Spalte zugeordnet, und nicht in der XML-Code angezeigt, werden sollen, können Sie angeben der **Sql: zugeordnet** Anmerkung.  
  
 Die **Sql: zugeordnet** -Anmerkung ist besonders hilfreich, wenn das Schema kann nicht geändert werden oder wenn das Schema zum Validieren von XML aus anderen Datenquellen und noch Daten enthält, die nicht in der Datenbank gespeichert werden. Die **Sql: zugeordnet** -Anmerkung unterscheidet sich von **Sql: ist Konstante** , die nicht zugeordneten Elemente und Attribute im XML-Dokument nicht angezeigt werden.  
  
 Die **Sql: zugeordnet** -Anmerkung akzeptiert einen booleschen Wert (0 = False, 1 = True). Zulässig sind die Werte 0, 1, true und false.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen für die Ausführung von SQLXML-Beispielen](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlmapped-annotation"></a>A. Angeben der "sql:mapped"-Anmerkung  
 Angenommen, Sie haben ein XSD-Schema von einer anderen Quelle. Dieses XSD-Schema besteht aus einem  **\<Person.Contact >** -Element mit **ContactID**, **FirstName**, **"LastName"**, und **HomeAddress** Attribute.  
  
 Beim Zuordnen dieses XSD-Schema der Person.Contact-Tabelle in der AdventureWorks-Datenbank **Sql: zugeordnet** angegeben ist, auf die **HomeAddress** Attribut, da der Startseite keine in die Employees-Tabelle gespeichert werden die Adressen der Angestellten. Daher wird dieses Attribut nicht der Datenbank zugeordnet und nicht im resultierenden XML-Dokument zurückgegeben, wenn eine XPath-Abfrage mit dem Zuordnungsschema ausgeführt wird.  
  
 Für den Rest des Schemas wird eine Standardzuordnung durchgeführt. Die  **\<Person.Contact >** Element wird der Person.Contact-Tabelle zugeordnet, und alle Attribute den Spalten mit demselben Namen in der Person.Contact-Tabelle zugeordnet.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:attribute name="ContactID"   type="xsd:string"/>  
      <xsd:attribute name="FirstName"    type="xsd:string" />  
      <xsd:attribute name="LastName"     type="xsd:string" />  
      <xsd:attribute name="HomeAddress" type="xsd:string"   
                     sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine Beispiel-XPath-Abfrage anhand des Schemas  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen sql-mapped.xml.  
  
2.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen sql-mappedT.xml im gleichen Verzeichnis, in dem Sie sql-mapped.xml gespeichert haben.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-mapped.xml">  
            /Person.Contact[@ContactID < 10]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (MySchema.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\sql-mapped.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML-Abfragen](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Dies ist das Resultset:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel" />   
  <Person.Contact ContactID="3" FirstName="Kim" LastName="Abercrombie" />   
  <Person.Contact ContactID="4" FirstName="Humberto" LastName="Acevedo" />   
  <Person.Contact ContactID="5" FirstName="Pilar" LastName="Ackerman" />   
  <Person.Contact ContactID="6" FirstName="Frances" LastName="Adams" />   
  <Person.Contact ContactID="7" FirstName="Margaret" LastName="Smith" />   
  <Person.Contact ContactID="8" FirstName="Carla" LastName="Adams" />   
  <Person.Contact ContactID="9" FirstName="Jay" LastName="Adams" />   
</ROOT>  
```  
  
 Beachten Sie, dass die ContactID, FirstName und LastName vorhanden sind, HomeAddress wird nicht verwendet werden, da das Zuordnungsschema für 0 angegeben die **Sql: zugeordnet** Attribut.  
  
## <a name="see-also"></a>Siehe auch  
 [Standardzuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
  
