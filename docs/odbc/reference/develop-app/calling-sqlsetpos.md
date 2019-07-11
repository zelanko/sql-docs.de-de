---
title: Aufrufen von SQLSetPos | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], calling
- upgrading applications [ODBC], SQLSetPos
- backward compatibility [ODBC], SqlSetPos
- application upgrades [ODBC], SQLSetPos
ms.assetid: 846354b8-966c-4c2c-b32f-b0c8e649cedd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f94b1191815f37728a2d8de8fc1175113644bc5a
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793890"
---
# <a name="calling-sqlsetpos"></a>Aufrufen von SQLSetPos
In ODBC *2.x*, der Zeiger auf die zeilenstatusarray wurde ein Argument für **SQLExtendedFetch**. Die zeilenstatusarray wurde durch einen Aufruf von später aktualisiert **SQLSetPos**. Einige Treiber auf die Tatsache, die dieses Array nicht zwischen ändert basierten **SQLExtendedFetch** und **SQLSetPos**. In ODBC *3.x*, der Zeiger auf die Statusarray wird einem Beschreibungsfeld und aus diesem Grund die Anwendung kann ganz einfach ändern, damit auf ein anderes Array zu verweisen. Dies liegt möglicherweise ein Problem bei der Verwendung einer ODBC *3.x* mit einer ODBC-Anwendung funktioniert *2.x* Treiber jedoch ist der Aufruf **SQLSetStmtAttr** der Zeiger für den arraystatus festgelegt und ist der Aufruf  **SQLFetchScroll** zum Abrufen von Daten. Der Treiber-Manager wird es als eine Sequenz von Aufrufen an zugeordnet **SQLExtendedFetch**. Im folgenden Code wird ein Fehler würde normalerweise ausgelöst, wenn der Treiber-Manager das zweite entspricht **SQLSetStmtAttr** bei der Arbeit mit einer ODBC-aufrufen *2.x* Treiber:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 Der Fehler wird ausgelöst, wenn gab es keine Möglichkeit, ändern den Status Zeilenzeiger in ODBC *2.x* zwischen den Aufrufen **SQLExtendedFetch**. Stattdessen führt der Treiber-Manager die folgenden Schritte aus, bei der Arbeit mit einer ODBC- *2.x* Treiber:  
  
1.  Initialisiert ein internes-Treiber-Manager-Flag *fSetPosError* auf "true".  
  
2.  Wenn eine Anwendung ruft **SQLFetchScroll**, legt der Treiber-Manager *fSetPosError* auf "false".  
  
3.  Wenn die Anwendung ruft **SQLSetStmtAttr** um SQL_ATTR_ROW_STATUS_PTR festzulegen, legt der Treiber-Manager *fSetPosError* gleich ToTRUE.  
  
4.  Wenn die Anwendung ruft **SQLSetPos**, mit *fSetPosError* gleich "true", der Treiber-Manager löst SQL_ERROR mit SQLSTATE HY011 (Attribut kann nicht jetzt festgelegt werden) an, dass die Anwendung Es wurde versucht, rufen Sie **SQLSetPos** nach dem Ändern der Status der Zeilenzeiger jedoch vor dem Aufruf **SQLFetchScroll**.
