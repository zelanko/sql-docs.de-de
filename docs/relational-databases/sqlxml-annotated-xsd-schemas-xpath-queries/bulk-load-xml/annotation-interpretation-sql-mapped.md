---
title: 'SQL: zugeordnet (SQLXML 4,0) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapped annotation
- element mapping [SQLXML], XML Bulk Load
- attribute mapping [SQLXML], XML Bulk Load
- overflow data [SQLXML]
- sql:mapped
- column mapping [SQLXML]
ms.assetid: 7042741e-ce4d-4912-9c4a-d77194a028fc
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7711386722d618b35a8d957b680244243b4de5d5
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72907137"
---
# <a name="annotation-interpretation---sqlmapped"></a>Interpretation von Anmerkungen – sql:mapped
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XML-Massen laden verarbeitet die **SQL:** zugeordnete Anmerkung im XSD-Schema erwartungsgemäß, d. h., wenn das Zuordnungsschema für ein beliebiges Element oder Attribut **SQL: zugeordnet = "false"** angibt, versucht XML-Massen laden nicht, die zugeordneten Daten im entsprechende Spalte.  
  
 XML-Massen laden ignoriert Elemente und Attribute, die nicht zugeordnet sind (entweder weil Sie im Schema nicht beschrieben werden, oder weil Sie im XSD-Schema mit **SQL: zugeordnet = "false"** ) kommentiert werden. Alle nicht zugeordneten Daten werden in die Überlauf Spalte umgewandelt, wenn eine solche Spalte mithilfe von **SQL: overflow-field**angegeben wird.  
  
 Das folgende XSD-Schema ist ein Beispiel dafür:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="ROOT" sql:is-constant="1">  
<xsd:complexType>  
<xsd:sequence>  
  <xsd:element name="Customers" sql:relation="Cust"  
                                sql:overflow-field="OverflowColumn" >  
   <xsd:complexType>  
       <xsd:attribute name="CustomerID"  type="xsd:integer" />  
       <xsd:attribute name="CompanyName" type="xsd:string" />  
       <xsd:attribute name="City"        type="xsd:string" />  
       <xsd:attribute name="HomePhone"   type="xsd:string"   
                                       sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:sequence>  
</xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
 Da das **HomePhone** -Attribut **SQL: zugeordnet = "false"** angibt, ordnet XML-Massen laden dieses Attribut nicht der entsprechenden Spalte zu. Das XSD-Schema identifiziert eine Überlauf Spalte (**OverflowColumn**), in der XML-Massen laden diese nicht verbrauchten Daten speichert.  
  
### <a name="to-test-a-working-sample"></a>So testen Sie ein funktionstüchtiges Beispiel  
  
1.  Erstellen Sie die folgende Tabelle in der **tempdb** -Datenbank:  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust  
              (CustomerID     int         PRIMARY KEY,  
               CompanyName    varchar(20) NOT NULL,  
               City           varchar(20) DEFAULT 'Seattle',  
               OverflowColumn nvarchar(200))  
    GO  
    ```  
  
2.  Speichern Sie das in diesem Beispiel bereitgestellte Schema unter dem Dateinamen SampleSchema.xml.  
  
3.  Speichern Sie die folgenden XML-Daten unter dem Dateinamen SampleXMLData.xml:  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1111" CompanyName="Sean Chai"   
                 City="NY" HomePhone="111-1111" />  
      <Customers CustomerID="1112" CompanyName="Dont Know"   
                 City="LA" HomePhone="222-2222" />  
    </ROOT>  
    ```  
  
4.  Speichern Sie dieses [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition-Beispiel (VBScript) unter dem Dateinamen Sample.vbs, und führen Sie es aus, um das XML-Massenladen auszuführen:  

    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
 Dies ist das entsprechende XDR-Schema:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="ROOT" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
   <ElementType name="Customers" sql:relation="Cust"  
                             sql:overflow-field="OverflowColumn" >  
      <AttributeType name="CustomerID" />  
      <AttributeType name="CompanyName"  />  
      <AttributeType name="City"  />  
      <AttributeType name="HomePhone" />  
      <attribute type="CustomerID"  />  
      <attribute type="CompanyName"  />  
      <attribute type="City" />  
      <attribute type="HomePhone" sql:map-field="0" />  
   </ElementType>  
</Schema>  
```  
  
  
