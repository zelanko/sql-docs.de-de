---
title: 'Schritt 4a: Abrufen der Ergebnisse | Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c4f810e5c42b54ec871c233ab498936abae610dc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302971"
---
# <a name="step-4a-fetch-the-results"></a>Schritt 4a: Abrufen der Ergebnisse
Der nächste Schritt besteht darin, die Ergebnisse abzurufen, wie in der folgenden Abbildung gezeigt.  
  
 ![Zeigt das Abrufen von Ergebnissen in einer ODBC-Anwendung](../../../odbc/reference/develop-app/media/pr14.gif "pr14")  
  
 Wenn es sich bei der in "Schritt 3: Build and Execute an SQL Statement" ausgeführten Anweisung um eine **SELECT-Anweisung** oder eine Katalogfunktion handelt, ruft die Anwendung **sqlNumResultCols** zuerst auf, um die Anzahl der Spalten im Resultset zu bestimmen. Dieser Schritt ist nicht erforderlich, wenn die Anwendung bereits die Anzahl der Ergebnissatzspalten kennt, z. B. wenn die SQL-Anweisung in einer vertikalen oder benutzerdefinierten Anwendung hartcodiert ist.  
  
 Als Nächstes ruft die Anwendung den Namen, den Datentyp, die Genauigkeit und den Maßstab jeder Ergebnissatzspalte mit **SQLDescribeCol**ab. Auch dies ist für Anwendungen wie vertikale und benutzerdefinierte Anwendungen, die diese Informationen bereits kennen, nicht erforderlich. Die Anwendung übergibt diese Informationen an **SQLBindCol**, das eine Anwendungsvariable an eine Spalte im Resultset bindet.  
  
 Die Anwendung ruft nun **SQLFetch** auf, um die erste Datenzeile abzurufen und die Daten aus dieser Zeile in den Variablen zu platzieren, die mit **SQLBindCol**gebunden sind. Wenn sich lange Daten in der Zeile befinden, ruft sie **SQLGetData** auf, um diese Daten abzurufen. Die Anwendung ruft weiterhin **SQLFetch** und **SQLGetData** auf, um zusätzliche Daten abzurufen. Nachdem das Abrufen von Daten abgeschlossen wurde, ruft es **SQLCloseCursor** auf, um den Cursor zu schließen.  
  
 Eine vollständige Beschreibung der Ergebnisse zum Abrufen finden Sie unter [Abrufen von Ergebnissen (Basic)](../../../odbc/reference/develop-app/retrieving-results-basic.md) und [Abrufen von Ergebnissen (Erweitert)](../../../odbc/reference/develop-app/retrieving-results-advanced.md).  
  
 Die Anwendung kehrt nun zu "Schritt 3: Erstellen und Ausführen einer SQL-Anweisung" zurück, um eine andere Anweisung in derselben Transaktion auszuführen. oder fährt mit "Schritt 5: Commit the Transaction" fort, um die Transaktion zu übertragen oder zurückzusetzen.
