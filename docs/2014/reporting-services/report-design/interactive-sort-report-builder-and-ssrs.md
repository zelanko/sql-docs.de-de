---
title: Interaktive Sortierung (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 00cafed5-1a3c-4ce0-a1fb-ff1e2613f495
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2f3e427e0bc407167f25d679954a8506256300fc
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56294322"
---
# <a name="interactive-sort-report-builder-and-ssrs"></a>Interaktive Sortierung (Berichts-Generator und SSRS)
  Sie können Schaltflächen für die interaktive Sortierung hinzufügen, um Benutzern das Umschalten zwischen der auf- und absteigenden Reihenfolge für Zeilen in einer Tabelle oder für Zeilen und Spalten in einer Matrix zu ermöglichen. Die häufigste Verwendung der interaktiven Sortierung besteht im Hinzufügen einer Sortierungsschaltfläche für die einzelnen Spaltenkopfzeilen. Benutzer können dann die Spalte auswählen, anhand derer die Sortierung erfolgen soll.  
  
 Interaktive Sortierungsschaltflächen können grundsätzlich jedem Textfeld hinzugefügt werden. Beispielsweise können Sie für ein Textfeld in einer Zeile außerhalb einer Zeilengruppe eine Sortierung für die übergeordneten Gruppenzeilen oder -spalten sowie für untergeordneten Gruppenzeilen oder -spalten oder für die Detailzeilen oder -spalten angeben. Sie können auch Felder in einem Gruppenausdruck kombinieren und eine Sortierung anhand mehrerer Felder durchführen.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Beim Hinzufügen einer interaktiven Sortierung müssen folgende Elemente angegeben werden:  
  
-   **Zu sortierende Elemente:** Zeilen oder Spalten?  
  
-   **Elemente, die Sortierkriterien:** Ein Feld, das in einer Tabellenspalte angezeigt wird? ein Feld, das nicht angezeigt wird.  
  
-   **Welche Kontext zum Sortieren in:** Beispielsweise können Sie Zeilen, die Zeilengruppen zugeordnet sortieren; Spalten, die Spaltengruppen zugeordnet werden; Detailzeilen; untergeordnete Gruppen in einer übergeordneten Gruppe oder über- und untergeordneten Gruppen zusammen.  
  
-   **Textfeld für die sortierungsschaltfläche:** In der Kopfzeile der Spalte oder in der Gruppenkopfzeile für die Zeile?  
  
-   **Synchronisierung die Sortierung mehrerer Datenbereiche:** Sie können einen Bericht entwerfen, sodass beim Umschalten der Sortierreihenfolge andere Datenbereiche mit den gleichen Vorgänger ebenfalls neu sortiert.  
  
 Eine Schritt-für-Schritt-Anleitung finden Sie unter [Hinzufügen einer interaktiven Sortierung zu einer Tabelle oder Matrix &#40;Berichts-Generator und SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).  
  
 In der folgenden Tabelle werden die Funktionen von interaktiven Sortierschaltflächen zusammengefasst.  
  
|Aktion|Sortierungselement|Positionierung der Sortierschaltfläche|Sortierungskriterium|Sortierungsbereich|  
|------------|------------------|----------------------------------|---------------------|----------------|  
|Sortierung von Detailzeilen für eine Tabelle ohne Gruppen|Details|Spaltenkopfzeile|Datasetfeld, das an diese Spalte gebunden ist|Datenbereich|  
|Sortieren von Gruppeninstanzen der obersten Ebene für eine Matrix|Gruppen|Spaltenkopfzeile|Gruppierungsausdruck für übergeordnete Gruppe|Datenbereich|  
|Sortierung von Detailzeilen für eine untergeordnete Gruppe in einer Tabelle|Details|Untergeordnete Gruppenkopfzeile|Datasetfeld für die Sortierung|Untergeordnete Gruppe|  
|Sortieren von Zeilen für mehrere Zeilengruppen und Detailzeilen in einer Tabelle|Gruppen (Neudefinierung des Gruppenausdrucks erforderlich)|Spaltenkopfzeile|Aggregat des Datasetfelds für die Sortierung|Datenbereich|  
|Synchronisieren der Sortierreihenfolge für mehrere Datenbereiche|Gruppen|Spaltenkopf (Standard)|Gruppierungsausdruck|Dataset|  
  
 Die interaktive Sortierung wird vom Berichtsprozessor nach Anwendung aller Datenbereichs- und Gruppensortierungsausdrücke angewendet. Weitere Informationen finden Sie unter [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
## <a name="adding-interactive-sort-for-multiple-groups"></a>Hinzufügen der interaktiven Sortierung für mehrere Gruppen  
 Sie können einer Tabelle mit geschachtelten Zeilengruppen, die jeweils auf einem Datasetfeld basieren, eine Schaltfläche für die interaktive Sortierung hinzufügen, um übergeordnete Gruppenwerte, untergeordnete Gruppenwerte oder Detailzeilen zu sortieren. Dabei können Sie Benutzern auch die Möglichkeit geben, die Tabelle sowohl nach übergeordneten als auch nach untergeordneten Werten zu sortieren, ohne mehrfach auf die Schaltfläche klicken zu müssen.  
  
 Hierzu müssen Sie die Tabelle umgestalten, um nach einem Ausdruck zu gruppieren, der mehrere Felder kombiniert. Wenn die Werte in der ursprünglichen Tabelle für ein Dataset mit Lagerbeständen beispielsweise erst nach der Größe und anschließend nach der Farbe sortiert werden, können Sie die beiden Kriterien mithilfe eines Gruppierungsausdrucks in einer Gruppe zusammenfassen. Weitere Informationen finden Sie unter [Hinzufügen einer interaktiven Sortierung zu einer Tabelle oder Matrix &#40;Berichts-Generator und SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Sortieren von Daten in einem Datenbereich &#40;Berichts-Generator und SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md)   
 [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Hinzufügen einer interaktiven Sortierung zu einer Tabelle oder Matrix &#40;Berichts-Generator und SSRS&#41;](add-interactive-sort-to-a-table-or-matrix-report-builder-and-ssrs.md)  
  
  
