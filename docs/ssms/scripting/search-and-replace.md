---
title: Suchen und Ersetzen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- match case [SQL Server]
- undo operations
- searches [SQL Server Management Studio]
- replacing text
- quick search and replaces [SQL Server Management Studio]
- Query Editor [SQL Server Management Studio], undo
- Query Editor [SQL Server Management Studio], searching
- regular expressions [SQL Server Management Studio]
- finding text [SQL Server Management Studio]
- text [SQL Server], search and replace operations
- finding [SQL Server Management Studio]
- locating text
- Query Editor [SQL Server Management Studio], replacing text
- Find and Replace dialog box
- wildcard options [SQL Server Management Studio]
- match whole word [SQL Server]
- searches [SQL Server Management Studio], replacing
ms.assetid: 3641c7b3-3e3e-4ddd-af82-c15b50004f94
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d84304f1ba307a55273ddd24aa11686cbd9743e1
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51643186"
---
# <a name="search-and-replace"></a>Suchen und Ersetzen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Es gibt mehrere verschiedene Möglichkeiten, Text zu suchen und zu ersetzen. Im Menü **Bearbeiten** stehen unter **Suchen und Ersetzen** vier Auswahlmöglichkeiten zur Verfügung: **Schnellsuche**, **Schnellersetzung**, **In Dateien suchen**oder **In Dateien ersetzen**. Durch jede dieser Optionen wird eine entsprechende Version des Dialogfelds **Suchen und Ersetzen** geöffnet. Mit Tastenkombinationen zur inkrementellen Suche können Sie auch einen Suchvorgang ohne Dialogfeld ausführen. Mit diesen Techniken können Sie den Bereich für den Such- und Ersetzungsvorgang steuern und die Methode zum Überprüfen von Suchübereinstimmungen und Ersetzungen auswählen.  
  
 Beim Suchen und Ersetzen von Text müssen Sie die folgenden Punkte beachten:  
  
-   Die im Dialogfeld **Suchen und Ersetzen** festgelegten Optionen betreffen alle Suchvorgänge. Zu diesen Optionen zählen **Groß-/Kleinschreibung beachten**, **Nur ganzes Wort suchen**, **Suchrichtung nach oben**, **Ausgeblendeten Text durchsuchen**, **Platzhalter**, **Reguläre Ausdrücke**, die Option zum **Suchen in allen geöffneten Dokumenten** und die Option zum **Suchen im aktuellen Projekt**. Diese Optionen sind nicht in allen Versionen des Dialogfelds **Suchen und Ersetzen** vollständig verfügbar.  
  
-   **Rückgängig** ist nur für Dokumente verfügbar, die nach einem Ersetzungsvorgang geöffnet bleiben.  
  
-   Wenn beim Vorgang**Alle ersetzen** , der sich über mehr als eine Datei erstreckt, die Option **Rückgängig** verwendet wird, wird sie als eine einzelne gesammelte Aktion über die betroffenen Dateien hinweg betrachtet. Das bedeutet, dass es nicht möglich ist, die Änderungen in einigen Dateien rückgängig zu machen und in anderen Dateien beizubehalten.  
  
 Im Allgemeinen können Sie keine Elemente mit grafischen Ansichten durchsuchen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Inkrementelles Durchsuchen eines aktiven Dokuments](../../relational-databases/scripting/search-an-active-document-incrementally.md)   
 [Interaktives Durchsuchen von Dokumenten](../../relational-databases/scripting/search-documents-interactively.md)   
 [Durchsuchen von Dokumenten mithilfe von Ergebnislisten](../../relational-databases/scripting/search-documents-using-results-lists.md)   
 [Suchen von Text mit Platzhaltern](../../relational-databases/scripting/search-text-with-wildcards.md)   
 [Suchen von Text mit regulären Ausdrücken](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  
