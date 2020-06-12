---
title: Durchsuchen und Bereinigen von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7c888c95-8986-461e-9f11-2395044b9d97
author: minewiskan
ms.author: owend
ms.openlocfilehash: a31ed2e8e79e6f3ebf6cbecfeac14d24b56bf303
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528336"
---
# <a name="exploring-and-cleaning-data"></a>Durchsuchen und Bereinigen von Daten
  Die Datenvorbereitung umfasst viel mehr als die Datenbereinigung. Die Art und Weise der Datenvorbereitung wirkt sich auch darauf aus, wie Ergebnisse am Ende interpretiert werden. Die Datenvorbereitung umfasst folgende Tasks:  
  
-   Untersuchen und Überprüfen der Verteilung von Daten  
  
-   Bereinigen ungültiger Datensätze und Auswählen von Spalten für Data Mining  
  
-   Korrekte Handhabung von NULL-Werten  
  
-   Klassifizieren von Werten oder Aggregieren von Werten nach unterschiedlichen Zeitblöcken  
  
-   Hinzufügen von Bezeichnungen, um die Nutzbarkeit der Ergebnisse zu verbessern  
  
-   Konvertieren von Datentypen oder Kategorisieren von Werten für die Analyse (wo erforderlich)  
  
 Wenn Sie mit der Datenmodellierung noch nicht vertraut sind, empfiehlt es sich, dass Sie das verwandte Thema, [Checkliste zur Vorbereitung für das Data Mining](checklist-of-preparation-for-data-mining.md), lesen.  
  
## <a name="data-preparation-tools"></a>Datenvorbereitungstools  
 Die Data Mining-Add-Ins für Office enthalten die folgenden Tools für die Datenbereinigung und-Vorbereitung:  
  
### <a name="explore-data"></a>Daten durchsuchen  
 Verwenden Sie den Assistenten zum durch **Suchen von Daten** für diese Daten Vorbereitungs Tasks:  
  
-   Anzeigen der Daten in der Vorschau und Ermitteln von Fehlern, die vor der Analyse korrigiert werden müssen.  
  
-   Sammeln statistischer Informationen, um das Gleichgewicht der Daten und die erforderlichen Cleanuptasks zu verstehen.  
  
-   Identifizieren hilfreicher Spalten für die Analyse und Planen der Datenmodellierungsphase.  
  
 [Erkunden Sie die Daten &#40;SQL Server Data Mining-Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md).  
  
### <a name="detect-and-handle-outliers"></a>Erkennen und Behandeln von Ausreißern  
 Der **ausreißerausreißerassistent** gibt eine Grafik zur Verteilung der Werte in Ihren Daten und hilft Ihnen, extreme Werte zu entfernen. Verwenden Sie das **ausreißertool** für die folgenden Daten Vorbereitungs Tasks:  
  
-   Bestimmen der Zuverlässigkeit einzelner Werte anhand von Mustern, die in den Daten festgestellt wurden.  
  
-   Überprüfen ungewöhnlicher Werte und Ergreifen von Maßnahmen (Löschen oder Ersetzen dieser Werte).  
  
-   Beschränken eines Modells auf einen bestimmten Bereich von Werten. Wenn Ihnen beispielsweise bekannt ist, dass für eine bestimmte Filiale Ausreißer vorliegen, können Sie den betreffenden Wert eliminieren und damit ein Modell erhalten, mit dem bessere Vorhersagen für die anderen Filialen getroffen werden.  
  
 [Ausreißer &#40;SQL Server Data Mining-Add-ins&#41;](outliers-sql-server-data-mining-add-ins.md).  
  
### <a name="relabel-and-bin-data"></a>Neubezeichnen und Klassifizieren von Daten  
 Der **Assistent zum** neubezeichnen gruppiert Daten nach Werten, damit Sie die Bezeichnungen für die Daten ändern können. Verwenden Sie das Tool Neu bezeichnen für die folgenden Datenvorbereitungstasks:  
  
-   Ändern von in Umfrageergebnissen enthaltenen numerischen Codes in Textbeschreibungen, die den jeweiligen numerischen Code erläutern.  
  
     Beispielsweise können Sie Dateneinträge wie Geschlecht = 1 durch Geschlecht = Weiblich ersetzen.  
  
-   Klassifizieren von Daten, indem Gruppen erstellt werden, die Zahlenbereiche darstellen.  
  
     Angenommen, Sie möchten eine Einkommens Spalte von Zahlen durch Bezeichnungen wie **Income-** Mittel und **Income-High**ersetzen.  
  
-   Reduzieren diskreter Werte auf Kategorien.  
  
     Wenn Sie beispielsweise ein Kaufmuster ermitteln möchten, Ihre Ausgangsbasis aber zu viele Einzelprodukte umfasst, könnten Sie Produkte allgemeineren Kategorien zuordnen.  
  
 [&#40;SQL Server Data Mining-Add-ins neu bezeichnen&#41;](relabel-sql-server-data-mining-add-ins.md)  
  
### <a name="cleanse-data"></a>Bereinigen von Daten  
 Die Datenbereinigung umfasst zahlreiche Aktivitäten, die größtenteils durch die Add-Ins unterstützt werden.  
  
-   Identifizieren von NULL-Werten und bestimmen, ob sie in einen reellen Wert geändert oder als `Missing`-Werte behandelt werden sollen.  
  
-   Erkennen von fehlenden Werten und Entfernen dieser Werte oder Berechnen eines geeigneten Werts (z. B. eines Mittelwerts, NULL-Werts oder sonstigen Werts).  
  
 [Durchsuchen von Daten &#40;SQL Server Data Mining-Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md)  
  
 [&#40;SQL Server Data Mining-Add-ins neu bezeichnen&#41;](relabel-sql-server-data-mining-add-ins.md)  
  
 [Aus Beispiel füllen](fill-from-example-table-analysis-tools-for-excel.md)  
  
### <a name="sample-data"></a>Beispieldaten  
 Der Assistent für Beispieldaten stellt zwei Methoden zum Erstellen von ausgeglichenen Datasets zum Trainieren und Testen von Modellen bereit.  
  
-   **Zufällige Stichprobenentnahme.** Verwenden Sie diese Option, um eine repräsentative Menge von Daten aus einem größeren Dataset zu extrahieren und zu Trainings- oder Testzwecken zu verwenden. Die Data Mining-Add-Ins verwenden eine *stratifilierte Stichprobe* , um sicherzustellen, dass für jede Stichprobe mit Stichproben eine ausgeglichene Menge von Werten abgerufen wird  
  
-   **Über Quotierung.** Verwenden Sie diese Option, wenn Sie über weniger Daten verfügen als für das Zielergebnis gewünscht und diese Daten stärker gewichten müssen. Beispiel: Obwohl Betrugsdelikte u. U. relativ selten vorkommen, können Sie Betrugsfälle überquotieren, um geeignete Daten für die Modellierung zu erhalten.  
  
 [Beispiel Daten &#40;SQL Server Data Mining-Add-ins&#41;](sample-data-sql-server-data-mining-add-ins.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)   
 [Validieren von Modellen und Verwenden von Modellen für Vorhersage &#40;Data Mining-Add-Ins für Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Bereitstellen und Skalieren von Mining Modellen &#40;Data Mining-Add-Ins für Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
