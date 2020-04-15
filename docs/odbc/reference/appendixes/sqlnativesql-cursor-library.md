---
title: SQLNativeSql (Cursorbibliothek) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLNativeSql function [ODBC], Cursor Library
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 41f7617530f34d49852ca67db9f47cab94292385
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300570"
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLNativeSql-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLNativeSql**finden Sie unter [SQLNativeSql Function](../../../odbc/reference/syntax/sqlnativesql-function.md).  
  
 Wenn der Treiber diese Funktion unterstützt, ruft die Cursorbibliothek **SQLNativeSql** im Treiber auf und übergibt ihm die SQL-Anweisung. Bei positionierten Aktualisierungs-, Positioniert-Lösch- und **SELECT FOR UPDATE-Anweisungen** ändert die Cursorbibliothek die Anweisung, bevor sie an den Treiber übergeben wird.  
  
> [!NOTE]  
>  Die Cursorbibliothek gibt fälschlicherweise SQLSTATE 34000 (Ungültiger Cursorname) zurück, wenn der Cursorname in einer positionierten Aktualisierungs- oder Löschanweisung ungültig ist, die im *InStatementText-Argument* von **SQLNativeSql**übergeben wird. **SQLNativeSql** ist nicht dazu gedacht, Syntaxfehler zurückzugeben, die nur bei der Anweisungsvorbereitung oder -ausführung zurückgegeben werden.
