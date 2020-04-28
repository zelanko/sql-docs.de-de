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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb28ec6f4ea299dae8737fc707fd53e4d102442d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305201"
---
# <a name="catalog-functions"></a>Katalogfunktionen
Alle Datenbanken verfügen über eine Struktur, die beschreibt, wie Daten in der Datenbank gespeichert werden. Beispielsweise könnte eine einfache Verkaufs Auftrags Datenbank die Struktur enthalten, die in der folgenden Abbildung dargestellt ist, in der die ID-Spalten zum Verknüpfen der Tabellen verwendet werden.  
  
 ![Zeigt die Struktur einer einfachen Datenbank](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Diese Struktur wird zusammen mit anderen Informationen, wie z. b. Berechtigungen, in einer Reihe von Systemtabellen gespeichert, die als Katalog der Datenbank bezeichnet *werden* . Dies wird auch als *Datenwörterbuch*bezeichnet.  
  
 Eine Anwendung kann diese Struktur durch Aufrufe der- *Katalog Funktionen*ermitteln. Die Katalog Funktionen geben Informationen in Resultsets zurück und werden in der Regel durch **Select** -Anweisungen für die Tabellen im Katalog implementiert. Beispielsweise könnte eine Anwendung ein Resultset mit Informationen über alle Tabellen im System oder alle Spalten in einer bestimmten Tabelle anfordern.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Verwendung von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Katalogfunktionen in ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)
