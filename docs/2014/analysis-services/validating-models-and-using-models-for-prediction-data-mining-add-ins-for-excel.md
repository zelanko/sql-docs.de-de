---
title: Überprüfen von Modellen und Verwenden von Modellen für Vorhersagen (Data Mining-Add-ins für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
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
ms.openlocfilehash: 0a9ae056818b260ed00df9111d8b06b37378285d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48148850"
---
# <a name="validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel"></a>Überprüfen von Modellen und Verwenden von Modellen für Vorhersagen (Data Mining-Add-Ins für Excel)
  Das Testen und Überprüfen des Modells ist ein wichtiger Schritt im Data Mining-Prozess. Sie müssen wissen, welche Leistung Ihre Miningmodelle mit echten Daten erzielen, bevor Sie die Modelle in Ihrer Produktionsumgebung bereitstellen.  
  
 Die Data Mining-Add-Ins bieten Tools, die Sie beim Testen erstellter Modelle und beim Erstellen von Vorhersagen und Empfehlungen auf Grundlage der Modelle unterstützen.  
  
## <a name="accuracy-chart"></a>Genauigkeitsdiagramm  
 Die **Genauigkeitsdiagramm** Assistent unterstützt Sie beim Erstellen einer Vorhersageabfrage und beim Bewerten von Datamining-Modells durch Erstellen eines prognosegütediagramms oder Punktdiagramms. Das Prognosegütediagramm hilft bei der Unterscheidung fast identischer Modelle in einer Struktur, sodass Sie feststellen können, von welchem Modell die besten Vorhersagen bereitgestellt werden.  
  
 [Genauigkeitsdiagramm &#40;SQL Server Data Mining-Add-ins&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
## <a name="classification-matrix"></a>Klassifikationsmatrix  
 Die **Klassifikationsmatrix** Assistenten können Sie eine Vorhersageabfrage, damit die Leistung eines klassifizierungsmodells bewerten zu erstellen. Als Ausgabe erhalten Sie ein Diagramm, in dem sowohl genaue als auch ungenaue Vorhersagen zusammengefasst sind, die mit dem Modell getroffen wurden. Die Matrix ist ein wichtiges Tool, da sie nicht nur die Häufigkeit anzeigt, mit der ein Wert von einem Modell richtig vorhergesagt worden ist, sondern auch, welche Werte vom Modell am häufigsten falsch vorhergesagt wurden.  
  
 [Klassifikationsmatrix &#40;SQL Server Data Mining-Add-ins&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
  
## <a name="profit-chart"></a>Gewinndiagramm  
 Die **Gewinndiagramm** Assistent unterstützt Sie abwägen der Vorteile der Verwendung von Datamining-Modelle und bewerten die Kosten falsch positive Ergebnisse und falsche negative  
  
 Dieser Diagrammtyp misst die Vorhersagegenauigkeit des Modells und schließt dabei die angegebenen Stückkosten und Gesamtkosten ein.  
  
 [Gewinndiagramm &#40;SQL Server Data Mining-Add-ins&#41;](profit-chart-sql-server-data-mining-add-ins.md).  
  
## <a name="cross-validation"></a>Kreuzvalidierung  
 Die Kreuzvalidierung gilt in der Data Mining-Community als bewährte Methode zum Bewerten der Gültigkeit eines Datasets und der Genauigkeit eines Miningmodells, das auf diesem Dataset beruht. Dabei wird ein Dataset in Teilsets unterteilt, und anschließend werden iterativ Modelle für die einzelnen Teilsets erstellt, trainiert und getestet.  
  
 Die **Kreuzvalidierung** Assistenten können Sie angeben, die Anzahl der Aufteilungen für Ihre Daten durch, und anschließend einen kreuzvalidierungsbericht, die die Unterschiede zwischen diesen Querschnitten statistisch beschrieben werden. Auf dieser Grundlage können Sie ermitteln, ob das Modell für alle Trainingsdaten geeignet ist oder ob es für eine bestimmte Teilmenge verfälschte Ergebnisse zurückgibt.  
  
 [Übergreifende Überprüfung &#40;SQL Server Data Mining-Add-ins&#41;](cross-validation-sql-server-data-mining-add-ins.md)  
  
## <a name="query-wizard"></a>Abfrage-Assistent  
 Die **Abfrage** -Assistent ist ein interaktives Tool, mit dem Sie eine Vorhersageabfrage erstellen kann. Über Abfragen generieren Sie Empfehlungen, Vorhersagen usw.  
  
 In der **Abfrage** Assistenten für Sie ein Modell, und geben Sie die Eingabedaten, entweder als einzelne Werte oder aus einer Tabelle oder den Bereich und dem Assistenten können Sie die Spalten auswählen, die Ausgabe. Sie können der Abfrage auch Funktionen hinzufügen, um Wahrscheinlichkeitsergebnisse und andere nützliche Statistiken zu generieren.  
  
 [Abfrage &#40;SQL Server Data Mining-Add-ins&#41;](query-sql-server-data-mining-add-ins.md)  
  
## <a name="advanced-query-editor"></a>Erweiterter Abfrage-Editor  
 Die **erweiterten Abfrage-Editor** ist eine interaktive Gruppe von Dialogfeldern, die Ihnen hilft, erstellen alle Arten von DMX-Anweisungen, etwas aus der Ausführung von benutzerdefinierter Abfragen zum Erstellen und Trainieren neuer Modelle, Löschen von Modellen oder neue Datasets erstellen.  
  
 [Erweiterter Data Mining-Abfrage-Editor](advanced-data-mining-query-editor.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen und Bereinigen von Daten](exploring-and-cleaning-data.md)   
 [Erstellen von Datamining-Modells](creating-a-data-mining-model.md)   
 [Bereitstellen und Skalieren von Miningmodellen &#40;Data Mining-Add-ins für Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
