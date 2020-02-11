---
title: SQLGetInfo (Paradox-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Paradox driver [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], Paradox Driver
ms.assetid: 43aab762-68f4-4128-b8f5-8878ea5f1258
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a35f3bdbd68b674736ac22f447a8be45c1342682
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68003245"
---
# <a name="sqlgetinfo-paradox-driver"></a>SQLGetInfo (Paradox-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Paradox-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLGetInfo** unterstützt den SQL_FILE_USAGE Informationstyp. Der zurückgegebene Wert ist eine 16-Bit-Ganzzahl, die angibt, wie der Treiberdateien direkt in einer Datenquelle behandelt:  
  
-   SQL_FILE_NOT_SUPPORTED: der Treiber ist kein Single-Tier-Treiber.  
  
-   SQL_FILE_TABLE: ein Single-Tier-Treiber behandelt Dateien in einer Datenquelle als Tabellen.  
  
-   SQL_FILE_QUALIFIER: ein Single-Tier-Treiber behandelt Dateien in einer Datenquelle als Qualifizierer.  
  
 Der ODBC-Treiber gibt SQL_FILE_TABLE zurück, da jede Datei eine Tabelle ist.  
  
## <a name="sql_alter_table"></a>SQL_ALTER_TABLE  
 SQL_AT_ADD_COLUMN &#124; SQL_AT_DROP_COLUMN  
  
## <a name="sql_ddl_index"></a>SQL_DDL_INDEX  
 SQL_DL_CREATE_INDEX  
  
 SQL_DL_DROP_INDEX  
  
## <a name="sql_dbms_ver"></a>SQL_DBMS_VER  
  
|ISAM|Version|Format der Versionsnummern|  
|----------|-------------|-------------------------------|  
|Gewissen|3.x|03.00.0000|  
||4.x|04.00.0000|  
||5. x|05.00.0000|  
  
## <a name="sql_catalog_usage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION &#124; SQL_QU_INDEX_DEFINITION  
  
## <a name="sql_timedate_functions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_DAYOFMONTH &#124; SQL_FN_TD_DAYOFWEEK &#124; SQL_FN_TD_DAYOFYEAR &#124; SQL_FN_TD_HOUR &#124; SQL_FN_TD_MINUTE &#124; SQL_FN_TD_MONTH &#124; SQL_FN_TD_SECOND &#124; SQL_FN_TD_WEEK &#124; SQL_FN_TD_YEAR
