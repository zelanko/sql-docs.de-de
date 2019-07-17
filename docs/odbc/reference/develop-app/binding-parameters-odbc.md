---
title: Binden von Parametern ODBC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- binding parameters [ODBC]
ms.assetid: 7538a82b-b08b-4c8f-9809-e4ccea16db11
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1bc40d4800e7cd013b7ac908400c0492286314e3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68107633"
---
# <a name="binding-parameters-odbc"></a>Binden von Parametern (ODBC)
Jeden Parameter in einer SQL-Anweisung muss zugeordnet ist, oder *gebunden,* auf eine Variable in der Anwendung, bevor die Anweisung ausgeführt wird. Wenn die Anwendung eine Variable einem Parameter bindet, beschreibt es die Variable - Adresse, C-Datentyp und So weiter – an den Treiber. Außerdem wird den Parameter selbst - SQL-Datentyp, Genauigkeit und So weiter erläutert. Der Treiber speichert diese Informationen in der Struktur, die sie für diese Anweisung verwaltet und verwendet die Informationen zum Abrufen des Werts aus der Variablen ein, wenn die Anweisung ausgeführt wird.  
  
 Parameter können gebunden oder erneut vor einer Anweisung jederzeit gebunden werden. Wenn ein Parameter neu gebunden wird, nachdem eine Anweisung ausgeführt wird, gilt die Bindung nicht erst die Anweisung erneut ausgeführt wird. Um einen Parameter an eine andere Variable binden, erneuerte Bindungen eine Anwendung einfach auf den Parameter mit der neuen Variablen; die vorherige Bindung wird automatisch freigegeben.  
  
 Eine Variable an Parameter gebunden bleibt, bis eine andere Variable an den Parameter gebunden ist, bis alle Parameter durch Aufrufen von nicht gebundenen sind **SQLFreeStmt** mit der Option SQL_RESET_PARAMS oder bis die Anweisung aufgehoben wird. Aus diesem Grund muss die Anwendung darauf achten, dass die Variablen nicht erst freigegeben werden, nachdem diese aufgehoben wurden. Weitere Informationen finden Sie unter [zuweisen und Freigeben von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Da parameterbindungen nur Informationen, die in der Struktur, die vom Treiber für die Anweisung verwaltet gespeichert sind, können sie in beliebiger Reihenfolge festgelegt werden. Sie sind auch unabhängig von der SQL-Anweisung, die ausgeführt wird. Nehmen wir beispielsweise an eine Anwendung drei Parameter gebunden, und klicken Sie dann die folgende SQL-Anweisung ausführt:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Wenn die Anwendung dann sofort die SQL-Anweisung ausgeführt wird  
  
```  
SELECT * FROM Orders WHERE OrderID = ?, OpenDate = ?, Status = ?  
```  
  
 über das Anweisungshandle die parameterbindungen für die **einfügen** Anweisung werden verwendet, da dies die Bindungen in der Anweisung Struktur gespeichert sind. In den meisten Fällen Dies ist eine schlechte Programmiermethode und sollte vermieden werden. Stattdessen sollte die Anwendung aufrufen **SQLFreeStmt** mit der SQL_RESET_PARAMS-Option zum Aufheben der Bindung alle alten Parameter, und dann binden Sie neue.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Binden von Parametermarkierungen](../../../odbc/reference/develop-app/binding-parameter-markers.md)  
  
-   [Binden von Parametern anhand des Namens (benannte Parameter)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)  
  
-   [Offsets der Parameterbindung](../../../odbc/reference/develop-app/parameter-binding-offsets.md)  
  
-   [Describing Parameters (Beschreiben von Parametern)](../../../odbc/reference/develop-app/describing-parameters.md)
