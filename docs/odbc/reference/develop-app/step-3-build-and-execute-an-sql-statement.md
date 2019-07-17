---
title: 'Schritt 3: Erstellen und Ausführen einer SQL­Anweisung | Microsoft-Dokumentation'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f0e369b74ef629c5fd7136b9098f579b5ad2b1b4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114264"
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>Schritt 3: Erstellen und Ausführen einer SQL­Anweisung
Der dritte Schritt ist zum Erstellen und Ausführen einer SQL­Anweisung, wie in der folgenden Abbildung dargestellt. Die Methoden verwendet, um diesen Schritt ausführen, sind wahrscheinlich erheblich variieren. Die Anwendung kann der Benutzer aufgefordert, geben eine SQL-Anweisung ein, und erstellen eine SQL-Anweisung, die auf Grundlage der Benutzereingabe oder eine hartcodierten SQL-Anweisung verwenden. Weitere Informationen finden Sie unter [SQL-Anweisungen konstruieren](../../../odbc/reference/develop-app/constructing-sql-statements.md).  
  
 ![Zeigt die Erstellung und Ausführung einer SQL-Anweisung](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 Wenn die SQL-Anweisung Parameter enthält, die Anwendung bindet diese an Anwendungsvariablen durch Aufrufen von **SQLBindParameter** für jeden Parameter. Weitere Informationen finden Sie unter [Anweisungsparametern](../../../odbc/reference/develop-app/statement-parameters.md).  
  
 Nachdem die SQL-Anweisung basiert, und alle Parameter gebunden werden, wird die Anweisung ausgeführt, mit **SQLExecDirect**. Wenn die Anweisung mehrmals ausgeführt wird, können sie mit vorbereitet werden **SQLPrepare** und mit ausgeführten **SQLExecute**. Weitere Informationen finden Sie unter [Ausführen einer Anweisung](../../../odbc/reference/develop-app/executing-a-statement.md).  
  
 Die Anwendung kann auch wird die Ausführung einer SQL-Anweisung komplett und stattdessen Aufrufen eine Funktion zum Zurückgeben eines Resultsets, die Kataloginformationen, z. B. die verfügbaren Spalten oder Tabellen enthält. Weitere Informationen finden Sie unter [von Katalogdaten verwendet](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Die Anwendung die nächste Aktion hängt von den Typ des ausgeführten SQL-Anweisung ab.  
  
|Typ der SQL-Anweisung|Fahren Sie fort mit|  
|---------------------------|----------------|  
|**Wählen Sie** oder Funktion|[Schritt 4a: Abrufen der Ergebnisse](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**UPDATE**, **löschen**, oder **einfügen**|[Schritt 4 b: Die Anzahl der Zeilen abrufen](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|Alle anderen SQL­Anweisungen|Schritt 3: Erstellen und Ausführen einer SQL-Anweisung (dieses Thema) oder [Schritt 5: Die Transaktion ein Commit ausgeführt](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md)|
