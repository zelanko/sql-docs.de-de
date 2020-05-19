---
title: 'Ausschließen von Schema Elementen aus dem resultierenden XML-Dokument mithilfe von SQL: zugeordnet (SQLXML 4,0) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bbf5bad0a8c8e633149e2868047b88833a400849
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703587"
---
# <a name="excluding-schema-elements-from-the-resulting-xml-document-using-sqlmapped-sqlxml-40"></a>Ausschließen von Schemaelementen aus dem resultierenden XML-Dokument mithilfe von 'sql:mapped' (SQLXML 4.0)
  Aufgrund der Standardzuordnung werden alle Elemente und Attribute im XSD-Schema einer Datenbanktabelle/-sicht und -spalte zugeordnet. Wenn Sie ein Element im XDR-Schema erstellen möchten, das keiner Datenbanktabelle (Sicht) oder -spalte zugeordnet und im XML-Dokument nicht angezeigt wird, können Sie die `sql:mapped`-Anmerkung angeben.  
  
 Die `sql:mapped`-Anmerkung ist besonders hilfreich, wenn das Schema nicht geändert werden kann oder verwendet wird, um XML aus anderen Quellen zu überprüfen, und außerdem Daten enthält, die nicht in der Datenbank gespeichert sind. Die `sql:mapped`-Anmerkung unterscheidet sich von der `sql:is-constant`-Anmerkung insofern, als dass die nicht zugeordneten Elemente und Attribute nicht im XML-Dokument angezeigt werden.  
  
 Die `sql:mapped`-Anmerkung akzeptiert einen booleschen Wert (0 = false und 1 = true). Zulässig sind die Werte 0, 1, true und false.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlmapped-annotation"></a>A. Angeben der "sql:mapped"-Anmerkung  
 Angenommen, Sie haben ein XSD-Schema von einer anderen Quelle. Dieses XSD-Schema besteht aus einer ** \< Person. Contact>** -Element mit den Attributen **ContactID**, **FirstName**, **LastName**und **HomeAddress** .  
  
 Beim Zuordnen dieses XSD-Schemas zur Person. Contact-Tabelle in der AdventureWorks-Datenbank `sql:mapped` wird im **HomeAddress** -Attribut angegeben, da in der Employees-Tabelle nicht die Privatadressen von Mitarbeitern gespeichert werden. Daher wird dieses Attribut nicht der Datenbank zugeordnet und nicht im resultierenden XML-Dokument zurückgegeben, wenn eine XPath-Abfrage mit dem Zuordnungsschema ausgeführt wird.  
  
 Für den Rest des Schemas wird eine Standardzuordnung durchgeführt. Das ** \< Person. Contact>** -Element wird der Person. Contact-Tabelle zugeordnet, und alle Attribute werden den gleichnamigen Spalten in der Person. Contact-Tabelle zugeordnet.  
  
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
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML-Abfragen](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
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
  
 ContactID, FirstName und LastName sind vorhanden, HomeAddress jedoch nicht, weil im Zuordnungsschema für das zugehörige `sql:mapped`-Attribut der Wert 0 (null) angegeben ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Standard Zuordnung von XSD-Elementen und-Attributen zu Tabellen und Spalten &#40;SQLXML 4,0&#41;](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
  
