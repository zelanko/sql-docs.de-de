---
title: Verwendung von Katalogdaten | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog data [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], using catalog data
ms.assetid: d5915d0c-eec3-4382-850e-bd863763c99a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 429d42d4a82d0f9f34e33eb4f5f3293100505da9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306811"
---
# <a name="uses-of-catalog-data"></a>Verwendung von Katalogdaten
Anwendungen verwenden Katalogdaten auf unterschiedliche Weise. Hier sind einige häufige Verwendungen:  
  
-   **Erstellen von SQL-Anweisungen zur Laufzeit.** Vertikale Anwendungen, z. B. eine Auftragseingabeanwendung, enthalten hartcodierte SQL-Anweisungen. Die Tabellen und Spalten, die von der Anwendung verwendet werden, werden im Voraus festgelegt, ebenso wie die Anweisungen, die auf diese Tabellen zugreifen. Beispielsweise enthält eine Auftragserfassungsanwendung in der Regel eine einzelne, parametrisierte **INSERT-Anweisung** zum Hinzufügen neuer Aufträge zum System.  
  
     Generische Anwendungen, z. B. ein Tabellenkalkulationsprogramm, das ODBC zum Abrufen von Daten verwendet, erstellen häufig SQL-Anweisungen zur Laufzeit basierend auf der Eingabe des Benutzers. Eine solche Anwendung kann verlangen, dass der Benutzer die Namen der zu verwendenden Tabellen und Spalten eingibt. Für den Benutzer wäre es jedoch einfacher, wenn die Anwendung Listen von Tabellen und Spalten anzeigt, aus denen der Benutzer eine Auswahl treffen könnte. Um diese Listen zu erstellen, ruft die Anwendung die **SQLTables-** und **SQLColumns-Katalogfunktionen** auf.  
  
-   **Erstellen von SQL-Anweisungen während der Entwicklung.** Anwendungsentwicklungsumgebungen ermöglichen es dem Programmierer in der Regel, Datenbankabfragen zu erstellen, während er ein Programm entwickelt. Die Abfragen werden dann in der zu erstellenden Anwendung hartcodiert.  
  
     Solche Umgebungen können auch **SQLTables** und **SQLColumns** verwenden, um Listen zu erstellen, aus denen der Programmierer eine Auswahl treffen kann. Diese Umgebungen können auch **SQLPrimaryKeys** und **SQLForeignKeys** verwenden, um Beziehungen zwischen ausgewählten Tabellen automatisch zu bestimmen und anzuzeigen, und **SQLStatistics** verwenden, um indizierte Felder zu bestimmen und hervorzuheben, damit der Programmierer effiziente Abfragen erstellen kann.  
  
-   **Konstruieren von Cursorn.** Eine Anwendung, ein Treiber oder eine Middleware, die ein scrollbares Cursormodul bereitstellt, kann **SQLSpecialColumns** verwenden, um zu bestimmen, welche Spalte oder Spalten eine Zeile eindeutig identifizieren. Das Programm könnte ein *Keyset* erstellen, das die Werte dieser Spalten für jede abgerufene Zeile enthält. Wenn die Anwendung zurück zur Zeile scrollt, wird diese Werte verwendet, um die neuesten Daten für die Zeile abzurufen. Weitere Informationen zu scrollbaren Cursorn und Keysets finden Sie unter [Scrollable Cursors](../../../odbc/reference/develop-app/scrollable-cursors.md).
