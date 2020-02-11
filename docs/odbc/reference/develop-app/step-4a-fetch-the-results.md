---
title: 'Schritt 4a: Abrufen der Ergebnisse | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], fetching results
- fetches [ODBC], fetching results
ms.assetid: 77d30142-c774-473c-96fb-b364bb92ac60
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3ab0bdabe8b2d66bf054f07ea51056a4044b4ae8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114186"
---
# <a name="step-4a-fetch-the-results"></a>Schritt 4a: Abrufen der Ergebnisse
Der nächste Schritt besteht im Abrufen der Ergebnisse, wie in der folgenden Abbildung dargestellt.  
  
 ![Zeigt das Abrufen von Ergebnissen in einer ODBC-Anwendung](../../../odbc/reference/develop-app/media/pr14.gif "pr14")  
  
 Wenn die in "Schritt 3: Erstellen und Ausführen einer SQL-Anweisung" ausgeführte Anweisung eine **Select** -Anweisung oder eine Katalog Funktion war, ruft die Anwendung zuerst **SQLNumResultCols** auf, um die Anzahl der Spalten im Resultset zu ermitteln. Dieser Schritt ist nicht erforderlich, wenn die Anwendung bereits die Anzahl von Resultsetspalten kennt, z. b. wenn die SQL-Anweisung in einer vertikalen oder benutzerdefinierten Anwendung hart codiert ist.  
  
 Als nächstes Ruft die Anwendung den Namen, den Datentyp, die Genauigkeit und die Dezimal Stellung der einzelnen Resultsetspalten mit **SQLDescribeCol**ab. Dies ist auch für Anwendungen, wie z. b. vertikale und benutzerdefinierte Anwendungen, die diese Informationen bereits kennen, nicht erforderlich. Die Anwendung übergibt diese Informationen an **SQLBindCol**, das eine Anwendungs Variable an eine Spalte im Resultset bindet.  
  
 Die Anwendung ruft nun **SQLFetch** auf, um die erste Daten Zeile abzurufen und die Daten aus dieser Zeile in den mit **SQLBindCol**gebundenen Variablen zu platzieren. Wenn in der Zeile lange Daten vorhanden sind, wird **SQLGetData** aufgerufen, um die Daten abzurufen. Die Anwendung ruft weiterhin **SQLFetch** und **SQLGetData** auf, um weitere Daten abzurufen. Nachdem das Abrufen von Daten abgeschlossen ist, wird **SQLCloseCursor** aufgerufen, um den Cursor zu schließen.  
  
 Eine umfassende Beschreibung zum Abrufen von Ergebnissen finden Sie unter [Abrufen](../../../odbc/reference/develop-app/retrieving-results-basic.md) von Ergebnissen (Standard) und [Abrufen von Ergebnissen (erweitert)](../../../odbc/reference/develop-app/retrieving-results-advanced.md).  
  
 Die Anwendung kehrt nun zu "Schritt 3: Erstellen und Ausführen einer SQL-Anweisung" zurück, um eine weitere Anweisung in derselben Transaktion auszuführen. oder fährt mit "Schritt 5: Commit der Transaktion ausführen" fort, um einen Commit oder Rollback der Transaktion auszuführen.
