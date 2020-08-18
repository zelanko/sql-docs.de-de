---
description: SQLColAttributes (Excel-Treiber)
title: SQLColAttribute (Excel-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], Excel Driver
ms.assetid: 7c4833e3-ff0c-4313-9ab8-21379ceab656
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9993fd239235a19fd02ffaa7fc43be0e66f2890f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412226"
---
# <a name="sqlcolattributes-excel-driver"></a>SQLColAttributes (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Excel-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|attribute|Kommentare|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Bei LONGVARBINARY-Daten ist SQL_COLUMN_DISPLAY_SIZE die maximale Länge der Spalte, nicht die maximale Länge der Spalten Zeit (2).|  
|SQL_OWNER_NAME|In dieser Spalte wird eine leere Zeichenfolge ("") zurückgegeben, da der Besitzer Name nicht unterstützt wird.|  
|SQL_QUALIFIER_NAME|Der Pfad zu einem Verzeichnis wird zurückgegeben.|  
|SQL_COLUMN_SEARCHABLE|Die Spalten LONGVARBINARY und LONGVARCHAR werden als SQL_UNSEARCHABLE gemeldet.<br /><br /> Binäre und Zeichen Datentypen mit fester Länge und variabler Länge sind durchsuchbar, obwohl LONGVARBINARY und LONGVARCHAR nicht sind.|  
  
> [!NOTE]  
>  Der obige Abschnitt ist keine komplette Liste der Attribute, die von **SQLColAttribute**zurückgegeben werden.
