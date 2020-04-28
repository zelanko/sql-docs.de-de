---
title: Symbolleiste (Registerkarte "Browser", Cube-Designer) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a1c6272d-e514-456b-9995-b73fec0112a2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4d1135be55065ab62e649d84c00cec4eebf60b58
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175579"
---
# <a name="toolbar-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>Symbolleiste (Registerkarte 'Browser', Cube-Designer) (Analysis Services – Mehrdimensionale Daten)
  Verwenden Sie die Funktionen in der **Symbolleiste** im Cube-Designer, um allgemeine Vorgänge auszuführen, während Sie einen Cube oder sein Objekt entwerfen oder durchsuchen oder eine MDX-Abfrage erstellen. Zu den Vorgängen, die der Entwurfszeit und der Abfragesicht gemeinsam sind, gehören das Festlegen des Benutzerkontexts, das Verarbeiten von Objekten und das Festlegen der Standardsprache.

 In der folgenden Tabelle sind die Schaltflächen der **Symbolleiste** und ihre Funktionen aufgeführt.

|Schaltfläche|BESCHREIBUNG|
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

 Im Allgemeinen sind die Symbolleistenschaltflächen für **Entwurfsmodus** und **Abfragemodus**dieselben. Die folgenden Schaltflächen werden jedoch nicht für den Abfragemodus aktiviert:

-   **Als Text bearbeiten**

-   **Berechnetes Element hinzufügen** (![Berechnetes Element hinzufügen](media/rsqdicon-addcalculatedmember.gif "Berechnetes Element hinzufügen"))

-   **Leere Zellen anzeigen** (![Schaltfläche zum ein-/ausblenden leerer Zellen](media/rsqdicon-showemptycells.gif "Leere Zellen anzeigen/nicht anzeigen"))

-   **AutoExecute** (![Abfrage automatisch ausführen](media/rsqdicon-autoexecute.gif "Abfrage automatisch ausführen"))

-   **Aggregationen anzeigen** (![Schaltfläche „Aggregationen anzeigen“](media/rsqdicon-showaggregations.gif "Aggregationen anzeigen (Schaltfläche)"))

## <a name="options"></a>Optionen

|Option|BESCHREIBUNG|
|------------|-----------------|
|**Prozess**|Klicken Sie auf diese Option, um das Dialogfeld **Verarbeiten** anzuzeigen und den Cube zu verarbeiten. Weitere Informationen zum Dialogfeld **Verarbeiten** finden Sie unter [Dialogfeld „Verarbeiten“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](process-dialog-box-analysis-services-multidimensional-data.md).|
|**Benutzer ändern**|Klicken Sie hier, um das Dialogfeld **Sicherheitskontext** anzuzeigen und den auf der Registerkarte **Browser** verwendeten Benutzer und die Rolle zu ändern. Weitere Informationen zum Dialogfeld **Sicherheitskontext** finden Sie im [Dialogfeld Sicherheitskontext &#40;Analysis Services-Multidimensional Data&#41;](security-context-dialog-box-analysis-services-multidimensional-data.md).|
|**Verbindung wiederherstellen**|Klicken Sie hier, um die Verbindung der Registerkarte **Berechnungen** mit der [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz und mit der Datenbank, die den Cube enhält, wiederherzustellen, falls die Sitzung der Registerkarte **Browser** aufgrund einer unterbrochenen Verbindung oder eines Timeouts beendet wurde.|
|**Aktualisieren**|Klicken Sie hier, um die Bereiche **Metadaten** und **Berichte** zu aktualisieren.|
|**Aufsteigend sortieren**|Klicken Sie hier, um die gleichgeordneten Elemente der ausgewählten Zeile im Bereich **Bericht** für die unter **Sprache**angegebene Sprache aufsteigend zu sortieren.<br /><br /> **Hinweis:** Diese Option wird nur aktiviert, wenn im Bereich **Berichte** eine Zelle ausgewählt wird.|
|**Absteigend sortieren**|Klicken Sie hier, um die gleichgeordneten Elemente der ausgewählten Zeile im Bereich **Bericht** für die unter **Sprache**angegebene Sprache absteigend zu sortieren.<br /><br /> Hinweis: diese Option ist nur aktiviert, wenn im Bereich **Berichte** eine Zelle ausgewählt ist.|
|**Automatisch filtern**|Klicken Sie hier, um die im Bereich **Ergebnis** angezeigten Ergebnisse automatisch zu filtern.|
|**Nur erste/letzte anzeigen**|Wählen Sie einen Wert oder einen Prozentsatz aus, um auf der Basis des ausgewählten Maßes im Bereich **Bericht** nur die angegebene Anzahl bzw. den Prozentsatz von ersten oder letzten Zellen anzuzeigen.<br /><br /> Weitere Informationen finden Sie unter [TopCount &#40;MDX&#41;](/sql/mdx/topcount-mdx), [TopPercent &#40;MDX&#41;](/sql/mdx/toppercent-mdx), [BottomCount &#40;MDX&#41;](/sql/mdx/bottomcount-mdx), und [BottomPercent &#40;MDX&#41;](/sql/mdx/bottompercent-mdx).|
|**Subtotal (Zwischensumme)**|Klicken Sie hier, um Teilergebnisse anzuzeigen.|
|**Gesamtergebnisse für alle Elemente**|Klicken Sie hier, um im Bereich **Bericht** die Gesamtergebnisse für alle Elemente anzuzeigen.|
|**Leere Zellen anzeigen**|Klicken Sie hier, um im Bereich **Bericht** die leeren Zellen anzuzeigen.|
|**Ergebnisse löschen**|Klicken Sie hier, um die im Bereich **Bericht** angezeigten Ergebnisse zu löschen.|
|**Befehle und Optionen**|Klicken Sie hier, um das Dialogfeld **Befehle und Optionen** anzuzeigen und die erweiterten Eigenschaften des im Bereich **Bericht** verfügbaren PivotTable-Steuerelements von Microsoft Office 11.0 zu bearbeiten. Weitere Informationen zum Dialogfeld **Befehle und Optionen** finden Sie in der Microsoft Office-Dokumentation.|
|**Perspektive**|Wählen Sie die Perspektive aus, mit der die Daten und Metadaten der Bereiche **Metadaten** und **Bericht** angezeigt werden sollen.<br /><br /> Wenn Sie den Cube ohne Verwendung einer Perspektive anzeigen möchten, wählen Sie den Cubenamen aus.|
|**Sprache**|Wählen Sie die Sprache aus, mit der die Daten und Metadaten der Bereiche **Metadaten** und **Bericht** angezeigt werden sollen.<br /><br /> Wenn Sie den Cube in der Standardsprache anzeigen möchten, wählen Sie die Option **Standard**aus.|


