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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114186"
---
# <a name="step-4a-fetch-the-results"></a>Schritt 4a: Abrufen der Ergebnisse
Im nächste Schritt werden die Ergebnisse abgerufen werden, wie in der folgenden Abbildung dargestellt.  
  
 ![Zeigt das Abrufen von Ergebnissen in einer ODBC-Anwendung](../../../odbc/reference/develop-app/media/pr14.gif "pr14")  
  
 Bei Ausführung die Anweisung in "Schritt 3: Erstellen und Ausführen einer SQL-Anweisung"wurde ein **wählen** Anweisung oder eine Katalogfunktion auf, ruft die Anwendung zuerst **SQLNumResultCols** um die Anzahl der Spalten im Resultset zu ermitteln. Dieser Schritt ist nicht erforderlich, wenn die Anwendung bereits bekannt, die Anzahl der Resultsets, die Spalten ist, z. B. wenn die SQL-Anweisung in eine vertikale oder benutzerdefinierten Anwendung hartcodiert wird.  
  
 Als Nächstes ruft die Anwendung ab, der Name, Datentyp, Genauigkeit und Skalierung von jeder Resultsetspalte mit **SQLDescribeCol**. In diesem Fall ist dies nicht erforderlich für Anwendungen wie vertikale und benutzerdefinierte Anwendungen, die diese Informationen bereits kennen. Die Anwendung übergibt diese Informationen, um **SQLBindCol**, die eine Anwendungsvariable bindet, auf eine Spalte im Resultset.  
  
 Die Anwendung jetzt ruft **SQLFetch** zum Abrufen der ersten Zeile der Daten, und platzieren Sie die Daten aus dieser Zeile in den Variablen gebunden **SQLBindCol**. Wenn keine lange Daten in die Zeile vorhanden ist, ruft es dann **SQLGetData** zum Abrufen der Daten. Rufen Sie die Anwendung weiterhin **SQLFetch** und **SQLGetData** weitere Daten ab. Nachdem sie das Abrufen von Daten abgeschlossen hat, ruft **SQLCloseCursor** Schließen des Cursors.  
  
 Eine vollständige Beschreibung der Ergebnisse abrufen, finden Sie unter [Abrufen von Ergebnissen (Standard)](../../../odbc/reference/develop-app/retrieving-results-basic.md) und [Abrufen von Ergebnissen (Erweitert)](../../../odbc/reference/develop-app/retrieving-results-advanced.md).  
  
 Die Anwendung jetzt zurückgegeben werden, um "Schritt 3: Erstellen und eine SQL-Anweisung ausführen"zum Ausführen von einer anderen Anweisung in derselben Transaktion; oder geht zur "Schritt 5: Commit die Transaktion"für einen commit oder Rollback der Transaktion.
