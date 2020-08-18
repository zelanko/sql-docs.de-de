---
description: SQLColAttributes (Access-Treiber)
title: SQLColAttribute (Access-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Access Driver
- Access driver [ODBC], SQLColAttributes
ms.assetid: adb6f81d-e8c7-4748-9b1d-f7a053788bbc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d9758bb5c473971d3ed9acea52559da0a4aac67d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412276"
---
# <a name="sqlcolattributes-access-driver"></a>SQLColAttributes (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Zugriffs Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|attribute|Kommentare|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Bei LONGVARBINARY-Daten ist SQL_COLUMN_DISPLAY_SIZE die maximale Länge der Spalte, nicht die maximale Länge der Spalten Zeit (2).|  
|SQL_OWNER_NAME|In dieser Spalte wird eine leere Zeichenfolge ("") zurückgegeben, da der Besitzer Name nicht unterstützt wird.|  
|SQL_QUALIFIER_NAME|Der Pfad zu einer Datenbankdatei wird zurückgegeben.|  
|SQL_COLUMN_SEARCHABLE|Die Spalten LONGVARBINARY und LONGVARCHAR werden als SQL_UNSEARCHABLE gemeldet.<br /><br /> Binäre und Zeichen Datentypen mit fester Länge und variabler Länge sind durchsuchbar, obwohl LONGVARBINARY und LONGVARCHAR nicht sind.|  
  
> [!NOTE]  
>  Der obige Abschnitt ist keine komplette Liste der Attribute, die von **SQLColAttribute**zurückgegeben werden.
