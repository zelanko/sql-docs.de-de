---
title: Deskriptoren und Desktop-Datenbanktreiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], descriptors
- Jet-based ODBC drivers [ODBC], descriptors
- descriptors [ODBC], Jet-supported descriptor fields
- ODBC desktop database drivers [ODBC], descriptors
ms.assetid: 9ae2d9b5-365f-4f0a-9116-defe9498b401
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c0096dad8fbb4cf9847385759702e39ac074c4c6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68112051"
---
# <a name="descriptors-and-desktop-database-drivers"></a>Deskriptoren und Desktop-Datenbanktreiber
Ein Deskriptor ist eine Datenstruktur, die Informationen zu Spaltendaten oder dynamischen Parametern enthält. **SQLGetDescField** kann verwendet werden, um die unten aufgeführten unterstützten Deskriptoren abzurufen. Implementierungs Parameter Deskriptoren (IPD) werden nicht automatisch aufgefüllt, da **SQLDescribeParam** nicht unterstützt wird. Deskriptorfelder, die nicht über Jet (z. b. SQL_DESC_BASE_TABLE_NAME) verfügbar sind, werden ebenfalls nicht unterstützt.  
  
 Weitere Informationen zu den von Jet unterstützten Deskriptorfeldern finden Sie im *Microsoft Jet Datenbank-Engine Programmer es Guide*.  
  
 Weitere Informationen zu Deskriptoren finden Sie in den Themen unter "Deskriptoren" in der *ODBC Programmer es Reference*.  
  
|Deskriptorfelder|Supportebene|  
|-----------------------|-------------------|  
|SQL_DESC_ALLOC_TYPE|Unterstützt|  
|SQL_DESC_ARRAY_SIZE|Nur für ARD unterstützt|  
|SQL_DESC_ARRAY_STATUS_PTR|Unterstützt|  
|SQL_DESC_BIND_OFFSET_PTR|Unterstützt|  
|SQL_DESC_BIND_TYPE|Unterstützt|  
|SQL_DESC_COUNT|Unterstützt|  
|SQL_DESC_ROWS_PROCESSED_PTR|Nur für ARD unterstützt|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Unterstützt|  
|SQL_DESC_BASE_COLUMN_NAME|Unterstützt (neu)|  
|SQL_DESC_BASE_TABLE_NAME|Unterstützt (neu)|  
|SQL_DESC_CASE_SENSITIVE|Immer false|  
|SQL_DESC_CATALOG_NAME|Nicht unterstützt|  
|SQL_DESC_CONCISE_TYPE|Unterstützt|  
|SQL_DESC_DATA_PTR|Unterstützt|  
|SQL_DESC_DATETIME_INTERVAL_CODE|Unterstützt|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|Unterstützt für Interval C-Typen|  
|SQL_DESC_DISPLAY_SIZE|Unterstützt|  
|SQL_DESC_FIXED_PREC_SCALE|Unterstützt (true für Money)|  
|SQL_DESC_INDICATOR_PTR|Unterstützt|  
|SQL_DESC_LABEL|Unterstützt|  
|SQL_DESC_LENGTH|Unterstützt|  
|SQL_DESC_LITERAL_PREFIX|Unterstützt|  
|SQL_DESC_LITERAL_SUFFIX|Unterstützt|  
|SQL_DESC_LOCAL_TYPE_NAME|Nicht unterstützt (gibt eine leere Zeichenfolge zurück)|  
|SQL_DESC_NAME|Unterstützt|  
|SQL_DESC_NULLABLE|Unterstützt<br /><br /> **Hinweis** Nicht unterstützt in den vor dem Jet 4,0 vorangehenden Versionen|  
|SQL_DESC_NUM_PREC_RADIX|Unterstützt|  
|SQL_DESC_OCTET_LENGTH|Unterstützt|  
|SQL_DESC_OCTET_LENGTH_PTR|Unterstützt|  
|SQL_DESC_PARAMETER_TYPE|Nur Eingabeparameter|  
|SQL_DESC_PRECISION|Unterstützt|  
|SQL_DESC_SCALE|Unterstützt|  
|SQL_DESC_SCHEMA_NAME|Nicht unterstützt|  
|SQL_DESC_SEARCHABLE|Unterstützt|  
|SQL_DESC_TABLE_NAME|Nicht unterstützt|  
|SQL_DESC_TYPE|Unterstützt|  
|SQL_DESC_TYPE_NAME|Unterstützt|  
|SQL_DESC_UNNAMED|Unterstützt|  
|SQL_DESC_UNSIGNED|Unterstützt|  
|SQL_DESC_UPDATABLE|Unterstützt|
