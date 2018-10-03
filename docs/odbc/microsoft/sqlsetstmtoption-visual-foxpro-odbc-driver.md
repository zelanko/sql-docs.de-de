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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d7bcecfbd880f53d1067fd68202b62c34fce398
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854396"
---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: vollständige  
  
 ODBC-API-Übereinstimmung: Ebene 1  
  
 Legt fest, die im Zusammenhang mit der ein Anweisungshandle *Befehls beschäftigt*.  
  
|*fOption*|Zulässige Werte|Kommentare|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|Wenn Sie versuchen, diese festzulegen *fOption*, gibt der Treiber den Fehler: "Vom Treiber nicht unterstützt". Visual FoxPro unterstützt asynchrone Ausführung nicht.|  
|SQL_BIND_TYPE|Eine 32-Bit-Wert, der die Länge der Struktur oder einer Instanz eines Puffers, in welche Ergebnis Spalten gebunden werden, der angibt, oder SQL_BIND_BY_COLUMN ein.||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Der Treiber nicht SQL_CONCUR_ROWVER, gestattet werden, da Visual FoxPro keine zeilenversionsverwaltung auf Zeitstempeln basiert.|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|Der Treiber lässt sich nicht auf SQL_CURSOR_KEYSET_DRIVEN oder SQL_CURSOR_DYNAMIC aus. finden Sie unter [SQLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md) für Weitere Informationen.|  
|SQL_KEYSET_SIZE|Fehler: "vom Treiber nicht unterstützt"|Visual FoxPro unterstützt nicht das Keyset-Cursor-Modell.|  
|SQL_MAX_LENGTH|0|Wenn Sie versuchen, diese festzulegen *fOption* Wert, gibt der Treiber den Fehler "Vom Treiber nicht unterstützt".|  
|SQL_MAX_ROWS|0|Wenn Sie versuchen, diese festzulegen *fOption* Wert, gibt der Treiber den Fehler "Vom Treiber nicht unterstützt".|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|Wenn Sie versuchen, diese festzulegen *fOption* Wert, gibt der Treiber den Fehler "Vom Treiber nicht unterstützt".|  
|SQL_RETRIEVE_DATA|SQL_RD_ON, SQL_RD_OFF||  
|SQL_ROWSET_SIZE SETZEN|zu 4.294.967.296 1||  
|SQL_SIMULATE_CURSOR|Fehler: "vom Treiber nicht unterstützt"||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 Weitere Informationen finden Sie unter [SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md) in die *ODBC Programmer's Reference*.
