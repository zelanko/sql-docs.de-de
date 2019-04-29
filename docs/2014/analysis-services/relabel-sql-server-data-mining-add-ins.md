---
title: Neu bezeichnen (SQL Server Data Mining-Add-ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- relabel
- data cleaning
ms.assetid: af041b39-fdd1-4cb5-a5ef-2f3ddab84614
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 74e2322416ec06c36a7834f35581ed611480b6e6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62748323"
---
# <a name="relabel-sql-server-data-mining-add-ins"></a>Neu bezeichnen (SQL Server Data Mining-Add-Ins)
  ![Office 13-Symbol für das Tool neu bezeichnen](media/dm13-relabel.gif "Office 13-Symbol für Tool neu bezeichnen")  
  
 Im Data Mining-Client für Excel können Sie neue Bezeichnungen für Ihre Daten erstellen, um die Ergebnisse der Analyse übersichtlicher zu gestalten.  
  
 Gründe für das Neubezeichnen umfassen:  
  
-   Die Daten enthalten codierte Ergebnisse, wie 1 für Männlich und 2 für Weiblich.  
  
-   Sie gruppieren numerische Werte und möchten den Bereichen einen aussagekräftigen Namen geben.  
  
-   Sie möchten lange Namen vereinfachen.  
  
## <a name="using-the-relabel-wizard"></a>Verwenden des Assistenten zum Neubezeichnen  
  
1.  In der **Data Mining** des Menübands, klicken Sie auf **Bereinigen** und wählen Sie dann **neu bezeichnen**.  
  
2.  Wählen Sie die Tabelle oder den Datenbereich mit den zu bereinigenden Daten aus.  
  
3.  In der **neu bezeichnen** Seite des Assistenten wählen Sie eine einzelne Spalte auswählen die Spalte aus der Dropdownliste aus, oder indem Sie auf die Spalte in der **Datenstichproben** Bereich.  
  
     Die **Datenstichproben** Bereich zeigt nur etwa 50 Datenzeilen, aber sie werden Stichproben erstellt, um sicherzustellen, dass Sie eine gute von Werten Spannweite.  
  
     Klicken Sie auf die Spaltenüberschrift für **Anzahl** durch die Anzahl der einzelnen Werte zu sortieren.  
  
     Sie können auch sortieren, indem **ursprüngliche Bezeichnungen**, dies ist hilfreich, wenn Sie zunächst alle höchsten oder niedrigsten Werte neu bezeichnen möchten.  
  
4.  In der **neu bezeichnen** Datenseite des Assistenten, überprüfen Sie die Werte in der **ursprüngliche Bezeichnungen** Spalte, und entscheiden Sie, wie Sie möchten die gruppiert oder bearbeitet werden.  
  
5.  Geben Sie einen neuen Wert in der Zeile unter **neue Bezeichnungen**. Sie können auch einen Wert aus der Liste der vorhandenen Werte auswählen. Bei der Eingabe neuer Werte werden diese sofort für die Wiederverwendung verfügbar.  
  
6.  Wenn Sie genügend Zeilen eingegeben haben, klicken Sie auf **Weiter**, und klicken Sie auf die **Ziel auswählen** Seite, und wählen Sie in dem Sie die neu bezeichneten Daten speichern müssen.  
  
    -   **Das aktuelle Arbeitsblatt als neue Spalte hinzugefügt**  
  
         Klicken Sie auf diese Option, um der Tabelle eine neue Spalte mit den neuen Werten hinzuzufügen.  
  
    -   **Kopieren Sie Blattdaten mit Änderungen in ein neues Arbeitsblatt**  
  
         Klicken Sie auf diese Option, um ein neues Arbeitsblatt mit den aktualisierten Daten zu erstellen.  
  
    -   **Daten direkt ändern**  
  
         Klicken Sie auf diese Option, um die ursprünglichen Daten durch die neuen Werte zu ersetzen.  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen und Bereinigen von Daten](exploring-and-cleaning-data.md)  
  
  
