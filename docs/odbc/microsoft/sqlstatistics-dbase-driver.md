---
description: SQLStatistics (dBASE-Treiber)
title: SQLStatistics (dBase-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLStatistics function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLStatistics
ms.assetid: 631cec1b-66b7-4103-b9a7-ffd81da3c442
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9285f78bbafb7594e3a9cbab2845cedeff0c1af9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421564"
---
# <a name="sqlstatistics-dbase-driver"></a>SQLStatistics (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu dBASE-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
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
