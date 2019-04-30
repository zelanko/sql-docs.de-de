---
title: SQLSetScrollOptions (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c2d78e26309d5ea7dc5e6eed5a04e84a1651b33
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63305737"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Teilweise  
  
 ODBC-API-Übereinstimmung: Ebene 2  
  
 Legt Optionen zum Steuern des Verhaltens von Cursorn, die ein Anweisungshandle zugeordnet *Befehls beschäftigt*.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt nur SQL_CONCUR_READ_ONLY; Er unterstützt nicht die *fConcurrency* SQL_CONCUR_ROWVER Wert. Der Treiber konvertiert SQL_KEYSET_SIZE SQL_CURSOR_DYNAMIC und SQL_CURSOR_KEYSET_DRIVEN in SQL_SCROLL_STATIC, mit der Warnung ODBC_01S02.  
  
 Weitere Informationen finden Sie unter [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) in die *ODBC Programmer's Reference*.
