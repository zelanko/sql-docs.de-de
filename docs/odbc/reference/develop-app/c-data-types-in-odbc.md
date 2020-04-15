---
title: C Datentypen in ODBC | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e1efba2187e2c1f2d813d43640fc9259ad4f2b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306295"
---
# <a name="c-data-types-in-odbc"></a>C-Datentypen in ODBC
ODBC definiert die C-Datentypen, die von Anwendungsvariablen und den entsprechenden Typidungen verwendet werden. Diese werden von den Puffern verwendet, die an Resultsetspalten und Anweisungsparameter gebunden sind. Angenommen, eine Anwendung möchte Daten aus einer Ergebnissatzspalte im Zeichenformat abrufen. Es deklariert eine Variable mit dem Datentyp SQLCHAR * und bindet diese Variable an die Ergebnissatzspalte mit dem Typbezeichner SQL_C_CHAR. Eine vollständige Liste der C-Datentypen und Typbezeichner finden Sie in [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 ODBC definiert auch eine Standardzuordnung von jedem SQL-Datentyp zu einem C-Datentyp. Beispielsweise wird eine 2-Byte-Ganzzahl in der Datenquelle einer 2-Byte-Ganzzahl in der Anwendung zugeordnet. Um die Standardzuordnung zu verwenden, gibt eine Anwendung den SQL_C_DEFAULT Typbezeichner an. Die Verwendung dieses Bezeichners wird jedoch aus Gründen der Interoperabilität abgeraten.  
  
 Alle in ODBC *1.x* definierten Ganzzahl-C-Datentypen wurden signiert. Nicht signierte C-Datentypen und die entsprechenden Typ-IDs wurden in ODBC 2.0 hinzugefügt. Aus diesem Grund müssen Anwendungen und Treiber besonders vorsichtig sein, wenn sie mit *1.x-Versionen* umgehen.  
  
## <a name="c-data-type-extensibility"></a>C-Datentyp-Erweiterbarkeit  
 In ODBC 3.8 können Sie treiberspezifische C-Datentypen angeben. Auf diese Weise können Sie einen SQL-Typ als treiberspezifischen C-Typ in ODBC-Anwendungen binden, wenn Sie [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)oder [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)aufrufen. Dies kann nützlich sein, um neue Servertypen zu unterstützen, da vorhandene C-Datentypen die neuen Serverdatentypen möglicherweise nicht korrekt darstellen. Die Verwendung treiberspezifischer C-Typen kann die Anzahl der Konvertierungen erhöhen, die Treiber durchführen können.  
  
 Angenommen, ein Datenbankverwaltungssystem (DBMS) hat einen neuen SQL-Typ, **DATETIMEOFFSET**, eingeführt, um Datum und Uhrzeit mit Zeitzoneninformationen darzustellen. Es gäbe keinen spezifischen C-Typ in ODBC, der **DATETIMEOFFSET**entsprach. Eine Anwendung müsste **DATETIMEOFFSET** als SQL_C_BINARY binden und in einen benutzerdefinierten Datentyp umsetzen. Ab ODBC 3.8 mit C-Datentyperweiterizierbarkeit kann ein Treiber einen neuen entsprechenden C-Typ definieren. Für den neuen SQL-Typ DATETIMEOFFSET kann der Treiber beispielsweise einen neuen entsprechenden C-Typ definieren, z. B. SQL_C_DATETIMEOFFSET. Anschließend kann eine Anwendung den neuen SQL-Typ als treiberspezifischen C-Typ binden.  
  
 Ein C-Datentyp wird im Treiber wie folgt definiert:  
  
-   Die ODBC-Konformitätsstufe für eine Anwendung, einen ODBC-Treiber und einen Treiber-Manager ist 3.8 (oder höher).  
  
-   Der Datenbereich eines treiberspezifischen C-Typs liegt zwischen 0x4000 und 0x7FFF.  
  
-   Der Treiber definiert die Struktur der Daten, die dem Typ C entsprechen.  Dies kann im treiberspezifischen SDK erfolgen.  
  
 Der Treiber-Manager überprüft keinen C-Typ, der im Bereich von 0x4000 und 0x7FFF definiert ist. Der Treiber führt die Validierung und alle Datentypkonvertierungen durch. Wenn der Datenbereich eines An den Treiber-Manager übergebenen C-Typs jedoch zwischen 0x0000 und 0x3FFF oder zwischen 0x8000 und 0xFFFF liegt, überprüft der Treiber-Manager den C-Datentyp.  
  
> [!NOTE]  
>  Treiberspezifische C-Datentypen sollten in der Treiberdokumentation beschrieben werden.  
  
 Um eine ODBC-Kompatibilitätsstufe von 3.8 anzugeben, ruft eine Anwendung [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md) auf, wobei das Attribut SQL_ATTR_ODBC_VERSION **auf SQL_OV_ODBC3_80**festgelegt ist. Um die Version des Treibers zu bestimmen, ruft eine Anwendung **SQLGetInfo** mit SQL_DRIVER_ODBC_VER auf.  
  
 Weitere Informationen zu ODBC 3.8 finden Sie [unter Neuerungen in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md)
