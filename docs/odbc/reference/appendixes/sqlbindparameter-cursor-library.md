---
title: SQLBindParameter (Cursor Library) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], Cursor Library
ms.assetid: 04c53e4c-cd1d-40b2-9997-684ebe43499f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7943987d52554e0f5cd7723e8c9ae8a0e3afddd2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093031"
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (Cursorbibliothek)
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 In diesem Thema erläutert die Verwendung von der **SQLBindParameter** -Funktion in der Cursorbibliothek. Allgemeine Informationen zur **SQLBindParameter**, finden Sie unter [SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Kann eine Anwendung aufrufen **SQLBindParameter** Parameter erneut binden, solange die C-Datentyp, die Spaltengröße und die Dezimalstellen der gebundenen Spalte unverändert bleiben.  
  
 Die Cursorbibliothek unterstützt das Festlegen der SQL_ATTR_ROW_BIND_OFFSET_PTR-Anweisungsattribut Bindung Offsets zu verwenden. (**SQLBindParameter** muss nicht aufgerufen werden, für diese erneute Bindung stattfinden.)  
  
 Die Cursorbibliothek unterstützt Bindung Data-at-Execution-Parameter.
