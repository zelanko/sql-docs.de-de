---
title: SQLColAttributes (Access-Treiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0fa4de89a1ca617f7955d89e18650b7cf1e0c0c2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62865739"
---
# <a name="sqlcolattributes-access-driver"></a>SQLColAttributes (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Access-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Attribut|Kommentare|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Für LONGVARBINARY-Daten ist die SQL_COLUMN_DISPLAY_SIZE die maximale Länge der Spalte nicht die maximale Länge der Spalte multipliziert 2.|  
|SQL_OWNER_NAME|Eine leere Zeichenfolge ("") wird die in dieser Spalte zurückgegeben werden, da der Name des Besitzers nicht unterstützt wird.|  
|SQL_QUALIFIER_NAME|Der Pfad zu einer Datenbankdatei wird zurückgegeben.|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY und LONGVARCHAR Spalten werden als SQL_UNSEARCHABLE gemeldet.<br /><br /> Fester Länge und variabler Länge binären und Zeichen-Datentypen können nicht durchsucht werden, obwohl LONGVARBINARY und LONGVARCHAR nicht sind.|  
  
> [!NOTE]  
>  Die oben genannten ist keine vollständige Liste der Attribute von zurückgegebenen **SQLColAttributes**.
