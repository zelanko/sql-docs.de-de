---
title: Verwenden eines Verbindungsobjekts | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 4b34f971-5699-43e7-9b15-137d334fa66e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4f1b867e1870b81641c7cea09d9a8fb3accfcc01
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67923645"
---
# <a name="using-a-connection-object"></a>Verwenden eines Connection-Objekts
Vor dem Öffnen einer **Verbindung** Objekt ist, müssen Sie bestimmte Informationen über die Datenquelle und die Art von Verbindung definieren. Frei, die meisten dieser Informationen wird die *"ConnectionString"* Parameter der [Open-Methode](../../../ado/reference/ado-api/open-method-ado-connection.md) auf die **Verbindung** -Objekt, oder durch die ["ConnectionString" Eigenschaft](../../../ado/reference/ado-api/connectionstring-property-ado.md) auf die **Verbindung** Objekt. Eine Verbindungszeichenfolge besteht aus einer Liste von Argument-Wert-Paaren, die getrennt durch Semikolons getrennt, mit den Werten, die in einfache Anführungszeichen eingeschlossen. Zum Beispiel:  
  
```  
Dim sConn As String  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
```  
  
> [!NOTE]
>  Sie können auch eine ODBC Data Datenquellennamen (DSN) oder eine Data Link (UDL)-Datei in einer Verbindungszeichenfolge angeben. Weitere Informationen zu DSNs, finden Sie unter [Datenquellen verwalten](../../../odbc/admin/managing-data-sources.md) in der ODBC Programmer's Reference. Weitere Informationen zu UDLs, finden Sie unter [Data Link-API – Übersicht](https://msdn.microsoft.com/95c180ea-bd4f-4dca-b95a-576afd135bbc) in der OLE DB Programmer's Reference.  
  
 In der Regel Herstellen einer Verbindung durch Aufrufen der **Connection.Open** Methode mit einem entsprechenden eine *Verbindungszeichenfolge* als Parameter. Ein Beispiel ist in den folgenden Visual Basic-Codeausschnitt gezeigt:  
  
```  
Dim oConn As ADODB.Connection  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
Dim sSQL as String  
  
' Open a connection.  
Set oConn = New ADODB.Connection  
.Open   
  
' Make a query over the connection.  
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " & _  
             "FROM Products"  
Set oRs = New ADODB.Recordset  
oRs.Open sSQL, , adOpenStatic, adLockBatchOptimistic, adCmdText  
  
MsgBox oRs.RecordCount  
  
' Close the connection.  
oConn.Close  
Set oConn = Nothing  
  
```  
  
 Hier **oRs.Open** nimmt eine **Verbindung** Objekt (*oConn*) als Wert der Variablen der *ActiveConnection* Parameter. Darüber hinaus die **Connection.CursorLocation** Eigenschaft geht davon aus, der Standardwert von **AdUseServer**. Vergleichen Sie diese Option, um die [HelloData](../../../ado/guide/data/hellodata-a-simple-ado-application.md) Beispiel im vorherigen Abschnitt. Die folgende Anweisung führt zu Laufzeitfehlern führen.  
  
```  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
```
