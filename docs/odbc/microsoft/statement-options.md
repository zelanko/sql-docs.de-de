---
title: Anweisungsoptionen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fe57ffa0d7628601fcb6dd19218715b32a57322b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270014"
---
# <a name="statement-options"></a>Anweisungsoptionen
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den ODBC-Treiber, die von Oracle bereitgestellt.  
  
 Diese Optionen ermöglichen die Anpassung einer bestimmten Ausführung-Anweisung in einer Anwendung.  
  
|Option-Anweisung|Hinweise|  
|----------------------|-----------|  
|SQL_BIND_TYPE|Kann 2.147.483.647 Bytes oder Speicherplatz nicht überschreiten.|  
|SQL_CONCURRENCY|Zulässige Werte finden Sie in der [Cursortyp und Parallelitätskombinationen](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_CURSOR_TYPE|Der Treiber lässt sich nicht auf SQL_CURSOR_DYNAMIC aus. Finden Sie unter [SQLSetScrollOptions](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) für Weitere Informationen. Zulässige Werte finden Sie in der [Cursortyp und Parallelitätskombinationen](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_GET_BOOKMARK|Gibt einen 32-Bit-Ganzzahl-Wert, der das Lesezeichen für die Nummer des aktuellen Datensatzes ist. Erhalten Sie nur; kann nicht festgelegt.|  
|SQL_KEYSET_SIZE|Kann nur auf 0 festgelegt werden.|  
|SQL_MAX_ROWS|Legen Sie die maximale Anzahl von Zeilen aus einem Resultset zurückgegeben.|  
|SQL_ROW_NUMBER|Gibt eine 32-Bit-Ganzzahl, die die Position der aktuellen Zeile im Resultset angeben. Erhalten Sie nur; kann nicht festgelegt.|  
|SQL_ROWSET_SIZE|4.294.967.296 Zeilen darf nicht überschreiten; Allerdings müssen Sie genügend virtuellen Arbeitsspeicher auf dem Computer zur Verarbeitung Ihrer Anforderung verfügen.|  
|SQL_USE_BOOKMARKS|Unterstützt das Festlegen von SQL_USE_BOOKMARKS zu SQL_UB_ON und macht Lesezeichen mit fester Länge.|
