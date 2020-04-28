---
title: Deskriptorfeld Konformität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptor field conformance levels [ODBC]
- conformance levels [ODBC], descriptor field
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 6c29d93b-696c-4960-bff3-4d6bc41bc513
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cce33adfdbfceef56936b22c549b6762521b4798
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305931"
---
# <a name="descriptor-field-conformance"></a>Deskriptorfeldübereinstimmung
In der folgenden Tabelle ist die Übereinstimmungs Stufe der einzelnen ODBC-deskriptorheader Felder angegeben, in denen diese ordnungsgemäß definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|Kernspeicher|  
|SQL_DESC_ARRAY_SIZE|Kernspeicher|  
|SQL_DESC_ARRAY_STATUS_PTR|Core (für APD, IPR und IRD); Ebene 1 (für die ARD)|  
|SQL_DESC_BIND_OFFSET_PTR|Kernspeicher|  
|SQL_DESC_BIND_TYPE|Kernspeicher|  
|SQL_DESC_COUNT|Kernspeicher|  
|SQL_DESC_ROWS_PROCESSED_PTR|Kernspeicher|  
  
 In der folgenden Tabelle ist die Übereinstimmungs Stufe der einzelnen ODBC-Deskriptordatensatz-Felder angegeben, in denen diese klar definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Ebene 2|  
|SQL_DESC_BASE_COLUMN_NAME|Kernspeicher|  
|SQL_DESC_BASE_TABLE_NAME|Ebene 1|  
|SQL_DESC_CASE_SENSITIVE|Kernspeicher|  
|SQL_DESC_CATALOG_NAME|Ebene 2|  
|SQL_DESC_CONCISE_TYPE|Kernspeicher|  
|SQL_DESC_DATA_PTR|Kernspeicher|  
|SQL_DESC_DATETIME_INTERVAL_-Code|Kern [1]|  
|SQL_DESC_DATETIME_INTERVAL_ Genauigkeit|Kern [1]|  
|SQL_DESC_DISPLAY_SIZE|Kernspeicher|  
|SQL_DESC_FIXED_PREC_SCALE|Kernspeicher|  
|SQL_DESC_INDICATOR_PTR|Kernspeicher|  
|SQL_DESC_LABEL|Ebene 2|  
|SQL_DESC_LENGTH|Kernspeicher|  
|SQL_DESC_LITERAL_PREFIX|Kernspeicher|  
|SQL_DESC_LITERAL_SUFFIX|Kernspeicher|  
|SQL_DESC_LOCAL_TYPE_NAME|Kernspeicher|  
|SQL_DESC_NAME|Kernspeicher|  
|SQL_DESC_NULLABLE|Kernspeicher|  
|SQL_DESC_OCTET_LENGTH|Kernspeicher|  
|SQL_DESC_OCTET_LENGTH_PTR|Kernspeicher|  
|SQL_DESC_PARAMETER_TYPE|Kern/Ebene 2 [2]|  
|SQL_DESC_PRECISION|Kernspeicher|  
|SQL_DESC_ROWVER|Ebene 1|  
|SQL_DESC_SCALE|Kernspeicher|  
|SQL_DESC_SCHEMA_NAME|Ebene 1|  
|SQL_DESC_SEARCHABLE|Kernspeicher|  
|SQL_DESC_TABLE_NAME|Ebene 1|  
|SQL_DESC_TYPE|Kernspeicher|  
|SQL_DESC_TYPE_NAME|Kernspeicher|  
|SQL_DESC_UNNAMED|Kernspeicher|  
|SQL_DESC_UNSIGNED|Kernspeicher|  
|SQL_DESC_UPDATABLE|Kernspeicher|  
  
 [1] die Unterstützung für diese Daten Satz Felder ist nur erforderlich, wenn der Treiber die anwendbaren Datentypen unterstützt.  
  
 [2] für die Konformität auf Kern Ebene muss der Treiber SQL_PARAM_INPUT unterstützen. Bei der Schnittstellen Konformität der Ebene 2 muss der Treiber auch SQL_PARAM_INPUT_OUTPUT und SQL_PARAM_OUTPUT unterstützen.
