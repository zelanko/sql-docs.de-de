---
title: 'Identifizieren von Schlüssel Spalten mithilfe von SQL: key-fields (SQLXML 4,0) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nesting XML results
- proper nesting in results [SQLXML]
- sql:key-fields
- XSD schemas [SQLXML], key columns
- identifying key columns [SQLXML]
- annotated XSD schemas, key columns
- key columns [SQLXML]
- relationships [SQLXML], key columns
- hierarchical relationships [SQLXML]
- key-fields annotation
ms.assetid: 1a5ad868-8602-45c4-913d-6fbb837eebb0
author: rothja
ms.author: jroth
ms.openlocfilehash: 5628f0ef6a130d5f0fc88c78236a0352bc5f4b2d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85003245"
---
# <a name="identifying-key-columns-using-sqlkey-fields-sqlxml-40"></a>Identifizieren von Schlüsselspalten mithilfe von sql:key-Feldern (SQLXML 4.0)
  Wenn eine XPath-Abfrage für ein XSD-Schema angegeben wird, sind in den meisten Fällen wichtige Informationen erforderlich, um eine ordnungsgemäße Schachtelung im Ergebnis zu erhalten. Durch die Angabe der `sql:key-fields`-Anmerkung lässt sich sicherstellen, dass die entsprechende Hierarchie generiert wird.  
  
> [!NOTE]  
>  Um die richtige Schachtelung sicherzustellen, wird empfohlen, `sql:key-fields` für diejenigen Elemente anzugeben, die Tabellen zugeordnet werden. Das erzeugte XML wird durch die Anordnung des zugrunde liegenden Resultsets beeinflusst. Wenn `sql:key-fields` nicht angegeben wird, hat das generierte XML unter Umständen nicht das richtige Format.  
  
 Der Wert von `sql:key-fields` identifiziert die Spalte(n), welche die Zeilen in der Beziehung eindeutig identifiziert bzw. identifizieren. Wenn mehrere Spalten zur eindeutigen Identifizierung einer Zeile erforderlich sind, werden die Spaltenwerte jeweils durch ein Leerzeichen voneinander getrennt.  
  
 Sie müssen die-Anmerkung verwenden `sql:key-fields` , wenn ein-Element ein-Element enthält **\<sql:relationship>** , das zwischen dem-Element und einem untergeordneten-Element definiert ist, aber nicht den Primärschlüssel der im übergeordneten Element angegebenen Tabelle bereitstellt.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-producing-the-appropriate-nesting-when-sqlrelationship-does-not-provide-sufficient-information"></a>A. Erzeugen der passenden Schachtelung, wenn \<sql:relationship> keine ausreichenden Informationen bereitstellt  
 Dieses Beispiel zeigt, wo `sql:key-fields` angegeben werden muss.  
  
 Betrachten Sie folgendes Schema. Das Schema gibt eine Hierarchie zwischen dem **\<Order>** -Element und dem- **\<Customer>** Element an, in dem das- **\<Order>** Element das übergeordnete Element ist **\<Customer>**  
  
 Das **\<sql:relationship>** -Tag wird verwendet, um die Beziehung zwischen übergeordneten und untergeordneten Elementen anzugeben. In diesem Tag wird CustomerID als übergeordneter Schlüssel identifiziert, der auf die untergeordnete CustomerID-Schlüsselspalte in der Sales.Customer-Tabelle verweist. Die in bereitgestellten Informationen **\<sql:relationship>** reichen nicht aus, um Zeilen in der übergeordneten Tabelle (Sales. SalesOrderHeader) eindeutig zu identifizieren. Ohne die `sql:key-fields`-Anmerkung wird daher eine ungenaue Hierarchie generiert.  
  
 Bei Angabe `sql:key-fields` von für **\<Order>** identifiziert die Anmerkung die Zeilen in der übergeordneten Tabelle (Sales. SalesOrderHeader-Tabelle) eindeutig, und die untergeordneten Elemente werden unter dem übergeordneten Element angezeigt.  
  
 Das ist das Schema:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrdCust"  
        parent="Sales.SalesOrderHeader"  
        parent-key="CustomerID"  
        child="Sales.Customer"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"   
               sql:key-fields="SalesOrderID">  
   <xsd:complexType>  
     <xsd:sequence>  
     <xsd:element name="Customer" sql:relation="Sales.Customer"   
                       sql:relationship="OrdCust"  >  
       <xsd:complexType>  
         <xsd:attribute name="CustID" sql:field="CustomerID" />  
         <xsd:attribute name="SoldBy" sql:field="SalesPersonID" />  
       </xsd:complexType>  
     </xsd:element>  
     </xsd:sequence>  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name= "CustomerID" type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a>So erstellen Sie ein funktionstüchtiges Beispiel für dieses Schema  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen KeyFields1.xml.  
  
2.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen KeyFields1T.xml im gleichen Verzeichnis, in dem Sie KeyFields1.xml gespeichert haben. Die XPath-Abfrage in der Vorlage gibt alle-Elemente zurück, deren **\<Order>** CustomerID-Wert kleiner als 3 ist.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="KeyFields1.xml">  
            /Order[@CustomerID < 3]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (KeyFields1.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields1.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML-Abfragen](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden wird ein Teil des Resultsets aufgeführt:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
    <Order SalesOrderID="43860" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="44501" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    <Order SalesOrderID="45283" CustomerID="1">  
       <Customer CustID="1" SoldBy="280"/>  
    </Order>  
    .....  
</ROOT>  
```  
  
### <a name="b-specifying-sqlkey-fields-to-produce-proper-nesting-in-the-result"></a>B. Angeben der sql:key-Felder, um die richtige Schachtelung im Ergebnis zu erzeugen  
 Im folgenden Schema gibt es keine Hierarchie, die mit angegeben wird **\<sql:relationship>** . Das Schema erfordert trotzdem die Angabe der `sql:key-fields`-Anmerkung, um Mitarbeiter in der HumanResources.Employee-Tabelle eindeutig zu identifizieren.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="HumanResources.Employee" sql:key-fields="EmployeeID" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Title">  
          <xsd:complexType>  
            <xsd:simpleContent>  
              <xsd:extension base="xsd:string">  
                 <xsd:attribute name="EmployeeID" type="xsd:integer" />  
              </xsd:extension>  
            </xsd:simpleContent>  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
   </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a>So erstellen Sie ein funktionstüchtiges Beispiel für dieses Schema  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen KeyFields2.xml.  
  
2.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen KeyFields2T.xml im gleichen Verzeichnis, in dem Sie KeyFields2.xml gespeichert haben. Die XPath-Abfrage in der Vorlage gibt alle **\<HumanResources.Employee>** Elemente zurück:  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="KeyFields2.xml">  
        /HumanResources.Employee  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (KeyFields2.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\KeyFields2.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML-Abfragen](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Dies ist das Ergebnis:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <HumanResources.Employee>  
    <Title EmployeeID="1">Production Technician - WC60</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="2">Marketing Assistant</Title>   
  </HumanResources.Employee>  
  <HumanResources.Employee>  
    <Title EmployeeID="3">Engineering Manager</Title>   
  </HumanResources.Employee>  
  ...  
</ROOT>  
```  
  
  
