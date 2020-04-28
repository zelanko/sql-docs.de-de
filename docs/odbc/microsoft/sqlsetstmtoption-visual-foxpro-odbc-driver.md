---
title: SQLSetStmtOption (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 76b813e3-c7dc-4bb2-a710-d2aa9dcfdc36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb9677a9ccf307be847089c657964d96904eb20b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299400"
---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: Ebene 1  
  
 Legt Optionen fest, die sich auf ein Anweisungs Handle ( *hstmt*) beziehen.  
  
|*fOption*|Zulässige Werte|Kommentare|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|Wenn Sie versuchen, diese *fOption*festzulegen, gibt der Treiber den folgenden Fehler zurück: "Treiber ist nicht kompatibel". Visual FoxPro unterstützt keine asynchrone Ausführung.|  
|SQL_BIND_TYPE|SQL_BIND_BY_COLUMN oder ein 32-Bit-Wert, der die Länge der Struktur oder eine Instanz eines Puffers anzeigt, in die Ergebnis Spalten gebunden werden.||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Der Treiber lässt SQL_CONCUR_ROWVER nicht zu, da Visual FoxPro keine Zeilen Versionsverwaltung auf Grundlage von Zeitstempeln hat.|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|Der Treiber lässt keine SQL_CURSOR_KEYSET_DRIVEN oder SQL_CURSOR_DYNAMIC zu. Weitere Informationen finden Sie unter [SQLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md) .|  
|SQL_KEYSET_SIZE|Fehler: "Treiber nicht fähig"|Visual FoxPro unterstützt das Keyset-Cursor Modell nicht.|  
|SQL_MAX_LENGTH|0|Wenn Sie versuchen, diesen *fOption* -Wert festzulegen, gibt der Treiber den Fehler "Treiber nicht fähig" zurück.|  
|SQL_MAX_ROWS|0|Wenn Sie versuchen, diesen *fOption* -Wert festzulegen, gibt der Treiber den Fehler "Treiber nicht fähig" zurück.|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|Wenn Sie versuchen, diesen *fOption* -Wert festzulegen, gibt der Treiber den Fehler "Treiber nicht fähig" zurück.|  
|SQL_RETRIEVE_DATA|SQL_RD_ON SQL_RD_OFF||  
|SQL_ROWSET_SIZE|1 bis 4.294.967.296||  
|SQL_SIMULATE_CURSOR|Fehler: "Treiber nicht fähig"||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 Weitere Informationen finden Sie unter [SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md) in der *ODBC Programmer es Reference*.
