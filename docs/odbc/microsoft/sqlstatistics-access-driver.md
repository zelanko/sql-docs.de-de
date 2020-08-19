---
description: SQLStatistics (Access-Treiber)
title: SQLStatistics (Zugriffs Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Access Driver
ms.assetid: 6117ac77-1020-4f0c-8eed-e671c34c1f21
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 67ea4e7f2553d85837c1ece30327f24298d94c97
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421584"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Zugriffs Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Column|Kommentare|  
|------------|--------------|  
|TABLE_QUALIFIER|Der Pfad zu einer Datenbankdatei wird für Microsoft Access zurückgegeben.<br /><br /> Der Musterabgleich wird im *sztablequalifier* -Argument nicht unterstützt.|  
|TABLE_OWNER|In dieser Spalte wird NULL zurückgegeben, da der Besitzer Name nicht unterstützt wird.|  
|table_name|Nicht durch Trennzeichen getrennter Tabellenname.<br /><br /> Der Musterabgleich wird im Argument " *sztablename* " nicht unterstützt.|  
|INDEX_QUALIFIER|NULL wird immer zurückgegeben.|  
|INDEX_NAME|Index abhängig.|  
|TYPE|Für den Typ werden nur SQL_TABLE_STAT oder SQL_INDEX_OTHER zurückgegeben.|  
|SEQ_IN_INDEX|Index abhängig.|  
|COLUMN_NAME|Index abhängig.|  
|COLLATION|Index abhängig.|  
|CARDINALITY|Wird nur für Microsoft Access zurückgegeben.|  
|PAGES|NULL wird immer zurückgegeben.|  
  
 Das Filtern basiert auf der Eindeutigkeit (dem " *f Unique* "-Argument). Der *fakcurracy* -Parameter wird ignoriert.
