---
title: Funktionszuordnung im Treiber-Manager | Microsoft Docs
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
ms.openlocfilehash: db8e525bb7e8f3e167deb8061a4dd5b75073933c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305581"
---
# <a name="function-mapping-in-the-driver-manager"></a>Funktionszuordnung im Treiber-Manager
Der Treiber-Manager unterstützt zwei Einstiegspunkte für Funktionen, die Zeichenfolgenargumente verwenden. Die nicht dekorierte Funktion (**SQLDriverConnect**) ist die ANSI-Form der Funktion. Das Unicode-Formular ist mit einem *W* (**SQLDriverConnectW**.) verziert.  
  
 Die ODBC-Headerdatei unterstützt auch *Funktionen,* die mit einem A(**SQLDriverConnectA**) für die Bequemlichkeit gemischter ANSI/Unicode-Anwendungen dekoriert sind. Aufrufe der **A-Funktionen** sind eigentlich Aufrufe in den nicht dekorierten Einstiegspunkt (**SQLDriverConnect**.)  
  
 Wenn die Anwendung mit dem _UNICODE **#define**kompiliert wird, wird die ODBC-Headerdatei nicht dekorierten Funktionsaufrufen (**SQLDriverConnect**) der Unicode-Version (**SQLDriverConnectW**.) zuordnen.  
  
 Der Treiber-Manager erkennt einen Treiber als Unicode-Treiber, wenn **SQLConnectW** vom Treiber unterstützt wird.  
  
 Wenn der Treiber ein Unicode-Treiber ist, führt der Treiber-Manager Funktionsaufrufe wie folgt durch:  
  
-   Übergibt eine Funktion ohne Zeichenfolgenargumente oder Parameter direkt an den Treiber.  
  
-   Übergibt Unicode-Funktionen *W* (mit dem W-Suffix) direkt an den Treiber.  
  
-   Konvertiert eine ANSI-Funktion (mit dem *Suffix A)* in eine Unicode-Funktion (mit dem *Suffix W),* indem die Zeichenfolgenargumente in Unicode-Zeichen konvertiert werden, und übergibt die Unicode-Funktion an den Treiber.  
  
 Wenn der Treiber ein ANSI-Treiber ist, führt der Treiber-Manager Funktionsaufrufe wie folgt aus:  
  
-   Übergibt Funktionen ohne Zeichenfolgenargumente oder Parameter direkt an den Treiber.  
  
-   Konvertiert Unicode-Funktionen (mit dem W-Suffix) in einen ANSI-Funktionsaufruf und übergibt sie an den Treiber. *W*  
  
-   Übergibt eine ANSI-Funktion direkt an den Treiber.  
  
 Der Treiber-Manager ist intern Unicode-fähig. Die optimale Leistung wird dadurch erreicht, dass eine Unicode-Anwendung mit einem Unicode-Treiber arbeitet, da der Treiber-Manager unicode-Funktionen einfach an den Treiber weiterleitet. Wenn eine ANSI-Anwendung mit einem ANSI-Treiber arbeitet, muss der Treiber-Manager Zeichenfolgen von ANSI in Unicode konvertieren, wenn einige Funktionen verarbeitet werden, z. B. **SQLDriverConnect**. Nach der Verarbeitung der Funktion muss der Treiber-Manager die Unicode-Zeichenfolge zurück in ANSI konvertieren, bevor die Funktion an den ANSI-Treiber gesendet wird.  
  
 Eine Anwendung sollte ihre gebundenen Parameterpuffer nicht ändern oder lesen, wenn der Treiber SQL_STILL_EXECUTING oder SQL_NEED_DATA zurückgibt. Der Treiber-Manager belässt die an ANSI gebundenen Puffer, bis der Treiber SQL_SUCCESS, SQL_SUCCESS_WITH_INFO oder SQL_ERROR zurückgibt. Eine Multithreadanwendung sollte keinen Zugriff auf gebundene Parameterwerte erhalten, für die ein anderer Thread eine SQL-Anweisung ausführt. Der Treiber-Manager konvertiert die Daten von Unicode in ANSI "an Place", und der andere Thread sieht möglicherweise ANSI-Daten in diesen Puffern, während der Treiber die SQL-Anweisung noch verarbeitet. Anwendungen, die Unicode-Daten an einen ANSI-Treiber binden, dürfen nicht zwei verschiedene Spalten an dieselbe Adresse binden.
