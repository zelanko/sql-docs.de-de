---
title: SQLColAttributes (Excel-Treiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 67ba6df9955a1b138ebb919d410ef7817e1fb48e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62666272"
---
# <a name="sqlcolattributes-excel-driver"></a>SQLColAttributes (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Excel-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Attribut|Kommentare|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Für LONGVARBINARY-Daten ist die SQL_COLUMN_DISPLAY_SIZE die maximale Länge der Spalte nicht die maximale Länge der Spalte multipliziert 2.|  
|SQL_OWNER_NAME|Eine leere Zeichenfolge ("") wird die in dieser Spalte zurückgegeben werden, da der Name des Besitzers nicht unterstützt wird.|  
|SQL_QUALIFIER_NAME|Der Pfad zu einem Verzeichnis wird zurückgegeben.|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY und LONGVARCHAR Spalten werden als SQL_UNSEARCHABLE gemeldet.<br /><br /> Fester Länge und variabler Länge binären und Zeichen-Datentypen können nicht durchsucht werden, obwohl LONGVARBINARY und LONGVARCHAR nicht sind.|  
  
> [!NOTE]  
>  Die oben genannten ist keine vollständige Liste der Attribute von zurückgegebenen **SQLColAttributes**.
