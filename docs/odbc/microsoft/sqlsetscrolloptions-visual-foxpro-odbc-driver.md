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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19051fc83466bc40d72c029089cfe6ec45c20a08
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299420"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: partiell  
  
 ODBC-API-Konformität: Ebene 2  
  
 Legt Optionen zum Steuern des Verhaltens von Cursorn fest, die einem Anweisungs Handle ( *hstmt*) zugeordnet sind.  
  
 Der Visual FoxPro-ODBC-Treiber unterstützt nur SQL_CONCUR_READ_ONLY; der SQL_CONCUR_ROWVER für die von " *Datei* " wird nicht unterstützt. Der Treiber konvertiert SQL_KEYSET_SIZE, SQL_CURSOR_DYNAMIC und SQL_CURSOR_KEYSET_DRIVEN in SQL_SCROLL_STATIC mit Warn ODBC_01S02.  
  
 Weitere Informationen finden Sie unter [SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md) in der *ODBC Programmer es Reference*.
