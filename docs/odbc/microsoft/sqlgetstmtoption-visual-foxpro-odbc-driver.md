---
title: SQLGetStmtOption (Visual FoxPro-ODBC-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 984a8b1d-f12c-420c-8be4-f555114c764b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 373f5e13712ef7b0864401ea3d2c204cb03ebb09
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63240257"
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Vollständig  
  
 ODBC-API-Übereinstimmung: Ebene 1  
  
 Gibt die aktuelle Einstellung der Option-Anweisung ein.  
  
|*FOption*|Rückgabewert|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|32-Bit-Ganzzahl-Wert, der das Lesezeichen für die Nummer des aktuellen Datensatzes ist|  
|SQL_ROW_NUMBER|Legen Sie die 32-Bit-Ganzzahl, die die Position des die aktuelle Zeile in das Ergebnis angeben|  
|SQL_TRANSLATE_DLL|Fehler: "Vom Treiber nicht unterstützt"|  
  
 Der Visual FoxPro-ODBC-Treiber verfügt über keine Übersetzung DLLs.  
  
 Weitere Informationen finden Sie unter [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md) in die *ODBC Programmer's Reference*.
