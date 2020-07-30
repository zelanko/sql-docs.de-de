---
title: Deskriptorfelder | Microsoft-Dokumentation
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
ms.openlocfilehash: d363c3e42a97c5d520c1a693ebed935b202b7247
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87362560"
---
# <a name="descriptor-fields"></a>Deskriptorfelder
Deskriptoren enthalten *Header* -und *Daten Satz* Felder, in denen Spalten oder Parameter vollständig beschrieben werden.  
  
 Ein Deskriptor enthält eine einzelne Kopie der folgenden Header Felder. Das Ändern eines Header Felds wirkt sich auf alle Spalten oder Parameter aus.  

:::row:::
    :::column:::
        SQL_DESC_ALLOC_TYPE  
        SQL_DESC_ARRAY_SIZE  
        SQL_DESC_ARRAY_STATUS_PTR  
        SQL_DESC_BIND_OFFSET_PTR  
    :::column-end:::
    :::column:::
        SQL_DESC_BIND_TYPE  
        SQL_DESC_COUNT  
        SQL_DESC_ROWS_PROCESSED_PTR  
    :::column-end:::
:::row-end:::

 Ein Deskriptor enthält keine oder mehrere deskriptordaten Sätze. Jeder Datensatz beschreibt eine Spalte oder einen Parameter, abhängig vom Typ des Deskriptors. Wenn eine neue Spalte oder ein neuer Parameter gebunden wird, wird dem Deskriptor ein neuer Datensatz hinzugefügt. Wenn eine Spalte oder ein Parameter nicht gebunden ist, wird ein Datensatz aus dem Deskriptor entfernt. Jeder Datensatz enthält eine einzelne Kopie der folgenden Felder:  

:::row:::
    :::column:::
        SQL_DESC_AUTO_UNIQUE_VALUE  
        SQL_DESC_BASE_COLUMN_NAME  
        SQL_DESC_BASE_TABLE_NAME  
        SQL_DESC_CASE_SENSITIVE  
        SQL_DESC_CATALOG_NAME  
        SQL_DESC_CONCISE_TYPE  
        SQL_DESC_DATA_PTR  
        SQL_DESC_DATETIME_INTERVAL_CODE  
        SQL_DESC_DATETIME_INTERVAL_PRECISION  
        SQL_DESC_DISPLAY_SIZE  
        SQL_DESC_FIXED_PREC_SCALE  
        SQL_DESC_INDICATOR_PTR  
        SQL_DESC_LABEL  
        SQL_DESC_LENGTH  
        SQL_DESC_LITERAL_PREFIX  
        SQL_DESC_LITERAL_SUFFIX  
    :::column-end:::
    :::column:::
        SQL_DESC_LOCAL_TYPE_NAME  
        SQL_DESC_NAME  
        SQL_DESC_NULLABLE  
        SQL_DESC_OCTET_LENGTH  
        SQL_DESC_OCTET_LENGTH_PTR  
        SQL_DESC_PARAMETER_TYPE  
        SQL_DESC_PRECISION  
        SQL_DESC_SCALE  
        SQL_DESC_SCHEMA_NAME  
        SQL_DESC_SEARCHABLE  
        SQL_DESC_TABLE_NAME  
        SQL_DESC_TYPE  
        SQL_DESC_TYPE_NAME  
        SQL_DESC_UNNAMED  
        SQL_DESC_UNSIGNED  
        SQL_DESC_UPDATABLE  
    :::column-end:::
:::row-end:::

 Viele Anweisungs Attribute entsprechen dem Header Feld eines Deskriptors. Wenn diese Attribute durch einen Aufruf von **SQLSetStmtAttr** festgelegt werden und das entsprechende Deskriptorheaderfeld durch Aufrufen von **SQLSetDescField** festgelegt wird, hat dies die gleiche Wirkung. Das gleiche gilt für **SQLGetStmtAttr** und **SQLGetDescField**, von denen beide dieselben Informationen abrufen. Das Aufrufen der Anweisungs Funktionen anstelle der deskriptorfunktionen hat den Vorteil, dass ein Deskriptorhandle nicht abgerufen werden muss.  
  
 Die folgenden Header Felder können durch Festlegen der Anweisungs Attribute festgelegt werden:  

:::row:::
    :::column:::
        SQL_DESC_ARRAY_SIZE  
        SQL_DESC_ARRAY_STATUS_PTR  
        SQL_DESC_BIND_OFFSET_PTR  
    :::column-end:::
    :::column:::
        SQL_DESC_BIND_TYPE  
        SQL_DESC_ROWS_PROCESSED_PTR  
    :::column-end:::
:::row-end:::

 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Anzahl der Datensätze](../../../odbc/reference/develop-app/record-count.md)  
  
-   [Gebundene Deskriptordatensätze](../../../odbc/reference/develop-app/bound-descriptor-records.md)  
  
-   [Zurückgestellte Felder](../../../odbc/reference/develop-app/deferred-fields.md)  
  
-   [Konsistenzprüfung](../../../odbc/reference/develop-app/consistency-check.md)
