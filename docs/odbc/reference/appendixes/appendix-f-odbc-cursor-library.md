---
title: 'Anhang F: ODBC-Cursor Bibliothek | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- cursor library [ODBC]
ms.assetid: a03084df-4e48-48ef-917d-4a3fae48a605
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bfffd95dd88b0a25be682a3df581e55825ed9ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68090832"
---
# <a name="appendix-f-odbc-cursor-library"></a>Anhang F: ODBC-Cursorbibliothek
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Version von Windows entfernt. Vermeiden Sie die Verwendung dieses Features bei der Entwicklung neuer Anwendungen, und planen Sie das Ändern von Anwendungen, in denen diese Funktion derzeit verwendet wird Microsoft empfiehlt die Verwendung der Cursor-Funktionalität des Treibers.  
  
 Die ODBC-Cursor Bibliothek (odbccr32. dll) unterstützt die Verwendung von scrollfähigen Cursorn für alle Treiber, die dem API-Konformitäts Grad der Ebene 1 entsprechen und von Entwicklern mit Ihren Anwendungen oder Treibern neu verteilt werden können. Die Cursor Bibliothek unterstützt auch positionierte UPDATE-und DELETE-Anweisungen für von **Select** -Anweisungen generierte Resultsets. Obwohl es nur statische und Vorwärts Cursor unterstützt, erfüllt die Cursor Bibliothek die Anforderungen vieler Anwendungen. Außerdem bietet Sie eine gute Leistung, insbesondere für Resultsets kleiner und mittlerer Größe, sowie für Anwendungen, die keine gute Cursor Unterstützung haben.  
  
 Die Cursor Bibliothek ist eine Dynamic Link Library (dll), die sich zwischen dem Treiber-Manager und dem Treiber befindet. Wenn eine Anwendung eine Funktion aufruft, ruft der Treiber-Manager die Funktion in der Cursor Bibliothek auf, die entweder die Funktion ausführt oder Sie im angegebenen Treiber aufruft. Für eine bestimmte Verbindung gibt eine Anwendung an, ob die Cursor Bibliothek immer verwendet wird. Sie wird verwendet, wenn der Treiber keine scrollbaren Cursor unterstützt oder nie verwendet wird.  
  
 Die Cursor Bibliothek wird als Treiber für den Treiber-Manager angezeigt. Wenn sich die Cursor Bibliothek zwischen dem Treiber-Manager und einem ODBC *2. x* -Treiber befindet, wird die Cursor Bibliothek als ODBC *2. x* -Treiber angezeigt. Wenn sich die Cursor Bibliothek zwischen dem Treiber-Manager und einem ODBC *3. x* -Treiber befindet, wird die Cursor Bibliothek als ODBC *3. x* -Treiber angezeigt. Welches Verhalten von der Cursor Bibliothek angezeigt wird, hängt von der Version des Treibers ab, mit der er arbeitet, mit Ausnahme von Bindungs Offsets, die sowohl für ODBC *2. x* -als auch für ODBC *3. x* -Treiber unterstützt wird.  
  
 Zum Implementieren von Blockcursorn in **SQLFetch** und **SQLFetchScroll**Ruft die Cursor Bibliothek wiederholt **SQLFetch** im Treiber auf. Zum Implementieren von Bildlauf werden die Daten, die Sie im Arbeitsspeicher und in den Datenträger Dateien abgerufen haben, zwischengespeichert Wenn eine Anwendung ein neues Rowset anfordert, ruft die Cursor Bibliothek Sie nach Bedarf vom Treiber oder Cache ab.  
  
 Um positionierte UPDATE-und DELETE-Anweisungen zu implementieren, erstellt die Cursor Bibliothek eine **Update** -oder **Delete** -Anweisung mit einer **Where** -Klausel, die den zwischengespeicherten Wert der einzelnen gebundenen Spalten in der Zeile angibt. Wenn eine positionierte UPDATE-Anweisung ausgeführt wird, aktualisiert die Cursor Bibliothek Ihren Cache von den Werten in den rowsetpuffern.  
  
 Weitere Informationen zur ODBC-Cursor Bibliothek finden Sie in den folgenden Abschnitten dieses Anhangs:  
  
-   [Verwenden der ODBC-Cursorbibliothek](../../../odbc/reference/appendixes/using-the-odbc-cursor-library.md)  
  
-   [Ausführen einer positionierten Aktualisierung und von DELETE-Anweisungen](../../../odbc/reference/appendixes/executing-positioned-update-and-delete-statements.md)  
  
-   [Codebeispiel für Cursorbibliothek](../../../odbc/reference/appendixes/cursor-library-code-example.md)  
  
-   [Hinweise zur Implementierung](../../../odbc/reference/appendixes/implementation-notes.md)  
  
-   [ODBC-Cursorbibliothek – Fehlercodes](../../../odbc/reference/appendixes/odbc-cursor-library-error-codes.md)
