---
title: Deskriptorfelder für | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], fields
- header fields [ODBC]
- record fields [ODBC]
ms.assetid: f38623c8-fdd4-4601-b1f0-97c593d31177
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b512ff83d0002ef4a7c79b48cd8829fc2dbb9ba3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63049776"
---
# <a name="descriptor-fields"></a>Deskriptorfelder
Sicherheitsbeschreibungen enthalten *Header* und *Datensatz* Felder, die Spalten oder Parametern vollständig zu beschreiben.  
  
 Ein Deskriptor enthält eine einzige Kopie eines der folgenden Headerfelder. Ändern ein Headerfeld wirkt sich auf alle Spalten oder Parametern.  
  
|||  
|-|-|  
|SQL_DESC_ALLOC_TYPE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_COUNT|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 Ein Deskriptor enthält null oder mehr deskriptordatensätze. Jeder Datensatz wird beschrieben, eine Spalte oder des Parameters, je nach Art des Deskriptors. Wenn eine neue Spalte oder Parameter gebunden ist, wird ein neuer Datensatz auf den Deskriptor hinzugefügt. Wenn eine Spalte oder Parameter aufgehoben wird, wird ein Datensatz aus der Deskriptor entfernt. Jeder Datensatz enthält eine einzige Kopie der folgenden Felder:  
  
|||  
|-|-|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_DESC_LOCAL_TYPE_NAME|  
|SQL_DESC_BASE_COLUMN_NAME|SQL_DESC_NAME|  
|SQL_DESC_BASE_TABLE_NAME|SQL_DESC_NULLABLE|  
|SQL_DESC_CASE_SENSITIVE|SQL_DESC_OCTET_LENGTH|  
|SQL_DESC_CATALOG_NAME|SQL_DESC_OCTET_LENGTH_PTR|  
|SQL_DESC_CONCISE_TYPE|SQL_DESC_PARAMETER_TYPE|  
|SQL_DESC_DATA_PTR|SQL_DESC_PRECISION|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_DESC_SCALE|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|SQL_DESC_SCHEMA_NAME|  
|SQL_DESC_DISPLAY_SIZE|SQL_DESC_SEARCHABLE|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_DESC_TABLE_NAME|  
|SQL_DESC_INDICATOR_PTR|SQL_DESC_TYPE|  
|SQL_DESC_LABEL|SQL_DESC_TYPE_NAME|  
|SQL_DESC_LENGTH|SQL_DESC_UNNAMED|  
|SQL_DESC_LITERAL_PREFIX|SQL_DESC_UNSIGNED|  
|SQL_DESC_LITERAL_SUFFIX|SQL_DESC_UPDATABLE|  
  
 Das Headerfeld einen Deskriptor entsprechen viele Anweisungsattribute. Diese Attribute durch einen Aufruf von **SQLSetStmtAttr** und Festlegen der entsprechenden deskriptorheaderfeld durch Aufrufen von **SQLSetDescField** haben den gleichen Effekt. Das gleiche gilt für **SQLGetStmtAttr** und **SQLGetDescField**, beide die gleiche Informationen abzurufen. Aufrufen der Funktionen der Anweisung anstelle der Deskriptor Funktionen hat den Vorteil, die ein Handle für die Sicherheitsbeschreibung nicht abgerufen werden sollen.  
  
 Die folgenden Headerfelder können durch Festlegen von Anweisungsattribute festgelegt werden:  
  
|||  
|-|-|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Anzahl der Datensätze](../../../odbc/reference/develop-app/record-count.md)  
  
-   [Gebundene Deskriptordatensätze](../../../odbc/reference/develop-app/bound-descriptor-records.md)  
  
-   [Zurückgestellte Felder](../../../odbc/reference/develop-app/deferred-fields.md)  
  
-   [Konsistenzprüfung](../../../odbc/reference/develop-app/consistency-check.md)
