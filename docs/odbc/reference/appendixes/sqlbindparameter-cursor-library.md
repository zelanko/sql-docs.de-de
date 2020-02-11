---
title: SQLBindParameter (Cursor Bibliothek) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093031"
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (Cursorbibliothek)
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 In diesem Thema wird die Verwendung der **SQLBindParameter** -Funktion in der Cursor Bibliothek erläutert. Allgemeine Informationen zu **SQLBindParameter**finden Sie unter [SQLBindParameter-Funktion](../../../odbc/reference/syntax/sqlbindparameter-function.md).  
  
 Eine Anwendung kann **SQLBindParameter** aufrufen, um Parameter erneut zu binden, solange der C-Datentyp, die Spaltengröße und die Dezimalziffern der gebundenen Spalte unverändert bleiben.  
  
 Die Cursor Bibliothek unterstützt das Festlegen des SQL_ATTR_ROW_BIND_OFFSET_PTR Anweisungs Attributs für die Verwendung von Bindungs Offsets. (**SQLBindParameter** muss nicht aufgerufen werden, damit diese erneute Bindung stattfindet.)  
  
 Die Cursor Bibliothek unterstützt das Binden von Data-at-Execution-Parametern.
