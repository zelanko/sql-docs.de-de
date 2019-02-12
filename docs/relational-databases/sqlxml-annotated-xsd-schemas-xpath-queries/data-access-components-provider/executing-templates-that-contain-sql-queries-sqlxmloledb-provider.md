---
title: Ausführen von Vorlagen, die SQL-Abfragen (SQLXMLOLEDB-Anbieter) enthalten. | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- templates [SQLXML]
- SQLXMLOLEDB Provider, executing template files
- templates [SQLXML], SQL queries
- XML templates [SQLXML]
- SQL queries [SQLXML]
ms.assetid: ff2bc36f-e3fb-4d8f-8e3a-2680a39eda11
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 93553959d6a9bc10933b6612c64499bb73c2a475
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56022941"
---
# <a name="executing-templates-that-contain-sql-queries-sqlxmloledb-provider"></a>Ausführen von Vorlagen, die SQL-Abfragen enthalten (SQLXMLOLEDB-Anbieter)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Dieses Beispiel veranschaulicht die Verwendung der SQLXMLOLEDB-Anbieter spezifischen ClientSideXML-Eigenschaft. In dieser clientseitigen ADO-Beispielanwendung wird eine XML-Vorlage, die aus einer einfachen SQL-Abfrage besteht, auf dem Server ausgeführt.  
  
 Da die ClientSideXML-Eigenschaft auf "true" festgelegt ist, wird die SELECT-Anweisung ohne die FOR XML-Klausel an den Server gesendet. Der Server führt die Abfrage aus und gibt ein Rowset an den Client zurück. Der Client wendet dann die FOR XML-Transformation auf das Rowset an und generiert ein XML-Dokument.  
  
 Die XML-Vorlage stellt ein einzelnes Stammelement für der obersten Ebene (\<ROOT >) für die XML-Dokument, das generiert wird; daher wird die XML-Stammeigenschaft nicht bereitgestellt.  
  
 Zum Ausführen der XML-Vorlagen muss der Dialekt {5d531cb2-e6ed-11d2-b252-00c04f681b71} angegeben werden.  
  
> [!NOTE]  
>  Im Code müssen Sie den Namen der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Verbindungszeichenfolge bereitstellen. In diesem Beispiel wird überdies die Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) als Datenanbieter beschrieben, was die Installation zusätzlicher Netzwerkclientsoftware erforderlich macht. Weitere Informationen finden Sie unter [Systemanforderungen für SQL Server Native Client](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md).  
  
```  
Option Explicit  
  
Sub Main()  
  Dim oTestStream As New ADODB.Stream  
  Dim oTestConnection As New ADODB.Connection  
  Dim oTestCommand As New ADODB.Command  
  oTestConnection.Open "Provider=SQLXMLOLEDB.4.0;Data Provider=SQLNCLI11;Data Source=SqlServerName;Initial Catalog=AdventureWorks;Integrated Security=SSPI;"  
  
  Set oTestCommand.ActiveConnection = oTestConnection  
  oTestCommand.Properties("ClientSideXML") = True  
  oTestCommand.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'> " & _  
        " <sql:query> " & _  
        "   SELECT TOP 10 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
  oTestStream.Open  
  ' You need the dialect if you are executing   
  ' XML templates (not for SQL queries).  
  oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
  oTestCommand.Properties("Output Stream").Value = oTestStream  
  oTestCommand.Execute , , adExecuteStream  
  
  oTestStream.Position = 0  
  oTestStream.Charset = "utf-8"  
  Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
  
Sub Form_Load()  
  Main  
End Sub  
```  
  
  
