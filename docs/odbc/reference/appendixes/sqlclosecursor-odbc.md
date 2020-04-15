---
title: SQLCloseCursor_ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLCloseCursor function [ODBC], ODBC
ms.assetid: 5e47e3f7-e1b8-451f-bf75-daa19b7c7271
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e1b61267d093e11bf7ea25158f5dc6a29ccba6a1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296300"
---
# <a name="sqlclosecursor_odbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLCloseCursor-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLCloseCursor**finden Sie unter [SQLCloseCursor-Funktion](../../../odbc/reference/syntax/sqlclosecursor-function.md).  
  
 Die Cursorbibliothek unterstützt den Aufruf von **SQLCloseCursor** ohne geöffneten Cursor nicht. Wenn Sie dies versuchen, wird SQLSTATE 24000 (Ungültiger Cursorstatus) zurückgegeben. Das Aufrufen von **SQLFreeStmt** mit der *Option* SQL_CLOSE, wenn kein Cursor geöffnet ist, wird von der Cursorbibliothek unterstützt.
