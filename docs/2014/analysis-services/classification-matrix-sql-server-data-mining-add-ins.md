---
title: Klassifikationsmatrix (SQL Server Data Mining-Add-ins) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- mining models, validating
- classification matrix
- confusion table
- mining models, testing
ms.assetid: d6f620f4-39af-4714-9628-28ce3c361fca
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1944620e5c83485a01b9bc856cc67e9e6908c769
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048638"
---
# <a name="classification-matrix-sql-server-data-mining-add-ins"></a>Klassifikationsmatrix (SQL Server Data Mining-Add-Ins)
  ![Schaltfläche für Klassifizierung Matrix, Data Mining-Menüband](media/dmc-cmatrix.gif "Klassifikationsmatrix-Schaltfläche, Data Mining-Menüband")  
  
 Mithilfe der Klassifikationsmatrix können Sie die Genauigkeit eines Modells in Bezug auf Vorhersagen bewerten. Um eine Klassifikationsmatrix zu erstellen, führen Sie ein Testdataset für das Modell aus. Das Tool Klassifikationsmatrix vergleicht die tatsächlichen Werte aus dem Testsatz mit den vom Modell getroffenen Vorhersagen. Indem Sie die Matrix überprüfen, können Sie auf Anhieb feststellen, wie oft das Modell richtige Vorhersagen und wie oft es falsche Vorhersagen trifft.  
  
 Verwenden Sie in diesen Add-Ins, die **Klassifikationsmatrix** Assistenten wählen Sie ein Modell, die Testdaten anzugeben, und anschließend eine Ergebnismatrix zu generieren.  
  
## <a name="how-to-read-a-classification-matrix"></a>Interpretieren einer Klassifikationsmatrix  
 Angenommen, Sie möchten ein Kundentreueprogramm entwickeln und Kunden in geeignete Kategorien einteilen, um ihnen angemessene Bonusstufen zuzuweisen. Sie haben für das Bonusprogramm die drei Stufen "Bronze", "Silber" und "Gold" implementiert und in einer Erprobungsphase an Ihre Kunden vergeben. Zusätzlich haben Sie ein Modell entworfen, mit dem Kunden analysiert und die richtigen Kategorien vorhergesagt werden. Jetzt ermitteln Sie anhand der Klassifikationsmatrix und der Testdaten, wie gut das Modell bei der Vorhersage des richtigen Angebots für alle Kunden abgeschnitten hat.  
  
 An der Tabelle der Klassifikationsmatrix können Sie ablesen, wie viele Kunden auf Grundlage des Modells den einzelnen Kategorien zugewiesen würden, und das Ergebnis mit der Anzahl der Kunden vergleichen, die sich tatsächlich für die einzelnen Bonusstufen eingetragen haben.  
  
||Bronze (IST-Wert)|Gold (IST-Wert)|Silber (IST-Wert)|  
|-|-----------------------|---------------------|-----------------------|  
|Bronze|**94.45 %**|15.18 %|1.70 %|  
|Gold|2.72 %|**84.82 %**|0,00 %|  
|Silber|1.84 %|0,00 %|**93.80 %**|  
|*Richtig*|*95.45 %*|*84.82 %*|*98.30 %*|  
|*Fälschlicherweise klassifiziert*|*4.55 %*|*15.18 %*|*1.70 %*|  
  
-   In jeder Spalte werden die tatsächlichen Werte im Testdataset angezeigt.  
  
-   In jeder Zeile werden die vorhergesagten Werte angezeigt.  
  
-   Die fett dargestellten Werte, die in der Matrix diagonal von der oberen linken zur unteren rechten Ecke verlaufen, zeigen, welche Vorhersagen vom Modell richtig getroffen wurden.  
  
-   Alle anderen Werte außerhalb der Diagonalen stellen Fehler dar. Einige Fehler sind falsch positive Ergebnisse. Dies bedeutet, dass vom Modell vorhergesagt wurde, dass der Kunde am Gold-Programm teilnehmen würde, die Annahme aber falsch war.  Abhängig von Ihrer Problemdomäne können falsch positive Ergebnisse erhebliche Kosten verursachen.  
  
     Andere Fehler sind falsch negative Ergebnisse. Dies bedeutet, dass vom Modell vorhergesagt wurde, dass der Kunde kein Interesse zeigen würde, obwohl er letztlich am Programm teilgenommen hat. Auch hier kann die entgangene Geschäftschance abhängig von der Problemdomäne erhebliche Verluste verursachen.  
  
