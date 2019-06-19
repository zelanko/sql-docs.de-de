---
title: Funktionszuordnung im Treiber-Manager | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 40dc214fa7f77dfb81c941095ecd71d3d4bf5a36
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63061558"
---
# <a name="function-mapping-in-the-driver-manager"></a>Funktionszuordnung im Treiber-Manager
Der Treiber-Manager unterstützt zwei Einstiegspunkte für Funktionen, die Zeichenfolgenargumente verwenden. Der nicht ergänzten-Funktion (**SQLDriverConnect**) ist die ANSI-Form der Funktion. Das Unicode-Formular mit ergänzt wird eine *W* (**SQLDriverConnectW**.)  
  
 Die ODBC-Header-Datei unterstützt auch Funktionen ergänzt, die mit einer *A* (**SQLDriverConnectA**) für die Vorteile von gemischten ANSI/Unicode-Anwendungen. Aufrufe an die **ein** Funktionen sind tatsächlich Aufrufe an den nicht ergänzten Einstiegspunkt (**SQLDriverConnect**.)  
  
 Wenn die Anwendung, mit dem _UNICODE kompiliert wird **#define**, die ODBC-Header-Datei ordnet nicht ergänzte Funktionsaufrufe (**SQLDriverConnect**) auf die Unicode-Version (**SQLDriverConnectW** .)  
  
 Der Treiber-Manager erkennt einen Treiber als Unicode-Treiber, wenn **SQLConnectW** wird vom Treiber unterstützt.  
  
 Wenn der Treiber einen Unicode-Treiber ist, führt der Treiber-Manager Funktionsaufrufe wie folgt aus:  
  
-   Eine Funktion ohne Argumente oder Parameter können direkt über an den Treiber übergeben werden.  
  
-   Übergeben von Unicode-Funktionen (mit der *W* Suffix) direkt über dem Treiber.  
  
-   Konvertiert eine ANSI-Funktion (mit der *ein* Suffix) an eine Unicode-Funktion (mit der *W* Suffix) durch die Zeichenfolgenargumente in Unicode konvertiert Zeichen aus, und übergibt Sie an den Treiber Unicode-Funktion.  
  
 Wenn der Treiber eine ANSI-Treiber ist, führt der Treiber-Manager Funktionsaufrufe wie folgt aus:  
  
-   Funktionen ohne Argumente oder Parameter, die direkt über übergeben an den Treiber.  
  
-   Konvertiert Unicode-Funktionen (mit der *W* Suffix) in das ANSI-Funktionsaufruf aus, und übergibt sie an den Treiber.  
  
-   Eine ANSI-Funktion übergeben direkt an den Treiber.  
  
 Der Treiber-Manager ist Unicode-fähige intern. Daher wird die optimale Leistung von einer Unicode-Anwendung, die Arbeit mit einer Unicode-Treiber abgerufen werden, da der Treiber-Manager über die Unicode-Funktionen für den Treiber übergibt. Wenn eine ANSI-Anwendung mit einem ANSI-Treiber funktioniert, des Treiber-Managers müssen Zeichenfolgen von ANSI in Unicode konvertiert bei der Verarbeitung von einige Funktionen, z. B. **SQLDriverConnect**. Nach der Verarbeitung der Funktion, muss der Treiber-Manager klicken Sie dann die Unicode-Zeichenfolge wieder in ANSI konvertieren vor dem Senden der Funktion für den ANSI-Treiber.  
  
 Eine Anwendung sollte nicht ändern oder lesen die Puffern für gebundene Parameter aus, wenn der Treiber SQL_STILL_EXECUTING oder SQL_NEED_DATA zurückgibt. Der Treiber-Manager bewirkt, dass der Puffer in ANSI gebunden werden, bis der Treiber SQL_SUCCESS, SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgegeben. Eine Multithreadanwendung sollte nicht auf alle gebundenen Parameterwerte zugreifen, die ein anderer Thread auf eine SQL-Anweisung ausführt. Der Treiber-Manager konvertiert die Daten von Unicode in ANSI "Direktes", und der andere Thread möglicherweise ANSI-Daten in diesen Puffern angezeigt, während der Treiber noch die SQL-Anweisung verarbeitet wird. Anwendungen, die Unicode-Daten an eine ANSI-Treiber zu binden, müssen nicht zwei verschiedene Spalten an die gleiche Adresse binden.
