---
title: Cluster-Assistent (Data Mining-Add-ins für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [data mining]
ms.assetid: 85b25625-a7ab-4960-9f9c-df22e8ecae37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7803b5a5a2fccd3381b827eb15a19e036ffa017e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48164610"
---
# <a name="cluster-wizard-data-mining-add-ins-for-excel"></a>Cluster-Assistent (Data Mining-Add-Ins für Excel)
  ![Clustererstellungs-Assistenten im Data Mining-Menüband](media/dmc-cluster.gif "Clustererstellungs-Assistenten im Data Mining-Menüband")  
  
 Mit dem Cluster-Assistenten erstellen Sie ein Modell, das Gruppen von Zeilen erkennt, die über ähnliche Merkmale verfügen, und diese gruppiert, um den Abstand zwischen den Gruppen zu maximieren. Dieser Assistent ist hilfreich beim Suchen von Mustern in sämtlichen Daten.  
  
 Der Cluster-Assistent verwendet den Microsoft Clustering-Algorithmus und kann umfassend angepasst werden. Er kann für vorhandene Daten aus einer Excel-Tabelle, einem Excel-Bereich oder einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Abfrage verwendet werden. Ähnliche Funktionalität geboten wird durch die [Kategorien erkennen](detect-categories-table-analysis-tools-for-excel.md) -Tool, von den Tabellenanalysetools für Excel. Das Tool Kategorien erkennen kann jedoch nicht angepasst werden und muss Daten in Excel-Tabellen verwenden.  
  
## <a name="using-the-cluster-wizard"></a>Verwenden des Cluster-Assistenten  
  
1.  Klicken Sie in der Data Mining-Menüband auf **Cluster**, und klicken Sie dann auf **Weiter**.  
  
2.  In der **Quelldaten auswählen** Seite, wählen Sie eine Excel-Tabelle oder ein Bereich. Oder geben Sie eine externe Datenquelle an.  
  
     Wenn Sie eine externe Datenquelle verwenden, können Sie benutzerdefinierte Sichten erstellen oder benutzerdefinierten Abfragetext einfügen und das Dataset als [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquelle speichern.  
  
3.  Auf der **Clustering** Seite Sie können anpassen, wie das Modell erstellt wird.  
  
    -   Für **Anzahl von Segmenten**, können Sie den Assistenten anweisen, eine feste Anzahl von Kategorien zu erstellen oder laden, damit sie die optimale Anzahl von Gruppierungen automatisch zu erkennen.  
  
    -   Überprüfen Sie die Liste der Spalten in der **Eingabespalten** aus, und deaktivieren Sie alle Spalten, die nicht in das Erstellen von Mustern nützlich sind. Sie sollten Spalten ausschließen, die IDs, Kundennamen usw. enthalten.  
  
4.  Klicken Sie optional auf **Parameter** die Algorithmusparameter ändern und das Verhalten des Clusteringmodells anzupassen.  
  
5.  In der **Daten in Trainings- und Testsätze aufteilen** Seite, wie viele Daten zum Testen zurückgehalten angeben. Der Rest wird immer zum Trainieren des Modells verwendet.  
  
     In der Standardeinstellung sind 30 % als Testdaten und 70 % als Trainingsdaten festgelegt.  
  
6.  Auf der **Fertig stellen** Seite Geben Sie einen beschreibenden Namen für das DataSet und das Modell, und legen Sie die folgenden Optionen, die steuern, wie Sie mit dem fertigen Modell arbeiten:  
  
    -   **Modell durchsuchen,**. Wenn diese Option ausgewählt ist, sobald der Assistent nach Abschluss der Verarbeitung des Modells, öffnen ein **Durchsuchen** Fenster können Sie die Ergebnisse zu untersuchen. Der Inhalt des Viewers hängt vom Typ des erstellten Modells ab. Weitere Informationen finden Sie unter [Durchsuchen eines Modells Clustering](browsing-a-clustering-model.md).  
  
    -   **Aktivieren von Drillthrough**. Wählen Sie diese Option aus, um die zugrunde liegenden Daten des fertigen Modells anzuzeigen. Diese Option ist nur verfügbar, wenn Sie ein Decision Tree-Modell erstellen.  
  
    -   **Temporäres Modell**. Wenn Sie diese Option auswählen, wird das Modell nicht auf dem Server gespeichert. Temporäre Modelle werden beim Schließen von Excel gelöscht.  
  
## <a name="more-about-clustering-models"></a>Weitere Informationen zu Clustermodellen  
 Sie können ändern, den clustering-Algorithmus von diesem Assistenten verwendet werden, indem Sie auf **erweitert** und Verwenden der **Algorithmusparameter** Dialogfeld.  
  
 Der Microsoft Clustering-Algorithmus stellt folgende Clustering-Methoden bereit:  
  
-   K-Means – skalierbar oder nicht skalierbar  
  
-   Expectation Maximization (EM) – skalierbar oder nicht skalierbar  
  
 Mit dem Parameter CLUSTER_SEED können Sie den Anfangswert festlegen und sicherstellen, dass wiederholte Modelle, die dasselbe Dataset verwenden, die gleichen Ergebnisse liefern.  
  
### <a name="requirements"></a>Anforderungen  
 Zum Verwenden des Cluster-Assistenten muss eine Verbindung mit einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank bestehen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Datamining-Modells](creating-a-data-mining-model.md)   
 [Kategorien erkennen &#40;Tabellenanalysetools für Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
  
