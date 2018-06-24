---
title: Durchsuchen und Bereinigen von Daten | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c888c95-8986-461e-9f11-2395044b9d97
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0c39eaa58152fd1a75eeaefdc79bae93ccd36b98
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047521"
---
# <a name="exploring-and-cleaning-data"></a>Durchsuchen und Bereinigen von Daten
  Die Datenvorbereitung umfasst viel mehr als die Datenbereinigung. Die Art und Weise der Datenvorbereitung wirkt sich auch darauf aus, wie Ergebnisse am Ende interpretiert werden. Die Datenvorbereitung umfasst folgende Tasks:  
  
-   Untersuchen und Überprüfen der Verteilung von Daten  
  
-   Bereinigen ungültiger Datensätze und Auswählen von Spalten für Data Mining  
  
-   Korrekte Handhabung von NULL-Werten  
  
-   Klassifizieren von Werten oder Aggregieren von Werten nach unterschiedlichen Zeitblöcken  
  
-   Hinzufügen von Bezeichnungen, um die Nutzbarkeit der Ergebnisse zu verbessern  
  
-   Konvertieren von Datentypen oder Kategorisieren von Werten für die Analyse (wo erforderlich)  
  
 Wenn Sie die datenmodellierung vertraut sind, wird empfohlen, das verwandte Thema zu lesen [Prüfliste der Vorbereitung für Data Mining](checklist-of-preparation-for-data-mining.md).  
  
## <a name="data-preparation-tools"></a>Datenvorbereitungstools  
 Die Data Mining Add-ins für Office umfasst die folgenden Tools für die DatenBereinigung und vorbereiten:  
  
### <a name="explore-data"></a>Daten durchsuchen  
 Verwenden der **Stichprobenoptionen** Assistenten für die folgenden datenvorbereitungstasks:  
  
-   Anzeigen der Daten in der Vorschau und Ermitteln von Fehlern, die vor der Analyse korrigiert werden müssen.  
  
-   Sammeln statistischer Informationen, um das Gleichgewicht der Daten und die erforderlichen Cleanuptasks zu verstehen.  
  
-   Identifizieren hilfreicher Spalten für die Analyse und Planen der Datenmodellierungsphase.  
  
 [Durchsuchen Sie Daten &#40;SQL Server Data Mining-Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md).  
  
### <a name="detect-and-handle-outliers"></a>Erkennen und Behandeln von Ausreißern  
 Die **Ausreißer** Assistenten für die Verteilung der Werte in Ihren Daten Diagramme bereit und hilft Extremwerten. Verwenden der **Ausreißer** Tool für die folgenden datenvorbereitungstasks:  
  
-   Bestimmen der Zuverlässigkeit einzelner Werte anhand von Mustern, die in den Daten festgestellt wurden.  
  
-   Überprüfen ungewöhnlicher Werte und Ergreifen von Maßnahmen (Löschen oder Ersetzen dieser Werte).  
  
-   Beschränken eines Modells auf einen bestimmten Bereich von Werten. Wenn Ihnen beispielsweise bekannt ist, dass für eine bestimmte Filiale Ausreißer vorliegen, können Sie den betreffenden Wert eliminieren und damit ein Modell erhalten, mit dem bessere Vorhersagen für die anderen Filialen getroffen werden.  
  
 [Ausreißer &#40;SQL Server Data Mining-Add-ins&#41;](outliers-sql-server-data-mining-add-ins.md).  
  
### <a name="relabel-and-bin-data"></a>Neubezeichnen und Klassifizieren von Daten  
 Die **neu bezeichnen** Assistent gruppiert Daten nach Werten, sodass Sie die Bezeichnungen für die Daten ändern können. Verwenden Sie das Tool Neu bezeichnen für die folgenden Datenvorbereitungstasks:  
  
-   Ändern von in Umfrageergebnissen enthaltenen numerischen Codes in Textbeschreibungen, die den jeweiligen numerischen Code erläutern.  
  
     Beispielsweise können Sie Dateneinträge wie Geschlecht = 1 durch Geschlecht = Weiblich ersetzen.  
  
-   Klassifizieren von Daten, indem Gruppen erstellt werden, die Zahlenbereiche darstellen.  
  
     Angenommen, Sie möchten möglicherweise ersetzen Sie z. B. eine numerische einkommensspalte mit Bezeichnungen **Einkommen – Mittel** und **Einkommen – hoch**.  
  
-   Reduzieren diskreter Werte auf Kategorien.  
  
     Wenn Sie beispielsweise ein Kaufmuster ermitteln möchten, Ihre Ausgangsbasis aber zu viele Einzelprodukte umfasst, könnten Sie Produkte allgemeineren Kategorien zuordnen.  
  
 [Neu bezeichnen &#40;SQL Server Data Mining-Add-ins&#41;](relabel-sql-server-data-mining-add-ins.md)  
  
### <a name="cleanse-data"></a>Bereinigen von Daten  
 Die Datenbereinigung umfasst zahlreiche Aktivitäten, die größtenteils durch die Add-Ins unterstützt werden.  
  
-   Identifizieren von NULL-Werten und bestimmen, ob sie in einen reellen Wert geändert oder als `Missing`-Werte behandelt werden sollen.  
  
-   Erkennen von fehlenden Werten und Entfernen dieser Werte oder Berechnen eines geeigneten Werts (z. B. eines Mittelwerts, NULL-Werts oder sonstigen Werts).  
  
 [Durchsuchen Sie Daten &#40;SQL Server Data Mining-Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md)  
  
 [Neu bezeichnen &#40;SQL Server Data Mining-Add-ins&#41;](relabel-sql-server-data-mining-add-ins.md)  
  
 [Aus Beispiel füllen](fill-from-example-table-analysis-tools-for-excel.md)  
  
### <a name="sample-data"></a>Beispieldaten  
 Der Assistent für Beispieldaten stellt zwei Methoden zum Erstellen von ausgeglichenen Datasets zum Trainieren und Testen von Modellen bereit.  
  
-   **Zufällige Stichprobenentnahme.** Verwenden Sie diese Option, um eine repräsentative Menge von Daten aus einem größeren Dataset zu extrahieren und zu Trainings- oder Testzwecken zu verwenden. Verwenden Sie die Data Mining-Add-ins *geschichtete Stichprobenentnahme* um sicherzustellen, dass für jede stichprobenvariable eine ausgeglichene Gruppe von Werten abgerufen wird.  
  
-   **Überquotierung.** Verwenden Sie diese Option, wenn Sie über weniger Daten verfügen als für das Zielergebnis gewünscht und diese Daten stärker gewichten müssen. Beispiel: Obwohl Betrugsdelikte u. U. relativ selten vorkommen, können Sie Betrugsfälle überquotieren, um geeignete Daten für die Modellierung zu erhalten.  
  
 [Beispieldaten &#40;SQL Server Data Mining-Add-ins&#41;](sample-data-sql-server-data-mining-add-ins.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Datamining-Modells](creating-a-data-mining-model.md)   
 [Überprüfen von Modellen und Verwenden von Modellen für Vorhersagen &#40;Data Mining-Add-ins für Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Bereitstellen und Skalieren von Miningmodellen &#40;Data Mining-Add-ins für Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  