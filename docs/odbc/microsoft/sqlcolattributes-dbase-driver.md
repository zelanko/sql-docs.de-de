---
title: SQLColAttributes (dBASE-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLColAttributes
ms.assetid: ed44de2b-0b01-4dce-a340-f5eb3aac30b7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a9e9d5adb75a99784d7244852bfda0499e481fc4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307951"
---
# <a name="sqlcolattributes-dbase-driver"></a>SQLColAttributes (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält dBASE-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Attribut|Kommentare|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Bei LONGVARBINARY-Daten ist SQL_COLUMN_DISPLAY_SIZE die maximale Länge der Spalte und nicht die maximale Länge der Spaltenzeiten 2.|  
|SQL_OWNER_NAME|Eine leere Zeichenfolge ("") wird in dieser Spalte zurückgegeben, da der Besitzername nicht unterstützt wird.|  
|SQL_QUALIFIER_NAME|Der Pfad zu einem Verzeichnis wird zurückgegeben.|  
|SQL_COLUMN_SEARCHABLE|Die Spalten LONGVARBINARY und LONGVARCHAR werden als SQL_UNSEARCHABLE gemeldet.<br /><br /> Binär- und Zeichendatentypen mit fester Länge und variabler Länge sind durchsuchbar, obwohl LONGVARBINARY und LONGVARCHAR dies nicht sind.|  
  
> [!NOTE]  
>  Die obige Ist keine vollständige Liste der Attribute, die von **SQLColAttributes**zurückgegeben werden.
