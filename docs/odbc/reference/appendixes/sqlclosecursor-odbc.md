---
description: SQLCloseCursor_ODBC
title: SQLCloseCursor_ODBC | Microsoft-Dokumentation
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
ms.openlocfilehash: d91ce573a48602ad6dce4f0cb0759c2c8dddd3aa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466052"
---
# <a name="sqlclosecursor_odbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLCloseCursor** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLCloseCursor**finden Sie unter [SQLCloseCursor-Funktion](../../../odbc/reference/syntax/sqlclosecursor-function.md).  
  
 Die Cursor Bibliothek unterstützt das Aufrufen von **SQLCloseCursor** ohne einen geöffneten Cursor nicht. Wenn Sie dies versuchen, wird SQLSTATE 24000 (Ungültiger Cursor Zustand) zurückgegeben. Das Aufrufen von **SQLFreeStmt** mit der *Option* SQL_CLOSE, wenn kein Cursor geöffnet ist, wird von der Cursor Bibliothek unterstützt.
