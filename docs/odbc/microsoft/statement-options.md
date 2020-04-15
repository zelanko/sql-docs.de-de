---
title: Anweisungsoptionen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- custom statement options [ODBC]
- statement options [ODBC]
- ODBC driver for Oracle [ODBC], statement options
ms.assetid: cd73b769-c8b5-43e0-9f80-b3011b7a6162
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca40765dff98e9102fbe36e88c7e79535f311d97
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299210"
---
# <a name="statement-options"></a>Anweisungsoptionen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Diese Optionen ermöglichen die Anpassung einer bestimmten Ausführungsanweisung innerhalb einer Anwendung.  
  
|Anweisungsoption|Notizen|  
|----------------------|-----------|  
|SQL_BIND_TYPE|2.147.483.647 Byte oder verfügbaren Speicher dürfen nicht überschritten werden.|  
|SQL_CONCURRENCY|Zulässige Werte finden Sie im [Cursortyp und in den Parallelitätskombinationen](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_CURSOR_TYPE|Der Treiber lässt SQL_CURSOR_DYNAMIC nicht zu. Weitere Informationen finden Sie unter [SQLSetScrollOptions.](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) Zulässige Werte finden Sie im [Cursortyp und in den Parallelitätskombinationen](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_GET_BOOKMARK|Gibt einen 32-Bit-Ganzzahlwert zurück, der das Lesezeichen für die aktuelle Datensatznummer ist. Nur erhalten; kann nicht festgelegt werden.|  
|SQL_KEYSET_SIZE|Kann nur auf 0 gesetzt werden.|  
|SQL_MAX_ROWS|Die maximale Anzahl von Zeilen, die von einem Resultset zurückgegeben werden sollen.|  
|SQL_ROW_NUMBER|Gibt eine 32-Bit-Ganzzahl zurück, die die Position der aktuellen Zeile innerhalb des Resultsets angibt. Nur erhalten; kann nicht festgelegt werden.|  
|SQL_ROWSET_SIZE|4.294.967.296 Zeilen nicht überschreiten; Sie müssen jedoch über genügend virtuellen Speicher auf Ihrem Computer verfügen, um Ihre Anforderung zu verarbeiten.|  
|SQL_USE_BOOKMARKS|Unterstützt das Festlegen SQL_USE_BOOKMARKS auf SQL_UB_ON und macht Lesezeichen mit fester Länge verfügbar.|
