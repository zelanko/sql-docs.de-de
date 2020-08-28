---
description: Verwenden eines Recordset-Objekts
title: Verwenden eines Recordset-Objekts | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 01c630d8-eb35-4bd0-a99f-7c0f85316cc1
author: rothja
ms.author: jroth
ms.openlocfilehash: a9f75190ae5375b357d6baba93aac7aa2959e188
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979101"
---
# <a name="using-a-recordset-object"></a>Verwenden eines Recordset-Objekts
Alternativ können Sie " **Recordset. Open** " verwenden, um implizit eine Verbindung herzustellen und in einem einzelnen Vorgang einen Befehl über diese Verbindung auszugeben. Beispielsweise in Visual Basic:  
  
```  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
Dim sSQL as String  
  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
  
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " & _  
             "FROM Products"  
  
' Create and Open the Recordset object.  
Set oRs = New ADODB.Recordset  
oRs.CursorLocation = adUseClient  
oRs.Open sSQL, sConn, adOpenStatic, _  
               adLockBatchOptimistic, adCmdText  
  
MsgBox oRs.RecordCount  
  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
oRs.Close          
Set oRs = Nothing  
```  
  
 Beachten Sie, dass **ORS. Open** eine Verbindungs Zeichenfolge (*sConn*) anstelle eines **Verbindungs** Objekts (*oconn*) als Wert des **ActiveConnection** -Parameters verwendet. Außerdem wird der Client seitige Cursortyp erzwungen, indem die **CursorLocation** -Eigenschaft für das **Recordset** -Objekt festgelegt wird. Vergleichen Sie dies wieder mit dem **HelloData** -Beispiel.
