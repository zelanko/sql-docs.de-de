---
title: 'Schritt 8: Kommentieren und Formatieren des Pakets aus Lektion 1| Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/29/2020
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: e3751e53-77c7-47d0-8fe8-73ed1a53413a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 93a1ea1dd8fac01bb07aa2f2f8ffd4d363f57ffe
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86917322"
---
# <a name="lesson-1-8-annotate-and-format-the-lesson-1-package"></a>Lektion 1.8: Kommentieren und Formatieren des Pakets aus Lektion 1 

[!INCLUDE[sqlserver-ssis](../includes/applies-to-version/sqlserver-ssis.md)]



Nachdem Sie nun die Konfiguration des Pakets aus Lektion 1 abgeschlossen haben, bietet es sich an, den Inhalt des Paketlayouts wieder in eine klare Anordnung zu bringen. Wenn die Formen in den Layouts für Ablaufsteuerung und den Datenfluss unterschiedlich groß oder auf unübersichtliche Weise angeordnet sind, ist es möglicherweise schwieriger, das Paket zu verstehen.  
  
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools beinhaltet Tools zur einfachen Formatierung des Paketlayouts. Mit den bereitgestellten Formatierungsfunktionen können Sie u. a. die Größe von Formen anpassen, Formen ausrichten und die horizontalen und vertikalen Abstände zwischen Formen ändern.  
  
Eine weitere Möglichkeit, die Paketfunktionalität einfacher verständlich zu machen, besteht darin, Anmerkungen hinzuzufügen, in denen die Paketfunktionalität beschrieben wird.  
  
In dieser Aufgabe verwenden Sie die Formatierungsfeatures von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Data Tools, um das Layout des Datenflusses zu verbessern und eine Anmerkung hinzuzufügen.  
  
## <a name="format-the-layout-of-the-data-flow"></a>Formatieren des Layouts des Datenflusses  
  
1.  Wenn das Paket aus Lektion 1 noch nicht geöffnet ist, doppelklicken Sie auf **Lesson 1.dtsx** im **Projektmappen-Explorer**.  
  
2.  Klicken Sie auf die Registerkarte **Datenfluss**.  
  
3.  Wenn Sie alle Datenflusskomponenten gleichzeitig auswählen möchten, klicken Sie auf **Bearbeiten** > **Alles markieren**.
  
4.  Klicken Sie im Menü **Format** erst auf **Größe angleichen** und dann auf **Beides**.  
  
5.  Wenn die Datenflussobjekte ausgewählt sind, zeigen Sie im Menü **Format** auf **Ausrichten**, und klicken Sie dann auf **Centers** (Zentriert).  

6.  Wenn die Datenflussobjekte ausgewählt sind, zeigen Sie im Menü **Format** auf **Vertikaler Abstand**, und klicken Sie dann auf **Make Equal** (Gleich).  
  
## <a name="add-an-annotation-to-the-data-flow"></a>Hinzufügen einer Anmerkung zu einem Datenfluss  
  
1.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Hintergrund der Entwurfsoberfläche des Datenflusses, und klicken Sie anschließend auf **Anmerkung hinzufügen**.  
  
2.  Geben oder fügen Sie den folgenden Text in das Feld „Anmerkung“ ein.  
  
    Der Datenfluss extrahiert Daten aus einer Datei, schlägt Werte in der CurrencyKey-Spalte der DimCurrency-Tabelle und in der DateKey-Spalte der DimDate-Tabelle nach und schreibt die Daten in die NewFactCurrencyRate-Tabelle.
  
    Wenn der Text im Feld „Anmerkung“ umschlossen werden soll, müssen Sie den Cursor an der Stelle platzieren, an der eine neue Zeile beginnen soll, und dann die **EINGABETASTE** drücken.  
  
    Wenn Sie keinen Text in das Feld „Anmerkung“ eingeben, wird es nicht mehr angezeigt, sobald Sie außerhalb des Felds klicken.  Wenn Sie Text in das Feld „Anmerkung“ einfügen möchten, kopieren Sie daher den Text in die Zwischenablage, bevor Sie „Anmerkung hinzufügen“ auswählen. 
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe
[Schritt 9: Testen des Tutorialpakets aus Lektion 1](../integration-services/lesson-1-9-testing-the-lesson-1-tutorial-package.md)  
  
  
  
