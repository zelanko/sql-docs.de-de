---
description: Cursoreigenschaften und Cursortyp
title: Cursor Merkmale und Cursortyp | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: 6f67edd2-ae71-4ca0-9b2d-abf4c20dc17b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10ec9c7fc42ad20ce0a5a6d70ef4a2a692afbec3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429422"
---
# <a name="cursor-characteristics-and-cursor-type"></a>Cursoreigenschaften und Cursortyp
Eine Anwendung kann die Merkmale eines Cursors angeben, anstatt den Cursortyp anzugeben (vorwärts, statisch, keysetgesteuert oder dynamisch). Hierzu wählt die Anwendung die Scrollbarkeit des Cursors (durch Festlegen des Attributs der SQL_ATTR_CURSOR_SCROLLABLE Anweisung) und die Empfindlichkeit (durch Festlegen des Attributs der SQL_ATTR_CURSOR_SENSITIVITY Anweisung) vor dem Öffnen des Cursors auf dem Anweisungs Handle aus. Der Treiber wählt dann den Cursortyp aus, der die von der Anwendung angeforderten Merkmale am effizientesten bereitstellt.  
  
 Wenn eine Anwendung eines der Anweisungs Attribute SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY oder SQL_ATTR_CURSOR_TYPE festlegt, führt der Treiber alle erforderlichen Änderungen an den anderen Anweisungs Attributen in diesem Satz von vier Attributen aus, damit ihre Werte konsistent bleiben. Wenn die Anwendung also ein Cursor Merkmal angibt, kann der Treiber das Attribut, das den Cursortyp angibt, basierend auf dieser impliziten Auswahl ändern. Wenn die Anwendung einen Typ angibt, kann der Treiber alle anderen Attribute ändern, damit Sie mit den Merkmalen des ausgewählten Typs konsistent sind. Weitere Informationen zu diesen Anweisungs Attributen finden Sie in der Beschreibung der [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) -Funktion.  
  
 Eine Anwendung, in der Anweisungs Attribute festgelegt werden, um sowohl einen Cursortyp als auch Cursor Merkmale anzugeben, birgt das Risiko, dass ein Cursor erhalten wird, der nicht die effizienteste Methode für diesen Treiber ist, um die Anforderungen der Anwendung zu erfüllen.  
  
 Die implizite Einstellung der Anweisungs Attribute ist Treiber definiert, mit dem Unterschied, dass Sie die folgenden Regeln einhalten muss:  
  
-   Vorwärts Cursor können niemals scrollfähig sein. Weitere Informationen finden Sie in der Definition von SQL_ATTR_CURSOR_SCROLLABLE in [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
-   Unempfindliche Cursor können nie aktualisiert werden (und somit ist Ihre Parallelität schreibgeschützt). Dies basiert auf der Definition von unsensiblen Cursorn im ISO-SQL-Standard.  
  
 Folglich erfolgt die implizite Einstellung der Anweisungs Attribute in den in der folgenden Tabelle beschriebenen Fällen.  
  
|Anwendungs Satz Attribut auf|Andere Attribute implizit festgelegt|  
|-----------------------------------|-------------------------------------|  
|SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY|SQL_ATTR_CURSOR_SENSITIVITY SQL_INSENSITIVE.|  
|SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES|SQL_ATTR_CURSOR_SENSITIVITY SQL_UNSPECIFIED oder SQL_SENSITIVE, wie vom Treiber definiert. Sie kann nie auf SQL_INSENSITIVE festgelegt werden, da unempfindliche Cursor immer schreibgeschützt sind.|  
|SQL_ATTR_CURSOR_SCROLLABLE SQL_NONSCROLLABLE|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE SQL_SCROLLABLE|SQL_ATTR_CURSOR_TYPE auf SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN oder SQL_CURSOR_DYNAMIC, wie vom Treiber angegeben. Es ist nie auf SQL_CURSOR_FORWARD_ONLY festgelegt.|  
|SQL_ATTR_CURSOR_SENSITIVITY SQL_INSENSITIVE|SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC.|  
|SQL_ATTR_CURSOR_SENSITIVITY SQL_SENSITIVE|SQL_ATTR_CONCURRENCY auf SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES, wie vom Treiber angegeben. Es ist nie auf SQL_CONCUR_READ_ONLY festgelegt.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN oder SQL_CURSOR_DYNAMIC, wie vom Treiber angegeben.|  
|SQL_ATTR_CURSOR_SENSITIVITY SQL_UNSPECIFIED|SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY, SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES, wie vom Treiber angegeben.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN oder SQL_CURSOR_DYNAMIC, wie vom Treiber angegeben.|  
|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_DYNAMIC|SQL_ATTR_SCROLLABLE SQL_SCROLLABLE.<br /><br /> SQL_ATTR_CURSOR_SENSITIVITY SQL_SENSITIVE. (Jedoch nur, wenn SQL_ATTR_CONCURRENCY nicht gleich SQL_CONCUR_READ_ONLY ist. Aktualisierbare dynamische Cursor sind immer sensibel für Änderungen, die in ihrer eigenen Transaktion vorgenommen wurden.)|  
|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY|SQL_ATTR_CURSOR_SCROLLABLE SQL_NONSCROLLABLE.|  
|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_KEYSET_DRIVEN|SQL_ATTR_SCROLLABLE SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED oder SQL_SENSITIVE (gemäß den vom Treiber definierten Kriterien, wenn SQL_ATTR_CONCURRENCY nicht SQL_CONCUR_READ_ONLY ist).|  
|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC|SQL_ATTR_SCROLLABLE SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY SQL_INSENSITIVE (wenn SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY).<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED oder SQL_SENSITIVE (wenn SQL_ATTR_CONCURRENCY nicht SQL_CONCUR_READ_ONLY ist).|
