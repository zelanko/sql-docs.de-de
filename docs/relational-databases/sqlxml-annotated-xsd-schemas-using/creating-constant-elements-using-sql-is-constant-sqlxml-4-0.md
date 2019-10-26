---
title: 'Erstellen konstanter Elemente mithilfe von SQL: is-constant (SQLXML 4,0) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- sql:is-constant
- XSD schemas [SQLXML], constant elements
- element mapping [SQLXML], constant elements
- is-constant annotation
- constant elements [SQLXML]
- annotated XSD schemas, constant elements
ms.assetid: 940eea1b-54f5-445f-b844-c894d9f3941b
author: MightyPen
ms.author: genemi
ms.reviewer: ''
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1cb1223c7c72aa091a3dd15da3beacaf65c4b21b
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72906044"
---
# <a name="creating-constant-elements-using-sqlis-constant-sqlxml-40"></a>Erstellen von 'constant'-Elementen unter Verwendung von sql:is-constant (SQLXML 4.0)

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Zum Angeben eines konstanten Elements, d. h. eines Elements im XSD-Schema, das keiner Datenbanktabelle oder-Spalte zugeordnet ist, können Sie die **SQL: is-constant-** Anmerkung verwenden. Diese Anmerkung akzeptiert einen booleschen Wert (0 = false, 1 = true). Zulässig sind die Werte 0, 1, true und false. Die **SQL: is-constant-** Anmerkung kann für ein Element angegeben werden, das keine Attribute besitzt. Wenn sie für ein Element mit dem Wert true (oder 1) festgelegt ist, wird dieses Element nicht der Datenbank zugeordnet, aber dennoch im XML-Dokument angezeigt.  
  
 Die **SQL: is-constant-** Anmerkung kann für Folgendes verwendet werden:  
  
-   Hinzufügen eines Elements der obersten Ebene zum XML-Dokument. XML erfordert ein einzelnes Element (Stammelement) der obersten Ebene für das Dokument.  
  
-   Erstellen von Container Elementen, z. b. ein **\<Orders >** Element, das alle Bestellungen umschließt.  
  
 Die **SQL: is-constant-** Anmerkung kann einem **\<complexType->** Element hinzugefügt werden.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlis-constant-to-add-a-container-element"></a>A. Angeben von "sql:is-constant" zum Hinzufügen eines Containerelements  
 In diesem mit Anmerkungen versehene XSD-Schema wird **\<CustomerOrders->** als konstantes Element definiert, indem das Attribut " **SQL: is-constant** " mit dem Wert "1" angegeben wird. Daher ist **\<CustomerOrders->** keiner Datenbanktabelle oder-Spalte zugeordnet. Dieses Konstante Element besteht aus den **\<Reihenfolge >** untergeordneten Elementen.  
  
 Obwohl **\<CustomerOrders->** keiner Datenbanktabelle oder-Spalte zugeordnet ist, wird Sie weiterhin im resultierenden XML-Code als Containerelement angezeigt, das die **\<Reihenfolge >** untergeordneten Elemente enthält.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
        parent="Sales.Customer"  
        parent-key="CustomerID"  
        child="Sales.SalesOrderHeader"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="CustomerOrders" sql:is-constant="1" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"  
                           sql:relationship="CustOrders"   
                           maxOccurs="unbounded" >  
                <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="OrderDate" type="xsd:date" />  
                   <xsd:attribute name="CustomerID" type="xsd:string" />  
                </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>  
         </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>So testen Sie eine XPath-Beispiel Abfrage für das Schema  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen isConstant.xml.  
  
2.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen isConstantT.xml im gleichen Verzeichnis, in dem Sie  isConstant.xml gespeichert haben.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="isConstant.xml">  
            Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (isConstant.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\isConstant.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  

     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML-Abfragen](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden wird ein Teil des Resultsets aufgeführt:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
<Customer CustomerID="1">   
  <CustomerOrders>   
    <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1" />   
    <Order SalesOrderID="44501" OrderDate="2001-11-01" CustomerID="1" />   
    <Order SalesOrderID="45283" OrderDate="2002-02-01" CustomerID="1" />   
    <Order SalesOrderID="46042" OrderDate="2002-05-01" CustomerID="1" />   
    ...  
  </CustomerOrders>   
</Customer>   
</ROOT>  
```  
  
  
