---
title: Erstellen einer zielgerichteten Mailing-Mining Modellstruktur (Lernprogramm zu Data Mining-Grundlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9c67f29-0c47-4a5a-862b-db0f5213c2c9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2bd2e9d0decc730a59b63ee600bec2d080cc85fb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62856161"
---
# <a name="creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial"></a>Erstellen der Miningmodellstruktur "Targeted Mailing" (Basic Data Mining-Lernprogramm)
  Der erste Schritt beim Erstellen eines Targeted Mailing-Szenarios besteht darin, mit dem Data Mining-Assistenten in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] eine neue Miningstruktur und ein Entscheidungsstruktur-Miningmodell zu erstellen.  
  
 In dieser Aufgabe richten Sie eine neue Mining Struktur ein und fügen basierend auf dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees-Algorithmus ein ursprüngliches Mining Modell hinzu. Um die Struktur zu erstellen, wählen Sie zuerst Tabellen und Sichten aus. Anschließend legen Sie fest, welche Spalten für das Trainieren und welche für das Testen verwendet werden.  
  
### <a name="to-create-a-mining-structure-for-the-targeted-mailing-scenario"></a>So erstellen Sie eine Miningstruktur für das Targeted Mailing-Szenario  
  
1.  Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **Mining Strukturen** , und wählen Sie **neue Mining Struktur** , um den Data Mining-Assistenten zu starten.  
  
2.  Klicken Sie auf der Seite **Willkommen** auf **Weiter**.  
  
3.  Überprüfen Sie auf der Seite **Definitions Methode auswählen** , ob **aus vorhandener relationaler Datenbank oder Data Warehouse** ausgewählt ist, und klicken Sie dann auf **weiter**.  
  
