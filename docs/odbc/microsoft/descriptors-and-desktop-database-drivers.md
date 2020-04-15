---
title: Deskriptoren und Desktopdatenbanktreiber | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ef79855f71d23e5a884822371f1894eb83442a9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303511"
---
# <a name="descriptors-and-desktop-database-drivers"></a>Deskriptoren und Desktop-Datenbanktreiber
Ein Deskriptor ist eine Datenstruktur, die Informationen über Spaltendaten oder dynamische Parameter enthält. **SQLGetDescField** kann verwendet werden, um die unten aufgeführten unterstützten Deskriptoren abzurufen. Implementierungsparameterdeskriptoren (IPD) werden nicht automatisch aufgefüllt, da **SQLDescribeParam** nicht unterstützt wird. Deskriptorfelder, die über Jet nicht verfügbar sind (z. B. SQL_DESC_BASE_TABLE_NAME), werden ebenfalls nicht unterstützt.  
  
 Weitere Informationen zu Jet-unterstützten Deskriptorfeldern finden Sie im *Microsoft Jet Database Engine Programmer es Guide*.  
  
 Weitere Informationen zu Deskriptoren finden Sie in den Themen unter "Deskriptoren" in der *ODBC-Programmiererreferenz*.  
  
|Deskriptorfelder|Supportebene|  
|-----------------------|-------------------|  
|SQL_DESC_ALLOC_TYPE|Unterstützt|  
|SQL_DESC_ARRAY_SIZE|Nur für die ARD unterstützt|  
|SQL_DESC_ARRAY_STATUS_PTR|Unterstützt|  
|SQL_DESC_BIND_OFFSET_PTR|Unterstützt|  
|SQL_DESC_BIND_TYPE|Unterstützt|  
|SQL_DESC_COUNT|Unterstützt|  
|SQL_DESC_ROWS_PROCESSED_PTR|Nur für die ARD unterstützt|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Unterstützt|  
|SQL_DESC_BASE_COLUMN_NAME|Unterstützt (NEU)|  
|SQL_DESC_BASE_TABLE_NAME|Unterstützt (NEU)|  
|SQL_DESC_CASE_SENSITIVE|Immer FALSE|  
|SQL_DESC_CATALOG_NAME|Nicht unterstützt|  
|SQL_DESC_CONCISE_TYPE|Unterstützt|  
|SQL_DESC_DATA_PTR|Unterstützt|  
|SQL_DESC_DATETIME_INTERVAL_CODE|Unterstützt|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|Unterstützt für INTERVAL C-Typen|  
|SQL_DESC_DISPLAY_SIZE|Unterstützt|  
|SQL_DESC_FIXED_PREC_SCALE|Unterstützt (TRUE für Geld)|  
|SQL_DESC_INDICATOR_PTR|Unterstützt|  
|SQL_DESC_LABEL|Unterstützt|  
|SQL_DESC_LENGTH|Unterstützt|  
|SQL_DESC_LITERAL_PREFIX|Unterstützt|  
|SQL_DESC_LITERAL_SUFFIX|Unterstützt|  
|SQL_DESC_LOCAL_TYPE_NAME|Nicht unterstützt (gibt EMPTY-Zeichenfolge zurück)|  
|SQL_DESC_NAME|Unterstützt|  
|SQL_DESC_NULLABLE|Unterstützt<br /><br /> **Hinweis** Nicht unterstützt in Versionen vor Jet 4.0|  
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
