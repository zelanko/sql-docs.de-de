---
title: 'Schritt 3: Erstellen und Ausführen einer SQL-Anweisung | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], building and executing statements
- SQL statements [ODBC], building and executing
ms.assetid: 133b8bd4-a3c8-4f7e-93c5-c05283c8e96f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e8322cf5e7b4a91bfc5f5f0204cfb25fa4bdad92
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306831"
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>Schritt 3: Erstellen und Ausführen einer SQL­Anweisung
Der dritte Schritt besteht darin, eine SQL-Anweisung zu erstellen und auszuführen, wie in der folgenden Abbildung gezeigt. Die Methoden, die zum Ausführen dieses Schritts verwendet werden, werden wahrscheinlich sehr unterschiedlich sein. Die Anwendung fordert den Benutzer möglicherweise auf, eine SQL-Anweisung einzugeben, eine SQL-Anweisung basierend auf Benutzereingaben zu erstellen oder eine hartcodierte SQL-Anweisung zu verwenden. Weitere Informationen finden Sie unter [Erstellen von SQL-Anweisungen](../../../odbc/reference/develop-app/constructing-sql-statements.md).  
  
 ![Zeigt das Erstellen und Ausführen einer SQL-Anweisung](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 Wenn die SQL-Anweisung Parameter enthält, bindet die Anwendung sie an Anwendungsvariablen, indem **sie SQLBindParameter** für jeden Parameter aufruft. Weitere Informationen finden Sie unter [Anweisungsparameter](../../../odbc/reference/develop-app/statement-parameters.md).  
  
 Nachdem die SQL-Anweisung erstellt wurde und alle Parameter gebunden sind, wird die Anweisung mit **SQLExecDirect**ausgeführt. Wenn die Anweisung mehrmals ausgeführt wird, kann sie mit **SQLPrepare** vorbereitet und mit **SQLExecute**ausgeführt werden. Weitere Informationen finden Sie unter [Ausführen einer Anweisung](../../../odbc/reference/develop-app/executing-a-statement.md).  
  
 Die Anwendung kann auch auf die Ausführung einer SQL-Anweisung ganz verzichten und stattdessen eine Funktion aufrufen, um ein Resultset zurückzugeben, das Kataloginformationen enthält, z. B. die verfügbaren Spalten oder Tabellen. Weitere Informationen finden Sie unter [Verwendung von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Die nächste Aktion der Anwendung hängt vom Typ der ausgeführten SQL-Anweisung ab.  
  
|Typ der SQL-Anweisung|Fahren Sie fort,|  
|---------------------------|----------------|  
|**SELECT-** oder Katalogfunktion|[Schritt 4a: Abrufen der Ergebnisse](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**UPDATE**, **DELETE**oder **INSERT**|[Schritt 4b: Abrufen der Zeilenanzahl](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|Alle anderen SQL-Anweisungen|Schritt 3: Erstellen und Ausführen einer SQL-Anweisung (dieses Thema) oder [Schritt 5: Commit der Transaktion](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
