---
title: Deskriptorfelder | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94e70de7d237c2eca9aee81979cb19d5295561b5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305921"
---
# <a name="descriptor-fields"></a>Deskriptorfelder
Deskriptoren enthalten *Header-* und *Datensatzfelder,* die Spalten oder Parameter vollständig beschreiben.  
  
 Ein Deskriptor enthält eine einzelne Kopie der folgenden Headerfelder. Das Ändern eines Kopfzeilenfeldes wirkt sich auf alle Spalten oder Parameter aus.  
  
|||  
|-|-|  
|SQL_DESC_ALLOC_TYPE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_COUNT|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 Ein Deskriptor enthält null oder mehr Deskriptordatensätze. Jeder Datensatz beschreibt eine Spalte oder einen Parameter, abhängig vom Typ des Deskriptors. Wenn eine neue Spalte oder ein neuer Parameter gebunden ist, wird dem Deskriptor ein neuer Datensatz hinzugefügt. Wenn eine Spalte oder ein Parameter ungebunden ist, wird ein Datensatz aus dem Deskriptor entfernt. Jeder Datensatz enthält eine einzelne Kopie der folgenden Felder:  
  
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
  
 Viele Anweisungsattribute entsprechen dem Kopfzeilenfeld eines Deskriptors. Das Festlegen dieser Attribute durch einen Aufruf von **SQLSetStmtAttr** und das Festlegen des entsprechenden Deskriptorheaderfelds durch Aufrufen von **SQLSetDescField** haben den gleichen Effekt. Dasselbe gilt für **SQLGetStmtAttr** und **SQLGetDescField**, die beide dieselben Informationen abrufen. Das Aufrufen der Anweisungsfunktionen anstelle der Deskriptorfunktionen hat den Vorteil, dass kein Deskriptorhandle abgerufen werden muss.  
  
 Die folgenden Headerfelder können durch Festlegen von Anweisungsattributen festgelegt werden:  
  
|||  
|-|-|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Anzahl der Datensätze](../../../odbc/reference/develop-app/record-count.md)  
  
-   [Gebundene Deskriptordatensätze](../../../odbc/reference/develop-app/bound-descriptor-records.md)  
  
-   [Zurückgestellte Felder](../../../odbc/reference/develop-app/deferred-fields.md)  
  
-   [Konsistenzprüfung](../../../odbc/reference/develop-app/consistency-check.md)
