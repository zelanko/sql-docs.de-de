---
title: Katalog Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], about catalog functions
- data dictionary [ODBC]
- catalog functions [ODBC]
- functions [ODBC], catalog functions
ms.assetid: 81ba9453-c085-47c0-b411-90ca6a5ee428
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 232d2e9b7e9eb695a40058075ea511392e464a32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064400"
---
# <a name="catalog-functions"></a>Katalogfunktionen
Alle Datenbanken verfügen über eine Struktur, die beschreibt, wie Daten in der Datenbank gespeichert werden. Beispielsweise könnte eine einfache Verkaufs Auftrags Datenbank die Struktur enthalten, die in der folgenden Abbildung dargestellt ist, in der die ID-Spalten zum Verknüpfen der Tabellen verwendet werden.  
  
 ![Zeigt die Struktur einer einfachen Datenbank](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Diese Struktur wird zusammen mit anderen Informationen, wie z. b. Berechtigungen, in einer Reihe von Systemtabellen gespeichert, die als Katalog der Datenbank bezeichnet *werden* . Dies wird auch als *Datenwörterbuch*bezeichnet.  
  
 Eine Anwendung kann diese Struktur durch Aufrufe der- *Katalog Funktionen*ermitteln. Die Katalog Funktionen geben Informationen in Resultsets zurück und werden in der Regel durch **Select** -Anweisungen für die Tabellen im Katalog implementiert. Beispielsweise könnte eine Anwendung ein Resultset mit Informationen über alle Tabellen im System oder alle Spalten in einer bestimmten Tabelle anfordern.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Verwendung von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Katalogfunktionen in ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)
