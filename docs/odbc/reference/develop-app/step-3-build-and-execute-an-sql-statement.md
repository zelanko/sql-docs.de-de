---
title: 'Schritt 3: Erstellen und Ausführen einer SQL-Anweisung | Microsoft-Dokumentation'
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114264"
---
# <a name="step-3-build-and-execute-an-sql-statement"></a>Schritt 3: Erstellen und Ausführen einer SQL­Anweisung
Der dritte Schritt besteht darin, eine SQL-Anweisung zu erstellen und auszuführen, wie in der folgenden Abbildung dargestellt. Die Methoden, die zum Ausführen dieses Schritts verwendet werden, sind wahrscheinlich sehr unterschiedlich. Die Anwendung kann den Benutzer auffordern, eine SQL-Anweisung einzugeben, eine SQL-Anweisung auf der Grundlage von Benutzereingaben zu erstellen oder eine hart codierte SQL-Anweisung zu verwenden. Weitere Informationen finden Sie unter [Erstellen von SQL-Anweisungen](../../../odbc/reference/develop-app/constructing-sql-statements.md).  
  
 ![Zeigt das Erstellen und Ausführen einer SQL-Anweisung](../../../odbc/reference/develop-app/media/pr13.gif "pr13")  
  
 Wenn die SQL-Anweisung Parameter enthält, bindet die Anwendung Sie an Anwendungsvariablen, indem **SQLBindParameter** für jeden Parameter aufgerufen wird. Weitere Informationen finden Sie unter [Anweisungs Parameter](../../../odbc/reference/develop-app/statement-parameters.md).  
  
 Nachdem die SQL-Anweisung erstellt und alle Parameter gebunden wurden, wird die Anweisung mit **SQLExecDirect**ausgeführt. Wenn die Anweisung mehrmals ausgeführt wird, kann Sie mit **SQLPrepare** vorbereitet und mit **SQLExecute**ausgeführt werden. Weitere Informationen finden Sie unter [Ausführen einer-Anweisung](../../../odbc/reference/develop-app/executing-a-statement.md).  
  
 Die Anwendung kann auch eine SQL-Anweisung vollständig ausführen und stattdessen eine Funktion aufrufen, um ein Resultset mit Katalog Informationen, wie z. b. den verfügbaren Spalten oder Tabellen, zurückzugeben. Weitere Informationen finden Sie unter [Verwenden von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md).  
  
 Die nächste Aktion der Anwendung hängt vom Typ der ausgeführten SQL-Anweisung ab.  
  
|Typ der SQL-Anweisung|Fortfahren mit|  
|---------------------------|----------------|  
|**Select** -oder Catalog-Funktion|[Schritt 4a: Abrufen der Ergebnisse](../../../odbc/reference/develop-app/step-4a-fetch-the-results.md)|  
|**Aktualisieren**, **Löschen**oder **Einfügen**|[Schritt 4b: Abrufen der Zeilenanzahl](../../../odbc/reference/develop-app/step-4b-fetch-the-row-count.md)|  
|Alle anderen SQL-Anweisungen|Schritt 3: Erstellen und Ausführen einer SQL-Anweisung (dieses Thema) oder [Schritt 5: Commit für die Transaktion](../../../odbc/reference/develop-app/step-5-commit-the-transaction.md) ausführen|
