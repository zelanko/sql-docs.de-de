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
manager: craigg
ms.openlocfilehash: cad33f1ccf798a08ef1f11667e59b4d5fb4888d8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730648"
---
# <a name="step-4a-fetch-the-results"></a>Schritt 4a: Abrufen der Ergebnisse
Im nächste Schritt werden die Ergebnisse abgerufen werden, wie in der folgenden Abbildung dargestellt.  
  
 ![Zeigt das Abrufen von Ergebnissen in einer ODBC-Anwendung](../../../odbc/reference/develop-app/media/pr14.gif "pr14")  
  
 Wenn die Anweisung, die in "Schritt 3: Erstellen und eine SQL-Anweisung ausführen" ausgeführt wurde eine **wählen** Anweisung oder eine Katalogfunktion auf, ruft die Anwendung zuerst **SQLNumResultCols** um zu bestimmen, die Anzahl der Spalten im Resultset. Dieser Schritt ist nicht erforderlich, wenn die Anwendung bereits bekannt, die Anzahl der Resultsets, die Spalten ist, z. B. wenn die SQL-Anweisung in eine vertikale oder benutzerdefinierten Anwendung hartcodiert wird.  
  
 Als Nächstes ruft die Anwendung ab, der Name, Datentyp, Genauigkeit und Skalierung von jeder Resultsetspalte mit **SQLDescribeCol**. In diesem Fall ist dies nicht erforderlich für Anwendungen wie vertikale und benutzerdefinierte Anwendungen, die diese Informationen bereits kennen. Die Anwendung übergibt diese Informationen, um **SQLBindCol**, die eine Anwendungsvariable bindet, auf eine Spalte im Resultset.  
  
 Die Anwendung jetzt ruft **SQLFetch** zum Abrufen der ersten Zeile der Daten, und platzieren Sie die Daten aus dieser Zeile in den Variablen gebunden **SQLBindCol**. Wenn keine lange Daten in die Zeile vorhanden ist, ruft es dann **SQLGetData** zum Abrufen der Daten. Rufen Sie die Anwendung weiterhin **SQLFetch** und **SQLGetData** weitere Daten ab. Nachdem sie das Abrufen von Daten abgeschlossen hat, ruft **SQLCloseCursor** Schließen des Cursors.  
  
 Eine vollständige Beschreibung der Ergebnisse abrufen, finden Sie unter [Abrufen von Ergebnissen (Standard)](../../../odbc/reference/develop-app/retrieving-results-basic.md) und [Abrufen von Ergebnissen (Erweitert)](../../../odbc/reference/develop-app/retrieving-results-advanced.md).  
  
 Die Anwendung jetzt zurückgibt auf "Schritt 3: Erstellen und Ausführen einer SQL-Anweisung" zum Ausführen von einer anderen Anweisung in derselben Transaktion; oder mit "Schritt 5: Commit der Transaktion" für einen commit oder Rollback der Transaktion.
