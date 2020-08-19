---
description: SQLStatistics (Excel-Treiber)
title: SQLStatistics (Excel-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Excel Driver
ms.assetid: 02506664-8dcc-4bd0-a8bb-d49fcbdd5722
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6482de71907962fe9734f2167072a56a045a271
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421574"
---
# <a name="sqlstatistics-excel-driver"></a>SQLStatistics (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Excel-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Column|Kommentare|  
|------------|--------------|  
|TABLE_QUALIFIER|Der Pfad zu einem Verzeichnis.<br /><br /> Der Musterabgleich wird im *sztablequalifier* -Argument nicht unterstützt.|  
|TABLE_OWNER|In dieser Spalte wird NULL zurückgegeben, da der Besitzer Name nicht unterstützt wird.|  
|table_name|Nicht durch Trennzeichen getrennter Tabellenname.<br /><br /> Der Musterabgleich wird im Argument " *sztablename* " nicht unterstützt.|  
|INDEX_QUALIFIER|NULL wird immer zurückgegeben.|  
|INDEX_NAME|Index abhängig.|  
|TYPE|Für den Typ werden nur SQL_TABLE_STAT oder SQL_INDEX_OTHER zurückgegeben.|  
|SEQ_IN_INDEX|Index abhängig.|  
|COLUMN_NAME|Index abhängig.|  
|COLLATION|Index abhängig.|  
|PAGES|NULL wird immer zurückgegeben.|  
  
 Das Filtern basiert auf der Eindeutigkeit (dem " *f Unique* "-Argument). Der *fakcurracy* -Parameter wird ignoriert.
