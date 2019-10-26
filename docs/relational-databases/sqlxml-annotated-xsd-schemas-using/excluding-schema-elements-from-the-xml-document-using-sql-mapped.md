---
title: 'Ausschließen von Schema Elementen aus dem XML-Dokument mithilfe von SQL: zugeordnet | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
author: MightyPen
ms.author: genemi
ms.reviewer: ''
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d466ad57d7644f73d7fdd44df62aac6a0c2a1b0b
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72905960"
---
# <a name="excluding-schema-elements-from-the-xml-document-using-sqlmapped"></a>Ausschließen von Schemaelementen aus dem XML-Dokument mithilfe von „sql:mapped“
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Aufgrund der Standardzuordnung werden alle Elemente und Attribute im XSD-Schema einer Datenbanktabelle/-sicht und -spalte zugeordnet. Wenn Sie ein Element im XSD-Schema erstellen möchten, das keiner Datenbanktabelle (Sicht) oder Spalte zugeordnet ist und nicht in der XML-Datei angezeigt wird, können Sie die **SQL:** zugeordnete Anmerkung angeben.  
  
 Die **SQL:** zugeordnete Anmerkung ist besonders nützlich, wenn das Schema nicht geändert werden kann oder wenn das Schema verwendet wird, um XML aus anderen Quellen zu validieren und noch Daten enthält, die nicht in der Datenbank gespeichert sind. Die **SQL:** zugeordnete Anmerkung unterscheidet sich von **SQL: is-constant** in, dass die nicht zugeordneten Elemente und Attribute nicht im XML-Dokument angezeigt werden.  
  
 Die **SQL:** zugeordnete Anmerkung nimmt einen booleschen Wert (0 = false, 1 = true). Zulässig sind die Werte 0, 1, true und false.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlmapped-annotation"></a>A. Angeben der "sql:mapped"-Anmerkung  
 Angenommen, Sie haben ein XSD-Schema von einer anderen Quelle. Dieses XSD-Schema besteht aus einem **\<Person. Contact >** -Element mit den Attributen **ContactID**, **FirstName**, **LastName**und **HomeAddress** .  
  
 Beim Zuordnen dieses XSD-Schemas zur Person. Contact-Tabelle in der AdventureWorks-Datenbank wird **SQL: zugeordnet** im **HomeAddress** -Attribut angegeben, da in der Employees-Tabelle nicht die Privatadressen von Mitarbeitern gespeichert werden. Daher wird dieses Attribut nicht der Datenbank zugeordnet und nicht im resultierenden XML-Dokument zurückgegeben, wenn eine XPath-Abfrage mit dem Zuordnungsschema ausgeführt wird.  
  
 Für den Rest des Schemas wird eine Standardzuordnung durchgeführt. Die **\<Person. Contact >** -Element wird der Person. Contact-Tabelle zugeordnet, und alle Attribute werden den gleichnamigen Spalten in der Person. Contact-Tabelle zugeordnet.  
  
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
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
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
  
 Beachten Sie, dass "ContactID", "FirstName" und "LastName" vorhanden sind, aber "HomeAddress" nicht ist, weil das Zuordnungsschema "0" für das Attribut " **SQL:**  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Standard Zuordnung von XSD-Elementen und-Attributen zu Tabellen &#40;und Spalten SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
  
