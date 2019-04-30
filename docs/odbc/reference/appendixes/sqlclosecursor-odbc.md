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
manager: craigg
ms.openlocfilehash: 827f7195c5d4eb4f67cb3298b75519a5583053d1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199504"
---
# <a name="sqlclosecursorodbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLCloseCursor** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLCloseCursor**, finden Sie unter [SQLCloseCursor-Funktion](../../../odbc/reference/syntax/sqlclosecursor-function.md).  
  
 Die Cursorbibliothek unterstützt keine Aufrufen **SQLCloseCursor** ohne einen geöffneten Cursor. Es wird versucht, dies wird SQLSTATE 24000 (Ungültiger Cursorstatus) zurückgegeben. Aufrufen von **SQLFreeStmt** mit einer *Option* von SQL_CLOSE, wenn kein Cursor geöffnet ist, wird von der Cursorbibliothek unterstützt.
