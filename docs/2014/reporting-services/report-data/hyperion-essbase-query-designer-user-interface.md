---
title: Benutzeroberfläche des Abfrage-Designers von Hyperion Essbase | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10013"
- sql12.rtp.rptdesigner.dataview.hyperionessbasequerydesigner.f1
helpviewer_keywords:
- Hyperion Essbase Query Designer
- data sources [Reporting Services], Hyperion Essbase
- multidimensional data [Reporting Services]
- query designers [Reporting Services]
- Hyperion Essbase [Reporting Services], query designer
ms.assetid: bc91b422-c6ab-4062-a300-8290fae6191b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1c7a12ec8f9e2bd49c9aecc1080fe0b5cff854ce
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81387964"
---
# <a name="hyperion-essbase-query-designer-user-interface"></a>Benutzeroberfläche des Abfrage-Designers von Hyperion Essbase
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] bietet einen grafischer Abfrage-Designer zum Erstellen von MDX-Abfragen (Multidimensional Expression) für eine [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] -Datenquelle. Der grafische MDX-Abfrage-Designer verfügt über zwei Modi: Entwurfsmodus und Abfragemodus. Jeder Modus stellt einen Metadatenbereich bereit, in dem Sie Elemente aus einem für die Datenquelle definierten Cube ziehen können, um eine MDX-Abfrage zu erstellen, die beim Verarbeiten des Berichts Daten abruft.

> [!IMPORTANT]
>  Benutzer greifen auf Datenquellen zu, wenn sie Abfragen erstellen und ausführen. Sie sollten minimale Berechtigungen für die Datenquellen gewähren, z. B. nur Leseberechtigungen.

 Weitere Informationen zum Arbeiten mit einer mehrdimensionalen [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)]-Datenquelle finden Sie unter [Hyperion Essbase-Verbindungstyp (SSRS)](hyperion-essbase-connection-type-ssrs.md).

 In diesem Abschnitt werden die Schaltflächen auf der Symbolleiste und die Bereiche des Abfrage-Designers für jeden Modus des grafischen Abfrage-Designers beschrieben.

## <a name="graphical-query-designer-in-design-mode"></a>Grafischer Abfrage-Designer im Entwurfsmodus
 Wenn Sie eine MDX-Abfrage für ein Dataset bearbeiten, das eine [!INCLUDE[extEssbase](../../../includes/extessbase-md.md)] -Datenquelle verwendet, wird der grafische Abfrage-Designer im Entwurfsmodus geöffnet.

 In der folgenden Abbildung werden die Bereiche für den Entwurfsmodus bezeichnet.

 ![Abfrage-Designer für Hyperion Essbase-Datenquelle](../media/rsqd-dshyperionessbase-mdx-designmode.gif "Abfrage-Designer für Hyperion Essbase-Datenquelle")

 In der folgenden Tabelle sind die Bereiche in diesem Modus aufgeführt.

|Bereich|Funktion|
|----------|--------------|
|Cube auswählen (Schaltfläche)|Zeigt den aktuell ausgewählten Cube an.|
|Metadaten (Bereich)|Zeigt eine hierarchische Liste mit Cubes an.|
|Berechnete Elemente (Bereich)|Zeigt die aktuell definierten berechneten Elemente an, die für eine Verwendung in der Abfrage verfügbar sind.|
|Filter (Bereich)|Zeigt die in der Abfrage anzuwendenden Filter an.|
|Daten (Bereich)|Zeigt die Ergebnisse des Ausführens der Abfrage an.|

 Sie können Dimensionen und Measures aus dem Metadatenbereich und berechnete Elemente aus dem Bereich Berechnete Elemente in den Datenbereich ziehen. Wenn die Umschaltfläche **AutoExecute** auf der Symbolleiste aktiviert ist, führt der Abfrage-Designer die Abfrage jedes Mal aus, wenn Sie ein Objekt im Datenbereich ablegen. Wenn **AutoExecute** deaktiviert ist, führt der Abfrage-Designer die Abfrage nicht aus, während Sie Änderungen am Datenbereich vornehmen. Sie können die Abfrage mithilfe der Schaltfläche **Ausführen** auf der Symbolleiste manuell ausführen.

 Im Filterbereich können Sie Dimensionswerte auswählen, um die aus der Datenquelle abgerufenen Daten zu begrenzen. Werte, die Sie im Filter im Entwurfsmodus definieren, werden in der MDX-Where-Klausel im Abfragemodus angezeigt.

### <a name="toolbar-for-the-graphical-query-designer-in-design-mode-toolbar"></a>Symbolleiste für den grafischen Abfrage-Designer im Entwurfsmodus
 Die Symbolleiste des Abfrage-Designers stellt Schaltflächen bereit, die Ihnen beim Entwurf von MDX-Abfragen mit der grafischen Oberfläche helfen. In der folgenden Tabelle werden die Schaltflächen gezeigt und ihre Funktionen beschrieben.

