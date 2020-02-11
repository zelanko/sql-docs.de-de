---
title: Ausführen von Vorlagen, die XPath-Abfragen enthalten (SQLXMLOLEDB-Anbieter) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing template files
- Base Path property
- templates [SQLXML], XPath queries
- XPath queries [SQLXML], templates
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- Mapping Schema property
- XML templates [SQLXML]
ms.assetid: 7368c188-607e-459e-8254-8f23352dfa01
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9c4b5d51597f41b5355acd4995aaf7f988ed53a5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013091"
---
# <a name="executing-templates-that-contain-xpath-queries-sqlxmloledb-provider"></a>Ausführen von Vorlagen, die XPath-Abfragen enthalten (SQLXMLOLEDB-Anbieter)
  In diesem Beispiel wird gezeigt, wie die folgenden für den SQLXMLOLEDB-Anbieter spezifischen Eigenschaften verwendet werden:  
  
-   ClientSideXML  
  
-   Basispfad  
  
-   Zuordnungsschema  
  
 In dieser ADO-Beispielanwendung wird eine XML-Vorlage, die aus einer XPath-Abfrage (root) besteht, für das XSD-Zuordnungsschema (MySchema. Xml) angegeben, das unter [Ausführen von XPath-Abfragen &#40;SQLXMLOLEDB-Anbieter&#41;](executing-xpath-queries-sqlxmloledb-provider.md)beschrieben wird.  
  
 Die Mapping-Schema Eigenschaft stellt das XSD-Zuordnungsschema bereit, für das die XPath-Abfrage ausgeführt wird. Die Eigenschaft Basispfad stellt den Dateipfad zum Zuordnungsschema bereit.  
  
 Die ClientSideXML-Eigenschaft ist auf true festgelegt. Deshalb wird das XML-Dokument auf dem Client generiert.  
  
 In der Anwendung wird eine XPath-Abfrage direkt angegeben. Daher muss der Dialekt {5d531cb2-e6ed-11d2-b252-00c04f681b71} eingeschlossen sein.  
  
> [!NOTE]  
>  Im Code müssen Sie den Namen der Instanz von Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Verbindungszeichenfolge bereitstellen. In diesem Beispiel wird überdies die Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) als Datenanbieter beschrieben, was die Installation zusätzlicher Netzwerkclientsoftware erforderlich macht. Weitere Informationen finden Sie unter [System Anforderungen für SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).  
  
```  
Option Explicit  
Sub Main()  
  
   Dim oTestStream As New ADODB.Stream  
   Dim oTestConnection As New ADODB.Connection  
   Dim oTestCommand As New ADODB.Command  
  
   oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
  
   oTestCommand.ActiveConnection = oTestConnection  
   oTestCommand.Properties("ClientSideXML") = "False"  
  
   oTestCommand.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'> " & _  
        " <sql:xpath-query mapping-schema='mySchema.xml' > " & _  
        "   root " & _  
        "   </sql:xpath-query> " & _  
        " </ROOT> "  
   oTestStream.Open  
   ' You need the dialect if you are executing a template.  
   oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
   oTestCommand.Properties("Output Stream").Value = oTestStream  
   oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\TemplateWithXPath\"  
   oTestCommand.Properties("Mapping Schema").Value = "mySchema.xml"  
   oTestCommand.Properties("Output Encoding") = "utf-8"  
   oTestCommand.Execute , , adExecuteStream  
   oTestStream.Position = 0  
   oTestStream.Charset = "utf-8"  
   Debug.Print oTestStream.ReadText(adReadAll)  
  
End Sub  
  
Sub Form_Load()  
   Main  
End Sub  
```  
  
 Das ist das Schema:  
  
```  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
   xmlns:sql='urn:schemas-microsoft-com:mapping-schema'>  
 <xsd:element name= 'root' sql:is-constant='1'>   
    <xsd:complexType>  
       <xsd:sequence>  
         <xsd:element ref = 'Contact'/>  
       </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
  
  <xsd:element name='Contact' sql:relation='Person.Contact'>  
     <xsd:complexType>  
          <xsd:attribute name='ContactID' type='xsd:integer' />  
          <xsd:attribute name='FirstName' type='xsd:string'/>   
          <xsd:attribute name='LastName' type='xsd:string' />   
     </xsd:complexType>  
   </xsd:element>  
</xsd:schema>  
```  
  
  
