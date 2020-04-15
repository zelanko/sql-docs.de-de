---
title: SQLGetInfo (Textdateitreiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetInfo
ms.assetid: 6b7a630e-47f8-4ee1-b2a7-476bc1d0b0d4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 09ca2e42e20a6f314de3b68fe5d5b143f41269c3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298501"
---
# <a name="sqlgetinfo-text-file-driver"></a>SQLGetInfo (Textdateitreiber)
> [!NOTE]  
>  Dieses Thema enthält Textdateitreiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLGetInfo** unterstützt den SQL_FILE_USAGE-Informationstyp. Der zurückgegebene Wert ist eine 16-Bit-Ganzzahl, die angibt, wie der Treiber Dateien in einer Datenquelle direkt behandelt:  
  
-   SQL_FILE_NOT_SUPPORTED - Der Treiber ist kein einstufiger Treiber.  
  
-   SQL_FILE_TABLE - Ein einstufiger Treiber behandelt Dateien in einer Datenquelle als Tabellen.  
  
-   SQL_FILE_QUALIFIER - Ein einstufiger Treiber behandelt Dateien in einer Datenquelle als Qualifizierer.  
  
 Der ODBC-Treiber gibt SQL_FILE_TABLE für den Textdriver zurück, da jede Datei eine Tabelle ist.  
  
## <a name="sql_dbms_ver"></a>SQL_DBMS_VER  
  
|Isam|Version|Format der Versionsnummern|  
|----------|-------------|-------------------------------|  
|Text|1.0|01.00.0000|  
  
## <a name="sql_catalog_usage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &#124; SQL_QU_TABLE_DEFINITION  
  
## <a name="sql_timedate_functions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_CURDATE &#124; SQL_FN_TD_CURTIME &#124; SQL_FN_TD_DAYOFMONTH &#124; SQL_FN_TD_DAYOFWEEK &#124; SQL_FN_TD_DAYOFYEAR &#124; SQL_FN_TD_HOUR &#124; SQL_FN_TD_MINUTE &#124; SQL_FN_TD_MONTH &#124; SQL_FN_TD_NOW &#124; SQL_FN_TD_SECOND &#124; SQL_FN_TD_WEEK &#124; SQL_FN_TD_YEAR
