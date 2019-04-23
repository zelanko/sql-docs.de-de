---
title: Benutzeroberfläche des DMX-Abfrage-Designers für Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10012"
- sql12.rtp.rptdesigner.dataview.asquerydesigner.f1
helpviewer_keywords:
- Analysis Services [DMX]
- DMX [Analysis Services], user interface
- query designers [DMX]
ms.assetid: 5fd726a4-aed7-4e6c-9404-ccb2db66cf26
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5333f3d56713d5b37ceabe92e831113a66bc491b
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59971966"
---
# <a name="analysis-services-dmx-query-designer-user-interface"></a>Benutzeroberfläche des DMX-Abfrage-Designers für Analysis Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt grafische Abfrage-Designer zum Erstellen von DMX-Abfragen (Data Mining-Erweiterungen) und MDX-Abfragen (Multidimensional Expression) für eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenquelle bereit. Dieses Thema beschreibt den DMX-Abfrage-Designer. Weitere Informationen zum MDX-Abfrage-Designer finden Sie unter [Analysis Services MDX Query Designer User Interface](analysis-services-mdx-query-designer-user-interface.md).  
  
 DMX grafischen Abfrage-Designer verfügt über drei Modi: Entwurf, Abfrage und Ergebnis. Klicken Sie mit der rechten Maustaste in den Abfrageentwurfsbereich, um zwischen den Modi zu wechseln, und wählen Sie den gewünschten Modus aus. Jeder Modus bietet einen Metadatenbereich, aus dem Sie Elemente aus den ausgewählten Cubes ziehen können, um eine DMX-Abfrage zu erstellen. Die DMX-Abfrage ruft Daten für ein Dataset ab, wenn der Bericht verarbeitet wird.  
  
## <a name="graphical-dmx-query-designer-toolbar"></a>Symbolleiste für den grafischen DMX-Abfrage-Designer  
 Die Symbolleiste des Abfrage-Designers beinhaltet Schaltflächen, die Ihnen den Entwurf von DMX-Abfragen mithilfe der grafischen Oberfläche ermöglichen. In der folgenden Tabelle werden die Schaltflächen und ihre Funktionen beschrieben.  
  
