---
title: SQLGetInfo (Textdateitreiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37d8d67300ec29a2b346f5f6b958c1955d08db0a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792168"
---
# <a name="sqlgetinfo-text-file-driver"></a>SQLGetInfo (Textdateitreiber)
> [!NOTE]  
>  Dieses Thema enthält die Textdatei-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLGetInfo** unterstützt die SQL_FILE_USAGE Informationstyp. Der zurückgegebene Wert ist eine 16-Bit-Ganzzahl, die angibt, wie der Treiber die Dateien in einer Datenquelle direkt behandelt:  
  
-   SQL_FILE_NOT_SUPPORTED – Der Treiber ist nicht nur einer Ebene Treiber.  
  
-   SQL_FILE_TABLE – Ein ein-Ebenen-Treiber behandelt Dateien in einer Datenquelle als Tabellen an.  
  
-   SQL_FILE_QUALIFIER – Ein ein-Ebenen-Treiber behandelt Dateien in einer Datenquelle als Qualifizierer an.  
  
 Der ODBC-Treiber gibt für die Textdriver SQL_FILE_TABLE zurück, da jede Datei eine Tabelle handelt.  
  
## <a name="sqldbmsver"></a>SQL_DBMS_VER  
  
|ISAM|Version|Format der Versionsnummer|  
|----------|-------------|-------------------------------|  
|Textmodus|1,0|01.00.0000|  
  
## <a name="sqlcatalogusage"></a>SQL_CATALOG_USAGE  
 SQL_QU_DML_STATEMENTS &AMP;#124; SQL_QU_TABLE_DEFINITION  
  
## <a name="sqltimedatefunctions"></a>SQL_TIMEDATE_FUNCTIONS  
 SQL_FN_TD_CURDATE &AMP;#124; SQL_FN_TD_CURTIME &AMP;#124; SQL_FN_TD_DAYOFMONTH &AMP;#124; SQL_FN_TD_DAYOFWEEK &AMP;#124; SQL_FN_TD_DAYOFYEAR &AMP;#124; SQL_FN_TD_HOUR &AMP;#124; SQL_FN_TD_MINUTE &AMP;#124; SQL_FN_TD_MONTH &AMP;#124; SQL_FN_TD_NOW &AMP;#124; SQL_FN_TD_SECOND &AMP;#124; SQL_FN_TD_WEEK &AMP;#124; SQL_FN_TD_YEAR
