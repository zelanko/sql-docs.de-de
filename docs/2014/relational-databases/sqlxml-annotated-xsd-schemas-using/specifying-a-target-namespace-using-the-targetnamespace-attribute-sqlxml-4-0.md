---
title: Angeben eines Target Namespace mit dem ' targetNamespace '-Attribut (SQLXML 4.0) | Microsoft-Dokumentation
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
- namespaces [SQLXML], annotated XSD schemas
- targetNamespace attribute
- XSD schemas [SQLXML], target namespaces
- annotated XSD schemas, target namespaces
- xsd:targetNamespace
- attributeFormDefault attribute
- elementFormDefault attribute
- target namespaces [SQLXML]
ms.assetid: f3df9877-6672-4444-8245-2670063c9310
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fa61e44575761d4ada96d68a887b584664735e7e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166731"
---
# <a name="specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-40"></a>Angeben eines Zielnamespaces mit dem 'targetNamespace'-Attribut (SQLXML 4.0)
  Beim Schreiben von XSD-Schemas, können Sie die XSD **TargetNamespace** Attribut, um einen Zielnamespace anzugeben. In diesem Thema wird beschrieben, wie das XSD **TargetNamespace**, **ElementFormDefault**, und **AttributeFormDefault** Attribute zu arbeiten, wie sie die XML-Instanz auswirken, die generiert, und wie XPath-Abfragen mit Namespaces festgelegt werden.  
  
 Sie können die **xsd: targetNamespace** Attribut zum Platzieren von Elementen und Attributen aus dem Standardnamespace in einen anderen Namespace. Sie können auch festlegen, ob lokal deklarierte Elemente und Attribute des Schemas durch einen Namespace qualifiziert werden sollen, sei es explizit durch ein Präfix oder standardmäßig implizit. Können Sie die **ElementFormDefault** und **AttributeFormDefault** Attribute der  **\<xsd: Schema >** Element Global angeben der Qualifikation von lokalen Elemente und Attribute, oder Sie können die **Formular** Attribut, um einzelne Elemente und Attribute separat festzulegen.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen für die Ausführung von SQLXML-Beispielen](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-a-target-namespace"></a>A. Angeben eines Zielnamespaces  
 Das folgende XSD-Schema gibt einen Zielnamespace an, mit der **xsd: targetNamespace** Attribut. Das Schema setzt auch die **ElementFormDefault** und **AttributeFormDefault** Attributwerte zu **"unqualified"** (der Standardwert für diese Attribute). Dies ist eine globale Deklaration und wirkt sich auf alle lokalen Elemente (**\<Reihenfolge >** im Schema) und Attribute (**"CustomerID"**, **ContactName**, und  **"OrderID"** im Schema).  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:CO="urn:MyNamespace"   
            targetNamespace="urn:MyNamespace" >  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer"   
               sql:relation="Sales.Customer"   
               type="CO:CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders"  
                     type="CO:OrderType" />  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesPersonID"  type="xsd:string" />  
  </xsd:complexType>  
  <xsd:complexType name="OrderType" >  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 Im Schema:  
  
-   Die **CustomerType** und **OrderType** Typdeklarationen sind global und aus diesem Grund befinden sich im Zielnamespace des Schemas. Daher, wenn diese Typen verwiesen wird in der Deklaration der  **\<Kunden >** Element und dessen  **\<Reihenfolge >** untergeordnetes Element, ein Präfix festgelegt, die verknüpft ist mit dem Zielnamespace.  
  
-   Die  **\<Kunden >** Element ist auch im Zielnamespace des Schemas enthalten, da es sich um ein globales Element im Schema handelt.  
  
 Führen Sie die folgende XPath-Abfrage für das Schema aus:  
  
```  
(/CO:Customer[@CustomerID=1)   
```  
  
 Die XPath-Abfrage generiert dieses Instanzdokument (nur einige der Bestellungen werden angezeigt):  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <y0:Customer xmlns:y0="urn:MyNamespace"   
      CustomerID="ALFKI" ContactName="Maria Anders">  
        <Order CustomerID="ALFKI" OrderID="10643" />   
        <Order CustomerID="ALFKI" OrderID="10692" />   
        ...  
  </y0:Customer>  
  </ROOT>  
```  
  
 Dieses Instanzdokument definiert den Namespace Urn: MyNamespace und ordnet ihm ein Präfix (y0) zuzuweisen. Das Präfix gilt nur für die  **\<Kunden >** globale Element. (Das Element ist global, da es als untergeordnetes Element deklariert ist  **\<xsd: Schema >** Elements im Schema.)  
  
 Das Präfix wird nicht auf die lokalen Elemente und Attribute angewendet, da der Wert des **ElementFormDefault** und **AttributeFormDefault** Attribute nastaven NA hodnotu **"unqualified"** im Schema. Beachten Sie, dass die  **\<Reihenfolge >** -Element lokal ist, da seine als untergeordnetes Element Deklaration der  **\<ComplexType >** Element, das definiert die  **\< CustomerType >** Element. Auf ähnliche Weise die Attribute (**"CustomerID"**, **"OrderID"**, und **ContactName**) sind lokal und nicht global.  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a>So erstellen Sie ein funktionstüchtiges Beispiel für dieses Schema  
  
1.  Kopieren Sie den oben stehenden Schemacode, und fügen Sie ihn in eine Textdatei ein. Speichern Sie die Datei unter dem Dateinamen targetNameSpace.xml.  
  
2.  Kopieren Sie die folgende Vorlage, und fügen Sie sie in eine Textdatei ein. Speichern Sie die Datei unter dem Namen targetNameSpaceT.xml im gleichen Verzeichnis, in dem Sie targetNameSpace.xml gespeichert haben.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="targetNamespace.xml"  
                       xmlns:CO="urn:MyNamespace" >  
        /CO:Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Die XPath-Abfrage in der Vorlage gibt die  **\<Kunden >** -Element für den Kunden mit "CustomerID" 1. Beachten Sie, dass die XPath-Abfrage das Namespace-Präfix für das Element, nicht für das Attribut, in der Abfrage festlegt. (Lokale Attribute sind nicht qualifiziert, wie im Schema angegeben.)  
  
     Der für das Zuordnungsschema (targetNameSpace.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert ist. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\targetNamepsace.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML-Abfragen](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Wenn das Schema gibt **ElementFormDefault** und **AttributeFormDefault** Attribute mit dem Wert **"qualified"**, Instanzdokument sind alle lokalen Elemente und Attribute gekennzeichnet. Sie können das vorherige Schema so ändern diese Attribute in umfassen die  **\<xsd: Schema >** Element und die Vorlage erneut ausführen. Da die Attribute nun auch in der Instanz qualifiziert sind, ändert sich die XPath-Abfrage so, dass auch das Namespace-Präfix enthalten ist.  
  
 Dies ist die geänderte XPath-Abfrage:  
  
```  
/CO:Customer[@CO:CustomerID=1]  
```  
  
 Dies ist das zurückgegebene XML-Dokument:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <y0:Customer xmlns:y0="urn:MyNamespace" CustomerID="1" SalesPersonID="280">  
      <Order SalesOrderID="43860" CustomerID="1" />   
      <Order SalesOrderID="44501" CustomerID="1" />   
      <Order SalesOrderID="45283" CustomerID="1" />   
      <Order SalesOrderID="46042" CustomerID="1" />   
   </y0:Customer>  
</ROOT>  
```  
  
  
