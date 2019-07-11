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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 597fe4f7697375cc2e75bef79059beeba9d91e14
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792761"
---
# <a name="sqlstate-mappings"></a>SQLSTATE-Zuordnungen
In diesem Thema SQLSTATE-Werten für ODBC *2.x* und ODBC *3.x*. Weitere Informationen zu ODBC *3.x* SQLSTATE-Werten, finden Sie unter [Anhang A: ODBC-Fehlercodes](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md).  
  
 In ODBC *3.x*HYxxx SQLSTATEs werden zurückgegeben, anstatt S1xxx und 42Sxx SQLSTATEs statt S00XX zurückgegeben werden. Dies erfolgte, um die Open Group und ISO-Standard entsprechen. In vielen Fällen ist die Zuordnung nicht 1: 1, da die Standards die Interpretation der mehrere SQLSTATEs neu definiert haben.  
  
 Wenn eine ODBC *2.x* Anwendung wird aktualisiert, an die ODBC *3.x* Anwendung geändert werden, um ODBC erwarten, dass die Anwendung muss *3.x* SQLSTATEs anstelle von ODBC *2.x* SQLSTATEs. Die folgende Tabelle listet die ODBC *3.x* SQLSTATEs, jede ODBC *2.x* SQLSTATE zugeordnet ist.  
  
 Wenn umgebungsattributs SQL_ATTR_ODBC_VERSION auf SQL_OV_ODBC2 festgelegt ist, sendet der Treiber ODBC *2.x* SQLSTATEs anstelle von ODBC *3.x* SQLSTATEs beim **SQLGetDiagField**oder **SQLGetDiagRec** aufgerufen wird. Eine bestimmte Zuordnung kann bestimmt werden, anhand der ODBC *2.x* SQLSTATE in Spalte 1 in der folgenden Tabelle, die die ODBC entspricht *3.x* SQLSTATE in Spalte 2.  
  
|ODBC *2.x* SQLSTATE|ODBC *3.x* SQLSTATE|Kommentare|  
|-------------------------|-------------------------|--------------|  
|01S03|01001||  
|01S04|01001||  
|22003|HY019||  
|22008|22007||  
|22005|22018||  
|24000|07005||  
|37000|42000||  
|70100|HY018||  
|S0001|42S01||  
|S0002|42S02||  
|S0011|42S11||  
|S0012|42S12||  
|S0021|42S21||  
|S0022|42S22||  
|S0023|42S23||  
|S1000|HY000||  
|S1001|HY001||  
|S1002|07009|ODBC *2.x* ODBC SQLSTATE S1002 zugeordnet *3.x* SQLSTATE 07009, wenn die zugrunde liegende Funktion **SQLBindCol**, **SQLColAttribute**, **SQLExtendedFetch**, **SQLFetch**, **SQLFetchScroll**, oder **SQLGetData**.|  
|S1003|HY003||  
|S1004|HY004||  
|S1008|HY008||  
|S1009|HY009|Für eine ungültige Verwendung des null-Zeiger zurückgegeben.|  
|S1009|HY024|Bei einem ungültigen Attributwert zurückgegeben.|  
|S1009|HY092|Zum Aktualisieren oder Löschen von Daten durch einen Aufruf zurückgegebenen **SQLSetPos**, oder hinzufügen, aktualisieren oder Löschen von Daten durch einen Aufruf von **SQLBulkOperations**, wenn die Parallelität schreibgeschützt ist.|  
|S1010|HY007 HY010|SQLSTATE S1010 SQLSTATE HY007 zugeordnet bei **SQLDescribeCol** aufgerufen wird, vor dem Aufruf **SQLPrepare**, **SQLExecDirect**, oder einer Katalogfunktion für die *StatementHandle*. Andernfalls ist SQLSTATE S1010 SQLSTATE HY010 zugeordnet.|  
|S1011|HY011||  
|S1012|HY012||  
|S1090|HY090||  
|S1091|HY091||  
|S1092|HY092||  
|S1093|07009|ODBC *3.x* ODBC SQLSTATE 07009 zugeordnet *2.x* SQLSTATE S1093 ist die zugrunde liegende Funktion **SQLBindParameter** oder **SQLDescribeParam**.|  
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
>  ODBC *3.x* ODBC SQLSTATE 07008 zugeordnet *2.x* SQLSTATE S1000.
