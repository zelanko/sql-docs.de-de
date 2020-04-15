---
title: SQLStatistics (Zugriffstreiber) | Microsoft Docs
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
ms.openlocfilehash: f75f41bf63cbf224772955effa0f120b5d384111
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299360"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Access Driver-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Column|Kommentare|  
|------------|--------------|  
|TABLE_QUALIFIER|Der Pfad zu einer Datenbankdatei wird für Microsoft Access zurückgegeben.<br /><br /> Der Musterabgleich wird im Argument *szTableQualifier* nicht unterstützt.|  
|TABLE_OWNER|NULL wird in dieser Spalte zurückgegeben, da der Besitzername nicht unterstützt wird.|  
|table_name|Undelimited Tabellenname.<br /><br /> Der Musterabgleich wird im *Argument szTableName* nicht unterstützt.|  
|INDEX_QUALIFIER|NULL wird immer zurückgegeben.|  
|INDEX_NAME|Indexabhängig.|  
|TYPE|Nur SQL_TABLE_STAT oder SQL_INDEX_OTHER werden für TYPE zurückgegeben.|  
|SEQ_IN_INDEX|Indexabhängig.|  
|COLUMN_NAME|Indexabhängig.|  
|COLLATION|Indexabhängig.|  
|CARDINALITY|Nur für Microsoft Access zurückgegeben.|  
|PAGES|NULL wird immer zurückgegeben.|  
  
 Die Filterung basiert auf der Eindeutigkeit (dem *fUnique-Argument).* Der *Parameter fAccuracy* wird ignoriert.
