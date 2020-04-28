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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e1efba2187e2c1f2d813d43640fc9259ad4f2b3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306295"
---
# <a name="c-data-types-in-odbc"></a>C-Datentypen in ODBC
ODBC definiert die C-Datentypen, die von Anwendungsvariablen und den entsprechenden typbezeichlen verwendet werden. Diese werden von den Puffern verwendet, die an Resultsetspalten und Anweisungs Parameter gebunden sind. Nehmen wir beispielsweise an, dass eine Anwendung Daten aus einer Resultsetspalte im Zeichenformat abrufen möchte. Er deklariert eine Variable mit dem SQLCHAR *-Datentyp und bindet diese Variable an die Resultsetspalte mit einem Typbezeichner SQL_C_CHAR. Eine umfassende Liste der C-Datentypen und-Typbezeichner finden Sie unter [Anhang D: Datentypen](../../../odbc/reference/appendixes/appendix-d-data-types.md).  
  
 ODBC definiert auch eine Standard Zuordnung von jedem SQL-Datentyp zu einem C-Datentyp. Beispielsweise wird eine 2-Byte-Ganzzahl in der Datenquelle einer 2-Byte-Ganzzahl in der Anwendung zugeordnet. Um die Standard Zuordnung zu verwenden, gibt eine Anwendung den SQL_C_DEFAULT Typbezeichners an. Allerdings wird die Verwendung dieses Bezeichners aus Interoperabilitäts Gründen nicht empfohlen.  
  
 Alle in ODBC *1. x* definierten ganzzahligen C-Datentypen wurden signiert. Nicht signierte C-Datentypen und die entsprechenden Typbezeichner wurden in ODBC 2,0 hinzugefügt. Aus diesem Grund müssen Anwendungen und Treiber beim Umgang mit *1. x* -Versionen besonders vorsichtig sein.  
  
## <a name="c-data-type-extensibility"></a>Erweiterbarkeit des C-Datentyps  
 In ODBC 3,8 können Sie Treiber spezifische C-Datentypen angeben. Dies ermöglicht es Ihnen, einen SQL-Typ als treiberspezifischen C-Typ in ODBC-Anwendungen zu binden, wenn Sie [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md), [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)oder [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)aufrufen. Dies kann für die Unterstützung neuer Server Typen nützlich sein, da vorhandene C-Datentypen die neuen Server Datentypen möglicherweise nicht ordnungsgemäß darstellen. Die Verwendung von treiberspezifischen C-Typen kann die Anzahl der Konvertierungen erhöhen, die von Treibern durchgeführt werden können.  
  
 Nehmen wir beispielsweise an, ein Datenbank-Management System (DBMS) hat den neuen SQL-Typ **DateTimeOffset**eingeführt, um das Datum und die Uhrzeit mit Zeitzoneninformationen darzustellen. Es gibt keinen spezifischen C-Typ in ODBC, der **DateTimeOffset**entsprach. Eine Anwendung muss **DateTimeOffset** als SQL_C_BINARY binden und in einen benutzerdefinierten Datentyp umwandeln. Ab ODBC 3,8 mit Erweiterbarkeit des c-Datentyps kann ein Treiber einen neuen entsprechenden c-Typ definieren. Für den neuen SQL-Typ DateTimeOffset kann der Treiber z. b. einen neuen entsprechenden C-Typ definieren, z. b. SQL_C_DATETIMEOFFSET. Anschließend kann eine Anwendung den neuen SQL-Typ als treiberspezifischen C-Typ binden.  
  
 Ein C-Datentyp wird im Treiber wie folgt definiert:  
  
-   Der ODBC-Kompatibilitäts Grad für eine Anwendung, einen ODBC-Treiber und einen Treiber-Manager ist 3,8 (oder höher).  
  
-   Der Datenbereich eines treiberspezifischen C-Typs liegt zwischen 0x4000 und 0x7FFF.  
  
-   Der Treiber definiert die Struktur der Daten, die dem C-Typ entsprechen.  Dies kann im treiberspezifischen SDK durchgeführt werden.  
  
 Der Treiber-Manager überprüft keinen C-Typ, der im Bereich von 0x4000 und 0x7FFF definiert ist. der Treiber führt die Validierung und jede Datentyp Konvertierung durch. Wenn jedoch der Datenbereich eines C-Typs, der an den Treiber-Manager übermittelt wird, zwischen 0x0000 und 0x3fff oder zwischen 0X8000 und 0xFFFF liegt, wird der C-Datentyp vom Treiber-Manager überprüft.  
  
> [!NOTE]  
>  Treiber spezifische C-Datentypen sollten in der Treiber Dokumentation beschrieben werden.  
  
 Um eine ODBC-Kompatibilitäts Stufe von 3,8 anzugeben, ruft eine Anwendung [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md) auf, wobei das SQL_ATTR_ODBC_VERSION-Attribut auf **SQL_OV_ODBC3_80**festgelegt ist. Um die Version des Treibers zu ermitteln, ruft eine Anwendung **SQLGetInfo** mit SQL_DRIVER_ODBC_VER auf.  
  
 Weitere Informationen zu ODBC 3,8 finden Sie unter [What es New in ODBC 3,8](../../../odbc/reference/what-s-new-in-odbc-3-8.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [C-Datentypen](../../../odbc/reference/appendixes/c-data-types.md)
