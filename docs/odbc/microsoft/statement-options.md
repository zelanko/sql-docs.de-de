---
description: Anweisungsoptionen
title: Anweisungs Optionen | Microsoft-Dokumentation
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
ms.openlocfilehash: 024fc10441f3b24da33d5742fdd15454561187c4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449142"
---
# <a name="statement-options"></a>Anweisungsoptionen
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Verwenden Sie stattdessen den von Oracle bereitgestellten ODBC-Treiber.  
  
 Diese Optionen ermöglichen die Anpassung einer bestimmten Ausführungs Anweisung in einer Anwendung.  
  
|Anweisungs Option|Notizen|  
|----------------------|-----------|  
|SQL_BIND_TYPE|Darf nicht mehr als 2.147.483.647 Bytes oder den verfügbaren Arbeitsspeicher|  
|SQL_CONCURRENCY|Zulässige Werte finden Sie unter [Cursor Type und](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md)Parallelitäts Kombinationen.|  
|SQL_CURSOR_TYPE|Der Treiber lässt keine SQL_CURSOR_DYNAMIC zu. Weitere Informationen finden Sie unter [SQLSetScrollOptions](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) . Zulässige Werte finden Sie unter [Cursor Type und](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md)Parallelitäts Kombinationen.|  
|SQL_GET_BOOKMARK|Gibt einen ganzzahligen 32-Bit-Wert zurück, der das Lesezeichen für die aktuelle Datensatznummer ist. Nur Get; Festlegen von nicht möglich.|  
|SQL_KEYSET_SIZE|Kann nur auf 0 festgelegt werden.|  
|SQL_MAX_ROWS|Die maximale Anzahl von Zeilen, die aus einem Resultset zurückgegeben werden sollen.|  
|SQL_ROW_NUMBER|Gibt eine 32-Bit-Ganzzahl zurück, die die Position der aktuellen Zeile innerhalb des Resultsets angibt. Nur Get; Festlegen von nicht möglich.|  
|SQL_ROWSET_SIZE|Kann 4.294.967.296 Zeilen nicht überschreiten. Sie müssen jedoch über ausreichend virtuellen Arbeitsspeicher auf dem Computer verfügen, um Ihre Anforderung zu verarbeiten.|  
|SQL_USE_BOOKMARKS|Unterstützt das Festlegen von SQL_USE_BOOKMARKS zum SQL_UB_ON und verfügbar machen von Lesezeichen mit fester Länge.|
