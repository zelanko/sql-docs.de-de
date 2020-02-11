---
title: Erstellen von Vorhersagen für die Callcentermodelle (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5be0cec7-f639-4eeb-835e-e3204ae619e9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 30f24ab457669f572189d2eb13deca3f672f5e18
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63217873"
---
# <a name="creating-predictions-for-the-call-center-models-intermediate-data-mining-tutorial"></a>Erstellen von Vorhersagen für Callcentermodelle (Data Mining-Lernprogramm für Fortgeschrittene)
  Nachdem Sie Informationen zu Interaktionen zwischen Arbeitsschichten, der Anzahl der Telefonisten und Anrufe sowie der Dienstqualität gesammelt haben, können Sie einige Vorhersageabfragen für Geschäftsanalysen und Planungen erstellen. Sie erstellen zunächst einige Vorhersagen über das explorative Modell, um bestimmte Annahmen zu testen. Als Nächstes erstellen Sie Massen Vorhersagen mithilfe des logistischen Regressionsmodells.  
  
 Für diese Lektion wird davon ausgegangen, dass Sie bereits mit dem Konzept von Vorhersageabfragen vertraut sind.  
  
## <a name="creating-predictions-using-the-neural-network-model"></a>Erstellen von Vorhersagen mit dem neuronalen Netzwerkmodell  
 Im folgenden Beispiel wird veranschaulicht, wie eine SINGLETON-Vorhersage mithilfe des neuronalen Netzwerkmodells getroffen wird, das für Untersuchungen erstellt wurde. Mit SINGLETON-Vorhersagen können verschiedene Werte und deren Auswirkungen auf das Modell auf einfache Weise getestet werden. In diesem Szenario werden Sie die Dienstqualität für die Nachtschicht (kein Wochentag angegeben) vorhersagen, wenn sechs erfahrene Telefonisten Dienst haben.  
  
#### <a name="to-create-a-singleton-query-by-using-the-neural-network-model"></a>So erstellen Sie eine SINGLETON-Abfrage mithilfe des neuronalen Netzwerkmodells  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] die Lösung, die das zu verwendende Modell enthält.  
  
2.  Klicken Sie im Data Mining-Designer auf die Registerkarte **Mining Modellvorhersage** .  
  
3.  Klicken Sie im Bereich **Mining Modell** auf **Modell auswählen**.  
  
4.  Im Dialogfeld **Mining Modell auswählen** wird eine Liste mit Mining Strukturen angezeigt. Erweitern Sie die Miningstruktur, um eine Liste der dieser Struktur zugeordneten Miningmodelle anzuzeigen.  
  
5.  Erweitern Sie die Miningstruktur "Call Center Default", und wählen Sie das neuronale Netzwerkmodell "Call Center - LR" aus.  
  
6.  Klicken Sie im Menü **Miningmodell** auf **SINGLETON-Abfrage**.  
  
     Das Dialogfeld **Singleton-Abfrage Eingabe** wird angezeigt, wobei die Spalten den Spalten im Mining Modell zugeordnet sind.  
  
7.  Klicken Sie im Dialogfeld **Singleton-Abfrage Eingabe** auf die Zeile für Shift, und wählen Sie dann *Mitternacht*aus.  
  
8.  Klicken Sie auf die Zeile für LVL 2-Operatoren, und geben `6`Sie ein.  
  
9. Klicken Sie in der unteren Hälfte der Registerkarte **Mining Modellvorhersage** auf die erste Zeile im Raster.  
  
10. Klicken Sie in der Spalte **Quelle** auf den Pfeil nach unten, und wählen Sie **Vorhersagefunktion**aus. Wählen Sie in der Spalte **Feld** die Option **präthistogram**aus.  
  
     Eine Liste von Argumenten, die Sie mit dieser Vorhersagefunktion verwenden können, wird automatisch im Feld **Kriterium/Argument** angezeigt.  
  
11. Ziehen Sie die Spalte Service Grade aus der Liste der Spalten im Bereich **Mining Modell** in das Feld **Kriterium/Argument** .  
  
     Der Name der Spalte wird automatisch als Argument eingefügt. Sie können jede vorhersagbare Attributspalte in dieses Textfeld ziehen.  
  
12. Klicken Sie in der oberen Ecke der Vorhersage Abfrage-Generator auf die Schaltfläche **zur Abfrageergebnis Sicht wechseln**.  
  
 Die erwarteten Ergebnisse enthalten die möglichen vorhergesagten Werte für jede Dienstqualität bei Berücksichtigung der angegebenen Eingaben zusammen mit Unterstützungs- und Wahrscheinlichkeitswerten für jede Vorhersage. Sie können jederzeit zur Entwurfsansicht zurückkehren und die Eingaben ändern oder weitere Eingaben hinzufügen.  
  
## <a name="creating-predictions-by-using-a-logistic-regression-model"></a>Erstellen von Vorhersagen mithilfe eines logistischen Regressionsmodells  
 Wenn Sie die Attribute bereits kennen, die für das Geschäftsproblem relevant sind, können Sie ein logistisches Regressionsmodell verwenden, um die Auswirkungen bei Änderungen an bestimmten unabhängigen Variablen vorherzusagen. Die logistische Regression ist eine statistische Methode, die häufig verwendet wird, um Vorhersagen auf der Grundlage von Änderungen in unabhängigen Variablen zu treffen: Sie wird z. B. für finanzielle Bewertungen verwendet, um das Kundenverhalten auf der Grundlage der Kundendemografie vorherzusagen.  
  
 In dieser Aufgabe erfahren Sie, wie Sie eine Datenquelle für Vorhersagen erstellen und anschließend Vorhersagen zur Beantwortung verschiedener Geschäftsfragen treffen.  
  
### <a name="generating-data-used-for-bulk-prediction"></a>Generieren von Daten für Massenvorhersagen  
 Es gibt viele Möglichkeiten, Eingabedaten bereitzustellen: Sie können beispielsweise die Personalausstattung aus einer Tabelle importieren und diese Daten durch das Modell laufen lassen, um die Dienstqualität für den nächsten Monat vorherzusagen.  
  
 In diesem Lektion erstellen Sie mithilfe des Datenquellensicht-Designers eine benannte Abfrage. Diese benannte Abfrage ist eine benutzerdefinierte Transact-SQL-Anweisung, die für jede Schicht im Dienstplat die maximale Anzahl von Operatoren, die Mindestanzahl angenommener Anrufe und die durchschnittliche Anzahl generierter Fragen berechnet. Sie verknüpfen dann diese Daten mit einem Miningmodell, um Vorhersagen für eine Reihe bevorstehender Tage zu treffen.  
  
##### <a name="to-generate-input-data-for-a-bulk-prediction-query"></a>So generieren Sie Eingabedaten für eine Massenvorhersageabfrage  
  
1.  Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **Datenquellen Sichten**, und wählen Sie dann **neue Datenquellen Sicht**aus.  
  
2.  Wählen Sie [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] im Datenquellen Sicht-Assistenten als Datenquelle aus, und klicken Sie dann auf **weiter**.  
  
3.  Klicken Sie auf der Seite **Tabellen und Sichten auswählen** auf **weiter** , ohne Tabellen auszuwählen.  
  
4.  Geben Sie auf der Seite **Assistenten abschließen** den Namen ein `Shifts`.  
  
     Dieser Name wird im Projektmappen-Explorer als Name der Datenquellensicht angezeigt.  
  
5.  Klicken Sie mit der rechten Maustaste auf den leeren Entwurfs Bereich, und wählen Sie **neue benannte Abfrage**aus.  
  
6.  Geben `Shifts for Call Center`Sie im Dialogfeld **benannte Abfrage erstellen** im Feld **Name den Namen**ein.  
  
     Dieser Name wird im Datenquellensicht-Designer nur als der Name der benannten Abfrage angezeigt.  
  
7.  Fügen Sie in der unteren Hälfte des Dialogfelds die folgende Abfrageanweisung in den SQL-Textbereich ein.  
  
    ```  
    SELECT DISTINCT WageType, Shift,   
    AVG(Orders) as AvgOrders, MIN(Orders) as MinOrders, MAX(Orders) as MaxOrders,  
    AVG(Calls) as AvgCalls, MIN(Calls) as MinCalls, MAX(Calls) as MaxCalls,  
    AVG(LevelTwoOperators) as AvgOperators, MIN(LevelTwoOperators) as MinOperators, MAX(LevelTwoOperators) as MaxOperators,  
    AVG(IssuesRaised) as AvgIssues, MIN(IssuesRaised) as MinIssues, MAX(IssuesRaised) as MaxIssues  
    FROM dbo.FactCallCenter  
    GROUP BY Shift, WageType  
    ```  
  
8.  Klicken Sie im Entwurfs Bereich mit der rechten Maustaste auf die Tabelle, wechseln Sie zum Callcenter, und wählen Sie **Daten durchsuchen** aus, um eine Vorschau der von der T-SQL-Abfrage zurückgegebenen Daten anzuzeigen.  
  
9. Klicken Sie mit der rechten Maustaste auf die Registerkarte **Verschiebungen. DSV (Entwurf),** und klicken Sie dann auf **Speichern** , um die neue Datenquellen Sicht-Definition zu speichern.  
  
### <a name="predicting-service-metrics-for-each-shift"></a>Vorhersagen der Dienstmetrik für jede Schicht  
 Nachdem Sie nun einige Werte für jede Schicht generiert haben, verwenden Sie diese Werte als Eingabe für das logistische Regressionsmodell, das Sie erstellt haben, um Vorhersagen für die weitere Geschäftsplanung zu generieren.  
  
##### <a name="to-use-the-new-dsv-as-input-to-a-prediction-query"></a>So verwenden Sie die neue DSV als Eingabe für eine Vorhersageabfrage  
  
1.  Klicken Sie im Data Mining-Designer auf die Registerkarte **Mining Modellvorhersage** .  
  
2.  Klicken Sie im Bereich **Mining Modell** auf **Modell auswählen**, und wählen Sie in der Liste der verfügbaren Modelle die Option Callcenter-LR aus.  
  
3.  Deaktivieren Sie im Menü **Mining Modell** die Option **Singleton-Abfrage**. Eine Warnung weist Sie darauf hin, dass die Eingaben für die SINGLETON-Abfrage verloren gehen. Klicken Sie auf **OK**.  
  
     Das Dialogfeld **Singleton-Abfrage Eingabe** wird durch das Dialogfeld **Eingabe Tabelle (n) auswählen** ersetzt.  
  
4.  Klicken Sie auf **Falltabelle auswählen**.  
  
5.  Wählen Sie im Dialogfeld **Tabelle auswählen** aus der Liste der Datenquellen aus. Wählen Sie in der Liste **Tabellen-/Sichtname** die Option Verschiebungen für Callcenter (möglicherweise automatisch ausgewählt) aus, und klicken Sie dann auf **OK.**  
  
     Die Entwurfs Oberfläche **Mining Modellvorhersage** wird aktualisiert und zeigt die Zuordnungen an, die basierend auf den Namen und Datentypen der Spalten in den Eingabedaten und im Modell erstellt werden.  
  
6.  Klicken Sie mit der rechten Maustaste auf eine der joinlinien, und wählen Sie dann **Verbindungen ändern**aus.  
  
     In diesem Dialogfeld können Sie genau sehen, welche Spalten zugeordnet werden und welche nicht. Das Miningmodell enthält Spalten für Calls, Orders, IssuesRaised und LvlTwoOperators, die Sie beliebig den Aggregaten zuordnen können, die Sie basierend auf diesen Spalten in den Quelldaten erstellt haben. In diesem Szenario nehmen Sie eine Zuordnung zu den Mittelwerten vor.  
  
7.  Klicken Sie auf die leere Zelle neben LevelTwoOperators, und wählen Sie **Verschiebungen für Callcenter. AvgOperators aus**.  
  
8.  Klicken Sie auf die leere Zelle neben Aufrufe, und wählen Sie **Verschiebungen für Callcenter. AvgCalls aus**. ein, und klicken Sie dann auf **OK**.  
  
##### <a name="to-create-the-predictions-for-each-shift"></a>So erstellen Sie die Vorhersagen für jede Schicht  
  
1.  Klicken Sie im Raster in der unteren Hälfte der **Vorhersage Abfrage-Generator**auf die leere Zelle unter **Quelle,** und wählen Sie dann Verschiebungen für Callcenter aus.  
  
2.  Wählen Sie in der leeren Zelle unter **Feld**die Option Shift aus.  
  
3.  Klicken Sie auf die nächste leere Zeile im Raster und wiederholen Sie die oben beschriebene Prozedur, um eine weitere Zeile für WageType hinzuzufügen.  
  
4.  Klicken Sie auf die nächste leere Zeile im Raster. Wählen Sie in der Spalte **Quelle** die Option **Vorhersagefunktion**aus. Wählen Sie in der Spalte **Feld** die Option **Vorhersagen**aus.  
  
5.  Ziehen Sie die Spalte Service Grade aus dem Bereich **Mining Modell** in das Raster und in die Zelle **Kriterium/Argument** . Geben Sie im Feld **Alias** den Wert **vorhergesagte Dienst Qualität**ein.  
  
6.  Klicken Sie auf die nächste leere Zeile im Raster. Wählen Sie in der Spalte **Quelle** die Option **Vorhersagefunktion**aus. Wählen Sie in der Spalte **Feld** die Option **prätwahrscheinlichkeit**aus.  
  
7.  Ziehen Sie die Spalte Service Grade aus dem Bereich **Mining Modell** in das Raster und in die Zelle **Kriterium/Argument** . Geben Sie im Feld **Alias** den Wert **Wahrscheinlichkeit**ein.  
  
8.  Klicken Sie auf **zur Abfrageergebnis Sicht wechseln** , um die Vorhersagen anzuzeigen.  
  
 In der folgenden Tabelle werden Beispielergebnisse für jede Schicht angezeigt.  
  
|Shift|WageType|Predicted Service Grade|Probability|  
|-----------|--------------|-----------------------------|-----------------|  
|AM|holiday|0,165|0,377520666|  
|midnight|holiday|0,105|0,364105573|  
|PM1|holiday|0,165|0,40056055|  
|PM2|holiday|0,165|0,338532973|  
|AM|weekday|0,165|0,370847617|  
|midnight|weekday|0.08|0,352999173|  
|PM1|weekday|0,165|0,317419177|  
|PM2|weekday|0,105|0,311672027|  
  
### <a name="predicting-the-effect-of-reduced-response-time-on-service-grade"></a>Vorhersagen zu den Auswirkungen kürzerer Antwortzeiten auf die Dienstqualität  
 Sie haben mehrere Durchschnittswerte für jede Schicht generiert und diese Werte als Eingaben für das logistische Regressionsmodell verwendet. Da als Geschäftsziel jedoch eine Abbruchrate zwischen 0,00 und 0,05 vorgegeben ist, sind die Ergebnisse nicht sehr ermutigend.  
  
 Vom Betriebsteam wird daher beschlossen, einige Vorhersagen auf der Grundlage des ursprünglichen Modells auszuführen, das gezeigt hat, dass sich die Antwortzeit stark auf die Dienstqualität auswirkt. Mit diesen Vorhersagen soll untersucht werden, ob durch eine Verkürzung der durchschnittlichen Antwortzeit für Anrufe die Dienstqualität verbessert werden kann. Was geschieht beispielsweise mit den Werten für Dienstqualität, wenn die Antwortzeit auf 90 Prozent oder sogar 80 Prozent der aktuellen Antwortzeit verkürzt wird?  
  
 Es ist einfach, eine Datenquellensicht (Data Source View, DSV) zu erstellen, die die durchschnittlichen Antwortzeiten für jede Schicht berechnet, und dann Spalten hinzuzufügen, die einen Prozentsatz von 80% oder 90% dieser durchschnittlichen Antwortzeit berechnen. Sie können dann die DSV als Eingabe für das Modell verwenden.  
  
 Auch wenn die genauen Schritte nicht hier gezeigt werden, vergleicht die folgende Tabelle die Auswirkungen auf Dienstqualität, wenn Sie Antwortzeiten auf 80% oder 90% aktueller Antwortzeiten reduzieren.  
  
 Aus diesen Ergebnissen können Sie schließen, dass Sie die Antwortzeit in bestimmten Schichten auf 90 Prozent der aktuellen Rate reduzieren sollten, um die Dienstqualität zu verbessern.  
  
|Schicht, Lohn und Tag|Vorhergesagte Dienstqualität bei aktueller Durchschnittsantwortzeit|Vorhergesagte Dienst Qualität mit einer Verringerung der Antwortzeit von 90%|Vorhergesagte Dienstqualität bei Reduzierung der Antwortzeit auf 80 Prozent|  
|--------------------------|------------------------------------------------------------------|--------------------------------------------------------------------------|--------------------------------------------------------------------------|  
|Feiertag Vormittag|0,165|0.05|0.05|  
|Feiertag Nachmittag 1|0.05|0.05|0.05|  
|Feiertag Nacht|0,165|0.05|0.05|  
  
 Es gibt eine Vielzahl anderer Vorhersageabfragen, die Sie für dieses Modell erstellen können. Sie können zum Beispiel vorhersagen, wie viele Telefonisten erforderlich sind, um eine bestimmte Dienstqualität zu erreichen oder um eine bestimmte Anzahl von eingehenden Aufrufen entgegenzunehmen. Da Sie in einem logistischen Regressionsmodell mehrere Ausgaben einschließen können, ist es leicht, mit verschiedenen unabhängigen Variablen und Ergebnissen zu experimentieren, ohne mehrere separate Modelle erstellen zu müssen.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Data Mining-Add-Ins für Excel 2007 stellen einen Logistic Regression-Assistenten bereit, mit dem komplexe Fragen einfach beantwortet werden können, beispielsweise wie viele Operatoren der Ebene 2 benötigt werden, um die Dienstqualität für eine bestimmte Schicht auf ein Zielniveau anzuheben. Die Data Mining-Add-Ins können kostenlos heruntergeladen werden und enthalten Assistenten, die auf dem neuronalen Netzwerk oder den Logistic Regression-Algorithmen basieren. Weitere Informationen finden Sie unter den folgenden Links:  
  
-   [SQL Server 2005 Data Mining-Add-Ins für Office 2007](https://www.microsoft.com/sql/technologies/dm/addins.mspx): Zielsuche und What if Szenarioanalyse  
  
-   [SQL Server 2008 Data Mining-Add-Ins für Office 2007](https://go.microsoft.com/fwlink/?LinkID=117790): Analyse von zielsuchszenarios, What if Szenarioanalyse und Vorhersagerechner  
  
## <a name="conclusion"></a>Zusammenfassung  
 Sie haben gelernt, Miningmodelle zu erstellen, anzupassen und zu interpretieren, die auf dem Microsoft Neural Network-Algorithmus und dem Microsoft Logistic Regression-Algorithmus basieren. Diese Modelltypen bieten sehr umfassende Möglichkeiten und erlauben nahezu unendlich viele Variationen bei der Analyse. Ihre Verwendung kann daher komplex und schwierig sein.  
  
 Diese Algorithmen können jedoch viele Kombinationen von Faktoren durcharbeigten und automatisch die stärksten Korrelationen identifizieren. Sie bieten statistische Unterstützung für Erkenntnisse, zu denen Sie bei manuellem Durchsuchen von Daten mit Transact-SQL oder sogar PowerPivot kaum gelangen würden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Logistische Regressionsmodell-Abfrage Beispiele](../../2014/analysis-services/data-mining/logistic-regression-model-query-examples.md)   
 [Microsoft Logistic Regression-Algorithmus](../../2014/analysis-services/data-mining/microsoft-logistic-regression-algorithm.md)   
 [Microsoft Neural Network-Algorithmus](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm.md)   
 [Neuronale Beispiele für Netzwerkmodellabfragen](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)  
  
  