|Schaltfläche|Description|  
|------------|-----------------|  
|**Als Text bearbeiten**|Deaktiviert für diesen Datenquellentyp.|  
|**Importieren**|Importieren einer vorhandenen Abfrage aus einer Berichtsdefinitionsdatei (.rdl) im Dateisystem. Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Wechseln zur MDX-Abfrageansicht](../../analysis-services/media/rsqdicon-commandtypemdx.gif "Change to MDX query view")|Wechseln zum Modus für den MDX-Abfrage-Designer.|  
|![Wechseln zur DMX-Abfragesprachenansicht](../media/rsqdicon-commandtypedmx.gif "Change to DMX query language view")|Wechseln zum Modus für den DMX-Abfrage-Designer.|  
|![Aktualisieren der Ergebnisdaten](../../analysis-services/media/rsqdicon-refresh.gif "Refresh result data")|Aktualisieren von Metadaten aus der Datenquelle.|  
|![Löschen](../../analysis-services/media/rsqdicon-delete.gif "Löschen")|Löschen der ausgewählten Spalte im Datenbereich aus der Abfrage.|  
|![Symbol für das Dialogfeld „Abfrageparameter“](../../analysis-services/media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")|Anzeigen des Dialogfelds **Abfrageparameter** . Wenn Sie einer Variablen einen Standardwert zuweisen, wird ein entsprechender Berichtsparameter erstellt, wenn Sie im Berichts-Designer zur Layoutansicht wechseln.|  
|![Führen Sie die Abfrage aus](../../analysis-services/media/rsqdicon-run.gif "Run the query")|Bereitet die Abfrage vor.|  
|![In Entwurfsmodus wechseln](../../analysis-services/media/rsqdicon-designmode.gif "Switch to Design mode")|Umschalten zwischen Entwurfsmodus und Abfragemodus. Klicken Sie mit der rechten Maustaste in den Entwurfsbereich, und wählen Sie **Ergebnis**aus, um zur Ergebnisansicht zu wechseln.|  
  
## <a name="graphical-dmx-query-designer-in-design-mode"></a>Grafischer DMX-Abfrage-Designer im Entwurfsmodus  
 Wenn Sie ein Dataset bearbeiten, das eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Datenquelle ohne gültige Cubes verwendet, aber gültige Miningmodelle aufweist, wird der grafische Abfrage-Designer im Entwurfsmodus geöffnet. In der folgenden Abbildung werden die Bereiche für den Entwurfsmodus bezeichnet.  
  
 ![Analysis Services-DMX-Abfrage-Designer, Entwurfsansicht](../media/rsqd-dsawas-dmx-designmode.gif "Analysis Services DMX query designer, design view")  
  
 Die folgende Tabelle beschreibt die Funktion jedes Bereichs.  
  
|Bereich|Funktion|  
|----------|--------------|  
|Abfrageentwurfsbereich|Verwenden Sie die Dialogfelder **Miningmodell** und **Eingabetabelle(n) auswählen** , um die DMX-Abfrage zu erstellen.|  
|Rasterbereich|Verwenden Sie für jede Zeile im Raster die Dropdownliste **Quelle** , um eine Funktion oder einen Ausdruck auszuwählen, und wählen Sie Felder, Gruppen und Kriterien oder Argumente aus, die in der DMX-Abfrage verwendet werden sollen. Klicken Sie zum Anzeigen des durch Ihre Auswahl generierten DMX-Abfragetexts auf die Schaltfläche **Entwurfsmodus** auf der Symbolleiste.|  
  
 Klicken Sie mit der rechten Maustaste in den Abfrageentwurfsbereich, und wählen Sie **Ergebnis**aus, um die DMX-Abfrage auszuführen und Ergebnisse im Ergebnisbereich anzuzeigen.  
  
## <a name="graphical-dmx-query-designer-in-query-mode"></a>Grafischer DMX-Abfrage-Designer im Abfragemodus  
 Wenn Sie den grafischen Abfrage-Designer in den Abfragemodus umschalten möchten, klicken Sie auf der Symbolleiste auf die Schaltfläche **Entwurfsmodus** , oder klicken Sie mit der rechten Maustaste auf die Abfrageentwurfsoberfläche, und wählen Sie im Kontextmenü **Abfrage** aus. Verwenden Sie diesen Modus, um DMX-Text direkt in den Abfragebereich einzugeben.  
  
 In der folgenden Abbildung sind die Bereiche für den Abfragemodus veranschaulicht.  
  
 ![Analysis Services-DMX-Abfrage-Designer, Abfrageansicht](../media/rsqd-dsawas-dmx-querymode.gif "Analysis Services DMX query designer, query view")  
  
 Die folgende Tabelle beschreibt die Funktion jedes Bereichs.  
  
|Bereich|Funktion|  
|----------|--------------|  
|Abfrageentwurfsbereich|Verwenden Sie die Dialogfelder **Miningmodell** und **Eingabetabelle(n) auswählen** , um die DMX-Abfrage zu erstellen.|  
|Abfragebereich|Anzeigen oder Bearbeiten von DMX-Abfragetext direkt im Bereich. Änderungen am DMX-Abfragetext bleiben nicht bestehen, wenn Sie zurück zum **Entwurfsmodus** wechseln.|  
  
 Klicken Sie mit der rechten Maustaste in den Abfrageentwurfsbereich, und wählen Sie **Ergebnis**aus, um die DMX-Abfrage auszuführen und Ergebnisse im Ergebnisbereich anzuzeigen.  
  
## <a name="graphical-dmx-query-designer-in-result-mode"></a>Grafischer DMX-Abfrage-Designer im Ergebnismodus  
 Klicken Sie zum Anzeigen des Ergebnismodus mit der rechten Maustaste auf die Abfrageentwurfsoberfläche, und wählen Sie im Kontextmenü **Ergebnis** aus. Wenn Sie zum Ergebnismodus wechseln, wird die DMX-Abfrage automatisch ausgeführt.  
  
 In der folgenden Abbildung ist der Abfrage-Designer im Ergebnismodus dargestellt.  
  
 ![Analysis Services-DMX-Abfrage-Designer, Ergebnisansicht](../media/rsqd-dsawas-dmx-resultmode.gif "Analysis Services DMX query designer, result view")  
  
 Klicken Sie zum Zurückwechseln in den Entwurfsmodus oder Abfragemodus mit der rechten Maustaste in den Ergebnisbereich, und wählen Sie **Entwurf** oder **Abfrage**aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Definieren von Parametern im MDX-Abfrage-Designer für Analysis Services &#40;Berichts-Generator und SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md)   
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Analysis Services-Verbindungstyp für DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md)   
 [Abrufen von Daten aus einem Data Mining-Modell &#40;DMX, SSRS&#41;](retrieve-data-from-a-data-mining-model-dmx-ssrs.md)   
 [RSReportDesigner-Konfigurationsdatei](../report-server/rsreportdesigner-configuration-file.md)   
 [Analysis Services-Verbindungstyp für MDX &#40;SSRS&#41;](analysis-services-connection-type-for-mdx-ssrs.md)   
 [Analysis Services-Verbindungstyp für DMX &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md)  
  
  
