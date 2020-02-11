---
title: Validieren von Modellen und Verwenden von Modellen für die Vorhersage (Data Mining-Add-Ins für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- mining models, charting
- validation [data mining]
- mining models, testing
ms.assetid: e245ac1f-1230-48e9-9091-e70b131aa2a8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97268dac1fef029bc35ff702ace0d422ee296d65
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66065501"
---
# <a name="validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel"></a>Überprüfen von Modellen und Verwenden von Modellen für Vorhersagen (Data Mining-Add-Ins für Excel)
  Das Testen und Überprüfen des Modells ist ein wichtiger Schritt im Data Mining-Prozess. Sie müssen wissen, welche Leistung Ihre Miningmodelle mit echten Daten erzielen, bevor Sie die Modelle in Ihrer Produktionsumgebung bereitstellen.  
  
 Die Data Mining-Add-Ins bieten Tools, die Sie beim Testen erstellter Modelle und beim Erstellen von Vorhersagen und Empfehlungen auf Grundlage der Modelle unterstützen.  
  
## <a name="accuracy-chart"></a>Genauigkeitsdiagramm  
 Der **Genauigkeits Diagramm** -Assistent unterstützt Sie beim Erstellen einer Vorhersage Abfrage und beim Bewerten der Leistung eines Data Mining Modells durch Erstellen eines Prognose Prognose-oder Punkt Diagramm. Das Prognosegütediagramm hilft bei der Unterscheidung fast identischer Modelle in einer Struktur, sodass Sie feststellen können, von welchem Modell die besten Vorhersagen bereitgestellt werden.  
  
 [Genauigkeits Diagramm &#40;SQL Server Data Mining-Add-ins&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
## <a name="classification-matrix"></a>Klassifikationsmatrix  
 Der **Klassifikations Matrix** -Assistent unterstützt Sie beim Erstellen einer Vorhersage Abfrage zur Bewertung der Leistung eines Klassifizierungs Modells. Als Ausgabe erhalten Sie ein Diagramm, in dem sowohl genaue als auch ungenaue Vorhersagen zusammengefasst sind, die mit dem Modell getroffen wurden. Die Matrix ist ein wichtiges Tool, da sie nicht nur die Häufigkeit anzeigt, mit der ein Wert von einem Modell richtig vorhergesagt worden ist, sondern auch, welche Werte vom Modell am häufigsten falsch vorhergesagt wurden.  
  
 [Klassifizierungs Matrix &#40;SQL Server Data Mining-Add-ins&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
  
## <a name="profit-chart"></a>Gewinndiagramm  
 Mit dem **Gewinn Diagramm** -Assistenten können Sie die Vorteile der Verwendung eines Data Mining Modells abwägen und die Kosten für falsch positive und falsche Negative Werte bewerten.  
  
 Dieser Diagrammtyp misst die Vorhersagegenauigkeit des Modells und schließt dabei die angegebenen Stückkosten und Gesamtkosten ein.  
  
 [Gewinn Diagramm &#40;SQL Server Data Mining-Add-ins&#41;](profit-chart-sql-server-data-mining-add-ins.md).  
  
## <a name="cross-validation"></a>Kreuzvalidierung  
 Die Kreuzvalidierung gilt in der Data Mining-Community als bewährte Methode zum Bewerten der Gültigkeit eines Datasets und der Genauigkeit eines Miningmodells, das auf diesem Dataset beruht. Dabei wird ein Dataset in Teilsets unterteilt, und anschließend werden iterativ Modelle für die einzelnen Teilsets erstellt, trainiert und getestet.  
  
 Mithilfe des **Kreuz Validierungs-** Assistenten können Sie die Anzahl der Aufteilungen angeben, nach denen die Daten aufgeteilt werden, und dann einen Kreuz Validierungsbericht bereitstellen, in dem die Unterschiede zwischen diesen quer Abschnitten statistisch beschrieben werden. Auf dieser Grundlage können Sie ermitteln, ob das Modell für alle Trainingsdaten geeignet ist oder ob es für eine bestimmte Teilmenge verfälschte Ergebnisse zurückgibt.  
  
 [&#40;SQL Server Data Mining-Add-ins&#41;der Kreuz Validierung](cross-validation-sql-server-data-mining-add-ins.md)  
  
## <a name="query-wizard"></a>Abfrage-Assistent  
 Der **Abfrage** -Assistent ist ein interaktives Tool, das Sie beim Erstellen einer Vorhersage Abfrage unterstützt. Über Abfragen generieren Sie Empfehlungen, Vorhersagen usw.  
  
 Wählen Sie im **Abfrage** -Assistenten ein Modell aus, und geben Sie dann Eingabedaten entweder als einzelne Werte oder aus einer Tabelle oder einem Bereich an, und der Assistent unterstützt Sie bei der Auswahl der auszulegenden Spalten. Sie können der Abfrage auch Funktionen hinzufügen, um Wahrscheinlichkeitsergebnisse und andere nützliche Statistiken zu generieren.  
  
 [Abfrage &#40;SQL Server Data Mining-Add-ins&#41;](query-sql-server-data-mining-add-ins.md)  
  
## <a name="advanced-query-editor"></a>Editor für erweiterte Abfragen  
 Der **Erweiterte Abfrage-Editor** ist ein interaktiver Satz von Dialogfeldern, mit denen Sie alle Arten von DMX-Anweisungen erstellen können, von der Ausführung benutzerdefinierter Abfragen bis hin zum Erstellen und trainieren neuer Modelle, zum Löschen von Modellen oder zum Erstellen neuer Datasets.  
  
 [Erweiterter Data Mining-Abfrage-Editor](advanced-data-mining-query-editor.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Durchsuchen und Bereinigen von Daten](exploring-and-cleaning-data.md)   
 [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md)   
 [Bereitstellen und Skalieren von Mining Modellen &#40;Data Mining-Add-Ins für Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
