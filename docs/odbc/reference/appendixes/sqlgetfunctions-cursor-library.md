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
manager: craigg
ms.openlocfilehash: 1123a6497207f40bd210edf35b9b4477bc9c7b6b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188730"
---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLGetFunctions** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLGetFunctions**, finden Sie unter [SQLGetFunctions-Funktion](../../../odbc/reference/syntax/sqlgetfunctions-function.md).  
  
 Beim Aufruf **SQLGetFunctions**, die Cursorbibliothek gibt, dass sie unterstützt **SQLExtendedFetch**, **SQLFetchScroll**, **SQLSetPos**, und **SQLSetScrollOptions**, zusätzlich zu den Funktionen, die vom Treiber unterstützt werden.
