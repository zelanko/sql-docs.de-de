---
title: SQLColAttributes (dBASE-Treiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 56d6a7cb3c2c071191a956c6aaf11479810698f8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62666514"
---
# <a name="sqlcolattributes-dbase-driver"></a>SQLColAttributes (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die dBASE-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Attribut|Kommentare|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Für LONGVARBINARY-Daten ist die SQL_COLUMN_DISPLAY_SIZE die maximale Länge der Spalte nicht die maximale Länge der Spalte multipliziert 2.|  
|SQL_OWNER_NAME|Eine leere Zeichenfolge ("") wird die in dieser Spalte zurückgegeben werden, da der Name des Besitzers nicht unterstützt wird.|  
|SQL_QUALIFIER_NAME|Der Pfad zu einem Verzeichnis wird zurückgegeben.|  
|SQL_COLUMN_SEARCHABLE|LONGVARBINARY und LONGVARCHAR Spalten werden als SQL_UNSEARCHABLE gemeldet.<br /><br /> Fester Länge und variabler Länge binären und Zeichen-Datentypen können nicht durchsucht werden, obwohl LONGVARBINARY und LONGVARCHAR nicht sind.|  
  
> [!NOTE]  
>  Die oben genannten ist keine vollständige Liste der Attribute von zurückgegebenen **SQLColAttributes**.
