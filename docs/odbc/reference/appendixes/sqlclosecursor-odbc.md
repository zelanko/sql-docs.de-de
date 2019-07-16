---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a4d0f88d2d9eaba7d95ba887ffbe11e728320b17
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68123384"
---
# <a name="sqlclosecursorodbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLCloseCursor** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLCloseCursor**, finden Sie unter [SQLCloseCursor-Funktion](../../../odbc/reference/syntax/sqlclosecursor-function.md).  
  
 Die Cursorbibliothek unterstützt keine Aufrufen **SQLCloseCursor** ohne einen geöffneten Cursor. Es wird versucht, dies wird SQLSTATE 24000 (Ungültiger Cursorstatus) zurückgegeben. Aufrufen von **SQLFreeStmt** mit einer *Option* von SQL_CLOSE, wenn kein Cursor geöffnet ist, wird von der Cursorbibliothek unterstützt.
