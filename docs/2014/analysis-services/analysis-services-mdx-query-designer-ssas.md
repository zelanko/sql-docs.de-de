---
title: Analysis Services MDX-Abfrage-Designer (SSAS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.asmdxquerydes.f1
ms.assetid: a2fb0b79-802a-4dac-bd9a-32dfe2e8c4d4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1b9088dc5dc222d8dd1c0c861746f225e6f5b469
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528076"
---
# <a name="analysis-services-mdx-query-designer-ssas"></a>Analysis Services MDX-Abfrage-Designer (SSAS)
  Der Analysis Services Multidimensional Expression (MDX)-Abfrage-Designer stellt eine grafische Benutzeroberfläche bereit, die Sie beim Erstellen von MDX-Abfragen für eine [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Datenquelle unterstützt. Der grafische MDX-Abfrage-Designer verfügt über zwei Modi: Entwurfsmodus und Abfragemodus. Jeder Modus stellt einen Metadatenbereich bereit, in dem Sie Elemente aus den ausgewählten Cubes ziehen können, um eine MDX-Abfrage zum Abrufen der gewünschten Daten zu erstellen.  
  
> [!IMPORTANT]  
>  Benutzer greifen auf Datenquellen zu, wenn sie Abfragen erstellen und ausführen. Sie sollten minimale Berechtigungen für die Datenquellen gewähren, z. B. nur Leseberechtigungen.  
>   
>  Die Anmeldeinformationen des aktuellen Benutzers, nicht die auf der Seite Identitätswechselinformationen angegebenen Anmeldeinformationen, werden zum Herstellen einer Verbindung mit der Datenquelle verwendet, wenn eine Abfrage ausgeführt wird.  
  
 In den folgenden Abschnitten werden die Schaltflächen auf der Symbolleiste und die Bereiche des Abfrage-Designers für jeden Modus des grafischen Abfrage-Designers beschrieben.  
  
## <a name="graphical-mdx-query-designer-in-design-mode"></a>Grafischer MDX-Abfrage-Designer im Entwurfsmodus  
 Wenn Sie eine MDX-Abfrage bearbeiten, wird der grafische MDX-Abfrage-Designer im Entwurfsmodus geöffnet.  
  
 In der folgenden Abbildung werden die Bereiche für den Entwurfsmodus bezeichnet.  
  
 ![MDX-Abfrage-Designer für Analysis Services, Entwurfsansicht](media/rsqd-dsawas-mdx-designmode.gif "MDX-Abfrage-Designer für Analysis Services, Entwurfsansicht")  
  
 In der folgenden Tabelle sind die Bereiche in diesem Modus aufgeführt.  
  
|Bereich|Funktion|  
|----------|--------------|  
|Cube auswählen (Schaltfläche **...**)|Zeigt den aktuell ausgewählten Cube an.|  
|Metadaten (Bereich)|Zeigt eine hierarchische Liste von Measures, KPIs (Key Performance Indicators) und Dimensionen an, die für den ausgewählten Cube definiert sind.|  
|Berechnete Elemente (Bereich)|Zeigt die aktuell definierten berechneten Elemente an, die für eine Verwendung in der Abfrage verfügbar sind.|  
|Filter (Bereich)|Wird zum Auswählen von Dimensionen und zugehörigen Hierarchien verwendet, um Daten an der Quelle zu filtern und die zurückgegebenen Daten zu beschränken.|  
|Daten (Bereich)|Zeigt die Spaltenüberschriften für das Resultset an, während Sie Elemente aus dem Metadatenbereich und dem Bereich für berechnete Elemente ziehen. Aktualisiert automatisch das Resultset, wenn die Schaltfläche **Automatisch ausführen** ausgewählt wird.|  
  
 Sie können Dimensionen, Measures und KPIs aus dem Metadatenbereich sowie berechnete Elemente aus dem Bereich für berechnete Elemente in den Datenbereich ziehen. Im Filterbereich können Sie Dimensionen und zugehörige Hierarchien auswählen sowie Filterausdrücke festlegen, um die für eine Abfrage zur Verfügung stehenden Daten zu beschränken. Wenn die Umschaltfläche **AutoExecute** (![Abfrage automatisch ausführen](media/rsqdicon-autoexecute.gif "Abfrage automatisch ausführen")) in der Symbolliste angeklickt wird, führt der Abfrage-Designer die Abfrage jedes Mal aus, wenn Sie ein Metadatenobjekt im Datenbereich ablegen. Sie können die Abfrage mithilfe der Schaltfläche **Ausführen** (![Abfrage ausführen](media/rsqdicon-run.gif "Abfrage ausführen")) in der Symbolleiste manuell ausführen.  
  
 Wenn Sie in diesem Modus eine MDX-Abfrage erstellen, werden die folgenden zusätzlichen Eigenschaften automatisch in die Abfrage eingeschlossen:  
  
 **Elementeigenschaften** MEMBER_CAPTION, MEMBER_UNIQUE_NAME  
  
 **Zelleigenschaften** VALUE, BACK_COLOR, FORE_COLOR, FORMATTED_VALUE, FORMAT_STRING, FONT_NAME, FONT_SIZE, FONT_FLAGS  
  
 Um eigene zusätzliche Eigenschaften anzugeben, müssen Sie die MDX-Abfrage im Abfragemodus manuell bearbeiten.  
  
 Das Importieren einer MDX-Abfrage aus einer Datei wird nicht unterstützt.  
  
> [!NOTE]  
>  Weitere Informationen zu MDX sowie allgemeine Informationen zum MDX-Abfrage-Designer finden Sie in „MDX-Abfrage-Editor (Analysis Services – mehrdimensionale Daten)“ in der [SQL Server-Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=98335).  
  
### <a name="graphical-mdx-query-designer-toolbar-in-design-mode"></a>Symbolleiste des grafischen MDX-Abfrage-Designers im Entwurfsmodus  
 Die Symbolleiste des Abfrage-Designers stellt Schaltflächen bereit, die Ihnen beim Entwurf von MDX-Abfragen mit der grafischen Oberfläche helfen. In der folgenden Tabelle sind die Schaltflächen und ihre Funktionen aufgeführt.  
  
|Schaltfläche|Beschreibung|  
|------------|-----------------|  
|**Als Text bearbeiten**|Nicht aktiviert für diesen Datenquellentyp.|  
|**Importieren**|Importieren einer vorhandenen Abfrage aus einer Berichtsdefinitionsdatei (.rdl) im Dateisystem.|  
|![Zur MDX-Abfrageansicht wechseln](media/rsqdicon-commandtypemdx.gif "Zur MDX-Abfrageansicht wechseln")|Wechselt zum MDX-Befehlstyp.|  
|![Ergebnisdaten aktualisieren](media/rsqdicon-refresh.gif "Ergebnisdaten aktualisieren")|Aktualisieren von Metadaten aus der Datenquelle.|  
|![Berechnetes Element hinzufügen](media/rsqdicon-addcalculatedmember.gif "Berechnetes Element hinzufügen")|Zeigt das Dialogfeld **Generator für berechnete Elemente** an.|  
|![Leere Zellen anzeigen/nicht anzeigen](media/rsqdicon-showemptycells.gif "Leere Zellen anzeigen/nicht anzeigen")|Schaltet zwischen dem Anzeigen und Nichtanzeigen von leeren Zellen im Datenbereich um. (Dies entspricht dem Verwenden der NON EMPTY-Klausel in MDX.)|  
|![Abfrage automatisch ausführen](media/rsqdicon-autoexecute.gif "Abfrage automatisch ausführen")|Bei jeder Änderung wird die Abfrage automatisch ausgeführt, und das Ergebnis wird angezeigt. Die Ergebnisse werden im Datenbereich angezeigt.|  
|![Aggregationen anzeigen (Schaltfläche)](media/rsqdicon-showaggregations.gif "Aggregationen anzeigen (Schaltfläche)")|Zeigt Aggregationen im Datenbereich an.|  
|![Löschen](media/rsqdicon-delete.gif "Löschen")|Löschen der ausgewählten Spalte im Datenbereich aus der Abfrage.|  
|![Symbol für das Dialogfeld „Abfrageparameter“](media/iconqueryparameter.gif "Symbol für das Dialogfeld „Abfrageparameter“")|Anzeigen des Dialogfelds **Abfrageparameter** . Bei der Angabe von Werten für einen Abfrageparameter wird automatisch ein Parameter mit demselben Namen erstellt.|  
|![Abfrage vorbereiten (Schaltfläche)](media/rsqdicon-preparequery.gif "Abfrage vorbereiten (Schaltfläche)")|Bereitet die Abfrage vor.|  
|![Ausführen der Abfrage](media/rsqdicon-run.gif "Abfrage ausführen")|Führt die Abfrage aus und zeigt die Ergebnisse im Datenbereich an.|  
|![Abfrage abbrechen](media/rsqdicon-cancel.gif "Abfrage abbrechen")|Abbrechen der Abfrage.|  
|![In Entwurfsmodus wechseln](media/rsqdicon-designmode.gif "Wechselt in den Entwurfsmodus")|Umschalten zwischen Entwurfsmodus und Abfragemodus.|  
  
## <a name="graphical-mdx-query-designer-in-query-mode"></a>Grafischer MDX-Abfrage-Designer im Abfragemodus  
 Wenn Sie vom grafischen Abfrage-Designer in den **Abfragemodus** wechseln möchten, klicken Sie auf der Symbolleiste auf die Schaltfläche **Entwurfsmodus** .  
  
 In der folgenden Abbildung sind die Bereiche für den Abfragemodus veranschaulicht.  
  
 ![MDX-Abfrage-Designer für Analysis Services, Abfrageansicht](media/rsqd-dsawas-mdx-querymode.gif "MDX-Abfrage-Designer für Analysis Services, Abfrageansicht")  
  
 In der folgenden Tabelle sind die Bereiche in diesem Modus aufgeführt.  
  
|Bereich|Funktion|  
|----------|--------------|  
|Cube auswählen (Schaltfläche **...**)|Zeigt den aktuell ausgewählten Cube an.|  
|Metadaten/Funktionen/Vorlagen (Bereich)|Zeigt eine hierarchische Liste von Measures, KPIs und Dimensionen an, die für den ausgewählten Cube definiert sind.|  
|Abfragebereich|Zeigt den Abfragetext an.|  
|Ergebnisbereich|Zeigt die Ergebnisse des Ausführens der Abfrage an.|  
  
 Im Metadatenbereich werden Registerkarten für **Metadaten**, **Funktionen**und **Vorlagen**angezeigt. Auf der Registerkarte **Metadaten** können Sie Dimensionen, Hierarchien, KPIs und Measures in den MDX-Abfragebereich ziehen. Auf der Registerkarte **Funktionen** können Sie Funktionen in den MDX-Abfragebereich ziehen. Auf der Registerkarte **Vorlagen** können Sie dem MDX-Abfragebereich MDX-Vorlagen hinzufügen. Wenn Sie die Abfrage ausführen, werden im Ergebnisbereich die Ergebnisse für die MDX-Abfrage angezeigt.  
  
 Sie können die im Entwurfsmodus erstellte Standard-MDX-Abfrage um zusätzliche Elementeigenschaften und Zelleigenschaften erweitern. Wenn Sie die Abfrage ausführen, werden diese Werte nicht im Resultset angezeigt. Sie werden jedoch mit der Datasetfeldauflistung zurückgegeben, und Sie können diese Werte verwenden.  
  
### <a name="graphical-query-designer-toolbar-in-query-mode"></a>Symbolleiste für den grafischen Abfrage-Designer im Abfragemodus  
 Die Symbolleiste des Abfrage-Designers stellt Schaltflächen bereit, die Ihnen beim Entwurf von MDX-Abfragen mit der grafischen Oberfläche helfen.  
  
 Die Schaltflächen der Symbolleiste sind im Entwurfs- und Abfragemodus identisch, aber die folgenden Schaltflächen sind für den Abfragemodus nicht aktiviert:  
  
-   **Als Text bearbeiten**  
  
-   **Berechnetes Element hinzufügen** (![Berechnetes Element hinzufügen](media/rsqdicon-addcalculatedmember.gif "Berechnetes Element hinzufügen"))  
  
-   **Leere Zellen anzeigen** (![Schaltfläche zum ein-/ausblenden leerer Zellen](media/rsqdicon-showemptycells.gif "Leere Zellen anzeigen/nicht anzeigen"))  
  
-   **AutoExecute** (![Abfrage automatisch ausführen](media/rsqdicon-autoexecute.gif "Abfrage automatisch ausführen"))  
  
-   **Aggregationen anzeigen** (![Schaltfläche „Aggregationen anzeigen“](media/rsqdicon-showaggregations.gif "Aggregationen anzeigen (Schaltfläche)"))  
  
  
