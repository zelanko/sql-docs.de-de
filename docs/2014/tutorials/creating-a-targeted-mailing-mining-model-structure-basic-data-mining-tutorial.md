---
title: Erstellen eine Targeted Mailing-Miningmodellstruktur (Lernprogramm zu Datamining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: a9c67f29-0c47-4a5a-862b-db0f5213c2c9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 112b45f2d5797d6797903661de0376bd4d316c6a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087710"
---
# <a name="creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial"></a>Erstellen der Miningmodellstruktur "Targeted Mailing" (Basic Data Mining-Lernprogramm)
  Der erste Schritt beim Erstellen eines Targeted Mailing-Szenarios besteht darin, mit dem Data Mining-Assistenten in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] eine neue Miningstruktur und ein Entscheidungsstruktur-Miningmodell zu erstellen.  
  
 In dieser Aufgabe Sie richten Sie eine neue Miningstruktur, und fügen Sie ein erstes Miningmodell auf der Grundlage der [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Algorithmus. Um die Struktur zu erstellen, wählen Sie zuerst Tabellen und Sichten aus. Anschließend legen Sie fest, welche Spalten für das Trainieren und welche für das Testen verwendet werden.  
  
### <a name="to-create-a-mining-structure-for-the-targeted-mailing-scenario"></a>So erstellen Sie eine Miningstruktur für das Targeted Mailing-Szenario  
  
1.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **Miningstrukturen** , und wählen Sie **neue Miningstruktur** Data Mining-Assistenten zu starten.  
  
2.  Klicken Sie auf der Seite **Willkommen** auf **Weiter**.  
  
3.  Auf der **Definitionsmethode auswählen** überprüfen Sie, ob Seite **aus vorhandener relationaler Datenbank oder Data Warehouse** ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **Erstellen von Data Mining-Struktur** Seite **welche Datamining-Technik möchten Sie verwenden?** Option **Microsoft Decision Trees**.  
  
    > [!NOTE]  
    >  Wenn Sie eine Warnung erhalten, dass keine Data Mining-Algorithmen gefunden werden können, werden die Projekteigenschaften möglicherweise nicht korrekt konfiguriert. Diese Warnung tritt auf, wenn das Projekt versucht, eine Liste mit Data Mining-Algorithmen vom [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server abzurufen, und den Server nicht finden kann. In der Standardeinstellung [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] verwenden **"localhost"** als Server. Wenn Sie eine andere Instanz oder eine benannte Instanz verwenden, müssen die Projekteigenschaften geändert werden. Weitere Informationen finden Sie unter [Erstellen eines Analysis Services-Projekts &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md).  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der **Datenquellensicht auswählen** auf der Seite die **verfügbare Datenquellensichten** wählen Sie im Bereich **Targeted Mailing**. Klicken Sie auf **Durchsuchen** in den Tabellen in der Datenquellensicht anzeigen, und klicken Sie auf **schließen** um zum Assistenten zurückzukehren.  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Auf der **Tabellentypen angeben** Seite, wählen Sie das Kontrollkästchen in der **Fall** vTargetMail als Falltabelle verwenden, und klicken Sie dann auf Spalte **Weiter**. Sie werden die ProspectiveBuyer-Tabelle später verwenden, zu Testzwecken; vorerst ignorieren.  
  
9. Auf der **Trainingsdaten** Seite, Sie geben mindestens eine vorhersagbare Spalte, die eine Schlüsselspalte und eine Eingabespalte für Ihr Modell. Wählen Sie das Kontrollkästchen in der **vorhersagbar** -Spalte in der **BikeBuyer** Zeile.  
  
    > [!NOTE]  
    >  Beachten Sie die Warnung am unteren Rand des Fensters. Es ist nicht möglich, mit der nächsten Seite zu navigieren, bis Sie mindestens eine auswählen **Eingabe** eine **vorhersagbar** Spalte.  
  
10. Klicken Sie auf **vorschlagen** zum Öffnen der **verbundene Spalten vorschlagen** Dialogfeld.  
  
     Die **vorschlagen** Schaltfläche ist aktiviert, wenn mindestens ein vorhersagbares Attribut ausgewählt wurde. Die **verbundene Spalten vorschlagen** Dialogfeld listet die Spalten, die am ehesten der vorhersagbaren Spalte verknüpft sind, und sortiert die Attribute nach ihrer Korrelation mit dem vorhersagbaren Attribut. Spalten mit einer wesentlichen Korrelation (Vertrauen größer als 95 %) werden automatisch für die Aufnahme ins Modell ausgewählt.  
  
     Überprüfen Sie die Vorschläge, und klicken Sie dann auf **Abbrechen** Toignore Vorschläge.  
  
    > [!NOTE]  
    >  Wenn Sie auf **OK**, alle aufgelisteten Vorschläge werden im Assistenten als Eingabespalten gekennzeichnet werden. Wenn Sie nur einige der Vorschläge übernehmen möchten, müssen Sie die Werte manuell ändern.  
  
11. Überprüfen Sie, ob das Kontrollkästchen in der **Schlüssel** Spalte ausgewählt ist, der **CustomerKey** Zeile.  
  
    > [!NOTE]  
    >  Wenn in der Quelltabelle der Datenquellensicht ein Schlüssel angegeben ist, wählt der Data Mining-Assistent automatisch diese Spalte als Schlüssel für das Modell aus.  
  
12. Wählen Sie die Kontrollkästchen in der **Eingabe** Spalte in den folgenden Zeilen. Sie können mehrere Spalten auswählen, indem Sie einen Bereich von Zellen markieren und STRG drücken, während Sie ein Kontrollkästchen aktivieren.  
  
    -   **ALTER**  
  
    -   **CommuteDistance**  
  
    -   **EnglishEducation**  
  
    -   **EnglishOccupation**  
  
    -   **Geschlecht**  
  
    -   **GeographyKey**  
  
    -   **HouseOwnerFlag**  
  
    -   **MaritalStatus**  
  
    -   **NumberCarsOwned**  
  
    -   **NumberChildrenAtHome**  
  
    -   **Region**  
  
    -   **TotalChildren**  
  
    -   **YearlyIncome**  
  
13. Aktivieren Sie in der Spalte ganz links auf der Seite die Kontrollkästchen in den folgenden Zeilen.  
  
    -   **Adresszeile 1**  
  
    -   **AddressLine2**  
  
    -   **DateFirstPurchase**  
  
    -   **EmailAddress**  
  
    -   **Vorname**  
  
    -   **"LastName"**  
  
     Stellen Sie sicher, dass diese Zeilen nur Häkchen in der linken Spalte aufweisen. Diese Spalten werden der Struktur hinzugefügt, jedoch nicht in das Modell aufgenommen. Nachdem das Modell erstellt wurde, stehen sie jedoch für Drillthrough und Tests zur Verfügung. Weitere Informationen zu Drillthrough finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
14. Klicken Sie auf **Weiter**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Angeben von den Daten- und Inhaltstyp &#40;Lernprogramm zu Datamining-Grundlagen&#41;](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellentypen angeben &#40;Datamining-Assistent&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md)   
 [Datamining-Designer](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Microsoft Decision Trees-Algorithmus](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)  
  
  
