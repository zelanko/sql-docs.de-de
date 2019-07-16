---
title: SQLFreeStmt (Cursor Library) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], Cursor Library
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4bfe5c91a90f874b514abb661ea06631be87e69c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086412"
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLFreeStmt** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLFreeStmt**, finden Sie unter [SQLFreeStmt-Funktion](../../../odbc/reference/syntax/sqlfreestmt-function.md).  
  
 Wenn eine Anwendung ruft **SQLFreeStmt** mit der Option SQL_UNBIND, nach dem Aufruf **SQLExtendedFetch**, **SQLFetch**, oder **SQLFetchScroll**, die Cursorbibliothek gibt einen Fehler zurück. Bevor sie Resultset-Spalten aufheben kann, muss eine Anwendung aufrufen **SQLCloseCursor** oder **SQLFreeStmt** mit der Option SQL_CLOSE.
