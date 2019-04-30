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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d9b75d59d8fc28e364f5826d95e7fc50cb6afda7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63312533"
---
# <a name="uses-of-catalog-data"></a>Verwendung von Katalogdaten
Anwendungen verwenden die Daten im Katalog in einer Vielzahl von Möglichkeiten. Hier sind einige häufige Verwendungsmöglichkeiten:  
  
-   **Erstellen von SQL-Anweisungen zur Laufzeit.** Vertikale Anwendungen, z. B. auftragserfassungsanwendung, enthalten hartcodierte SQL-Anweisungen. Die Tabellen und Spalten, die von der Anwendung verwendet werden sind vorab festgelegt, ebenso wie die Anweisungen, die Zugriff auf diese Tabellen. Auftragserfassungsanwendung enthält z. B. in der Regel eine einzelne parametrisierte **einfügen** -Anweisung für das System neue Bestellungen hinzufügt.  
  
     Allgemeine Anwendungen, z. B. ein Tabellenkalkulationsprogramm, die ODBC verwendet wird, zum Abrufen von Daten, erstellen häufig SQL-Anweisungen zur Laufzeit basierend auf Benutzereingaben. Eine solche Anwendung könnte erfordern, dass der Benutzer zur Eingabe der Namen der Tabellen und Spalten verwendet. Allerdings wäre es einfacher für den Benutzer die Anwendung angezeigt, Listen, Tabellen und Spalten, die von denen der Benutzer eine Auswahl treffen kann. Um diese Listen zu erstellen, die Anwendung aufrufen, würden die **SQLTables** und **SQLColumns** Katalogfunktionen.  
  
-   **Erstellen von SQL-Anweisungen während der Entwicklung.** Anwendungsentwicklungsumgebungen ermöglichen in der Regel dem Programmierer Datenbankabfragen zu erstellen, während der Entwicklung eines Programms. Die Abfragen werden dann in der zu erstellenden Anwendung hartcodiert.  
  
     Umgebungen können auch **SQLTables** und **SQLColumns** zum Erstellen von Listen aus dem kann der Programmierer Auswahl vornehmen. Diese Umgebungen können auch **SQLPrimaryKeys** und **SQLForeignKeys** automatisch ermitteln und Anzeigen von Beziehungen zwischen ausgewählten Tabellen und verwenden **SQLStatistics** zu bestimmen, und markieren indizierte Felder aus, damit der Programmierer effiziente Abfragen erstellen kann.  
  
-   **Erstellen Cursor.** Eine Anwendung, Treiber oder Middleware, die eine bildlauffähigen Cursor-Engine bietet können **SQLSpecialColumns** um zu bestimmen, welche Spalte oder Spalten eine Zeile eindeutig identifizieren. Erstellen Sie das Programm konnte eine *Keyset* , die die Werte dieser Spalten für jede Zeile, die abgerufen wurde. Wenn die Anwendung wieder in die Zeile einen Bildlauf durchführt, würden sie diese Werte dann verwenden, zum Abrufen der neuesten Daten für die Zeile. Weitere Informationen zu scrollbare Cursor und Keysets, finden Sie unter [scrollfähige Cursor](../../../odbc/reference/develop-app/scrollable-cursors.md).
