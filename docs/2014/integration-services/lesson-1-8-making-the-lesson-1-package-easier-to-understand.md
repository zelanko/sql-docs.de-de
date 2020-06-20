---
title: 'Schritt 8: Vereinfachen des Layouts des Pakets aus Lektion 1 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e3751e53-77c7-47d0-8fe8-73ed1a53413a
author: janinezhang
ms.author: janinez
ms.openlocfilehash: ffd151332fe5aa0c152ba66c159472dc9745f2d0
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966120"
---
# <a name="step-8-making-the-lesson-1-package-easier-to-understand"></a>Schritt 8: Vereinfachen des Layouts des Pakets aus Lektion 1
  Nachdem Sie nun die Konfiguration des Lektion 1-Pakets abgeschlossen haben, bietet es sich an, den Inhalt des Paketlayouts wieder in eine klare Anordnung zu bringen. Wenn die Formen in den Ablaufsteuerungs- und Datenflusslayouts beliebig groß oder nicht ausgerichtet oder gruppiert sind, lässt sich die Funktionsweise des Pakets möglicherweise schwerer nachvollziehen.  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools werden Ihnen Tools bereitgestellt, mit denen Sie das Paketlayout schnell und problemlos formatieren können. Mit den bereitgestellten Formatierungsfunktionen können Sie u. a. die Größe von Formen anpassen, Formen ausrichten und die horizontalen und vertikalen Zwischenräume zwischen Formen ändern.  
  
 Eine weitere Möglichkeit, die Paketfunktionalität einfacher verständlich zu machen, besteht darin, Anmerkungen hinzuzufügen, in denen die Paketfunktionalität beschrieben wird.  
  
 In dieser Aufgabe verwenden Sie die Formatierungsfunktionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools, um das Layout des Datenflusses zu verbessern und dem Datenfluss eine Anmerkung hinzuzufügen.  
  
### <a name="to-format-the-layout-of-the-data-flow"></a>So formatieren Sie das Layout des Datenflusses  
  
1.  Wenn das Lektion 1-Paket noch nicht geöffnet ist, doppelklicken Sie auf Lesson 1.dtsx im Projektmappen-Explorer.  
  
2.  Klicken Sie auf die Registerkarte **Datenfluss** .  
  
3.  Setzen Sie den Cursor an eine Position oben rechts von der Extract Sample Currency-Transformation, klicken Sie, und ziehen Sie dann den Cursor über alle Datenflusskomponenten.  
  
4.  Zeigen Sie im Menü **Format** auf **Größe angleichen**, und klicken Sie dann auf **Beides**.  
  
5.  Belassen Sie die Datenflussobjekte ausgewählt, zeigen Sie im Menü **Format** auf **Ausrichten**, und klicken Sie dann auf **Links**.  
  
### <a name="to-add-an-annotation-to-the-data-flow"></a>So fügen Sie dem Datenfluss eine Anmerkung hinzu  
  
1.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Hintergrund der Entwurfsoberfläche des Datenflusses, und klicken Sie anschließend auf **Anmerkung hinzufügen**.  
  
2.  Geben Sie den folgenden Text in das Anmerkungenfeld ein, oder fügen Sie ihn mit Kopieren und Einfügen ein.  
  
     **Der Datenfluss extrahiert Daten aus einer Datei, schlägt Werte in der CurrencyKey-Spalte der DimCurrency-Tabelle und in der DateKey-Spalte der DimDate-Tabelle nach und schreibt die Daten in die NewFactCurrencyRate-Tabelle.**  
  
     Wenn der Text im Anmerkungsfeld umbrochen werden soll, müssen Sie den Cursor an der Stelle platzieren, an der eine neue Zeile beginnen soll, und dann die EINGABETASTE drücken.  
  
     Wenn Sie keinen Text in das Anmerkungenfeld eingeben, ist es nicht mehr vorhanden, sobald Sie außerhalb des Felds klicken.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Schritt 9: Testen des Tutorialpakets aus Lektion 1](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
  
