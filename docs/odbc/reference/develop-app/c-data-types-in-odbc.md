---
title: C-Datentypen in ODBC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
ms.assetid: c91bef31-3794-4736-966a-d50997b2233c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 748347b0a5b20f22cf7191213c59d2879df67522
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118716"
---
# <a name="c-data-types-in-odbc"></a>C-Datentypen in ODBC
ODBC definiert die C-Datentypen, die von Anwendungsvariablen und ihren entsprechenden Typ-IDs verwendet werden. Diese werden von den Puffern verwendet, die Resultset-Spalten und Parameter gebunden sind. Nehmen wir beispielsweise an, dass eine Anwendung Daten zum Abrufen von Daten aus einer Resultsetspalte im Zeichenformat vorliegen. Deklariert eine Variable mit der SQLCHAR *-Datentyp, und diese Variable an die Resultsetspalte mit einem Typbezeichner SQL_C_CHAR gebunden. Eine vollständige Liste der C-Datentypen und Typ-IDs, finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 ODBC definiert auch eine standardzuordnung von jeder SQL-Datentyp in einen C-Datentyp. Beispielsweise wird eine 2-Byte-Ganzzahl in der Datenquelle eine 2-Byte-Ganzzahl in der Anwendung zugeordnet. Um die standardzuordnung zu verwenden, gibt eine Anwendung die SQL_C_DEFAULT-Typ-ID an. Mit dieser Bezeichner wird jedoch aus Gründen der Interoperabilität abgeraten.  
  
 Alle ganzzahligen C-Datentypen in ODBC definiert *1.x* signiert wurden. Nicht signierte C-Datentypen und ihre entsprechenden Typ-IDs wurden in ODBC 2.0 hinzugefügt. Aus diesem Grund Anwendungen und Treiber müssen insbesondere darauf achten, beim Umgang mit *1.x* Versionen.  
  
## <a name="c-data-type-extensibility"></a>C-Daten-Typ-Erweiterbarkeit  
 In ODBC 3.8 können Sie die Treiber-spezifischen C-Datentypen angeben. Dadurch können Sie einen SQL-Typ als einen Treiber-spezifischen C-Typ in ODBC-Anwendungen zu binden, beim Aufrufen [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md), oder [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md). Dies kann nützlich für die Unterstützung der neuen Server-Typen sein, da vorhandene C-Datentypen die neuen Server-Datentypen nicht ordnungsgemäß darstellen können. Mit Treiber-spezifischen C-Typen kann die Anzahl der Konvertierungen erhöhen, die Treiber ausführen können.  
  
 Nehmen wir beispielsweise an eine Datenbank-Managementsystem (DBMS) eingeführt, einen neuen SQL-Typ, **DATETIMEOFFSET**, um das Datum und Uhrzeit mit Zeitzoneninformationen darzustellen. Es wird kein bestimmter C-Typ in ODBC, die auf entsprach **DATETIMEOFFSET**. Eine Anwendung müssten binden **DATETIMEOFFSET** als SQL_C_BINARY und Umwandlung Geben sie einen benutzerdefinierten Daten. In ODBC 3.8-Typ C die datenerweiterung ab, kann ein Treiber einen neuen entsprechenden C-Typ definieren. Der Treiber für den neuen SQL-Typ "DateTimeOffset" kann z. B. einen neuen entsprechenden C-Typ wie z. B. SQL_C_DATETIMEOFFSET definieren. Anschließend kann eine Anwendung den neuen SQL-Typ als Treiber-spezifischen C-Typ binden.  
  
 C-Datentyp ist im Treiber wie folgt definiert:  
  
-   Die ODBC-Kompatibilitätsstufe für eine Anwendung, ODBC-Treiber und Treiber-Manager ist 3.8 (oder höher).  
  
-   Datenbereich eine treiberspezifische C-Typ liegt zwischen 0 x 4000 und 0x7FFF.  
  
-   Der Treiber definiert die Struktur der Daten entspricht des C-Typs.  Dies kann im Treiber-spezifische SDK erfolgen.  
  
 Der Treiber-Manager überprüft nicht, einen C-Typ, der im Bereich von 0 x 4000 und 0x7FFF definiert; der Treiber führt die Überprüfung und alle datentypkonvertierungen. Aber wenn Datenbereich eine C-Typ, der an den Treiber-Manager übergeben zwischen 0 x 0000 und 0x3FFF oder 0 x 8000 bis 0xFFFF ist, überprüft der Treiber-Manager die C-Datentyp.  
  
> [!NOTE]  
>  Treiber-spezifischen C-Datentypen sollte in der Dokumentation zu Driver beschrieben werden.  
  
 Wenn eine ODBC-Kompatibilitätsstufe der 3.8 angeben möchten, eine Anwendung ruft [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md) mit der SQL_ATTR_ODBC_VERSION-Attribut festgelegt ist, um **SQL_OV_ODBC3_80**. Um zu bestimmen, die Version des Treibers, ruft eine Anwendung **SQLGetInfo** mit SQL_DRIVER_ODBC_VER.  
  
 Weitere Informationen zu ODBC 3.8, finden Sie unter [Neuigkeiten in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
## <a name="see-also"></a>Siehe auch  
 [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md)
