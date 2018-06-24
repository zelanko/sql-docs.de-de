---
title: Symbolleiste (Registerkarte ' Browser ', Cube-Designer) (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1c6272d-e514-456b-9995-b73fec0112a2
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c20904d56add8256de37351c1435d06f8f526277
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047473"
---
# <a name="toolbar-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>Symbolleiste (Registerkarte 'Browser', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Verwenden Sie die Funktionen in der **Symbolleiste** im Cube-Designer, um allgemeine Vorgänge auszuführen, während Sie einen Cube oder sein Objekt entwerfen oder durchsuchen oder eine MDX-Abfrage erstellen. Zu den Vorgängen, die der Entwurfszeit und der Abfragesicht gemeinsam sind, gehören das Festlegen des Benutzerkontexts, das Verarbeiten von Objekten und das Festlegen der Standardsprache.  
  
 In der folgenden Tabelle sind die Schaltflächen der **Symbolleiste** und ihre Funktionen aufgeführt.  
  
|Schaltfläche|Description|  
|------------|-----------------|  
|**Als Text bearbeiten**|Nicht aktiviert für diesen Datenquellentyp.|  
|**Importieren**|Importieren einer vorhandenen Abfrage aus einer Berichtsdefinitionsdatei (.rdl) im Dateisystem.|  
|![Wechseln zur MDX-Abfrageansicht](media/rsqdicon-commandtypemdx.gif "Change to MDX query view")|Wechselt zum MDX-Befehlstyp.|  
|![Aktualisieren der Ergebnisdaten](media/rsqdicon-refresh.gif "Refresh result data")|Aktualisieren von Metadaten aus der Datenquelle.|  
|![Berechnetes Element hinzufügen](media/rsqdicon-addcalculatedmember.gif "berechnetes Element hinzufügen")|Zeigt das Dialogfeld **Generator für berechnete Elemente** an.|  
|![Umschalten zum Anzeigen von leeren Zellen](media/rsqdicon-showemptycells.gif "Toggle for show empty cells")|Schaltet zwischen dem Anzeigen und Nichtanzeigen von leeren Zellen im Datenbereich um. (Dies entspricht dem Verwenden der NON EMPTY-Klausel in MDX.)|  
|![Automatisches Ausführen der Abfrage](media/rsqdicon-autoexecute.gif "AutoExecute the query")|Bei jeder Änderung wird die Abfrage automatisch ausgeführt, und das Ergebnis wird angezeigt. Die Ergebnisse werden im Datenbereich angezeigt.|  
|![Anzeigen der Schaltfläche „Aggregationen“](media/rsqdicon-showaggregations.gif "Show Aggregations button")|Zeigt Aggregationen im Datenbereich an.|  
|![Löschen Sie](media/rsqdicon-delete.gif "löschen")|Löschen der ausgewählten Spalte im Datenbereich aus der Abfrage.|  
|![Symbol für das Dialogfeld „Abfrageparameter“](media/iconqueryparameter.gif "Icon for the Query Parameters dialog box")|Anzeigen des Dialogfelds **Abfrageparameter** . Bei der Angabe von Werten für einen Abfrageparameter wird automatisch ein Parameter mit demselben Namen erstellt.|  
|![Schaltfläche „Abfrage vorbereiten“](media/rsqdicon-preparequery.gif "Prepare Query button")|Bereitet die Abfrage vor.|  
|![Führen Sie die Abfrage aus](media/rsqdicon-run.gif "Run the query")|Führt die Abfrage aus und zeigt die Ergebnisse im Datenbereich an.|  
|![Abbrechen der Abfrage](media/rsqdicon-cancel.gif "Cancel the query")|Abbrechen der Abfrage.|  
|![In Entwurfsmodus wechseln](media/rsqdicon-designmode.gif "Switch to Design mode")|Umschalten zwischen Entwurfsmodus und Abfragemodus.|  
  
 Im Allgemeinen sind die Symbolleistenschaltflächen für **Entwurfsmodus** und **Abfragemodus**dieselben. Die folgenden Schaltflächen werden jedoch nicht für den Abfragemodus aktiviert:  
  
-   **Als Text bearbeiten**  
  
-   **Berechnetes Element hinzufügen** (![berechnetes Element hinzufügen](media/rsqdicon-addcalculatedmember.gif "berechnetes Element hinzufügen"))  
  
-   **Leere Zellen anzeigen** (![Umschalten zum Anzeigen von leeren Zellen](media/rsqdicon-showemptycells.gif "Toggle for show empty cells"))  
  
-   **AutoExecute** (![Automatisches Ausführen der Abfrage](media/rsqdicon-autoexecute.gif "AutoExecute the query"))  
  
-   **Aggregationen anzeigen** (![Anzeigen der Schaltfläche „Aggregationen“](media/rsqdicon-showaggregations.gif "Show Aggregations button"))  
  
## <a name="options"></a>Tastatur  
  
|Option|Description|  
|------------|-----------------|  
|**Verarbeiten**|Klicken Sie auf diese Option, um das Dialogfeld **Verarbeiten** anzuzeigen und den Cube zu verarbeiten. Weitere Informationen zum Dialogfeld **Verarbeiten** finden Sie unter [Dialogfeld „Verarbeiten“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](process-dialog-box-analysis-services-multidimensional-data.md).|  
|**Benutzer wechseln**|Klicken Sie hier, um das Dialogfeld **Sicherheitskontext** anzuzeigen und um Rolle und Benutzer zu ändern, die auf der Registerkarte **Browser** verwendet werden. Weitere Informationen zum Dialogfeld **Sicherheitskontext** finden Sie unter [Dialogfeld „Sicherheitskontext“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](security-context-dialog-box-analysis-services-multidimensional-data.md).|  
|**Erneut eine Verbindung herstellen**|Klicken Sie hier, um die Verbindung der Registerkarte **Berechnungen** mit der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz und mit der Datenbank, die den Cube enhält, wiederherzustellen, falls die Sitzung der Registerkarte **Browser** aufgrund einer unterbrochenen Verbindung oder eines Timeouts beendet wurde.|  
|**Aktualisieren**|Klicken Sie hier, um die Bereiche **Metadaten** und **Berichte** zu aktualisieren.|  
|**Aufsteigend sortieren**|Klicken Sie hier, um die gleichgeordneten Elemente der ausgewählten Zeile im Bereich **Bericht** für die unter **Sprache**angegebene Sprache aufsteigend zu sortieren.<br /><br /> **Hinweis:** Diese Option wird nur aktiviert, wenn im Bereich **Berichte** eine Zelle ausgewählt wird.|  
|**Absteigend sortieren**|Klicken Sie hier, um die gleichgeordneten Elemente der ausgewählten Zeile im Bereich **Bericht** für die unter **Sprache**angegebene Sprache absteigend zu sortieren.<br /><br /> Hinweis: Diese Option wird nur aktiviert, wenn im Bereich **Berichte** eine Zelle ausgewählt wird.|  
|**Automatisch filtern**|Klicken Sie hier, um die im Bereich **Ergebnis** angezeigten Ergebnisse automatisch zu filtern.|  
|**Nur erste/letzte anzeigen**|Wählen Sie einen Wert oder einen Prozentsatz aus, um auf der Basis des ausgewählten Maßes im Bereich **Bericht** nur die angegebene Anzahl bzw. den Prozentsatz von ersten oder letzten Zellen anzuzeigen.<br /><br /> Weitere Informationen finden Sie unter [TopCount &#40;MDX&#41;](/sql/mdx/topcount-mdx), [TopPercent &#40;MDX&#41;](/sql/mdx/toppercent-mdx), [BottomCount &#40;MDX&#41;](/sql/mdx/bottomcount-mdx), und [BottomPercent &#40;MDX&#41;](/sql/mdx/bottompercent-mdx).|  
|**Zwischensumme**|Klicken Sie hier, um Teilergebnisse anzuzeigen.|  
|**Gesamtergebnisse für alle Elemente**|Klicken Sie hier, um im Bereich **Bericht** die Gesamtergebnisse für alle Elemente anzuzeigen.|  
|**Leere Zellen anzeigen**|Klicken Sie hier, um im Bereich **Bericht** die leeren Zellen anzuzeigen.|  
|**Ergebnisse löschen**|Klicken Sie hier, um die im Bereich **Bericht** angezeigten Ergebnisse zu löschen.|  
|**Befehle und Optionen**|Klicken Sie hier, um das Dialogfeld **Befehle und Optionen** anzuzeigen und die erweiterten Eigenschaften des im Bereich **Bericht** verfügbaren PivotTable-Steuerelements von Microsoft Office 11.0 zu bearbeiten. Weitere Informationen zum Dialogfeld **Befehle und Optionen** finden Sie in der Microsoft Office-Dokumentation.|  
|**Perspektive**|Wählen Sie die Perspektive aus, mit der die Daten und Metadaten der Bereiche **Metadaten** und **Bericht** angezeigt werden sollen.<br /><br /> Wenn Sie den Cube ohne Verwendung einer Perspektive anzeigen möchten, wählen Sie den Cubenamen aus.|  
|**Sprache**|Wählen Sie die Sprache aus, mit der die Daten und Metadaten der Bereiche **Metadaten** und **Bericht** angezeigt werden sollen.<br /><br /> Wenn Sie den Cube in der Standardsprache anzeigen möchten, wählen Sie die Option **Standard**aus.|  
  
  
