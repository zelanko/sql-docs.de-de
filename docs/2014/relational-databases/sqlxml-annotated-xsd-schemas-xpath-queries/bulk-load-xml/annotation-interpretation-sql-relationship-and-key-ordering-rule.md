---
title: 'SQL: Relationship und die Schlüsselsortierregel (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- key ordering rules [SQLXML]
- relationship annotation
ms.assetid: 914cb152-09f5-4b08-b35d-71940e4e9986
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 82ac5e6fb6abc886da542d7948b01fbf9437388b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049412"
---
# <a name="sqlrelationship-and-the-key-ordering-rule-sqlxml-40"></a>sql:relationship und die Schlüsselsortierregel (SQLXML 4.0)
  Da XML-Massenladen Datensätze generiert, wenn ihre Knoten in den Bereich gelangen, und diese Datensätze an Microsoft sendet [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Wenn ihre Knoten den Bereich verlassen, müssen die Daten für den Datensatz innerhalb des Bereichs des Knotens vorhanden sein.  
  
 Betrachten Sie das folgende XSD-Schema, in dem die 1: n-Beziehung zwischen  **\<Kunden >** und  **\<Reihenfolge >** Elementen (ein Kunde kann viele Aufträge vergeben) angegeben unter Verwendung der `<sql:relationship>` Element:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"<>   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Als die  **\<Kunden >** Elementknoten in den Bereich gelangt, generiert das XML-Massenladen einen Kundendatensatz. Dieser Datensatz bleibt, bis der XML-Massenladen liest  **\</Customer >**. Bei der Verarbeitung der  **\<Reihenfolge >** Elementknoten, XML-Massenladen verwendet `<sql:relationship>` zum Abrufen des Werts, der die CustomerID Fremdschlüsselspalte der CustOrder-Tabelle der **\<Kunden >** parent-Element, da die  **\<Reihenfolge >** Element nicht an die **CustomerID** Attribut. Dies bedeutet, Sie beim Definieren der  **\<Kunden >** -Element können Sie angeben müssen die **CustomerID** -Attribut im Schema vor dem angeben `<sql:relationship>`. Andernfalls gilt bei einer  **\<Reihenfolge >** Element in den Bereich gelangt, XML-Massenladen wird ein Datensatz für die CustOrder-Tabelle generiert und wenn das XML-Massenladen erreicht die  **\</Order >** Endtag, sendet es den Datensatz zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ohne den Wert für die CustomerID-Fremdschlüsselspalte.  
  
 Speichern Sie das in diesem Beispiel bereitgestellte Schema unter dem Dateinamen SampleSchema.xml.  
  
### <a name="to-test-a-working-sample"></a>So testen Sie ein funktionstüchtiges Beispiel  
  
1.  Erstellen Sie die folgenden Tabellen:  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int          PRIMARY KEY,  
               CompanyName    varchar(20)  NOT NULL,  
                  City           varchar(20)  DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID        varchar(10) PRIMARY KEY,  
               CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID))  
    GO  
    ```  
  
2.  Speichern Sie die folgenden Beispieldaten unter dem Dateinamen SampleXMLData.xml:  
  
    ```  
    <ROOT>    
      <Customers>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
        <CustomerID>1111</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <City>LA</City>    
        <Order OrderID="3" />  
        <CustomerID>1112</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
        <CustomerID>1113</CustomerID>  
      </Customers>  
    </ROOT>  
    ```  
  
3.  Um XML-Massenladen auszuführen, speichern, und führen Sie die folgenden [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript)-Beispiel unter mysample.vbs:  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
     Als Ergebnis fügt das XML-Massenladen einen NULL-Wert in die CustomerID-Fremdschlüsselspalte der CustOrder-Tabelle ein. Wenn Sie die XML-Beispieldaten überarbeiten, damit die  **\<CustomerID >** untergeordnete Element angezeigt wird, bevor die  **\<Reihenfolge >** untergeordnetes Element, erhalten Sie das erwartete Ergebnis: XML-Massenladen Fügt den angegebenen Fremdschlüsselwert in die Spalte an.  
  
 Dies ist das entsprechende XDR-Schema:  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="CustomerID"  />  
   <ElementType name="CompanyName" />  
   <ElementType name="City"        />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust" >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
                 <sql:relationship  
                        key-relation    ="Cust"  
                        key             ="CustomerID"  
                        foreign-key     ="CustomerID"  
                        foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
  