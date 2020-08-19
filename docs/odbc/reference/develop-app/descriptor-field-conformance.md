---
description: Deskriptorfeldübereinstimmung
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
ms.openlocfilehash: 36687cf456f4fcbbaa3f4b029e51098815dec3f4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476742"
---
# <a name="descriptor-field-conformance"></a>Deskriptorfeldübereinstimmung
In der folgenden Tabelle ist die Übereinstimmungs Stufe der einzelnen ODBC-deskriptorheader Felder angegeben, in denen diese ordnungsgemäß definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_DESC_ALLOC_TYPE|Core|  
|SQL_DESC_ARRAY_SIZE|Core|  
|SQL_DESC_ARRAY_STATUS_PTR|Core (für APD, IPR und IRD); Ebene 1 (für die ARD)|  
|SQL_DESC_BIND_OFFSET_PTR|Core|  
|SQL_DESC_BIND_TYPE|Core|  
|SQL_DESC_COUNT|Core|  
|SQL_DESC_ROWS_PROCESSED_PTR|Core|  
  
 In der folgenden Tabelle ist die Übereinstimmungs Stufe der einzelnen ODBC-Deskriptordatensatz-Felder angegeben, in denen diese klar definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Ebene 2|  
|SQL_DESC_BASE_COLUMN_NAME|Core|  
|SQL_DESC_BASE_TABLE_NAME|Ebene 1|  
|SQL_DESC_CASE_SENSITIVE|Core|  
|SQL_DESC_CATALOG_NAME|Ebene 2|  
|SQL_DESC_CONCISE_TYPE|Core|  
|SQL_DESC_DATA_PTR|Core|  
|SQL_DESC_DATETIME_INTERVAL_-Code|Kern [1]|  
|SQL_DESC_DATETIME_INTERVAL_ Genauigkeit|Kern [1]|  
|SQL_DESC_DISPLAY_SIZE|Core|  
|SQL_DESC_FIXED_PREC_SCALE|Core|  
|SQL_DESC_INDICATOR_PTR|Core|  
|SQL_DESC_LABEL|Ebene 2|  
|SQL_DESC_LENGTH|Core|  
|SQL_DESC_LITERAL_PREFIX|Core|  
|SQL_DESC_LITERAL_SUFFIX|Core|  
|SQL_DESC_LOCAL_TYPE_NAME|Core|  
|SQL_DESC_NAME|Core|  
|SQL_DESC_NULLABLE|Core|  
|SQL_DESC_OCTET_LENGTH|Core|  
|SQL_DESC_OCTET_LENGTH_PTR|Core|  
|SQL_DESC_PARAMETER_TYPE|Kern/Ebene 2 [2]|  
|SQL_DESC_PRECISION|Core|  
|SQL_DESC_ROWVER|Ebene 1|  
|SQL_DESC_SCALE|Core|  
|SQL_DESC_SCHEMA_NAME|Ebene 1|  
|SQL_DESC_SEARCHABLE|Core|  
|SQL_DESC_TABLE_NAME|Ebene 1|  
|SQL_DESC_TYPE|Core|  
|SQL_DESC_TYPE_NAME|Core|  
|SQL_DESC_UNNAMED|Core|  
|SQL_DESC_UNSIGNED|Core|  
|SQL_DESC_UPDATABLE|Core|  
  
 [1] die Unterstützung für diese Daten Satz Felder ist nur erforderlich, wenn der Treiber die anwendbaren Datentypen unterstützt.  
  
 [2] für die Konformität auf Kern Ebene muss der Treiber SQL_PARAM_INPUT unterstützen. Bei der Schnittstellen Konformität der Ebene 2 muss der Treiber auch SQL_PARAM_INPUT_OUTPUT und SQL_PARAM_OUTPUT unterstützen.
