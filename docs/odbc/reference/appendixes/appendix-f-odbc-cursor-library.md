---
title: 'Anhang F: ODBC-Cursorbibliothek | Microsoft-Dokumentation'
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
manager: craigg
ms.openlocfilehash: c27845976651b0d68b91b6269a21d1cae3518df8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649588"
---
# <a name="appendix-f-odbc-cursor-library"></a>Anhang F: ODBC-Cursorbibliothek
> [!IMPORTANT]  
>  Dieses Feature wird in einer zukünftigen Version von Windows entfernt werden. Zu vermeiden Sie, verwenden Sie diese Funktion beim Entwickeln neuer Anwendungen und Änderung von Anwendungen, die derzeit auf dieses Feature verwenden möchten. Microsoft empfiehlt die Verwendung von Cursor-Funktionalität des Treibers.  
  
 Die ODBC Cursor Library (Odbccr32.dll) unterstützt Block scrollfähige Cursor für alle Treiber, der mit dem Konformitätsgrad des API-Ebene-1 entsprechen und kann von Entwicklern mit ihrer Anwendungen oder die Treiber verteilt werden. Die Cursorbibliothek unterstützt auch positionierte Update- und Delete-Anweisungen für die Resultsets, die vom **wählen** Anweisungen. Obwohl es nur statische und Vorwärtscursor Cursor unterstützt, entspricht die Cursorbibliothek die Anforderungen vieler Anwendungen. Darüber hinaus kann er guten Leistung, insbesondere bei kleinen bis mittleren Resultsets und für Anwendungen, die keine gute cursorunterstützung bereitstellen.  
  
 Die Cursorbibliothek ist eine Dynamic Link Library (DLL), die zwischen der Treiber-Manager und der Treiber befindet. Wenn eine Anwendung eine Funktion aufruft, ruft der Treiber-Manager die Funktion in der Cursorbibliothek, die die Funktion ausgeführt, oder ruft sie in der angegebenen Treiber an. Für eine angegebene Verbindung gibt eine Anwendung an, ob die Cursorbibliothek ist immer verwendet, verwendet, wenn der Treiber scrollfähige Cursor nicht unterstützt oder noch nie verwendet.  
  
 Die Cursorbibliothek wird als einen Treiber in den Treiber-Manager angezeigt. Wenn die Cursorbibliothek zwischen der Treiber-Manager und einer ODBC 2. befindet. *x* -Treiber die Cursorbibliothek angezeigt, als einer ODBC 2. *X* Treiber. Wenn die Cursorbibliothek zwischen der Treiber-Manager "und" einen ODBC-3 befindet *.x* -Treiber die Cursor-Bibliothek angezeigt wird, als eine ODBC 3.*.x* Treiber. Das Verhalten, die von der Cursorbibliothek richtet sich nach der Version des Treibers, mit denen sie ist arbeiten, mit Ausnahme der Bindung Offsets, die für beide ODBC 2. unterstützt wird. *x* und ODBC 3. *X* Treiber.  
  
 Zum Implementieren von Blockcursor **SQLFetch** und **SQLFetchScroll**, ruft die Cursorbibliothek wiederholt **SQLFetch** im Treiber. Um einen Bildlauf zu implementieren, zwischengespeichert die Daten, die er, im Arbeitsspeicher und in Dateien auf Datenträgern abgerufen hat. Wenn eine Anwendung ein neues Rowset anfordert, ruft die Cursorbibliothek es nach Bedarf aus der Treiber oder dem Cache ab.  
  
 Zum Implementieren von positionierten Updates und delete-Anweisungen, die Cursorbibliothek erstellt eine **aktualisieren** oder **löschen** -Anweisung mit einer **, in denen** Klausel, die die zwischengespeicherten angibt der Wert jeder gebundene Spalte in der Zeile. Wenn sie eine positioniertes Update-Anweisung ausgeführt wird, aktualisiert die Cursorbibliothek seinen-Cache von den Werten in den Puffern Rowset.  
  
 Weitere Informationen zu den ODBC-Cursorbibliothek finden Sie unter den folgenden Abschnitten in diesem Anhang:  
  
-   [Using the ODBC Cursor Library (Verwenden der ODBC-Cursorbibliothek)](../../../odbc/reference/appendixes/using-the-odbc-cursor-library.md)  
  
-   [Executing Positioned Update and Delete Statements (Ausführen einer positionierten Aktualisierung und von DELETE-Anweisungen)](../../../odbc/reference/appendixes/executing-positioned-update-and-delete-statements.md)  
  
-   [Cursor-Bibliothek-Codebeispiel](../../../odbc/reference/appendixes/cursor-library-code-example.md)  
  
-   [Hinweise zur Implementierung](../../../odbc/reference/appendixes/implementation-notes.md)  
  
-   [ODBC Cursor Library Error Codes (ODBC-Cursorbibliothek – Fehlercodes)](../../../odbc/reference/appendixes/odbc-cursor-library-error-codes.md)
