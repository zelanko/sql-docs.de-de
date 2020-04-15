---
title: Aufrufen von SQLSetPos | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 46cfbb4e2e6b60f620cd7e38272bf9308ece91bc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306241"
---
# <a name="calling-sqlsetpos"></a>Aufrufen von SQLSetPos
In ODBC *2.x*war der Zeiger auf das Zeilenstatusarray ein Argument für **SQLExtendedFetch**. Das Zeilenstatusarray wurde später durch einen Aufruf von **SQLSetPos**aktualisiert. Einige Treiber haben sich auf die Tatsache verlassen, dass sich dieses Array nicht zwischen **SQLExtendedFetch** und **SQLSetPos**ändert. In ODBC *3.x*ist der Zeiger auf das Statusarray ein Deskriptorfeld, und daher kann die Anwendung es leicht ändern, um auf ein anderes Array zu verweisen. Dies kann ein Problem sein, wenn eine ODBC *3.x-Anwendung* mit einem ODBC *2.x-Treiber* arbeitet, aber **SQLSetStmtAttr** aufruft, um den Arraystatuszeiger festzulegen, und **SQLFetchScroll** aufruft, um Daten abzurufen. Der Treiber-Manager ordnet sie als eine Folge von Aufrufen an **SQLExtendedFetch**zu. Im folgenden Code wird normalerweise ein Fehler ausgelöst, wenn der Treiber-Manager den zweiten **SQLSetStmtAttr-Aufruf** bei der Arbeit mit einem ODBC *2.x-Treiber* zuordnet:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 Der Fehler würde ausgelöst, wenn es keine Möglichkeit gäbe, den Zeilenstatuszeiger in ODBC *2.x* zwischen Aufrufen von **SQLExtendedFetch**zu ändern. Stattdessen führt der Treiber-Manager die folgenden Schritte aus, wenn er mit einem ODBC *2.x-Treiber* arbeitet:  
  
1.  Initialisiert ein internes Driver Manager-Flag *fSetPosError* in TRUE.  
  
2.  Wenn eine Anwendung **SQLFetchScroll**aufruft, legt der Treiber-Manager *fSetPosError* auf FALSE fest.  
  
3.  Wenn die Anwendung **SQLSetStmtAttr** aufruft, um SQL_ATTR_ROW_STATUS_PTR festzulegen, legt der Treiber-Manager *fSetPosError* gleichTRUE fest.  
  
4.  Wenn die Anwendung **SQLSetPos**aufruft, wobei *fSetPosError* gleich TRUE ist, löst der Treiber-Manager SQL_ERROR mit SQLSTATE HY011 (Attribut kann jetzt nicht festgelegt werden) aus, um anzugeben, dass die Anwendung versucht hat, **SQLSetPos** aufzurufen, nachdem sie den Zeilenstatuszeiger geändert hat, aber vor dem Aufruf von **SQLFetchScroll**.
