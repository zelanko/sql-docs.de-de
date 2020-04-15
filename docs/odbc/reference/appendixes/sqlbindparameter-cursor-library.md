---
title: SQLBindParameter (Cursorbibliothek) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55708cc5192fb40149d6db7710f6ee638c4880d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305428"
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLBindParameter-Funktion** in der Cursorbibliothek erläutert. Allgemeine Informationen zu **SQLBindParameter**finden Sie unter [SQLBindParameter Function](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Eine Anwendung kann **SQLBindParameter** aufrufen, um Parameter neu zu binden, solange der C-Datentyp, die Spaltengröße und die Dezimalstellen der gebundenen Spalte gleich bleiben.  
  
 Die Cursorbibliothek unterstützt das Festlegen des SQL_ATTR_ROW_BIND_OFFSET_PTR Anweisungsattributs für die Verwendung von Bindungsoffsets. (**SQLBindParameter** muss nicht aufgerufen werden, damit diese Neubindung erfolgt.)  
  
 Die Cursorbibliothek unterstützt die Bindung von Data-at-Execution-Parametern.
