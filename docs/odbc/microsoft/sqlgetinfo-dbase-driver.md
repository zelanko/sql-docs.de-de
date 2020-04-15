---
title: SQLGetInfo (dBASE-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLGetInfo
ms.assetid: 42ffdc9c-281b-4df5-ac6d-7b34f15ecd4c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9ac88f3b563ef7811d9112d8ef7169f533691938
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298600"
---
# <a name="sqlgetinfo-dbase-driver"></a>SQLGetInfo (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält dBASE-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLGetInfo** unterstützt den SQL_FILE_USAGE-Informationstyp. Der zurückgegebene Wert ist eine 16-Bit-Ganzzahl, die angibt, wie der Treiber Dateien in einer Datenquelle direkt behandelt:  
  
-   SQL_FILE_NOT_SUPPORTED - Der Treiber ist kein einstufiger Treiber.  
  
-   SQL_FILE_TABLE - Ein einstufiger Treiber behandelt Dateien in einer Datenquelle als Tabellen.  
  
-   SQL_FILE_QUALIFIER - Ein einstufiger Treiber behandelt Dateien in einer Datenquelle als Qualifizierer.  
  
 Der ODBC-Treiber gibt SQL_FILE_TABLE zurück, da jede Datei eine Tabelle ist.  
  
## <a name="sql_alter_table"></a>SQL_ALTER_TABLE  
 SQL_AT_ADD_COLUMN &#124; SQL_AT_DROP_COLUMN  
  
## <a name="sql_dbms_ver"></a>SQL_DBMS_VER  
  
|Isam|Version|Format der Versionsnummern|  
|----------|-------------|-------------------------------|  
|Dbase|3.0|03.00.0000|  
||4,0|04.00.0000|  
||5.0|05.00.0000|  
  
## <a name="sql_ddl_index"></a>SQL_DDL_INDEX  
 SQL_DL_CREATE_INDEX  
  
 SQL_DL_DROP_INDEX  
  
## <a name="sql_catalog_usage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION &#124; SQL_QU_INDEX_DEFINITION  
  
## <a name="sql_timedate_functions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_DAYOFMONTH &#124; SQL_FN_TD_DAYOFWEEK &#124; SQL_FN_TD_DAYOFYEAR &#124; SQL_FN_TD_HOUR &#124; SQL_FN_TD_MINUTE &#124; SQL_FN_TD_MONTH &#124; SQL_FN_TD_SECOND &#124; SQL_FN_TD_WEEK &#124; SQL_FN_TD_YEAR
