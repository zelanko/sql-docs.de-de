---
title: Benutzeroberfläche des DMX-Abfrage-Designers für Analysis Services | Microsoft-Dokumentation
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
f1_keywords:
- "10012"
- sql13.rtp.rptdesigner.dataview.asquerydesigner.f1
helpviewer_keywords:
- Analysis Services [DMX]
- DMX [Analysis Services], user interface
- query designers [DMX]
ms.assetid: 5fd726a4-aed7-4e6c-9404-ccb2db66cf26
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 42313894264979caf49ccbbe54d25b91261a8a10
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "65573578"
---
# <a name="analysis-services-dmx-query-designer-user-interface"></a>Benutzeroberfläche des DMX-Abfrage-Designers für Analysis Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt grafische Abfrage-Designer zum Erstellen von DMX-Abfragen (Data Mining-Erweiterungen) und MDX-Abfragen (Multidimensional Expression) für eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenquelle bereit. Dieses Thema beschreibt den DMX-Abfrage-Designer. Weitere Informationen zum MDX-Abfrage-Designer finden Sie unter [Analysis Services MDX Query Designer User Interface](../../reporting-services/report-data/analysis-services-mdx-query-designer-user-interface.md).  
  
 Der grafische DMX-Abfrage-Designer verfügt über drei Modi: „Entwurf“, „Abfrage“ und „Ergebnis“. Klicken Sie mit der rechten Maustaste in den Abfrageentwurfsbereich, um zwischen den Modi zu wechseln, und wählen Sie den gewünschten Modus aus. Jeder Modus bietet einen Metadatenbereich, aus dem Sie Elemente aus den ausgewählten Cubes ziehen können, um eine DMX-Abfrage zu erstellen. Die DMX-Abfrage ruft Daten für ein Dataset ab, wenn der Bericht verarbeitet wird.  
  
## <a name="graphical-dmx-query-designer-toolbar"></a>Symbolleiste für den grafischen DMX-Abfrage-Designer  
 Die Symbolleiste des Abfrage-Designers beinhaltet Schaltflächen, die Ihnen den Entwurf von DMX-Abfragen mithilfe der grafischen Oberfläche ermöglichen. In der folgenden Tabelle werden die Schaltflächen und ihre Funktionen beschrieben.  
  
|Taste|Beschreibung|  
|------------|-----------------|  
|**Als Text bearbeiten**|Deaktiviert für diesen Datenquellentyp.|  
|**Importieren**|Importieren einer vorhandenen Abfrage aus einer Berichtsdefinitionsdatei (.rdl) im Dateisystem. Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).|  
|![Zur MDX-Abfrageansicht wechseln](../../reporting-services/report-data/media/rsqdicon-commandtypemdx.gif "Zur MDX-Abfrageansicht wechseln")|Wechseln zum Modus für den MDX-Abfrage-Designer.|  
|![Zur DMX-Abfragesprachenansicht wechseln](../../reporting-services/report-data/media/rsqdicon-commandtypedmx.gif "Zur DMX-Abfragesprachenansicht wechseln")|Wechseln zum Modus für den DMX-Abfrage-Designer.|  
|![Ergebnisdaten aktualisieren](../../reporting-services/report-data/media/rsqdicon-refresh.gif "Ergebnisdaten aktualisieren")|Aktualisieren von Metadaten aus der Datenquelle.|  
|![Löschen](../../reporting-services/report-data/media/rsqdicon-delete.gif "Löschen")|Löschen der ausgewählten Spalte im Datenbereich aus der Abfrage.|  
|![Symbol für das Dialogfeld „Abfrageparameter“](../../reporting-services/report-data/media/iconqueryparameter.gif "Symbol für das Dialogfeld „Abfrageparameter“")|Anzeigen des Dialogfelds **Abfrageparameter** . Wenn Sie einer Variablen einen Standardwert zuweisen, wird ein entsprechender Berichtsparameter erstellt, wenn Sie im Berichts-Designer zur Layoutansicht wechseln.|  
|![Abfrage ausführen](../../reporting-services/report-data/media/rsqdicon-run.gif "Abfrage ausführen")|Bereitet die Abfrage vor.|  
|![In Entwurfsmodus wechseln](../../reporting-services/media/rsqdicon-designmode.gif "Wechselt in den Entwurfsmodus")|Umschalten zwischen Entwurfsmodus und Abfragemodus. Klicken Sie mit der rechten Maustaste in den Entwurfsbereich, und wählen Sie **Ergebnis**aus, um zur Ergebnisansicht zu wechseln.|  
  
## <a name="graphical-dmx-query-designer-in-design-mode"></a>Grafischer DMX-Abfrage-Designer im Entwurfsmodus  
 Wenn Sie ein Dataset bearbeiten, das eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenquelle ohne gültige Cubes verwendet, aber gültige Miningmodelle aufweist, wird der grafische Abfrage-Designer im Entwurfsmodus geöffnet. In der folgenden Abbildung werden die Bereiche für den Entwurfsmodus bezeichnet.  
  
 ![DMX-Abfrage-Designer für Analysis Services, Entwurfsansicht](../../reporting-services/report-data/media/rsqd-dsawas-dmx-designmode.gif "DMX-Abfrage-Designer für Analysis Services, Entwurfsansicht")  
  
 Die folgende Tabelle beschreibt die Funktion jedes Bereichs.  
  
