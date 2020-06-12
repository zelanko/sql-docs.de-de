---
title: Cluster-Assistent (Data Mining-Add-Ins für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [data mining]
ms.assetid: 85b25625-a7ab-4960-9f9c-df22e8ecae37
author: minewiskan
ms.author: owend
ms.openlocfilehash: 09aa5a282e02b778b759cbdfc83950d3a2559423
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527476"
---
# <a name="cluster-wizard-data-mining-add-ins-for-excel"></a>Cluster-Assistent (Data Mining-Add-Ins für Excel)
  ![Cluster-Assistent (Data Mining-Menüband)](media/dmc-cluster.gif "Cluster-Assistent (Data Mining-Menüband)")  
  
 Mit dem Cluster-Assistenten erstellen Sie ein Modell, das Gruppen von Zeilen erkennt, die über ähnliche Merkmale verfügen, und diese gruppiert, um den Abstand zwischen den Gruppen zu maximieren. Dieser Assistent ist hilfreich beim Suchen von Mustern in sämtlichen Daten.  
  
 Der Cluster-Assistent verwendet den Microsoft Clustering-Algorithmus und kann umfassend angepasst werden. Er kann für vorhandene Daten aus einer Excel-Tabelle, einem Excel-Bereich oder einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Abfrage verwendet werden. Ähnliche Funktionen werden vom Tool " [Kategorien erkennen](detect-categories-table-analysis-tools-for-excel.md) " bereitgestellt, das in den Tabellenanalyse Tools für Excel enthalten ist. Das Tool Kategorien erkennen kann jedoch nicht angepasst werden und muss Daten in Excel-Tabellen verwenden.  
  
## <a name="using-the-cluster-wizard"></a>Verwenden des Cluster-Assistenten  
  
1.  Klicken Sie im Menüband Data Mining auf **Cluster**, und klicken Sie dann auf **weiter**.  
  
2.  Wählen Sie auf der Seite **Quelldaten auswählen** eine Excel-Tabelle oder einen Excel-Bereich aus. Oder geben Sie eine externe Datenquelle an.  
  
     Wenn Sie eine externe Datenquelle verwenden, können Sie benutzerdefinierte Sichten erstellen oder benutzerdefinierten Abfragetext einfügen und das Dataset als [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenquelle speichern.  
  
3.  Auf der Seite **Clustering** können Sie die Art und Weise anpassen, in der das Modell erstellt wird.  
  
    -   Für die **Anzahl von Segmenten**können Sie den Assistenten anweisen, eine festgelegte Anzahl von Kategorien zu erstellen, oder die optimale Anzahl von Gruppierungen automatisch erkennen lassen.  
  
    -   Überprüfen Sie die Liste der Spalten in der Liste **Eingabe Spalten** , und deaktivieren Sie alle Spalten, die beim Erstellen von Mustern nicht nützlich sind. Sie sollten Spalten ausschließen, die IDs, Kundennamen usw. enthalten.  
  
4.  Klicken Sie optional auf **Parameter** , um die Algorithmusparameter zu ändern und das Verhalten des Clustering-Modells anzupassen.  
  
5.  Geben Sie auf der Seite **Daten in Trainings-und Testsätze aufteilen** an, wie viele Daten zum Testen aufbewahrt werden sollen. Der Rest wird immer zum Trainieren des Modells verwendet.  
  
     In der Standardeinstellung sind 30 % als Testdaten und 70 % als Trainingsdaten festgelegt.  
  
6.  Geben Sie auf der Seite **Fertig** stellen einen beschreibenden Namen für das DataSet und das Modell an, und legen Sie die folgenden Optionen fest, mit denen die Arbeit mit dem fertigen Modell gesteuert wird:  
  
    -   **Modell durchsuchen**. Wenn diese Option ausgewählt ist, wird das Fenster **Durchsuchen** geöffnet, sobald der Assistent die Verarbeitung des Modells abgeschlossen hat, damit Sie die Ergebnisse untersuchen können. Der Inhalt des Viewers hängt vom Typ des erstellten Modells ab. Weitere Informationen finden Sie unter durch [Suchen eines Clusteringmodells](browsing-a-clustering-model.md).  
  
    -   **Drillthrough aktivieren**. Wählen Sie diese Option aus, um die zugrunde liegenden Daten des fertigen Modells anzuzeigen. Diese Option ist nur verfügbar, wenn Sie ein Decision Tree-Modell erstellen.  
  
    -   **Temporäres Modell verwenden**. Wenn Sie diese Option auswählen, wird das Modell nicht auf dem Server gespeichert. Temporäre Modelle werden beim Schließen von Excel gelöscht.  
  
## <a name="more-about-clustering-models"></a>Weitere Informationen zu Clustermodellen  
 Sie können den von diesem Assistenten verwendeten Clustering-Algorithmus ändern, indem Sie auf **erweitert** klicken und das Dialogfeld **Algorithmusparameter** verwenden.  
  
 Der Microsoft Clustering-Algorithmus stellt folgende Clustering-Methoden bereit:  
  
-   K-Means – skalierbar oder nicht skalierbar  
  
-   Expectation Maximization (EM) – skalierbar oder nicht skalierbar  
  
 Mit dem Parameter CLUSTER_SEED können Sie den Anfangswert festlegen und sicherstellen, dass wiederholte Modelle, die dasselbe Dataset verwenden, die gleichen Ergebnisse liefern.  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 Zum Verwenden des Cluster-Assistenten muss eine Verbindung mit einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Datenbank bestehen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit Quelldaten &#40;Data Mining-Client für Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)   
 [Erkennen von Kategorien &#40;Tabellenanalyse Tools für Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
  
