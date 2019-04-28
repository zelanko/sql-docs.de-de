---
title: Mehrere Recordsets empfangen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- receiving multiple Recordsets [ADO]
- Recordset object [ADO], receiving multiple Recordsets
ms.assetid: 2a7ad7a6-f00d-4355-b0b5-d0ab957b0566
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e70dc047456549b625a1e66250d413009293f4a0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62910819"
---
# <a name="receiving-multiple-recordsets"></a>Empfangen von mehreren Recordsets
Die [Microsoft OLE DB-Anbieter für SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) unterstützt das Zurückgeben von mehreren **Recordset** Objekte für einen einzelnen Befehl, der mehrere SQL-Anweisungen, mit einem **Recordset**pro SQL-Anweisung. Die Reihenfolge, in der **Recordset**s zurückgegeben werden, erfolgt in der Reihenfolge, in dem die SQL-Anweisungen im Befehlstext abgelegt werden.  
  
 Microsoft OLE DB-Anbieter für SQL Server gibt auch mehrere Resultsets zu ADO zurück, wenn der Befehl eine COMPUTE-Klausel enthält. Z. B. ein Befehl mit den folgenden SQL-Anweisung gibt die Ergebnisse in zwei **Recordset** Objekte: eine für das Rowset der (*"ProductID"*, *ProductName*, *UnitPrice*), und die andere für den Durchschnittspreis aller Produkte in der Tabelle.  
  
```  
SELECT ProductID, ProductName, UnitPrice   
  FROM PRODUCTS   
  COMPUTE AVG(UnitPrice)  
```  
  
 Sie können die **Recordset.NextRecordset** Methode, um die beiden Objekte aufgelistet werden.  
  
 Weitere Informationen finden Sie unter [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md).
