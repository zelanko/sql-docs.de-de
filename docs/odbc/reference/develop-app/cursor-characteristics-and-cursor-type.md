---
title: Cursoreigenschaften und Cursortyp | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dbef278f3f25b572ddc44e87d60b5cdcd33058c1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63043825"
---
# <a name="cursor-characteristics-and-cursor-type"></a>Cursoreigenschaften und Cursortyp
Eine Anwendung kann die Merkmale eines Cursors, anstatt die Cursor-Datentyp (vorwärts-, statische, keysetgesteuerte und dynamische) angeben. Zu diesem Zweck wählt die Anwendung des Cursors bildlauffähigkeit (durch Festlegen der SQL_ATTR_CURSOR_SCROLLABLE-Anweisungsattribut) und Sensitivität (durch Festlegen der SQL_ATTR_CURSOR_SENSITIVITY-Anweisungsattribut) vor dem Öffnen des Cursors in der Anweisung Handle. Klicken Sie dann wählt der Treiber dem Cursortyp, der möglichst effizient die Merkmale enthält die Anwendung angefordert.  
  
 Wenn eine Anwendung eines die Anweisungsattribute SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY oder SQL_ATTR_CURSOR_TYPE SQL_ATTR_CONCURRENCY festlegt, stellt der Treiber alle erforderlichen Änderungen, die andere Anweisungsattribute, die Sie in diesem Satz von vier Attribute, sodass ihre Werte konsistent bleiben. Daher Wenn die Anwendung ein Merkmal des Cursors angegeben ist, kann der Treiber das Attribut ändern, die basierend auf dieser Auswahl implizite Cursortyp; Wenn die Anwendung einen Typ angegeben ist, kann der Treiber die anderen Attribute konsistent mit den Eigenschaften des ausgewählten Typs ändern. Weitere Informationen zu diesen Anweisungsattribute, finden Sie unter den [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) funktionsbeschreibung.  
  
 Eine Anwendung, die Anweisungsattribute sowohl ein anderer Cursortyp als auch Cursoreigenschaften angeben, legt diese fest ausgeführt wird, das Risiko des Abrufens eines Cursors, das nicht die effizienteste Methode, die auf diesen Treiber für die Erfüllung von den Anforderungen der Anwendung verfügbar ist.  
  
 Die implizite Einstellung Anweisungsattribute ist treiberdefinierten mit dem Unterschied, dass sie die folgenden Regeln einhalten muss:  
  
-   Vorwärtscursor werden niemals bildlauffähigen; Anzeigen der Definition der SQL_ATTR_CURSOR_SCROLLABLE in [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
-   INSENSITIVE-Cursor können nie aktualisiert werden (und somit die Parallelität ist, schreibgeschützt) Dies basiert auf ihre Definition von insensitive-Cursor in der ISO SQL standard.  
  
 Daher tritt auf, die implizite Einstellung Anweisungsattribute, in den Fällen, in der folgenden Tabelle beschrieben.  
  
|Anwendung wird das Attribut auf|Andere Attribute festgelegt implizit.|  
|-----------------------------------|-------------------------------------|  
|SQL_ATTR_CONCURRENCY auf SQL_CONCUR_READ_ONLY|SQL_ATTR_CURSOR_SENSITIVITY auf SQL_INSENSITIVE.|  
|SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER, SQL_CONCUR_VALUES oder|SQL_ATTR_CURSOR_SENSITIVITY auf SQL_UNSPECIFIED oder SQL_SENSITIVE, gemäß der Treiber. Sie können nie auf SQL_INSENSITIVE, festgelegt werden, da insensitive-Cursor immer schreibgeschützt sind.|  
|SQL_ATTR_CURSOR_SCROLLABLE auf SQL_NONSCROLLABLE|SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE auf SQL_SCROLLABLE|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN oder SQL_CURSOR_DYNAMIC, wie vom Treiber angegeben. Es wird nie auf SQL_CURSOR_FORWARD_ONLY festgelegt.|  
|SQL_ATTR_CURSOR_SENSITIVITY auf SQL_INSENSITIVE|SQL_ATTR_CONCURRENCY auf SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_STATIC.|  
|SQL_ATTR_CURSOR_SENSITIVITY auf SQL_SENSITIVE|SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES, wie vom Treiber angegeben. Es wird nie auf SQL_CONCUR_READ_ONLY festgelegt.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN oder SQL_CURSOR_DYNAMIC, wie vom Treiber angegeben.|  
|SQL_ATTR_CURSOR_SENSITIVITY auf SQL_UNSPECIFIED|SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY, SQL_CONCUR_ROWVER, SQL_CONCUR_LOCK oder SQL_CONCUR_VALUES, laut der Treiber.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN oder SQL_CURSOR_DYNAMIC, wie vom Treiber angegeben.|  
|SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_DYNAMIC|SQL_ATTR_SCROLLABLE auf SQL_SCROLLABLE.<br /><br /> SQL_ATTR_CURSOR_SENSITIVITY auf SQL_SENSITIVE. (Aber nur, wenn SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY nicht entspricht. Aktualisierbare dynamic-Cursor sind immer empfindlich gegenüber Änderungen, die in ihren eigenen Transaktion vorgenommen wurden.)|  
|SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY|SQL_ATTR_CURSOR_SCROLLABLE auf SQL_NONSCROLLABLE.|  
|SQL_ATTR_CURSOR_TYPE to SQL_CURSOR_KEYSET_DRIVEN|SQL_ATTR_SCROLLABLE auf SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED oder SQL_SENSITIVE (gemäß den treiberdefinierten Kriterien, wenn SQL_ATTR_CONCURRENCY nicht SQL_CONCUR_READ_ONLY ist).|  
|SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_STATIC|SQL_ATTR_SCROLLABLE auf SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY auf SQL_INSENSITIVE (wenn SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY ist).<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED oder SQL_SENSITIVE (wenn SQL_ATTR_CONCURRENCY nicht SQL_CONCUR_READ_ONLY ist).|
