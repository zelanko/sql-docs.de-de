---
title: Angeben eines Ziel Namespace mit targetNamespace (SQLXML)
description: Erfahren Sie, wie Sie einen Ziel Namespace in einem XSD-Schema mithilfe des targetNamespace-Attributs in SQLXML 4,0 angeben.
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
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
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3daeaabe86d91d0986fb764c3a60304ec5e09faf
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84885159"
---
# <a name="specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-40"></a>Angeben eines Zielnamespaces mit dem 'targetNamespace'-Attribut (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Beim Schreiben von XSD-Schemas können Sie das XSD- **targetNamespace** -Attribut verwenden, um einen Ziel Namespace anzugeben. In diesem Thema wird beschrieben, wie das XSD-Attribut " **targetNamespace**", das **Element Form default**-Attribut und das **attributeFormDefault** -Attribut funktionieren, wie Sie sich auf die generierte XML-Instanz auswirken und wie XPath-Abfragen mit Namespaces angegeben werden.  
  
 Sie können das **xsd: targetNamespace** -Attribut verwenden, um Elemente und Attribute aus dem Standard Namespace in einen anderen Namespace zu platzieren. Sie können auch festlegen, ob lokal deklarierte Elemente und Attribute des Schemas durch einen Namespace qualifiziert werden sollen, sei es explizit durch ein Präfix oder standardmäßig implizit. Sie können die Attribute Element **Form default** und **attributeFormDefault** für das- **\<xsd:schema>** Element verwenden, um die Qualifizierung lokaler Elemente und Attribute global anzugeben, oder Sie können das **Form** -Attribut verwenden, um einzelne Elemente und Attribute separat anzugeben.  
  
## <a name="examples"></a>Beispiele  
 Es müssen bestimmte Anforderungen erfüllt sein, damit aus den folgenden Beispielen funktionierende Beispiele erstellt werden können. Weitere Informationen finden Sie unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-a-target-namespace"></a>A. Angeben eines Zielnamespaces  
 Das folgende XSD-Schema gibt einen Ziel Namespace mit dem **xsd: targetNamespace** -Attribut an. Das Schema legt auch die Attributwerte **Element Form default** und **attributeFormDefault** auf **"nicht qualifiziert"** (der Standardwert für diese Attribute) fest. Dies ist eine globale Deklaration und wirkt sich auf alle lokalen Elemente ( **\<Order>** im Schema) und Attribute (**CustomerID**, **ContactName**und **OrderID** im Schema) aus.  
  
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
  
-   Die Typdeklarationen **CustomerType** und **OrderType** sind global und sind daher im Ziel Namespace des Schemas enthalten. Wenn auf diese Typen in der Deklaration des **\<Customer>** -Elements und seines untergeordneten Elements verwiesen wird **\<Order>** , wird daher ein Präfix angegeben, das dem Ziel Namespace zugeordnet ist.  
  
-   Das- **\<Customer>** Element ist auch im Ziel Namespace des Schemas enthalten, da es sich um ein globales Element im Schema handelt.  
  
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
  
 Dieses Instanzdokument definiert den urn: MyNamespace-Namespace und ordnet ihm ein Präfix (y0) zu. Das-Präfix wird nur auf das **\<Customer>** globale-Element angewendet. (Das-Element ist Global, da es als untergeordnetes Element des- **\<xsd:schema>** Elements im Schema deklariert ist.)  
  
 Das-Präfix wird nicht auf die lokalen Elemente und Attribute angewendet, da der Wert der Attribute **Element Form default** und **attributeFormDefault** im Schema auf **"nicht qualifiziert"** festgelegt ist. Beachten Sie, dass das- **\<Order>** Element lokal ist, da seine Deklaration als untergeordnetes Element des-Elements angezeigt wird **\<complexType>** , das das **\<CustomerType>** Element definiert. Ebenso sind die Attribute (**CustomerID**, **OrderID**und **ContactName**) lokal und nicht global.  
  
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
  
     Die XPath-Abfrage in der Vorlage gibt das- **\<Customer>** Element für den Kunden mit dem CustomerID-Wert 1 zurück. Beachten Sie, dass die XPath-Abfrage das Namespace-Präfix für das Element, nicht für das Attribut, in der Abfrage festlegt. (Lokale Attribute sind nicht qualifiziert, wie im Schema angegeben.)  
  
     Der für das Zuordnungsschema (targetNameSpace.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert ist. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\targetNamepsace.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML-Abfragen](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Wenn das Schema die Attribute **Element Form default** und **attributeFormDefault** mit dem Wert **"qualified"** angibt, werden für das Instanzdokument alle lokalen Elemente und Attribute qualifiziert. Sie können das vorherige Schema so ändern, dass diese Attribute im **\<xsd:schema>** -Element enthalten sind, und die Vorlage erneut ausführen. Da die Attribute nun auch in der Instanz qualifiziert sind, ändert sich die XPath-Abfrage so, dass auch das Namespace-Präfix enthalten ist.  
  
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
  
  
