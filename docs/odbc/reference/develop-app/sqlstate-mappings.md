---
title: SQLSTATE-Zuordnungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSTATE
- backward compatibility [ODBC], SQLSTATE
- SQLSTATE [ODBC]
ms.assetid: 6e6cabcf-a204-40eb-b77d-8a0c4a5e8524
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec58c0e41869529bbba5fd31ad534976923a990d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299740"
---
# <a name="sqlstate-mappings"></a>SQLSTATE-Zuordnungen
In diesem Thema werden SQLSTATE-Werte für ODBC *2. x* und ODBC *3. x*erläutert. Weitere Informationen zu ODBC *3. x* SQLSTATE-Werten finden Sie unter [Anhang A: ODBC-Fehler Codes](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md).  
  
 In ODBC *3. x*werden hyxxx Sqlstates anstelle von S1xxx zurückgegeben, und 42sxx Sqlstates werden anstelle von S00XX zurückgegeben. Dies wurde erreicht, um die Standards "Open Group" und "ISO" auszurichten. In vielen Fällen ist die Zuordnung nicht eins zu eins, da die Standards die Interpretation mehrerer Sqlstates neu definiert haben.  
  
 Wenn eine ODBC *2. x* -Anwendung auf eine ODBC *3. x* -Anwendung aktualisiert wird, muss die Anwendung so geändert werden, dass ODBC *3. x* Sqlstates anstelle von ODBC *2. x* Sqlstates erwartet wird. In der folgenden Tabelle werden die ODBC *3. x* Sqlstates aufgelistet, denen die einzelnen ODBC *2. x* SQLSTATE zugeordnet sind.  
  
 Wenn das SQL_ATTR_ODBC_VERSION-Umgebungs Attribut auf SQL_OV_ODBC2 festgelegt ist, sendet der Treiber ODBC *2. x* Sqlstates anstelle von ODBC *3. x* Sqlstates, wenn **SQLGetDiagField** oder **SQLGetDiagRec** aufgerufen wird. Eine bestimmte Zuordnung kann durch Notieren von ODBC *2. x* SQLSTATE in Spalte 1 der folgenden Tabelle ermittelt werden, die dem ODBC *3. x* SQLSTATE in Spalte 2 entspricht.  
  
|ODBC *2. x* SQLSTATE|ODBC *3. x* SQLSTATE|Kommentare|  
|-------------------------|-------------------------|--------------|  
|01s03|01001||  
|01s04|01001||  
|22003|HY019||  
|22008|22007||  
|22005|22018||  
|24.000|07005||  
|37000|42000||  
|70100|HY018||  
|S0001|42s01||  
|S0002|42s02||  
|S0011|42s11||  
|S0012|42s12||  
|S0021|42s21||  
|S0022|42s22||  
|S0023|42s23||  
|S1000|HY000||  
|S1001|HY001||  
|S1002|07009|ODBC *2. x* SQLSTATE S1002 ist ODBC *3. x* SQLSTATE 07009 zugeordnet, wenn die zugrunde liegende Funktion **SQLBindCol**, **SQLColAttribute**, **sqlextendebug**, **SQLFetch**, **SQLFetchScroll**oder **SQLGetData**ist.|  
|S1003|HY003||  
|S1004|HY004||  
|S1008|HY008||  
|S1009|HY009|Wird für eine ungültige Verwendung eines NULL-Zeigers zurückgegeben.|  
|S1009|HY024|Wird für einen ungültigen Attribut Wert zurückgegeben.|  
|S1009|HY092|Wird zum Aktualisieren oder Löschen von Daten durch einen Aufrufen von **SQLSetPos**oder zum Hinzufügen, aktualisieren oder Löschen von Daten durch einen **SQLBulkOperations**-Befehl zurückgegeben, wenn die Parallelität schreibgeschützt ist.|  
|S1010|HY007 HY010|SQLSTATE S1010 wird SQLSTATE HY007 zugeordnet, wenn **SQLDescribeCol** vor dem Aufrufen von **SQLPrepare**, **SQLExecDirect**oder einer Katalog Funktion für das *StatementHandle*aufgerufen wird. Andernfalls wird SQLSTATE S1010 SQLSTATE HY010 zugeordnet.|  
|S1011|HY011||  
|S1012|HY012||  
|S1090|HY090||  
|S1091|HY091||  
|S1092|HY092||  
|S1093|07009|ODBC *3. x* SQLSTATE 07009 ist ODBC *2. x* SQLSTATE S1093 zugeordnet, wenn die zugrunde liegende Funktion **SQLBindParameter** oder **SQLDescribeParam**ist.|  
|S1096|HY096||  
|S1097|HY097||  
|S1098|HY098||  
|S1099|HY099||  
|S1100|HY100||  
|S1101|HY101||  
|S1103|HY103||  
|S1104|HY104||  
|S1105|HY105||  
|S1106|HY106||  
|S1107|HY107||  
|S1108|HY108||  
|S1109|HY109||  
|S1110|HY110||  
|S1111|HY111||  
|S1C00|HYC00||  
|S1T00|HYT00||  
  
> [!NOTE]  
>  ODBC *3. x* SQLSTATE 07008 ist ODBC *2. x* SQLSTATE S1000 zugeordnet.
