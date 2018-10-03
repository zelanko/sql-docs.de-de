---
title: 'SQL: Overflow-Feld (SQLXML 4.0) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- overflow-field annotation
- unconsumed data
- overflow data [SQLXML]
- sql:overflow-field
ms.assetid: f005182b-6151-432d-ab22-3bc025742cd3
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 004a9a695dc286c08aea413e819b82d927e1bc94
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47648708"
---
# <a name="annotation-interpretation---sqloverflow-field"></a>Interpretation von Anmerkungen – sql:overflow-field
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  In einem Schema können Sie eine Spalte als Überlaufspalte festlegen, die alle nicht verbrauchten Daten aus dem XML-Dokument aufnimmt. Diese Spalte wird im Schema mithilfe der **sql:overflow-field** -Anmerkung angegeben. Sie können mit mehreren Überlaufspalten arbeiten.  
  
 Immer, wenn ein XML-Knoten (Element oder Attribut), für den eine **sql:overflow-field** -Anmerkung definiert ist, in den Bereich eintritt, wird die Überlaufspalte aktiviert und empfängt nicht verbrauchte Daten. Wenn der Knoten den Bereich verlässt, ist die Überlaufspalte nicht mehr aktiv und das vorherige Überlauffeld (sofern vorhanden) wird durch das XML-Massenladen aktiviert.  
  
 Bei der Speicherung der Daten in der Überlaufspalte speichert der XML-Massenladevorgang ebenfalls die Start- und Endtags des übergeordneten Elements, für das **sql:overflow-field** definiert ist.  
  
 Das folgende Schema beschreibt zum Beispiel die  **\<Kunden >** und  **\<CustOrder >** Elemente. Beide Elemente geben eine Überlaufspalte an:  
  
```  
<?xml version="1.0" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
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
 <xsd:element name="ROOT" sql:is-constant="1">  
  <xsd:complexType>  
    <xsd:sequence>   
      <xsd:element name="Customers"   
                   sql:relation="Cust"  
                   sql:overflow-field="OverflowColumn">  
        <xsd:complexType>  
             <xsd:sequence>   
             <xsd:element name="CustomerID" type="xsd:integer"/>  
             <xsd:element name="CompanyName"  type="xsd:string"/>  
             <xsd:element name="City" type="xsd:string"/>  
             <xsd:element name="Order"  
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder"  
                          sql:overflow-field="OverflowColumn">  
               <xsd:complexType>  
                 <xsd:attribute name="OrderID"/>  
                 <xsd:attribute name="CustomerID"/>  
               </xsd:complexType>  
             </xsd:element>  
          </xsd:sequence>   
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 Im Schema die  **\<Kunden >** -Element ordnet die Cust-Tabelle und die  **\<Reihenfolge >** -Element der CustOrder-Tabelle zugeordnet.  
  
 Sowohl die  **\<Kunden >** und  **\<Reihenfolge >** Elemente geben eine Überlaufspalte. Daher speichert XML-Massenladen alle nicht verbrauchten untergeordneten Elemente und Attribute der  **\<Kunden >** -Element in der Überlaufspalte der Cust-Tabelle, und alle nicht verbrauchten untergeordneten Elemente und Attribute der  **\<Reihenfolge >** Element in der Überlaufspalte der CustOrder-Tabelle.  
  
### <a name="to-test-a-working-sample"></a>So testen Sie ein funktionstüchtiges Beispiel  
  
1.  Speichern Sie das in diesem Beispiel bereitgestellte Schema unter dem Dateinamen SampleSchema.xml.  
  
2.  Erstellen Sie die folgenden Tabellen:  
  
    ```  
    CREATE TABLE Cust (  
              CustomerID     int         PRIMARY KEY,  
              CompanyName    varchar(20) NOT NULL,  
              City           varchar(20) DEFAULT 'Seattle',  
              OverflowColumn nvarchar(200))  
    GO  
    CREATE TABLE CustOrder (  
              OrderID        int         PRIMARY KEY,  
              CustomerID     int         FOREIGN KEY REFERENCES  
                                              Cust(CustomerID),  
              OverflowColumn nvarchar(200))  
    GO  
    ```  
  
3.  Speichern Sie die folgenden XML-Daten unter dem Dateinamen SampleXMLData.xml:  
  
    ```  
    <ROOT>  
      <Customers>  
        <CustomerID>1111</CustomerID>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City><![CDATA[NY]]> </City>  
          <Junk>garbage in overflow</Junk>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
     </Customers>  
     <Customers>  
       <CustomerID>1112</CustomerID>  
       <CompanyName>Toms Spezialitten</CompanyName>  
       <City><![CDATA[LA]]> </City>  
       <xyz><address>111 Maple, Seattle</address></xyz>     
       <Order OrderID="3" />  
     </Customers>  
       <Customers>  
       <CustomerID>1113</CustomerID>  
       <CompanyName>Victuailles en stock</CompanyName>  
       <Order OrderID="4" />  
      </Customers>  
    </ROOT>  
    ```  
  
4.  Speichern Sie dieses [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition-Beispiel (VBScript) unter dem Dateinamen Sample.vbs, und führen Sie es aus, um das XML-Massenladen auszuführen:  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
  
