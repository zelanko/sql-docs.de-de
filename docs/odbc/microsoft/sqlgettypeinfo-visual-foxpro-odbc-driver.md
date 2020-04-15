---
title: SQLGetTypeInfo (Visual FoxPro ODBC-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5f25e20b-a4ef-42da-aeb6-00e0510fb1cc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 23db0350f0f7271f85e2bc5c6a9e6c8767443a85
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299520"
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (Visual FoxPro-ODBC-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Visual FoxPro ODBC-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Support: Voll  
  
 ODBC-API-Konformität: Ebene 1  
  
 Gibt Informationen zu den Datentypen zurück, die von einer Datenquelle unterstützt werden. Der Treiber gibt die Informationen in einem SQL-Ergebnissatz zurück. In der folgenden Tabelle sind ODBC-Datentypen und der entsprechende Visual FoxPro-Datentyp aufgeführt.  
  
|ODBC-Typ|Visual FoxPro-Typ|  
|---------------|------------------------|  
|SQL_BIGINT|Wird nicht unterstützt. Es gibt keinen 64-Bit Visual FoxPro-Typ.|  
|SQL_BIT|Logisch|  
|SQL_CHAR|Zeichen|  
|SQL_DATE|Date|  
|SQL_DECIMAL|Numeric|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Integer|  
|SQL_LONGVARBINARY|Memo (Binär)|  
|SQL_LONGVARCHAR|Memo|  
|SQL_NUMERIC|Numerisch*, Währung, Float|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Integer|  
|SQL_TIME|Wird nicht unterstützt. Es gibt keinen Visual *FoxPro-Zeittyp.*|  
|SQL_TIMESTAMP|Datetime|  
|SQL_TINYINT|Integer|  
|SQL_VARBINARY|Memo (Binary)*, Allgemein|  
|SQL_VARCHAR|Zeichen|  
  
 *Standardtyp  
  
 Weitere Informationen zu Visual FoxPro-Datentypen finden Sie unter [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md). Weitere Informationen zu dieser Funktion finden Sie unter [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) in der *ODBC-Programmiererreferenz*.
