---
title: Ausführen von Vorlagen mit SQL-Abfragen (SQLXMLOLEDB)
description: Sehen Sie sich ein Beispiel für eine Client seitige ADO-Anwendung an, die den SQLXMLOLEDB-Anbieter verwendet, um eine serverseitige XML-Vorlage mit einer SQL-Abfrage auszuführen.
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
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 82f770d8b17ee1ec93e33efa07b6658363b0de2d
ms.sourcegitcommit: 9921501952147b9ce3e85a1712495d5b3eb13e5b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2020
ms.locfileid: "84215658"
---
# <a name="executing-templates-that-contain-sql-queries-sqlxmloledb-provider"></a>Ausführen von Vorlagen, die SQL-Abfragen enthalten (SQLXMLOLEDB-Anbieter)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Dieses Beispiel veranschaulicht die Verwendung der anbieterspezifischen SQLXMLOLEDB-Eigenschaft ClientSideXML. In dieser clientseitigen ADO-Beispielanwendung wird eine XML-Vorlage, die aus einer einfachen SQL-Abfrage besteht, auf dem Server ausgeführt.  
  
 Da die ClientSideXML-Eigenschaft auf true festgelegt ist, wird die SELECT-Anweisung ohne die for XML-Klausel an den Server gesendet. Der Server führt die Abfrage aus und gibt ein Rowset an den Client zurück. Der Client wendet dann die FOR XML-Transformation auf das Rowset an und generiert ein XML-Dokument.  
  
 Die XML-Vorlage stellt ein einzelnes Stamm Element der obersten Ebene ( \<ROOT> ) für das generierte XML-Dokument bereit. Daher wird die XML-Stamm Eigenschaft nicht bereitgestellt.  
  
 Zum Ausführen der XML-Vorlagen muss der Dialekt {5d531cb2-e6ed-11d2-b252-00c04f681b71} angegeben werden.  
  
> [!NOTE]  
>  Im Code müssen Sie den Namen der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in der Verbindungszeichenfolge bereitstellen. In diesem Beispiel wird überdies die Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) als Datenanbieter beschrieben, was die Installation zusätzlicher Netzwerkclientsoftware erforderlich macht. Weitere Informationen finden Sie unter [System Anforderungen für SQL Server Native Client](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md).  
  
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
  
  