4.  Wählen Sie auf der Seite **Data Mining-Struktur erstellen** unter **welche Data Mining Technik möchten Sie verwenden?** die Option **Microsoft Decision Trees**aus.  
  
    > [!NOTE]  
    >  Wenn Sie eine Warnung erhalten, dass keine Data Mining-Algorithmen gefunden werden können, werden die Projekteigenschaften möglicherweise nicht korrekt konfiguriert. Diese Warnung tritt auf, wenn das Projekt versucht, eine Liste mit Data Mining-Algorithmen vom [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server abzurufen, und den Server nicht finden kann. Standardmäßig [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] verwendet **localhost** als Server. Wenn Sie eine andere Instanz oder eine benannte Instanz verwenden, müssen die Projekteigenschaften geändert werden. Weitere Informationen finden Sie unter [Erstellen eines Analysis Services Projekts &#40;Lernprogramm zu Data Mining-Grundlagen&#41;](../../2014/tutorials/creating-an-analysis-services-project-basic-data-mining-tutorial.md).  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Wählen Sie auf der Seite **Datenquellen Sicht auswählen** im Bereich **Verfügbare Datenquellen Sichten** die Option **Ziel Versand**aus. Sie können auf **Durchsuchen** klicken, um die Tabellen in der Datenquellen Sicht anzuzeigen, und dann auf **Schließen** klicken, um zum Assistenten zurückzukehren.  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Aktivieren Sie auf der Seite **Tabellentypen angeben** das Kontrollkästchen in der Spalte **Fall** für vTargetMail, um es als Fall Tabelle zu verwenden, und klicken Sie dann auf **weiter**. Sie verwenden die ProspectiveBuyer-Tabelle später zum Testen. ignorieren Sie es vorerst.  
  
9. Auf der Seite **Trainingsdaten angeben** identifizieren Sie mindestens eine vorhersagbare Spalte, eine Schlüssel Spalte und eine Eingabe Spalte für das Modell. Aktivieren Sie das Kontrollkästchen in der Spalte **vorhersagbare** Spalte in der Zeile **BikeBuyer** .  
  
    > [!NOTE]  
    >  Beachten Sie die Warnung am unteren Rand des Fensters. Sie können erst zur nächsten Seite navigieren, wenn Sie mindestens eine **Eingabe** und eine **vorhersagbare** Spalte ausgewählt haben.  
  
10. Klicken Sie auf **vorschlagen** , um das Dialogfeld **Verbundene Spalten vorschlagen** zu öffnen.  
  
     Die Schaltfläche **vorschlagen** wird immer dann aktiviert, wenn mindestens ein vorhersagbares Attribut ausgewählt wurde. Im Dialogfeld verknüpfte **Spalten vorschlagen** werden die Spalten aufgelistet, die am ehesten mit der vorhersagbaren Spalte verknüpft sind, und die Attribute werden nach ihrer Korrelation mit dem vorhersagbaren Attribut sortiert. Spalten mit einer wesentlichen Korrelation (Vertrauen größer als 95 %) werden automatisch für die Aufnahme ins Modell ausgewählt.  
  
     Überprüfen Sie die Vorschläge, und klicken Sie dann auf **Abbrechen** , um die Vorschläge zu ignorieren.  
  
    > [!NOTE]  
    >  Wenn Sie auf " **OK**" klicken, werden alle aufgeführten Vorschläge im Assistenten als Eingabe Spalten gekennzeichnet. Wenn Sie nur einige der Vorschläge übernehmen möchten, müssen Sie die Werte manuell ändern.  
  
11. Vergewissern Sie sich, dass das Kontrollkästchen in der Spalte **Schlüssel** in der Zeile **CustomerKey** ausgewählt ist.  
  
    > [!NOTE]  
    >  Wenn in der Quelltabelle der Datenquellensicht ein Schlüssel angegeben ist, wählt der Data Mining-Assistent automatisch diese Spalte als Schlüssel für das Modell aus.  
  
12. Aktivieren Sie die Kontrollkästchen in der **Eingabe** Spalte in den folgenden Zeilen. Sie können mehrere Spalten auswählen, indem Sie einen Bereich von Zellen markieren und STRG drücken, während Sie ein Kontrollkästchen aktivieren.  
  
    -   **Eder**  
  
    -   **Pendel Entfernung**  
  
    -   **Englischschulen**  
  
    -   **Englischen shoccupations**  
  
    -   **Geschlechter**  
  
    -   **GeographyKey**  
  
    -   **Housebesitzflag**  
  
    -   **Marital Status**  
  
    -   **Nummerierte nummerierte**  
  
    -   **NumberChildrenAtHome**  
  
    -   **Region**  
  
    -   **Totalchildren**  
  
    -   **YearlyIncome**  
  
13. Aktivieren Sie in der Spalte ganz links auf der Seite die Kontrollkästchen in den folgenden Zeilen.  
  
    -   **AddressLine1**  
  
    -   **AddressLine2**  
  
    -   **Spalte datefirstpurchase**  
  
    -   **EmailAddress**  
  
    -   **FirstName**  
  
    -   **LastName**  
  
     Stellen Sie sicher, dass diese Zeilen nur Häkchen in der linken Spalte aufweisen. Diese Spalten werden der Struktur hinzugefügt, jedoch nicht in das Modell aufgenommen. Nachdem das Modell erstellt wurde, stehen sie jedoch für Drillthrough und Tests zur Verfügung. Weitere Informationen zu Drillthrough finden Sie unter [Drillthrough-Abfragen &#40;Data Mining-&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
14. Klicken Sie auf **Weiter**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Angeben des Datentyps und des Inhaltstyps &#40;grundlegenden Data Mining-Lernprogramm&#41;](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Geben Sie die Tabellentypen &#40;Data Mining-Assistenten an&#41;](../../2014/analysis-services/specify-table-types-data-mining-wizard.md)   
 [Data Mining-Designer](../../2014/analysis-services/data-mining/data-mining-designer.md)   
 [Microsoft Decision Trees-Algorithmus](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)  
  
  
