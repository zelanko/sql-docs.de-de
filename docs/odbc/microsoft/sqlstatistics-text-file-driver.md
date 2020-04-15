---
title: SQLStatistics (Textdateitreiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Text File Driver
ms.assetid: 311afc01-d656-425f-be43-4a8e7cbc9a97
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 76b9810236b4ec415f8abb8ecefca748c13b51c8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299310"
---
# <a name="sqlstatistics-text-file-driver"></a>SQLStatistics (Textdateitreiber)
> [!NOTE]  
>  Dieses Thema enthält Textdateitreiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Column|Kommentare|  
|------------|--------------|  
|TABLE_QUALIFIER|Der Pfad zu einem Verzeichnis.<br /><br /> Der Musterabgleich wird im Argument *szTableQualifier* nicht unterstützt.|  
|TABLE_OWNER|NULL wird in dieser Spalte zurückgegeben, da der Besitzername nicht unterstützt wird.|  
|table_name|Undelimited Tabellenname.<br /><br /> Der Musterabgleich wird im *Argument szTableName* nicht unterstützt.|  
|INDEX_QUALIFIER|NULL wird immer zurückgegeben.|  
|INDEX_NAME|Indexabhängig.|  
|TYPE|Nur SQL_TABLE_STAT oder SQL_INDEX_OTHER werden für TYPE zurückgegeben.|  
|SEQ_IN_INDEX|Indexabhängig.|  
|COLUMN_NAME|Indexabhängig.|  
|COLLATION|Indexabhängig.|  
|PAGES|NULL wird immer zurückgegeben.|  
  
 Die Filterung basiert auf der Eindeutigkeit (dem *fUnique-Argument).* Der *Parameter fAccuracy* wird ignoriert.
