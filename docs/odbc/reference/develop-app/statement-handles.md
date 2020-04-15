---
title: Anweisungsgriffe | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 65d6d78b-a8c8-489a-9dad-f8d127a44882
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1be90fe10d10a0b087d1c9724fed249805eb4dba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299676"
---
# <a name="statement-handles"></a>Anweisungshandles
Eine *Anweisung* wird am einfachsten als SQL-Anweisung betrachtet, z. B. **SELECT \* FROM Employee**. Eine Anweisung ist jedoch mehr als nur eine SQL-Anweisung – sie besteht aus allen Informationen, die dieser SQL-Anweisung zugeordnet sind, z. B. aus Resultsets, die von der Anweisung erstellt werden, und Parametern, die bei der Ausführung der Anweisung verwendet werden. Eine Anweisung muss nicht einmal über eine anwendungsdefinierte SQL-Anweisung verfügen. Wenn z. B. eine Katalogfunktion wie **SQLTables** für eine Anweisung ausgeführt wird, wird eine vordefinierte SQL-Anweisung ausgeführt, die eine Liste von Tabellennamen zurückgibt.  
  
 Jede Anweisung wird durch ein Anweisungshandle identifiziert. Eine Anweisung ist einer einzelnen Verbindung zugeordnet, und es können mehrere Anweisungen für diese Verbindung vorhanden sein. Einige Treiber begrenzen die Anzahl der aktiven Anweisungen, die sie unterstützen. Die Option SQL_MAX_CONCURRENT_ACTIVITIES in **SQLGetInfo** gibt an, wie viele aktive Anweisungen ein Treiber für eine einzelne Verbindung unterstützt. Eine Anweisung wird als *aktiv* definiert, wenn Ergebnisse ausstehen, bei denen ergebnisse entweder ein Resultset oder die Anzahl der Zeilen sind, die von einer **INSERT-,** **UPDATE-** oder **DELETE-Anweisung** betroffen sind, oder Daten mit mehreren Aufrufen an **SQLPutData**gesendet werden.  
  
 Innerhalb eines Codes, der ODBC implementiert (der Treiber-Manager oder ein Treiber), identifiziert das Anweisungshandle eine Struktur, die Anweisungsinformationen enthält, z. B.:  
  
-   Der Zustand der Erklärung  
  
-   Die aktuelle Diagnose auf Anweisungsebene  
  
-   Die Adressen der Anwendungsvariablen, die an die Parameter und Ergebnissatzspalten der Anweisung gebunden sind  
  
-   Die aktuellen Einstellungen der einzelnen Anweisungsattribute  
  
 Anweisungshandles werden in den meisten ODBC-Funktionen verwendet. Insbesondere werden sie in den Funktionen verwendet, um Parameter und Resultsetspalten zu binden (**SQLBindParameter** und **SQLBindCol**), Anweisungen vorzubereiten und auszuführen (**SQLPrepare**, **SQLExecute**und **SQLExecDirect**), Metadaten abzurufen (**SQLColAttribute** und **SQLDescribeCol**), Ergebnisse (**SQLFetch**) abrufen und Diagnosen abrufen (**SQLGetDiagField** und **SQLGetDiagRec**). Sie werden auch in Katalogfunktionen (**SQLColumns**, **SQLTables**usw.) und einer Reihe anderer Funktionen verwendet.  
  
 Anweisungshandles werden mit **SQLAllocHandle** zugewiesen und mit **SQLFreeHandle**freigegeben.