|Taste|BESCHREIBUNG|
|------------|-----------------|
|**Als Text bearbeiten**|Wechseln zwischen dem textbasierten Abfrage-Designer und dem grafischen Abfrage-Designer. Nicht verfügbar für diesen Datenquellentyp.|
|**Importieren**|Importieren einer vorhandenen Abfrage aus einer Berichtsdefinitionsdatei (.rdl) im Dateisystem. Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|
|![Datasetfelder aktualisieren](../media/rsqdicon-refreshfields.gif "Aktualisieren der Datasetfelder")|Aktualisieren von Metadaten aus der Datenquelle.|
|![Berechnetes Element hinzufügen](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "Berechnetes Element hinzufügen")|Zeigt das Dialogfeld **Generator für berechnete Elemente** an. Verwenden Sie dies, um Ausdrücke für ein berechnetes Element zu erstellen bzw. zu bearbeiten, sowie zum Festlegen der **Lösungsreihenfolge** -Eigenschaft.|
|![Zum Anzeigen von leeren Zellen umschalten](../../analysis-services/media/rsqdicon-showemptycells.gif "Leere Zellen anzeigen/nicht anzeigen")|Umschalten zwischen Einblenden und Ausblenden leerer Zellen im Datenbereich. (Dies entspricht dem Verwenden der NON EMPTY-Klausel in MDX.)|
|![Abfrage automatisch ausführen](../../analysis-services/media/rsqdicon-autoexecute.gif "Abfrage automatisch ausführen")|Automatisches Ausführen der Abfrage und Anzeigen des Ergebnisses, sobald eine Änderung vorgenommen wird, beispielsweise Löschen einer Spalte im Datenbereich. Die Ergebnisse werden im Datenbereich angezeigt.|
|![Löschen](../../analysis-services/media/rsqdicon-delete.gif "Löschen")|Löschen des ausgewählten Elements aus der Abfrage. Verwenden Sie diese Schaltfläche, um ausgewählte Zeilen im Filterbereich zu löschen.|
|![Abfrage ausführen](../../analysis-services/media/rsqdicon-run.gif "Abfrage ausführen")|Führt die Abfrage aus und zeigt die Ergebnisse im Datenbereich an.|
|![Abfrage abbrechen](../../analysis-services/media/rsqdicon-cancel.gif "Abfrage abbrechen")|Abbrechen der Abfrage.|
|![In Entwurfsmodus wechseln](../../analysis-services/media/rsqdicon-designmode.gif "Wechselt in den Entwurfsmodus")|Umschalten zwischen Entwurfsmodus und Abfragemodus.|

## <a name="graphical-query-designer-in-query-mode"></a>Grafischer Abfrage-Designer im Abfragemodus
 Klicken Sie zum Umschalten des grafischen Abfrage-Designers in den Abfragemodus auf der Symbolleiste auf die Umschaltfläche **Entwurfsmodus** . In der folgenden Abbildung werden die Teile des Abfrage-Designers im Abfragemodus angezeigt.

 ![Abfrage-Designer im Abfragemodus für Hyperion](../media/rsqd-hyperionessbase-mdx-querymode.gif "Abfrage-Designer im Abfragemodus für Hyperion")

 Die folgende Tabelle beschreibt die Funktion jedes Bereichs.

|Bereich|Funktion|
|----------|--------------|
|Cube auswählen (Schaltfläche)|Zeigt den aktuell ausgewählten Cube an.|
|Metadaten/Funktionen (Bereich)|Zeigt ein Fenster im Registerformat mit einer Liste verfügbarer Metadaten oder Funktionen an, die zum Erstellen des Abfragetexts verwendet werden können.|
|Abfragebereich|Zeigt den aktuellen Abfragetext an.|
|Ergebnisbereich|Zeigt die Ergebnisse der Abfrage an.|

 Aus dem Metadatenbereich können Sie Measures und Dimensionen von der Registerkarte **Metadaten** in den MDX-Abfragebereich ziehen. Sie können Funktionen von der Registerkarte **Funktionen** in den MDX-Abfragebereich ziehen. Wenn Sie die Abfrage ausführen, zeigt der Ergebnisbereich die Ergebnisse für die aktuelle MDX-Abfrage an.

### <a name="toolbar-for-the-graphical-query-designer-in-query-mode"></a>Symbolleiste für den grafischen Abfrage-Designer im Abfragemodus
 Die Symbolleiste des Abfrage-Designers stellt Schaltflächen bereit, die Ihnen beim Entwurf von MDX-Abfragen mit der grafischen Oberfläche helfen. Die Schaltflächen der Symbolleiste sind im Entwurfs- und Abfragemodus identisch, aber die folgenden Schaltflächen sind für den Abfragemodus nicht aktiviert:

-   **Als Text bearbeiten**

-   **Berechnetes Element hinzufügen** (![Berechnetes Element hinzufügen](../../analysis-services/media/rsqdicon-addcalculatedmember.gif "Berechnetes Element hinzufügen"))

-   **Leere Zellen anzeigen** (![Schaltfläche zum ein-/ausblenden leerer Zellen](../../analysis-services/media/rsqdicon-showemptycells.gif "Leere Zellen anzeigen/nicht anzeigen"))

-   **AutoExecute** (![Abfrage automatisch ausführen](../../analysis-services/media/rsqdicon-autoexecute.gif "Abfrage automatisch ausführen"))

## <a name="see-also"></a>Weitere Informationen
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generators und SSRS-&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md) [RSReportDesigner-Konfigurationsdatei](../report-server/rsreportdesigner-configuration-file.md)


