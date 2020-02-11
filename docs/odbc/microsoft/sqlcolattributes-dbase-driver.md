---
title: SQLColAttribute (dBase-Treiber) | Microsoft-Dokumentation
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
ms.openlocfilehash: 66a37f3c9ceccdf3fb226ea423552886d36ed99f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67903975"
---
# <a name="sqlcolattributes-dbase-driver"></a>SQLColAttributes (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu dBASE-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|attribute|Kommentare|  
|---------------|--------------|  
|SQL_COLUMN_DISPLAY_SIZE|Bei LONGVARBINARY-Daten ist SQL_COLUMN_DISPLAY_SIZE die maximale Länge der Spalte, nicht die maximale Länge der Spalten Zeit (2).|  
|SQL_OWNER_NAME|In dieser Spalte wird eine leere Zeichenfolge ("") zurückgegeben, da der Besitzer Name nicht unterstützt wird.|  
|SQL_QUALIFIER_NAME|Der Pfad zu einem Verzeichnis wird zurückgegeben.|  
|SQL_COLUMN_SEARCHABLE|Die Spalten LONGVARBINARY und LONGVARCHAR werden als SQL_UNSEARCHABLE gemeldet.<br /><br /> Binäre und Zeichen Datentypen mit fester Länge und variabler Länge sind durchsuchbar, obwohl LONGVARBINARY und LONGVARCHAR nicht sind.|  
  
> [!NOTE]  
>  Der obige Abschnitt ist keine komplette Liste der Attribute, die von **SQLColAttribute**zurückgegeben werden.
