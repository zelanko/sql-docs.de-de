---
title: Empfangen von mehreren Recordsets | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 12aa80b918d11dad07119a26da3da8f27ef82cdb
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759106"
---
# <a name="receiving-multiple-recordsets"></a>Empfangen von mehreren Recordsets
Der [Microsoft OLE DB-Anbieter für SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) unterstützt die Rückgabe mehrerer **Recordset** -Objekte für einen einzelnen Befehl, der mehrere SQL-Anweisungen enthält, ein **Recordset** pro SQL-Anweisung. Die Reihenfolge, in der die **Recordsets**zurückgegeben werden, folgt der Reihenfolge, in der die SQL-Anweisungen in den Befehls Text eingefügt werden.  
  
 Der Microsoft OLE DB-Anbieter für SQL Server gibt auch mehrere Resultsets an ADO zurück, wenn der Befehl eine COMPUTE-Klausel enthält. Beispielsweise gibt ein Befehl, der die folgende SQL-Anweisung enthält, die Ergebnisse in zwei **Recordset** -Objekten zurück: eine für das Rowset von (*ProductID*, *ProductName*, *UnitPrice*) und die andere für den Durchschnittspreis aller Produkte in der Tabelle.  
  
```  
SELECT ProductID, ProductName, UnitPrice   
  FROM PRODUCTS   
  COMPUTE AVG(UnitPrice)  
```  
  
 Sie können die **Recordset. NextRecordset** -Methode verwenden, um die beiden-Objekte aufzulisten.  
  
 Weitere Informationen finden Sie unter [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md).
