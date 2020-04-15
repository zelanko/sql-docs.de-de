---
title: SQLGetInfo (Cursorbibliothek) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Cursor Library
ms.assetid: 1b4d220d-2c07-4f56-987e-36813bb1a6ce
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9067fd8b33cb2408f1ef6f0e58603eb4f1f7eb09
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307811"
---
# <a name="sqlgetinfo-cursor-library"></a>SQLGetInfo (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLGetInfo-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLGetInfo**finden Sie unter [SQLGetInfo-Funktion](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
 Die Cursorbibliothek gibt Werte für die folgenden Werte von *InfoType* zurück (&#124; stellt ein bitweises ODER dar); für alle anderen Werte von *InfoType*ruft es **SQLGetInfo** im Treiber auf.  
  
|*Infotyp*|Rückgabewert|  
|----------------|--------------------|  
|SQL_BOOKMARK_PERSISTENCE|SQL_BP_SCROLL|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|0|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|0|  
|SQL_FETCH_DIRECTION[1]|SQL_FD_FETCH_ABSOLUTE &#124; SQL_FD_FETCH_FIRST &#124; SQL_FD_FETCH_LAST &#124; SQL_FD_FETCH_NEXT &#124; SQL_FD_FETCH_PRIOR &#124; SQL_FD_FETCH_RELATIVE &#124; SQL_FD_FETCH_BOOKMARK|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT &#124; SQL_CA1_ABSOLUTE &#124; SQL_CA1_RELATIVE &#124; SQL_CA1_LOCK_NO_CHANGE &#124; SQL_CA1_POS_POSITION &#124; SQL_CA1_POSITIONED_DELETE &#124; SQL_CA1_POSITIONED_UPDATE &#124; SQL_CA1_SELECT_FOR_UPDATE|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|SQL_CA2_READ_ONLY_CONCUR &#124; SQL_CA2_OPT_VALUES_CONCURRENCY &#124; SQL_CA2_SENSITIVITY_UPDATES|  
|SQL_GETDATA_EXTENSIONS|SQL_GD_BLOCK &#124; alle Werte, die vom Treiber zurückgegeben werden **Hinweis:** Wenn Daten mit **SQLFetchScroll**abgerufen werden, unterstützt **SQLGetData** die Mit-SQL_GD_ANY_COLUMN- und SQL_GD_BOUND-Bitmasken.|  
|SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES1|0|  
|SQL_KEYSET_DRIVEN_CURSOR_ATTRIBUTES2|0|  
|SQL_LOCK_TYPES[1]|SQL_LCK_NO_CHANGE|  
|SQL_STATIC_CURSOR_ATTRIBUTES1|SQL_CA1_NEXT &#124; SQL_CA1_ABSOLUTE &#124; SQL_CA1_RELATIVE &#124; SQL_CA1_BOOKMARK &#124; SQL_CA1_LOCK_NO_CHANGE &#124; SQL_CA1_POS_POSITION &#124; SQL_CA1_POSITIONED_DELETE &#124; SQL_CA1_POSITIONED_UPDATE &#124; SQL_CA1_SELECT_FOR_UPDATE|  
|SQL_STATIC_CURSOR_ATTRIBUTES2|SQL_CA2_READ_ONLY_CONCUR &#124; SQL_CA2_OPT_VALUES_ CONCURRENCY &#124; SQL_CA2_SENSITIVITY_UPDATES|  
|SQL_POS_OPERATIONS[1]|SQL_POS_POSITION|  
|SQL_POSITIONED_STATEMENTS[1]|SQL_PS_POSITIONED_DELETE &#124; SQL_PS_POSITIONED_UPDATE &#124; SQL_PS_SELECT_FOR_UPDATE|  
|SQL_ROW_UPDATES|"Y"|  
|SQL_SCROLL_CONCURRENCY[1]|SQL_SCCO_READ_ONLY &#124; SQL_SCCO_OPT_VALUES|  
|SQL_SCROLL_OPTIONS|SQL_SO_FORWARD_ONLY &#124; SQL_SO_STATIC|  
|SQL_STATIC_SENSITIVITY[1]|SQL_SS_UPDATES|  
  
 [1] Wird nur verwendet, wenn die Cursorbibliothek mit einem ODBC 2.x-Treiber verwendet wird.  
  
> [!IMPORTANT]  
>  Die Cursorbibliothek implementiert dasselbe Cursorverhalten, wenn Transaktionen festgeschrieben oder zurückgesetzt werden wie die Datenquelle. Das heißt, das Übertragen oder Zurücksetzen einer Transaktion, entweder durch Aufrufen von **SQLEndTran** oder mithilfe des SQL_ATTR_AUTOCOMMIT-Verbindungsattributs, kann dazu führen, dass die Datenquelle die Zugriffspläne löscht und die Cursor für alle Anweisungen für eine Verbindung schließt. Weitere Informationen finden Sie unter SQL_CURSOR_COMMIT_BEHAVIOR und SQL_CURSOR_ROLLBACK_BEHAVIOR Informationstypen in [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).
