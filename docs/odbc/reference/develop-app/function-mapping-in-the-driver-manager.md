---
description: Funktionszuordnung im Treiber-Manager
title: Funktions Zuordnung im Treiber-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], functions
- driver manager [ODBC], function mapping
- functions [ODBC], Unicode functions
ms.assetid: ff093b29-671a-4fc0-86c9-08a311a98e54
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69434638dee25cdbad8428a1e09cb05a270f99de
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499844"
---
# <a name="function-mapping-in-the-driver-manager"></a>Funktionszuordnung im Treiber-Manager
Der Treiber-Manager unterstützt zwei Einstiegspunkte für Funktionen, die Zeichen folgen Argumente annehmen. Die nicht ergänzte Funktion (**SQLDriverConnect**) ist die ANSI-Form der Funktion. Das Unicode-Formular wird mit einem *W* (**sqldriverconnectw**) versehen.  
  
 Die ODBC-Header Datei unterstützt auch Funktionen, die mit einem (**sqldriverconnecta**) versehen *sind,* um die Verwendung gemischter ANSI/Unicode-Anwendungen zu erleichtern. Aufrufe an die **A** -Funktionen sind tatsächlich Aufrufe des nicht ergänzten Einstiegs Punkts (**SQLDriverConnect**).  
  
 Wenn die Anwendung mit dem _UNICODE **#define**kompiliert wird, ordnet die ODBC-Header Datei nicht ergänzte Funktionsaufrufe (**SQLDriverConnect**) der Unicode-Version zu (**sqldriverconnectw**).  
  
 Der Treiber-Manager erkennt einen Treiber als Unicode-Treiber, wenn **sqlconnectw** vom Treiber unterstützt wird.  
  
 Wenn es sich bei dem Treiber um einen Unicode-Treiber handelt, führt der Treiber-Manager Funktionsaufrufe wie folgt aus:  
  
-   Übergibt eine Funktion ohne Zeichen folgen Argumente oder Parameter direkt an den Treiber.  
  
-   Übergibt Unicode-Funktionen (mit dem *W* -Suffix) direkt an den Treiber.  
  
-   Konvertiert eine ANSI-Funktion (mit *einem* Suffix) in eine Unicode-Funktion (mit dem *W* -Suffix), indem die Zeichen folgen Argumente in Unicode-Zeichen konvertiert werden und übergibt die Unicode-Funktion an den Treiber.  
  
 Wenn der Treiber ein ANSI-Treiber ist, führt der Treiber-Manager Funktionsaufrufe wie folgt aus:  
  
-   Übergibt Funktionen ohne Zeichen folgen Argumente oder Parameter direkt an den Treiber.  
  
-   Konvertiert Unicode-Funktionen (mit dem *W* -Suffix) in einen ANSI-Funktions aufrufund übergibt sie an den Treiber.  
  
-   Übergibt eine ANSI-Funktion direkt an den Treiber.  
  
 Der Treiber-Manager ist intern Unicode-aktiviert. Folglich wird die optimale Leistung durch eine Unicode-Anwendung erzielt, die mit einem Unicode-Treiber arbeitet, da der Treiber-Manager einfach Unicode-Funktionen an den Treiber übergibt. Wenn eine ANSI-Anwendung mit einem ANSI-Treiber arbeitet, muss der Treiber-Manager Zeichen folgen von ANSI in Unicode konvertieren, wenn einige Funktionen verarbeitet werden, z. b. **SQLDriverConnect**. Nachdem die Funktion verarbeitet wurde, muss der Treiber-Manager die Unicode-Zeichenfolge wieder in ANSI konvertieren, bevor die Funktion an den ANSI-Treiber gesendet wird.  
  
 Eine Anwendung sollte die gebundenen Parameter Puffer nicht ändern oder lesen, wenn der Treiber SQL_STILL_EXECUTING oder SQL_NEED_DATA zurückgibt. Der Treiber-Manager verlässt die Puffer an ANSI, bis der Treiber SQL_SUCCESS, SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgibt. Eine Multithreadanwendung sollte keinen Zugriff auf gebundene Parameterwerte erhalten, für die ein anderer Thread eine SQL-Anweisung ausführt. Der Treiber-Manager konvertiert die Daten von Unicode in ANSI "an Ort und Stelle", während der andere Thread ANSI-Daten in diesen Puffern sehen kann, während der Treiber die SQL-Anweisung noch verarbeitet. Anwendungen, die Unicode-Daten an einen ANSI-Treiber binden, dürfen nicht zwei verschiedene Spalten an dieselbe Adresse binden.
