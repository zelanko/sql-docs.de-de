---
title: Erstellen einer Targeted Mailing-Miningmodellstruktur (Lernprogramm zu Datamining-Lernprogramm) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9c67f29-0c47-4a5a-862b-db0f5213c2c9
caps.latest.revision: 54
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3f0a8632df2009846d8b17d956c750ae12356829
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312478"
---
# <a name="creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial"></a>Erstellen der Miningmodellstruktur "Targeted Mailing" (Basic Data Mining-Lernprogramm)
  Der erste Schritt beim Erstellen eines Targeted Mailing-Szenarios besteht darin, mit dem Data Mining-Assistenten in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] eine neue Miningstruktur und ein Entscheidungsstruktur-Miningmodell zu erstellen.  
  
 In dieser Aufgabe werden Sie richten Sie eine neue Miningstruktur und fügen Sie ein initiales Data Mining-Modell basierend auf den [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Algorithmus. Um die Struktur zu erstellen, wählen Sie zuerst Tabellen und Sichten aus. Anschließend legen Sie fest, welche Spalten für das Trainieren und welche für das Testen verwendet werden.  
  
### <a name="to-create-a-mining-structure-for-the-targeted-mailing-scenario"></a>So erstellen Sie eine Miningstruktur für das Targeted Mailing-Szenario  
  
1.  Klicken Sie im Projektmappen-Explorer mit der Maustaste **Miningstrukturen** , und wählen Sie **neue Miningstruktur** Data Mining-Assistenten zu starten.  
  
2.  Klicken Sie auf der Seite **Willkommen** auf **Weiter**.  
  
3.  Auf der **Definitionsmethode auswählen** Seite, überprüfen Sie, ob **aus vorhandener relationaler Datenbank oder vorhandenem Data Warehouse** ausgewählt ist, und klicken Sie dann auf **Weiter**.  
  
4.  Auf der **Data Mining-Struktur erstellen** Seite **welche Datamining-Technik möchten Sie verwenden?** Option **Microsoft Decision Trees**.  
  
    > [!NOTE]  
    >  Wenn Sie eine Warnung erhalten, dass keine Data Mining-Algorithmen gefunden werden können, werden die Projekteigenschaften möglicherweise nicht korrekt konfiguriert. Diese Warnung tritt auf, wenn das Projekt versucht, eine Liste mit Data Mining-Algorithmen vom [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server abzurufen, und den Server nicht finden kann. Standardmäßig [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] verwenden **"localhost"** als Server. Wenn Sie eine andere Instanz oder eine benannte Instanz verwenden, müssen die Projekteigenschaften geändert werden. Weitere Informationen finden Sie unter [Erstellen eines Analysis Services-Projekts &#40;Basic Data Mining Tutorial&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md).  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der **Datenquellensicht auswählen** Seite in der **verfügbare Datenquellensichten** wählen Sie im Bereich **Targeted Mailing**. Klicken Sie auf **Durchsuchen** die Tabellen in der Datenquellensicht anzeigen, und klicken Sie dann auf **schließen** um zum Assistenten zurückzukehren.  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Auf der **Tabellentypen angeben** Seite, wählen Sie das Kontrollkästchen in der **Fall** Spalte für vTargetMail als Falltabelle verwenden, und klicken Sie dann auf **Weiter**. Die ProspectiveBuyer-Tabelle wird später Testzwecken verwenden; ignorieren Sie ihn jetzt ein.  
  
9. Auf der **Trainingsdaten angeben** Seite Geben Sie mindestens eine vorhersagbare Spalte, eine Schlüsselspalte, und eine Eingabespalte für Ihr Modell. Wählen Sie das Kontrollkästchen in der **vorhersagbar** Spalte in der **BikeBuyer** Zeile.  
  
    > [!NOTE]  
    >  Beachten Sie die Warnung am unteren Rand des Fensters. Sie werden nicht in der Lage, zur nächsten Seite navigieren, bis Sie mindestens eine auswählen **Eingabe** eine **vorhersagbar** Spalte.  
  
10. Klicken Sie auf **vorschlagen** So öffnen die **verbundene Spalten vorschlagen** (Dialogfeld).  
  
     Die **vorschlagen** Schaltfläche ist aktiviert, wenn mindestens ein vorhersagbares Attribut ausgewählt wurde. Die **verbundene Spalten vorschlagen** Dialogfeld listet die Spalten, die am ehesten der vorhersagbaren Spalte verknüpft sind, und sortiert die Attribute nach ihrer Korrelation mit dem vorhersagbaren Attribut. Spalten mit einer wesentlichen Korrelation (Vertrauen größer als 95 %) werden automatisch für die Aufnahme ins Modell ausgewählt.  
  
     Überprüfen Sie die Vorschläge, und klicken Sie dann auf **"Abbrechen"** Toignore Vorschläge.  
  
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
  
    -   **Nachname**  
  
     Stellen Sie sicher, dass diese Zeilen nur Häkchen in der linken Spalte aufweisen. Diese Spalten werden der Struktur hinzugefügt, jedoch nicht in das Modell aufgenommen. Nachdem das Modell erstellt wurde, stehen sie jedoch für Drillthrough und Tests zur Verfügung. Weitere Informationen zu Drillthrough finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
14. Klicken Sie auf **Weiter**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Angeben von den Daten- und Inhaltstyp &#40;Lernprogramm zu Datamining-Lernprogramm&#41;](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellentypen angeben &#40;Datamining-Assistenten&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md)   
 [Datamining-Designer](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Microsoft Decision Trees-Algorithmus](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)  
  
  