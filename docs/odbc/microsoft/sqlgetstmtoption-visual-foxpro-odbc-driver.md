---
title: SQLGetStmtOption (Visual FoxPro ODBC-Treiber) | Microsoft Docs
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
ms.openlocfilehash: 2624783f7bd55903f5741c62190626e455a9096d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295140"
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Ebene 1  
  
 Gibt die aktuelle Einstellung einer Anweisungsoption zurück.  
  
|*FOption*|Rückgabe|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|32-Bit-Ganzzahlwert, der die Textmarke für die aktuelle Datensatznummer ist|  
|SQL_ROW_NUMBER|32-Bit-Ganzzahl, die die Position der aktuellen Zeile innerhalb des Resultsets angibt|  
|SQL_TRANSLATE_DLL|Fehler: "Treiber nicht fähig"|  
  
 Der Visual FoxPro ODBC-Treiber verfügt über keine Übersetzungs-DLLs.  
  
 Weitere Informationen finden Sie unter [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md) in der *ODBC-Programmiererreferenz*.
