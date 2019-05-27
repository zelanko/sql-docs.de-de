---
title: Datamining-Designer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], structure
- mining structures [Analysis Services], modifying
- data mining editor [Analysis Services]
- Data Mining Designer
- data mining [Analysis Services], modifying
ms.assetid: 2540db5b-2bf3-4b6c-87c8-79c48d71acce
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b0a54a0ae2bab2c8019b706a51b94f0338dcb3cf
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66085109"
---
# <a name="data-mining-designer"></a>Data Mining Designer
  Der Data Mining-Designer ist die primäre Umgebung, in der Sie in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]mit Miningmodellen arbeiten. Sie können auf den Designer zugreifen, indem Sie eine vorhandene Miningstruktur auswählen oder indem Sie den Data Mining-Assistenten verwenden, um eine neue Miningstruktur und ein neues Miningmodell zu erstellen. Sie können mit dem Data Mining-Designer folgende Aufgaben ausführen:  
  
-   Modifizieren der Miningstruktur und des Miningmodells, die ursprünglich vom Data Mining-Assistenten erstellt wurden.  
  
-   Erstellen neuer Modelle basierend auf vorhandenen Miningstrukturen.  
  
-   Trainieren und Durchsuchen von Miningmodellen.  
  
-   Vergleichen von Modellen mithilfe von Genauigkeitsdiagrammen.  
  
-   Erstellen von Vorhersageabfragen basierend auf Miningmodellen.  
  
## <a name="mining-structure-tab"></a>Miningstruktur (Registerkarte)  
 Verwenden Sie die Registerkarte **Miningstruktur** , um Spalten hinzuzufügen und die Eigenschaften einer vorhandenen Miningstruktur zu ändern. Die folgenden Tasks und Themen enthalten weitere Informationen zum Arbeiten mit Miningstrukturen:  
  
 [Miningstrukturen &#40;Analysis Services – Data Mining&#41;](mining-structures-analysis-services-data-mining.md)  
  
 [Tasks und Anweisungen für Miningstrukturen](mining-structure-tasks-and-how-tos.md)  
  
## <a name="mining-models-tab"></a>Miningmodelle (Registerkarte)  
 Verwenden Sie die Registerkarte **Miningmodelle** , um vorhandene Miningmodelle zu verwalten und neue Modelle zu erstellen. Miningmodelle basieren stets auf einer vorhandenen Miningstruktur.  
  
 Auf der Registerkarte **Miningmodelle** können Sie den Algorithmustyp ändern, Spalten, die der Modellstruktur zugeordnet sind, hinzufügen oder entfernen, algorithmusspezifische Spalteneigenschaften zuweisen, die Verwendung der Miningmodellspalte angeben sowie Algorithmusparameter anpassen, die dem Miningmodell zugeordnet sind. Sie können die Miningstruktur zusammen mit den ausgewählten Modellen oder mit allen verknüpften Modellen verarbeiten.  
  
 In den folgenden Themen finden Sie weitere Informationen zum Arbeiten mit Miningmodellen:  
  
 [Miningmodelle &#40;Analysis Services – Data Mining&#41;](mining-models-analysis-services-data-mining.md)  
  
 [Miningmodelltasks und Anweisungen](mining-model-tasks-and-how-tos.md)  
  
## <a name="mining-model-viewer-tab"></a>Miningmodell-Viewer (Registerkarte)  
 Verwenden Sie die Registerkarte **Miningmodell-Viewer** , um Ihre Miningmodelle optisch zu analysieren. Jedes Miningmodell ist einem benutzerdefinierten Viewer zugeordnet, der Inhalte anzeigt, die für das Modell spezifisch sind. Sie können den Miningmodellinhalt auch anzeigen, indem Sie den Viewer für den Inhalt verwenden.  
  
 In den folgenden Themen finden Sie weitere Informationen zum Anzeigen von Miningmodellen mit den Data Mining-Viewern:  
  
 [Data Mining-Modell-Viewer](data-mining-model-viewers.md)  
  
 [Tasks und Anweisungen für Miningmodell-Viewer](mining-model-viewer-tasks-and-how-tos.md)  
  
## <a name="mining-accuracy-chart-tab"></a>Mininggenauigkeitsdiagramm (Registerkarte)  
 Verwenden Sie die Registerkarte **Mininggenauigkeitsdiagramm** , um die Vorhersagegenauigkeit eines einzelnen Miningmodells zu testen oder die Wirksamkeit mehrerer Miningmodelle in einer Miningstruktur zu vergleichen. Die Registerkarte enthält Tools zum Filtern der Daten, zum Auswählen der Miningmodelle und zum Anzeigen der Ergebnisse in einem Lift- oder Gewinndiagramm oder einer Klassifikationsmatrix.  
  
 Weitere Informationen zum Testen und Überprüfen von Miningmodellen finden Sie in den folgenden Themen:  
  
 [Tests und Überprüfung &#40;Data Mining&#41;](testing-and-validation-data-mining.md)  
  
 [Tasks und Anweisungen für Test und Überprüfung &#40;Data Mining&#41;](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
## <a name="mining-model-prediction-tab"></a>Miningmodellvorhersage (Registerkarte)  
 Die Registerkarte **Miningmodellvorhersage** enthält den Generator für Vorhersageabfragen, mit dem Sie eine DMX-Vorhersageabfrage (Data Mining Extensions; Data Mining-Erweiterungen) erstellen können. Die Registerkarte enthält Tools zum Angeben von Miningmodellen und Eingabetabellen, zum Zuordnen der Spalten des Miningmodells mit Spalten in der Eingabetabelle, zum Hinzufügen von Funktionen zu einer Abfrage und zum Angeben von Kriterien für jede Spalte.  
  
 Nachdem Sie eine Abfrage entworfen haben, können Sie verschiedene Sichten der Registerkarte verwenden, um die Ergebnisse der Abfrage anzuzeigen und die Abfrage manuell zu ändern. Sie können die Ergebnisse der Abfrage auch in einer Tabelle in einer Datenbank speichern.  
  
 Weitere Informationen zum Erstellen von Data Mining-Abfragen finden Sie in den folgenden Themen:  
  
 [Data Mining-Abfrage](data-mining-queries.md)  
  
 [Data Mining-Abfragetasks und Anweisungen](data-mining-query-tasks-and-how-tos.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Projektmappen](data-mining-solutions.md)  
  
  
