---
description: Binden von Parametern (ODBC)
title: Bindungs Parameter ODBC | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9893d6611ad2bfc7107df1cd2d4ffe72dbf32fad
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499953"
---
# <a name="binding-parameters-odbc"></a>Binden von Parametern (ODBC)
Jeder Parameter in einer SQL-Anweisung muss einer Variablen in der Anwendung zugeordnet oder *gebunden* werden, bevor die Anweisung ausgeführt wird. Wenn die Anwendung eine Variable an einen Parameter bindet, wird die Variable-Address, der C-Datentyp usw. für den Treiber beschrieben. Außerdem wird der Parameter selbst-SQL-Datentyp, Genauigkeit usw. beschrieben. Der Treiber speichert diese Informationen in der Struktur, die er für diese Anweisung verwaltet, und verwendet die Informationen, um den Wert aus der Variablen abzurufen, wenn die Anweisung ausgeführt wird.  
  
 Parameter können jederzeit vor der Ausführung einer-Anweisung gebunden oder erneut gebunden werden. Wenn ein Parameter nach dem Ausführen einer-Anweisung neu gebunden wird, gilt die Bindung erst, wenn die-Anweisung erneut ausgeführt wird. Um einen Parameter an eine andere Variable zu binden, bindet eine Anwendung einfach den Parameter an die neue Variable. die vorherige Bindung wird automatisch freigegeben.  
  
 Eine Variable bleibt an einen Parameter gebunden, bis eine andere Variable an den-Parameter gebunden ist, bis die Bindung aller Parameter durch Aufrufen von **SQLFreeStmt** mit der SQL_RESET_PARAMS-Option oder bis zur Freigabe der-Anweisung aufgehoben wird. Aus diesem Grund muss die Anwendung sicherstellen, dass die Variablen erst freigegeben werden, wenn die Bindung aufgehoben wurde. Weitere Informationen finden Sie unter [zuordnen und Freigeben von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Da Parameter Bindungen nur Informationen sind, die in der Struktur gespeichert sind, die vom Treiber für die-Anweisung verwaltet wird, können Sie in beliebiger Reihenfolge festgelegt werden. Sie sind auch unabhängig von der ausgeführten SQL-Anweisung. Angenommen, eine Anwendung bindet drei Parameter und führt dann die folgende SQL-Anweisung aus:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Wenn die Anwendung die SQL-Anweisung sofort ausführt  
  
```  
SELECT * FROM Orders WHERE OrderID = ?, OpenDate = ?, Status = ?  
```  
  
 beim gleichen Anweisungs Handle werden die Parameter Bindungen für die **Insert** -Anweisung verwendet, da es sich dabei um die in der Anweisungs Struktur gespeicherten Bindungen handelt. In den meisten Fällen ist dies eine schlechte Programmierpraxis und sollte vermieden werden. Stattdessen sollte die Anwendung **SQLFreeStmt** mit der SQL_RESET_PARAMS-Option aufgerufen werden, um die Bindung aller alten Parameter aufzuheben und neue zu binden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Binden von Parametermarkern](../../../odbc/reference/develop-app/binding-parameter-markers.md)  
  
-   [Binden von Parametern anhand des Namens (benannte Parameter)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)  
  
-   [Offsets der Parameterbindung](../../../odbc/reference/develop-app/parameter-binding-offsets.md)  
  
-   [Beschreiben von Parametern](../../../odbc/reference/develop-app/describing-parameters.md)