## <a name="using-the-classification-matrix-wizard"></a>Verwenden des Klassifikationsmatrix-Assistenten  
  
1.  Wählen Sie das Miningmodell aus, auf dem die Vorhersagen basieren sollen.  
  
2.  Wählen Sie eine Quelle für neue Testdaten aus, oder verwenden Sie die mit der Struktur gespeicherten Testdaten.  
  
3.  Wählen Sie die Spalte aus, deren Genauigkeit Sie überprüfen möchten. Sie können beim Erstellen einer Matrix nur eine Spalte auswählen, allerdings kann die Spalte mehrere Werte enthalten.  
  
     Tipp: Die Interpretation einer Klassifikationsmatrix kann schwierig werden, wenn für die vorhersagbare Spalte viele Vergleichsspalten vorhanden sind.  
  
     In der **Spalten auswählen, um vorhersagen** Seite, Sie können auch angeben, ob die Anzahl der richtige und falsche Werte anzuzeigen, oder als Prozentwert angezeigt werden sollen.  
  
4.  Geben Sie auf der Seite Quelldaten auswählen an, ob Sie externe Testdaten oder die mit dem Modell gespeicherten Testdaten verwenden.  
  
5.  Wenn Sie externe Testdaten verwenden, müssen Sie ordnen Sie das Modell den Eingabespalten auf die **Beziehung angeben** Seite des Assistenten.  
  
     Bei Verwendung des eingebetteten Testdatasets erfolgt die Zuordnung automatisch.  
  
6.  Klicken Sie auf **Fertig stellen** zum Ausführen von Vorhersagen für das Modell und die Klassifikationsmatrix zu generieren.  
  
     Vom Assistenten wird ein Bericht erstellt, der die Klassifikationsmatrix und andere Details der Analyse enthält. Der Bericht wird als Tabelle in Excel gespeichert. Oberhalb des Berichts befindet sich eine Zusammenfassung, die angibt, wie viele Fälle richtig vorhergesagt wurden und wie viele Vorhersagen falsch waren.  
  
### <a name="requirements"></a>Anforderungen  
  
-   Zum Erstellen einer Klassifikationsmatrix benötigen Sie Zugriff auf ein vorhandenes Miningmodell, das Genauigkeitsmessungen unterstützt. Vorhersagemodelle und Zuordnungsmodelle können nicht mithilfe dieses Tools ausgewertet werden.  
  
-   Das untersuchte Modell muss einen Wert vorhersagen, der entweder diskret ist oder bereits diskretisiert wurde.  
  
-   Wenn Sie zusammen mit der Struktur oder dem Modell keinen Testsatz gespeichert haben, benötigen Sie ein Eingabedataset, das im Wesentlichen dieselbe Anzahl von Spalten wie das im Modell verwendete Dataset enthält und auch die entsprechenden Datentypen aufweist.  
  
-   Sowohl das Data Mining-Modell als auch die neuen Daten, die Sie für den Test verwenden, müssen mindestens eine Spalte enthalten, die vorhergesagt werden kann, und die Spalten müssen denselben Datentyp enthalten.  
  
### <a name="known-issues"></a>Bekannte Probleme  
 In SQL Server 2012 und SQL Server 2014, die Möglichkeit, ordnen Sie interner testdatasets zum Modell funktioniert nicht der **Klassifikationsmatrix** Tool. Sie können jedoch ein externes Dataset angeben und anschließend den Trainingssatz als Eingabe auswählen, um Fehler im ursprünglichen Dataset zu ermitteln.  
  
## <a name="see-also"></a>Siehe auch  
 [Überprüfen von Modellen und Verwenden von Modellen für Vorhersagen &#40;Data Mining-Add-ins für Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)   
 [Durchsuchen Sie Daten &#40;SQL Server Data Mining-Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md)   
 [Kategorien erkennen &#40;Tabellenanalysetools für Excel&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
  