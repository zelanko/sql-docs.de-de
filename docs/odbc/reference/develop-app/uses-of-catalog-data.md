---
title: Verwendung von Katalogdaten | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306811"
---
# <a name="uses-of-catalog-data"></a>Verwendung von Katalogdaten
Anwendungen verwenden Katalogdaten auf verschiedene Weise. Hier sind einige gängige Verwendungsmöglichkeiten:  
  
-   **Erstellen von SQL-Anweisungen zur Laufzeit.** Vertikale Anwendungen, wie z. b. eine Order Entry-Anwendung, enthalten hart codierte SQL-Anweisungen. Die von der Anwendung verwendeten Tabellen und Spalten werden im Vorfeld korrigiert, ebenso wie die-Anweisungen, die auf diese Tabellen zugreifen. Beispielsweise enthält eine Order Entry-Anwendung in der Regel eine einzelne, parametrisierte **Insert** -Anweisung zum Hinzufügen neuer Aufträge zum System.  
  
     Generische Anwendungen, wie z. b. ein Tabellen Kalkulations Programm, das ODBC zum Abrufen von Daten verwendet, erstellen häufig SQL-Anweisungen zur Laufzeit basierend auf der Eingabe des Benutzers. Eine solche Anwendung kann verlangen, dass der Benutzer die Namen der zu verwendenden Tabellen und Spalten eingeben muss. Der Benutzer wäre jedoch einfacher, wenn die Anwendung Listen von Tabellen und Spalten zeigt, aus denen der Benutzer eine Auswahl treffen kann. Um diese Listen zu erstellen, ruft die Anwendung die **SQLTables** -und **SQLColumns** -Katalog Funktionen auf.  
  
-   **Erstellen von SQL-Anweisungen während der Entwicklung.** Anwendungsentwicklungsumgebungen ermöglichen es dem Programmierer in der Regel, beim Entwickeln eines Programms Datenbankabfragen zu erstellen. Die Abfragen werden dann in der erstellten Anwendung hart codiert.  
  
     In solchen Umgebungen können auch **SQLTables** und **SQLColumns** verwendet werden, um Listen zu erstellen, aus denen der Programmierer eine Auswahl treffen könnte. Diese Umgebungen können auch **SQLPrimaryKeys** und **sqlfremd nkeys** verwenden, um die Beziehungen zwischen ausgewählten Tabellen automatisch zu bestimmen und anzuzeigen. mit **SQLStatistics** können Sie indizierte Felder ermitteln und hervorheben, damit der Programmierer effiziente Abfragen erstellen kann.  
  
-   **Erstellen von Cursorn** Eine Anwendung, ein Treiber oder eine Middleware, die eine Bild lauffähige Cursor-Engine bereitstellt, kann mithilfe von **SQLSpecialColumns** ermitteln, welche Spalten oder Spalten eine Zeile eindeutig identifizieren. Das Programm kann ein *Keyset* erstellen, das die Werte dieser Spalten für jede abgerufene Zeile enthält. Wenn die Anwendung zurück zur Zeile führt, werden diese Werte verwendet, um die aktuellsten Daten für die Zeile abzurufen. Weitere Informationen zu scrollfähigen Cursorn und Keysets finden Sie unter [scrollfähige Cursor](../../../odbc/reference/develop-app/scrollable-cursors.md).
