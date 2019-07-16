---
title: SQLGetFunctions (Cursor Library) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetFunctions function [ODBC], Cursor Library
ms.assetid: 931acd12-4eb6-4a78-9a77-157a18a9a2d0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1497a7d2ec5951feedb36831ab541413e57152f4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073918"
---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLGetFunctions** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLGetFunctions**, finden Sie unter [SQLGetFunctions-Funktion](../../../odbc/reference/syntax/sqlgetfunctions-function.md).  
  
 Beim Aufruf **SQLGetFunctions**, die Cursorbibliothek gibt, dass sie unterstützt **SQLExtendedFetch**, **SQLFetchScroll**, **SQLSetPos**, und **SQLSetScrollOptions**, zusätzlich zu den Funktionen, die vom Treiber unterstützt werden.
