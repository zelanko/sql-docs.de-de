---
title: SQLSetScrollOptions (Cursor Library) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Cursor Library
ms.assetid: c5c0ac6d-a6c1-4077-8186-1644df1944f8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 18a0bc111f6b4e8d82d0ed353837b499f920479e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68023357"
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLSetScrollOptions** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLSetScrollOptions**, finden Sie unter [SQLSetScrollOptions-Funktion](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md).  
  
 Unterstützt die Cursorbibliothek **SQLSetScrollOptions** nur für Abwärtskompatibilität; Anwendungen sollten stattdessen die SQL_ATTR_CURSOR_TYPE, SQL_ATTR_CONCURRENCY und SQL_ATTR_ROW_ARRAY_SIZE Anweisungsattribute.
