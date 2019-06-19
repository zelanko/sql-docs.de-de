---
title: Katalogfunktionen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 268d5f00d787cef8dfdcb29bd9e091f81a5ed2c9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63125581"
---
# <a name="catalog-functions"></a>Katalogfunktionen
Alle Datenbanken verfügen über eine Struktur, die beschreibt, wie Daten in der Datenbank gespeichert werden. Eine einfache Verkaufsauftrag-Datenbank möglicherweise z. B. die Struktur, in der folgenden Abbildung, in der die ID-Spalten, zum Verknüpfen der Tabellen verwendet werden dargestellt.  
  
 ![Zeigt die Struktur einer einfachen Datenbank](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 Diese Struktur, zusammen mit anderen Informationen wie z. B. Berechtigungen befindet sich in einem Satz von Systemtabellen, die Namen der Datenbank *Katalog* Dies ist auch bekannt als eine *Datenwörterbuch*.  
  
 Eine Anwendung erkennen, diese Struktur durch Aufrufe von der *Katalogfunktionen*. Die Katalogfunktionen geben Informationen in Resultsets und sind in der Regel implementiert, über **wählen** Anweisungen für die Tabellen im Katalog. Beispielsweise könnte eine Anwendung ein Resultset mit Informationen über alle Tabellen im System oder alle Spalten in einer bestimmten Tabelle anfordern.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Verwendung von Katalogdaten](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [Katalogfunktionen in ODBC](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)
