---
title: Bindungsparameter ODBC | Microsoft Docs
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
ms.openlocfilehash: 6e314bb9e3a1a979976a450e2a45a286ec54dfe7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306381"
---
# <a name="binding-parameters-odbc"></a>Binden von Parametern (ODBC)
Jeder Parameter in einer SQL-Anweisung muss einer Variablen in der Anwendung zugeordnet oder *gebunden werden,* bevor die Anweisung ausgeführt wird. Wenn die Anwendung eine Variable an einen Parameter bindet, wird diese Variable - Adresse, C-Datentyp usw. - an den Treiber beschrieben. Außerdem wird der Parameter selbst beschrieben - SQL-Datentyp, Genauigkeit usw. Der Treiber speichert diese Informationen in der Struktur, die er für diese Anweisung verwaltet, und verwendet die Informationen, um den Wert aus der Variablen abzurufen, wenn die Anweisung ausgeführt wird.  
  
 Parameter können jederzeit gebunden oder zurückgeprallt werden, bevor eine Anweisung ausgeführt wird. Wenn ein Parameter zurückerprobt wird, nachdem eine Anweisung ausgeführt wurde, wird die Bindung erst angewendet, wenn die Anweisung erneut ausgeführt wird. Um einen Parameter an eine andere Variable zu binden, bindet eine Anwendung den Parameter einfach erneut an die neue Variable. die vorherige Bindung wird automatisch freigegeben.  
  
 Eine Variable bleibt an einen Parameter gebunden, bis eine andere Variable an den Parameter gebunden ist, bis alle Parameter durch Aufrufen von **SQLFreeStmt** mit der Option SQL_RESET_PARAMS oder bis die Anweisung freigegeben wird. Aus diesem Grund muss die Anwendung sicherstellen, dass Variablen erst freigegeben werden, nachdem sie ungebunden sind. Weitere Informationen finden Sie unter [Zuweisen und Verteilen von Puffern](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Da Parameterbindungen nur Informationen sind, die in der Vom Treiber für die Anweisung verwalteten Struktur gespeichert werden, können sie in beliebiger Reihenfolge festgelegt werden. Sie sind auch unabhängig von der SQL-Anweisung, die ausgeführt wird. Angenommen, eine Anwendung bindet drei Parameter und führt dann die folgende SQL-Anweisung aus:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Wenn die Anwendung dann sofort die SQL-Anweisung  
  
```  
SELECT * FROM Orders WHERE OrderID = ?, OpenDate = ?, Status = ?  
```  
  
 für dasselbe Anweisungshandle werden die Parameterbindungen für die **INSERT-Anweisung** verwendet, da dies die bindungen sind, die in der Anweisungsstruktur gespeichert sind. In den meisten Fällen ist dies eine schlechte Programmierpraxis und sollte vermieden werden. Stattdessen sollte die Anwendung **SQLFreeStmt** mit der SQL_RESET_PARAMS Option aufrufen, um alle alten Parameter zu binden und dann neue zu binden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Binden von Parametermarkern](../../../odbc/reference/develop-app/binding-parameter-markers.md)  
  
-   [Binden von Parametern anhand des Namens (benannte Parameter)](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)  
  
-   [Offsets der Parameterbindung](../../../odbc/reference/develop-app/parameter-binding-offsets.md)  
  
-   [Beschreiben von Parametern](../../../odbc/reference/develop-app/describing-parameters.md)
