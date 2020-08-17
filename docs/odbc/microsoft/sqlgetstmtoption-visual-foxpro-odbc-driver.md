---
description: SQLGetStmtOption (Visual FoxPro-ODBC-Treiber)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e57456ca05e39c12b83da80cd19c34f482c3d8df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340086"
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro-ODBC-Treiber spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Unterstützung: vollständig  
  
 ODBC-API-Konformität: Ebene 1  
  
 Gibt die aktuelle Einstellung einer Anweisungs Option zurück.  
  
|*FOption*|Rückgabe|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|32-Bit-ganzzahliger Wert, der das Lesezeichen für die aktuelle Datensatznummer ist|  
|SQL_ROW_NUMBER|32-Bit-Ganzzahl, die die Position der aktuellen Zeile innerhalb des Resultsets angibt.|  
|SQL_TRANSLATE_DLL|Fehler: "Treiber nicht fähig"|  
  
 Der Visual FoxPro-ODBC-Treiber hat keine Übersetzungs-DLLs.  
  
 Weitere Informationen finden Sie unter [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md) in der *ODBC Programmer es Reference*.