|Bereich|Funktion|  
|----------|--------------|  
|Abfrageentwurfsbereich|Verwenden Sie die Dialogfelder **Miningmodell** und **Eingabetabelle(n) auswählen** , um die DMX-Abfrage zu erstellen.|  
|Rasterbereich|Verwenden Sie für jede Zeile im Raster die Dropdownliste **Quelle** , um eine Funktion oder einen Ausdruck auszuwählen, und wählen Sie Felder, Gruppen und Kriterien oder Argumente aus, die in der DMX-Abfrage verwendet werden sollen. Klicken Sie zum Anzeigen des durch Ihre Auswahl generierten DMX-Abfragetexts auf die Schaltfläche **Entwurfsmodus** auf der Symbolleiste.|  
  
 Klicken Sie mit der rechten Maustaste in den Abfrageentwurfsbereich, und wählen Sie **Ergebnis**aus, um die DMX-Abfrage auszuführen und Ergebnisse im Ergebnisbereich anzuzeigen.  
  
## <a name="graphical-dmx-query-designer-in-query-mode"></a>Grafischer DMX-Abfrage-Designer im Abfragemodus  
 Wenn Sie den grafischen Abfrage-Designer in den Abfragemodus umschalten möchten, klicken Sie auf der Symbolleiste auf die Schaltfläche **Entwurfsmodus** , oder klicken Sie mit der rechten Maustaste auf die Abfrageentwurfsoberfläche, und wählen Sie im Kontextmenü **Abfrage** aus. Verwenden Sie diesen Modus, um DMX-Text direkt in den Abfragebereich einzugeben.  
  
 In der folgenden Abbildung sind die Bereiche für den Abfragemodus veranschaulicht.  
  
 ![DMX-Abfrage-Designer für Analysis Services, Abfrageansicht](../../reporting-services/report-data/media/rsqd-dsawas-dmx-querymode.gif "DMX-Abfrage-Designer für Analysis Services, Abfrageansicht")  
  
 Die folgende Tabelle beschreibt die Funktion jedes Bereichs.  
  
|Bereich|Funktion|  
|----------|--------------|  
|Abfrageentwurfsbereich|Verwenden Sie die Dialogfelder **Miningmodell** und **Eingabetabelle(n) auswählen** , um die DMX-Abfrage zu erstellen.|  
|Abfragebereich|Anzeigen oder Bearbeiten von DMX-Abfragetext direkt im Bereich. Änderungen am DMX-Abfragetext bleiben nicht bestehen, wenn Sie zurück zum **Entwurfsmodus** wechseln.|  
  
 Klicken Sie mit der rechten Maustaste in den Abfrageentwurfsbereich, und wählen Sie **Ergebnis**aus, um die DMX-Abfrage auszuführen und Ergebnisse im Ergebnisbereich anzuzeigen.  
  
## <a name="graphical-dmx-query-designer-in-result-mode"></a>Grafischer DMX-Abfrage-Designer im Ergebnismodus  
 Klicken Sie zum Anzeigen des Ergebnismodus mit der rechten Maustaste auf die Abfrageentwurfsoberfläche, und wählen Sie im Kontextmenü **Ergebnis** aus. Wenn Sie zum Ergebnismodus wechseln, wird die DMX-Abfrage automatisch ausgeführt.  
  
 In der folgenden Abbildung ist der Abfrage-Designer im Ergebnismodus dargestellt.  
  
 ![DMX-Abfrage-Designer für Analysis Services, Ergebnisansicht](../../reporting-services/report-data/media/rsqd-dsawas-dmx-resultmode.gif "DMX-Abfrage-Designer für Analysis Services, Ergebnisansicht")  
  
 Klicken Sie zum Zurückwechseln in den Entwurfsmodus oder Abfragemodus mit der rechten Maustaste in den Ergebnisbereich, und wählen Sie **Entwurf** oder **Abfrage**aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Definieren von Parametern im MDX-Abfrage-Designer für Analysis Services &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/define-parameters-in-the-mdx-query-designer-for-analysis-services.md)   
 [Erstellen eines freigegebenen Datasets oder eingebetteten Datasets &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Analysis Services-Verbindungstyp für DMX &#40;SSRS&#41;](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md)   
 [Abrufen von Daten aus einem Data Mining-Modell (DMX) (SSRS)](../../reporting-services/report-data/retrieve-data-from-a-data-mining-model-dmx-ssrs.md)   
 [RSReportDesigner-Konfigurationsdatei](../../reporting-services/report-server/rsreportdesigner-configuration-file.md)   
 [Analysis Services-Verbindungstyp für MDX &#40;SSRS&#41;](../../reporting-services/report-data/analysis-services-connection-type-for-mdx-ssrs.md)   
 [Analysis Services-Verbindungstyp für DMX &#40;SSRS&#41;](../../reporting-services/report-data/analysis-services-connection-type-for-dmx-ssrs.md)  
  
  
