---
title: Cursoreigenschaften und Cursortyp | Microsoft Docs
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
ms.openlocfilehash: 8354fdabf6830780ec2d128492c86cc1edd582ac
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301627"
---
# <a name="cursor-characteristics-and-cursor-type"></a>Cursoreigenschaften und Cursortyp
Eine Anwendung kann die Eigenschaften eines Cursors angeben, anstatt den Cursortyp anzugeben (vorwärtsgesteuert, statisch, Keyset-gesteuert oder dynamisch). Dazu wählt die Anwendung die Bildlauffähigkeit des Cursors (durch Festlegen des SQL_ATTR_CURSOR_SCROLLABLE Anweisungsattributs) und die Empfindlichkeit (durch Festlegen des Attributs SQL_ATTR_CURSOR_SENSITIVITY Anweisung) aus, bevor der Cursor für das Anweisungshandle geöffnet wird. Der Treiber wählt dann den Cursortyp aus, der die von der Anwendung angeforderten Eigenschaften am effizientesten bereitstellt.  
  
 Wenn eine Anwendung eines der Anweisungsattribute SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY oder SQL_ATTR_CURSOR_TYPE festlegt, nimmt der Treiber die erforderlichen Änderungen an den anderen Anweisungsattributen in diesem Satz von vier Attributen vor, damit ihre Werte konsistent bleiben. Wenn die Anwendung daher ein Cursormerkmal angibt, kann der Treiber das Attribut ändern, das den Cursortyp basierend auf dieser impliziten Auswahl angibt. Wenn die Anwendung einen Typ angibt, kann der Treiber eines der anderen Attribute so ändern, dass es mit den Merkmalen des ausgewählten Typs konsistent ist. Weitere Informationen zu diesen Anweisungsattributen finden Sie in der [SQLSetStmtAttr-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)  
  
 Eine Anwendung, die Anweisungsattribute festlegt, um sowohl einen Cursortyp als auch Cursoreigenschaften anzugeben, läuft Gefahr, einen Cursor zu erhalten, der nicht die effizienteste Methode ist, die für diesen Treiber verfügbar ist, um die Anforderungen der Anwendung zu erfüllen.  
  
 Die implizite Einstellung von Anweisungsattributen ist treiberdefiniert, außer dass sie den folgenden Regeln folgen muss:  
  
-   Vorwärts-Cursor können nie scrollbar werden. siehe definition von SQL_ATTR_CURSOR_SCROLLABLE in [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
-   Unempfindliche Cursor sind nie aufrüstbar (und daher ist ihre Parallelität schreibgeschützt); Dies basiert auf ihrer Definition von unsensiblen Cursorn im ISO SQL-Standard.  
  
 Folglich erfolgt die implizite Einstellung von Anweisungsattributen in den in der folgenden Tabelle beschriebenen Fällen.  
  
|Anwendung setzt Attribut auf|Andere Attribute implizit festgelegt|  
|-----------------------------------|-------------------------------------|  
|SQL_ATTR_CONCURRENCY zu SQL_CONCUR_READ_ONLY|SQL_ATTR_CURSOR_SENSITIVITY zu SQL_INSENSITIVE.|  
|SQL_ATTR_CONCURRENCY SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES|SQL_ATTR_CURSOR_SENSITIVITY SQL_UNSPECIFIED oder SQL_SENSITIVE, wie vom Fahrer definiert. Sie kann nie auf SQL_INSENSITIVE eingestellt werden, da unempfindliche Cursor immer schreibgeschützt sind.|  
|SQL_ATTR_CURSOR_SCROLLABLE zu SQL_NONSCROLLABLE|SQL_ATTR_CURSOR_TYPE zu SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE zu SQL_SCROLLABLE|SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN oder SQL_CURSOR_DYNAMIC, wie vom Fahrer angegeben. Es wird nie auf SQL_CURSOR_FORWARD_ONLY eingestellt.|  
|SQL_ATTR_CURSOR_SENSITIVITY zu SQL_INSENSITIVE|SQL_ATTR_CONCURRENCY zu SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE zu SQL_CURSOR_STATIC.|  
|SQL_ATTR_CURSOR_SENSITIVITY zu SQL_SENSITIVE|SQL_ATTR_CONCURRENCY, wie vom Fahrer angegeben, SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES. Es wird nie auf SQL_CONCUR_READ_ONLY eingestellt.<br /><br /> SQL_ATTR_CURSOR_TYPE, um SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN oder SQL_CURSOR_DYNAMIC zu SQL_CURSOR_FORWARD_ONLY, zu SQL_CURSOR_KEYSET_DRIVEN, wie vom Fahrer angegeben.|  
|SQL_ATTR_CURSOR_SENSITIVITY zu SQL_UNSPECIFIED|SQL_ATTR_CONCURRENCY, wie vom Fahrer angegeben, SQL_CONCUR_READ_ONLY, SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER oder SQL_CONCUR_VALUES.<br /><br /> SQL_ATTR_CURSOR_TYPE, um SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN oder SQL_CURSOR_DYNAMIC zu SQL_CURSOR_FORWARD_ONLY, zu SQL_CURSOR_KEYSET_DRIVEN, wie vom Fahrer angegeben.|  
|SQL_ATTR_CURSOR_TYPE zu SQL_CURSOR_DYNAMIC|SQL_ATTR_SCROLLABLE zu SQL_SCROLLABLE.<br /><br /> SQL_ATTR_CURSOR_SENSITIVITY zu SQL_SENSITIVE. (Aber nur, wenn SQL_ATTR_CONCURRENCY nicht gleich SQL_CONCUR_READ_ONLY ist. Dynamische Cursor, die aufdemweiterbar sind, sind immer empfindlich gegenüber Änderungen, die in ihrer eigenen Transaktion vorgenommen wurden.)|  
|SQL_ATTR_CURSOR_TYPE zu SQL_CURSOR_FORWARD_ONLY|SQL_ATTR_CURSOR_SCROLLABLE zu SQL_NONSCROLLABLE.|  
|SQL_ATTR_CURSOR_TYPE zu SQL_CURSOR_KEYSET_DRIVEN|SQL_ATTR_SCROLLABLE zu SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY zu SQL_UNSPECIFIED oder SQL_SENSITIVE (nach fahrerdefinierten Kriterien, wenn SQL_ATTR_CONCURRENCY nicht SQL_CONCUR_READ_ONLY ist).|  
|SQL_ATTR_CURSOR_TYPE zu SQL_CURSOR_STATIC|SQL_ATTR_SCROLLABLE zu SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY zu SQL_INSENSITIVE (wenn SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY ist).<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED oder SQL_SENSITIVE (wenn SQL_ATTR_CONCURRENCY nicht SQL_CONCUR_READ_ONLY ist).|
