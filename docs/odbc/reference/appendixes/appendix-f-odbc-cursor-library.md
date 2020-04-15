---
title: 'Anhang F: ODBC-Cursorbibliothek | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec7982150bfa805c7093ab445400ef5ad1ee070c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292430"
---
# <a name="appendix-f-odbc-cursor-library"></a>Anhang F: ODBC-Cursorbibliothek
> [!IMPORTANT]  
>  Diese Funktion wird in einer zukünftigen Windows-Version entfernt. Vermeiden Sie es, diese Funktion in neuen Entwicklungsarbeiten zu verwenden, und planen Sie, Anwendungen zu ändern, die diese Funktion derzeit verwenden. Microsoft empfiehlt die Verwendung der Cursorfunktionalität des Treibers.  
  
 Die ODBC-Cursorbibliothek (Odbccr32.dll) unterstützt Block-Scrollable-Cursor für alle Treiber, die der Level 1-API-Konformitätsstufe entsprechen und von Entwicklern mit ihren Anwendungen oder Treibern neu verteilt werden können. Die Cursorbibliothek unterstützt auch positionierte Aktualisierungs- und Löschanweisungen für Resultsets, die von **SELECT-Anweisungen** generiert werden. Obwohl sie nur statische und vorwärtsgerichtete Cursor unterstützt, erfüllt die Cursorbibliothek die Anforderungen vieler Anwendungen. Darüber hinaus kann es eine gute Leistung bieten, insbesondere für kleine bis mittlere Ergebnissätze und für Anwendungen, die keine gute Cursorunterstützung haben.  
  
 Die Cursorbibliothek ist eine Dynamic-Link-Bibliothek (DLL), die sich zwischen dem Treiber-Manager und dem Treiber befindet. Wenn eine Anwendung eine Funktion aufruft, ruft der Treiber-Manager die Funktion in der Cursorbibliothek auf, die entweder die Funktion oder im angegebenen Treiber ausführt. Für eine bestimmte Verbindung gibt eine Anwendung an, ob die Cursorbibliothek immer verwendet wird, wenn der Treiber keine scrollbaren Cursor unterstützt oder nie verwendet wird.  
  
 Die Cursorbibliothek wird als Treiber für den Treiber-Manager angezeigt. Wenn sich die Cursorbibliothek zwischen dem Treiber-Manager und einem ODBC *2.x-Treiber* befindet, wird die Cursorbibliothek als ODBC *2.x-Treiber* angezeigt. Wenn sich die Cursorbibliothek zwischen dem Treiber-Manager und einem ODBC *3.x-Treiber* befindet, wird die Cursorbibliothek als ODBC *3.x-Treiber* angezeigt. Das Verhalten der Cursorbibliothek hängt von der Version des Treibers ab, mit dem sie arbeitet, mit Ausnahme von Bindungsoffsets, die sowohl für ODBC *2.x-* als auch für ODBC *3.x-Treiber* unterstützt werden.  
  
 Um Blockcursor in **SQLFetch** und **SQLFetchScroll**zu implementieren, ruft die Cursorbibliothek **SQLFetch** im Treiber wiederholt auf. Um das Scrollen zu implementieren, werden die Daten zwischengespeichert, die es im Arbeitsspeicher und in Datenträgerdateien abgerufen hat. Wenn eine Anwendung ein neues Rowset anfordert, ruft die Cursorbibliothek es bei Bedarf vom Treiber oder Cache ab.  
  
 Um positionierte Aktualisierungs- und Löschanweisungen zu implementieren, erstellt die Cursorbibliothek eine **UPDATE-** oder **DELETE-Anweisung** mit einer **WHERE-Klausel,** die den zwischengespeicherten Wert jeder gebundenen Spalte in der Zeile angibt. Wenn eine positionierte Updateanweisung ausgeführt wird, aktualisiert die Cursorbibliothek ihren Cache von den Werten in den Rowset-Puffern.  
  
 Weitere Informationen zur ODBC-Cursorbibliothek finden Sie in den folgenden Abschnitten dieses Anhangs:  
  
-   [Using the ODBC Cursor Library (Verwenden der ODBC-Cursorbibliothek)](../../../odbc/reference/appendixes/using-the-odbc-cursor-library.md)  
  
-   [Executing Positioned Update and Delete Statements (Ausführen einer positionierten Aktualisierung und von DELETE-Anweisungen)](../../../odbc/reference/appendixes/executing-positioned-update-and-delete-statements.md)  
  
-   [Cursor-Bibliothek-Codebeispiel](../../../odbc/reference/appendixes/cursor-library-code-example.md)  
  
-   [Implementierungshinweise](../../../odbc/reference/appendixes/implementation-notes.md)  
  
-   [ODBC Cursor Library Error Codes (ODBC-Cursorbibliothek – Fehlercodes)](../../../odbc/reference/appendixes/odbc-cursor-library-error-codes.md)
