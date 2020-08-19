---
description: SQLSetScrollOptions (Visual FoxPro-ODBC-Treiber)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c0e7cecfb0ce7640575cb69f1e84e805a884b57b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421634"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: partiell  
  
 ODBC-API-Konformität: Ebene 2  
  
 Legt Optionen zum Steuern des Verhaltens von Cursorn fest, die einem Anweisungs Handle ( *hstmt*) zugeordnet sind.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt nur SQL_CONCUR_READ_ONLY; der SQL_CONCUR_ROWVER für die von " *Datei* " wird nicht unterstützt. Der Treiber konvertiert SQL_KEYSET_SIZE, SQL_CURSOR_DYNAMIC und SQL_CURSOR_KEYSET_DRIVEN in SQL_SCROLL_STATIC mit Warn ODBC_01S02.  
  
 Weitere Informationen finden Sie unter [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) in der *ODBC Programmer es Reference*.
