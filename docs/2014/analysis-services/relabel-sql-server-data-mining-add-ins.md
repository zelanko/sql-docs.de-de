---
title: Relabel (SQL Server Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- relabel
- data cleaning
ms.assetid: af041b39-fdd1-4cb5-a5ef-2f3ddab84614
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7f7d0accb835eb7da23ade6aec405066204fc415
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175599"
---
# <a name="relabel-sql-server-data-mining-add-ins"></a>Neu bezeichnen (SQL Server Data Mining-Add-Ins)
  ![Office 13-Symbol für das Tool "Neu bezeichnen"](media/dm13-relabel.gif "Office 13-Symbol für das Tool "Neu bezeichnen"")

 Im Data Mining-Client für Excel können Sie neue Bezeichnungen für Ihre Daten erstellen, um die Ergebnisse der Analyse übersichtlicher zu gestalten.

 Gründe für das Neubezeichnen umfassen:

-   Die Daten enthalten codierte Ergebnisse, wie 1 für Männlich und 2 für Weiblich.

-   Sie gruppieren numerische Werte und möchten den Bereichen einen aussagekräftigen Namen geben.

-   Sie möchten lange Namen vereinfachen.

## <a name="using-the-relabel-wizard"></a>Verwenden des Assistenten zum Neubezeichnen

1.  Klicken Sie im Menüband **Data Mining** auf **Bereinigen** , und wählen Sie dann **erneut Bezeichnung**aus.

2.  Wählen Sie die Tabelle oder den Datenbereich mit den zu bereinigenden Daten aus.

3.  Wählen Sie auf der Seite **neu bezeichnen** des Assistenten eine einzelne Spalte aus. Wählen Sie hierzu entweder die Spalte aus der Dropdown Liste aus, oder klicken Sie auf die Spalte im Bereich **Daten Stichproben** .

     Im Bereich **Daten Stichproben** werden nur ungefähr 50 Daten Zeilen angezeigt. Sie werden jedoch als Stichprobe angezeigt, um sicherzustellen, dass Sie eine gute Verteilung von Werten sehen.

     Klicken Sie auf die Spaltenüberschrift für **count** , um nach der Anzahl der einzelnen Werte zu sortieren.

     Sie können auch nach **ursprünglichen Bezeichnungen**sortieren. Dies ist praktisch, wenn Sie alle höchsten oder niedrigsten Werte zuerst neu bezeichnen möchten.

4.  Überprüfen Sie auf der Seite Daten **neu bezeichnen** des Assistenten die Werte in der Spalte **Original Bezeichnungen** , und entscheiden Sie, wie Sie diese gruppieren oder bearbeiten möchten.

5.  Geben Sie einen neuen Wert in die Zeile unter **neue Bezeichnungen**ein. Sie können auch einen Wert aus der Liste der vorhandenen Werte auswählen. Bei der Eingabe neuer Werte werden diese sofort für die Wiederverwendung verfügbar.

6.  Wenn Sie genügend Zeilen eingegeben haben, klicken Sie auf **weiter**, und wählen Sie auf der Seite **Ziel auswählen** aus, wo Sie die neu zu speichernden Daten speichern möchten.

    -   **Dem aktuellen Arbeitsblatt als neue Spalte hinzufügen**

         Klicken Sie auf diese Option, um der Tabelle eine neue Spalte mit den neuen Werten hinzuzufügen.

    -   **Blattdaten mit Änderungen in ein neues Arbeitsblatt kopieren**

         Klicken Sie auf diese Option, um ein neues Arbeitsblatt mit den aktualisierten Daten zu erstellen.

    -   **Daten direkt ändern**

         Klicken Sie auf diese Option, um die ursprünglichen Daten durch die neuen Werte zu ersetzen.

## <a name="see-also"></a>Weitere Informationen
 [Durchsuchen und Bereinigen von Daten](exploring-and-cleaning-data.md)


