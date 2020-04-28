---
title: Anweisungs Handles | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299676"
---
# <a name="statement-handles"></a>Anweisungshandles
Eine- *Anweisung* lässt sich am einfachsten als SQL-Anweisung vorstellen, wie z. b. ** \* Select from Employee**. Eine-Anweisung ist jedoch mehr als nur eine SQL-Anweisung. Sie besteht aus allen Informationen, die mit dieser SQL-Anweisung verknüpft sind, wie z. b. alle von der-Anweisung erstellten Resultsets und Parameter, die bei der Ausführung der-Anweisung verwendet werden. Eine-Anweisung muss nicht einmal über eine von der Anwendung definierte SQL-Anweisung verfügen. Wenn z. b. eine Katalog Funktion wie **SQLTables** für eine-Anweisung ausgeführt wird, führt Sie eine vordefinierte SQL-Anweisung aus, die eine Liste von Tabellennamen zurückgibt.  
  
 Jede-Anweisung wird durch ein Anweisungs Handle identifiziert. Eine-Anweisung ist einer einzelnen Verbindung zugeordnet, und es können mehrere-Anweisungen für diese Verbindung vorhanden sein. Einige Treiber schränken die Anzahl der aktiven Anweisungen ein, die Sie unterstützen. die Option SQL_MAX_CONCURRENT_ACTIVITIES in **SQLGetInfo** gibt an, wie viele aktive Anweisungen ein Treiber für eine einzelne Verbindung unterstützt. Eine-Anweisung ist so definiert, dass Sie *aktiv* ist, wenn Ergebnisse ausstehen, wobei Ergebnisse entweder ein Resultset oder die Anzahl der von einer **Insert**-, **Update**-oder **Delete** -Anweisung betroffenen Zeilen sind oder dass Daten mit mehreren Aufrufen von **SQLPutData**gesendet werden.  
  
 Innerhalb eines Code Abschnitts, der ODBC (Treiber-Manager oder Treiber) implementiert, identifiziert das Anweisungs Handle eine-Struktur, die Anweisungs Informationen enthält, wie z. b.:  
  
-   Der Status der Anweisung.  
  
-   Die aktuelle Diagnose auf Anweisungs Ebene  
  
-   Die Adressen der Anwendungsvariablen, die an die Parameter und Resultsetspalten der Anweisung gebunden sind.  
  
-   Die aktuellen Einstellungen der einzelnen Anweisungs Attribute  
  
 Anweisungs Handles werden in den meisten ODBC-Funktionen verwendet. Insbesondere werden Sie in den Funktionen verwendet, um Parameter und Resultsetspalten (**SQLBindParameter** und **SQLBindCol**) zu binden. vorbereiten und Ausführen von Anweisungen (**SQLPrepare**, **SQLExecute**und **SQLExecDirect**), Abrufen von Metadaten (**SQLColAttribute** und **SQLDescribeCol**), Abrufen von Ergebnissen (**SQLFetch**) und Abrufen der Diagnose (**SQLGetDiagField** und **SQLGetDiagRec**). Sie werden auch in Katalog Funktionen (**SQLColumns**, **SQLTables**usw.) und einer Reihe weiterer Funktionen verwendet.  
  
 Anweisungs Handles werden mit **sqlzuordchandle** zugeordnet und mit **SQLFreeHandle**freigegeben.
