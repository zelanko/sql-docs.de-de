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
ms.openlocfilehash: c64575777fc9210c36be5d417cd3def0c2c7102a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068684"
---
# <a name="calling-sqlsetpos"></a>Aufrufen von SQLSetPos
In ODBC *2. x*war der Zeiger auf das Zeilen Status Array ein Argument für **SQLExtendedFetch**. Das Zeilen Status Array wurde später durch einen-Befehl von **SQLSetPos**aktualisiert. Einige Treiber haben sich darauf verlassen, dass sich dieses Array zwischen **sqlextende** und **SQLSetPos**nicht ändert. In ODBC *3. x*ist der Zeiger auf das Status Array ein Deskriptorfeld, und die Anwendung kann Sie problemlos so ändern, dass Sie auf ein anderes Array verweist. Dies kann ein Problem darstellen, wenn eine ODBC *3. x* -Anwendung mit einem ODBC *2. x* -Treiber arbeitet, aber **SQLSetStmtAttr** aufruft, um den Array Status Zeiger festzulegen, und **SQLFetchScroll** zum Abrufen von Daten aufruft. Der Treiber-Manager ordnet ihn als Sequenz von Aufrufen von **SQLExtendedFetch**zu. Im folgenden Code wird normalerweise ein Fehler ausgelöst, wenn der Treiber-Manager beim Arbeiten mit einem ODBC *2. x* -Treiber den zweiten **SQLSetStmtAttr** -Befehl zuordnet:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 Der Fehler wird ausgelöst, wenn es keine Möglichkeit gab, den Zeilen Status Zeiger in ODBC *2. x* zwischen den Aufrufen von **SQLExtendedFetch**zu ändern. Stattdessen führt der Treiber-Manager bei der Arbeit mit einem ODBC *2. x* -Treiber die folgenden Schritte aus:  
  
1.  Initialisiert ein internes Treiber-Manager-Flag *fsetposerror* auf true.  
  
2.  Wenn eine Anwendung **SQLFetchScroll**aufruft, legt der Treiber-Manager *fsetposerror* auf false fest.  
  
3.  Wenn die Anwendung **SQLSetStmtAttr** aufruft, um SQL_ATTR_ROW_STATUS_PTR festzulegen, legt der Treiber-Manager *fsetposerror* auf den Wert "detrue" fest.  
  
4.  Wenn die Anwendung **SQLSetPos**aufruft, wobei *fsetposerror* gleich true ist, löst der Treiber-Manager SQL_ERROR mit SQLState HY011 (das Attribut kann jetzt nicht festgelegt werden) aus, um anzugeben, dass die Anwendung versucht hat, **SQLSetPos** nach dem Ändern des Zeilen Status Zeigers, aber vor dem Aufrufen von **SQLFetchScroll**aufzurufen.
