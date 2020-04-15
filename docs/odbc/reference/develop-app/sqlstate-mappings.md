---
title: SQLSTATE-Zuordnungen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299740"
---
# <a name="sqlstate-mappings"></a>SQLSTATE-Zuordnungen
In diesem Thema werden SQLSTATE-Werte für ODBC *2.x* und ODBC *3.x*erläutert. Weitere Informationen zu ODBC *3.x* SQLSTATE-Werten finden Sie in [Anhang A: ODBC-Fehlercodes](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md).  
  
 In ODBC *3.x*werden HYxxx SQLSTATEs anstelle von S1xxx zurückgegeben, und 42Sxx SQLSTATEs werden anstelle von S00XX zurückgegeben. Dies wurde getan, um sich an den Open Group- und ISO-Standards auszurichten. In vielen Fällen ist die Zuordnung nicht eins zu eins, da die Standards die Interpretation mehrerer SQLSTATEs neu definiert haben.  
  
 Wenn eine ODBC *2.x-Anwendung* auf eine ODBC *3.x-Anwendung* aktualisiert wird, muss die Anwendung so geändert werden, dass ODBC *3.x* SQLSTATEs anstelle von ODBC *2.x* SQLSTATEs erwartet wird. In der folgenden Tabelle sind die ODBC *3.x* SQLSTATEs aufgeführt, denen jede ODBC *2.x* SQLSTATE zugeordnet ist.  
  
 Wenn das SQL_ATTR_ODBC_VERSION Umgebungsattribut auf SQL_OV_ODBC2 festgelegt ist, gibt der Treiber ODBC *2.x* SQLSTATEs anstelle von ODBC *3.x* SQLSTATEs, wenn **SQLGetDiagField** oder **SQLGetDiagRec** aufgerufen wird. Eine bestimmte Zuordnung kann bestimmt werden, indem der ODBC *2.x* SQLSTATE in Spalte 1 der folgenden Tabelle notiert wird, der dem ODBC *3.x* SQLSTATE in Spalte 2 entspricht.  
  
|ODBC *2.x* SQLSTATE|ODBC *3.x* SQLSTATE|Kommentare|  
|-------------------------|-------------------------|--------------|  
|01S03|01001||  
|01S04|01001||  
|22003|HY019||  
|22008|22007||  
|22005|22018||  
|24.000|07005||  
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
|S1002|07009|ODBC *2.x* SQLSTATE S1002 wird ODBC *3.x* SQLSTATE 07009 zugeordnet, wenn die zugrunde liegende Funktion **SQLBindCol**, **SQLColAttribute**, **SQLExtendedFetch**, **SQLFetch**, **SQLFetchScroll**oder **SQLGetData**ist.|  
|S1003|HY003||  
|S1004|HY004||  
|S1008|HY008||  
|S1009|HY009|Wird für eine ungültige Verwendung eines Nullzeigers zurückgegeben.|  
|S1009|HY024|Wird für einen ungültigen Attributwert zurückgegeben.|  
|S1009|HY092|Wird zurückgegeben, um Daten durch einen Aufruf von **SQLSetPos**zu aktualisieren oder zu löschen oder Daten durch einen Aufruf von **SQLBulkOperations**hinzuzufügen oder zu löschen, wenn die Parallelität schreibgeschützt ist.|  
|S1010|HY007 HY010|SQLSTATE S1010 wird SQLSTATE HY007 zugeordnet, wenn **SQLDescribeCol** aufgerufen wird, bevor **SQLPrepare**, **SQLExecDirect**oder eine Katalogfunktion für das *StatementHandle*aufgerufen wird. Andernfalls wird SQLSTATE S1010 SQLSTATE HY010 zugeordnet.|  
|S1011|HY011||  
|S1012|HY012||  
|S1090|HY090||  
|S1091|HY091||  
|S1092|HY092||  
|S1093|07009|ODBC *3.x* SQLSTATE 07009 wird ODBC *2.x* SQLSTATE S1093 zugeordnet, wenn die zugrunde liegende Funktion **SQLBindParameter** oder **SQLDescribeParam**ist.|  
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
>  ODBC *3.x* SQLSTATE 07008 ist ODBC *2.x* SQLSTATE S1000 zugeordnet.
