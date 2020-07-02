---
title: Benutzerdefinierte XSD-Zuordnungen zu Tabellen/Spalten (SQLXML)
description: Erfahren Sie, wie Sie eine benutzerdefinierte Zuordnung in einer SQLXML XPath-Abfrage zwischen den Elementen und Attributen eines XSD-Schemas und den Tabellen und Spalten einer relationalen Datenbank erstellen.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- sql:field
- row mapping [SQLXML]
- attribute mapping [SQLXML], explicit mapping
- field annotation
- XSD schemas [SQLXML], mapping attributes and elements
- names [SQLXML]
- relation annotation
- table/view mapping [SQLXML], explicit mapping
- sql:relation
- mapping schema [SQLXML], explicit mapping
- annotated XSD schemas, mapping attributes and elements
- column mapping [SQLXML]
- element mapping [SQLXML], explicit mapping
- table mapping [SQLXML], explicit mapping
- element/attribute mapping [SQLXML]
ms.assetid: 7a5ebeb6-7322-4141-a307-ebcf95976146
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 534de76c28dea79ba52b28983fe56daf666760f5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750758"
---
# <a name="custom-xsd-mappings-to-tablescolumns-sqlxml"></a>Benutzerdefinierte XSD-Zuordnungen zu Tabellen/Spalten (SQLXML)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Wenn ein XSD-Schema zur Bereitstellung einer XML-Sicht der relationalen Datenbank verwendet wird, müssen die Elemente und Attribute des Schemas den Tabellen und Spalten der Datenbank zugeordnet werden. Die Zeilen in der Datenbanktabelle/-sicht werden den Elementen im XML-Dokument zugeordnet. Die Spaltenwerte in der Datenbank werden Attributen oder Elementen zugeordnet.  
  
 Wenn Xpath-Abfragen für das mit Anmerkungen versehene XSD-Schema angegeben werden, werden die Daten für die Elemente und Attribute im Schema aus den Tabellen und Spalten abgerufen, denen sie zugeordnet sind. Um einen einzelnen Wert aus der Datenbank abrufen zu können, muss die im XSD-Schema angegebene Zuordnung sowohl über eine Beziehungs- als auch eine Feldangabe verfügen. Wenn der Name eines Elements/Attributs nicht mit dem Namen der Tabelle/Sicht oder des Spaltennamens übereinstimmt, dem er zugeordnet ist, werden die **SQL: Relation** -und **SQL: Field** -Anmerkungen verwendet, um die Zuordnung zwischen einem Element oder Attribut in einem XML-Dokument und der Tabelle (Sicht) oder Spalte in einer Datenbank anzugeben.  
  
## <a name="sql-relation"></a>sql-Beziehung  
 Die **SQL: Relation** -Anmerkung wird hinzugefügt, um einen XML-Knoten im XSD-Schema einer Datenbanktabelle zuzuordnen. Der Name einer Tabelle (Sicht) wird als Wert der " **SQL: Relation** "-Anmerkung angegeben.  
  
 Wenn **SQL: Relation** für ein Element angegeben wird, gilt der Gültigkeitsbereich dieser Anmerkung für alle Attribute und untergeordneten Elemente, die in der komplexen Typdefinition dieses Elements beschrieben werden. Dadurch wird eine Verknüpfung zum Schreiben von Anmerkungen bereitgestellt.  
  
 Die **SQL: Relation** -Anmerkung ist auch nützlich, wenn Bezeichner, die in gültig sind, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in XML ungültig sind. Zum Beispiel ist "Order Details" ein gültiger Tabellenname in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], jedoch nicht in XML. In solchen Fällen kann die **SQL: Relation** -Anmerkung verwendet werden, um die Zuordnung anzugeben, z. b.:  
  
```  
<xsd:element name="OD" sql:relation="[Order Details]">  
```  
  
## <a name="sql-field"></a>sql-Feld  
 Die **SQL-Field-** Anmerkung ordnet ein Element oder Attribut einer Daten Bank Spalte zu. Die **SQL: Field** -Anmerkung wird hinzugefügt, um einen XML-Knoten im Schema einer Daten Bank Spalte zuzuordnen. Sie können **SQL: Field** nicht für ein leeres Inhalts Element angeben.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlrelation-and-sqlfield-annotations"></a>A. Angeben der Anmerkungen sql:relation und sql:field  
 In diesem Beispiel besteht das XSD-Schema aus einem **\<Contact>** Element des komplexen Typs mit **\<FName>** den untergeordneten **\<LName>** Elementen und und dem **ContactID** -Attribut.  
  
 Die **SQL: Relation** -Anmerkung ordnet das- **\<Contact>** Element der Person. Contact-Tabelle in der AdventureWorks-Datenbank zu. Die **SQL: Field** -Anmerkung ordnet das **\<FName>** -Element der FirstName-Spalte und das- **\<LName>** Element der LastName-Spalte zu.  
  
 Für das **ContactID** -Attribut wird keine Anmerkung angegeben. Dies führt zu einer Standardzuordnung des Attributs zur Spalte mit dem gleichen Namen.  
  
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
        <xsd:attribute name="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen MySchema-annotated.xml.  
  
2.  Kopieren Sie die unten stehende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen MySchema-annotatedT.xml im gleichen Verzeichnis, in dem Sie MySchema-annotated.xml gespeichert haben.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="MySchema-annotated.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (MySchema-annotated.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema-annotated.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML-Abfragen](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden wird ein Teil des Resultsets aufgeführt:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
 <Contact ContactID="1">   
    <FName>Gustavo</FName>   
    <LName>Achong</LName>   
 </Contact>   
  .....  
</ROOT>  
```  
  
  
