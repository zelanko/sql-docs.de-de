---
title: Auswählen eines Genauigkeitsdiagrammtyps und festlegen Diagrammoptionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services]
- mining models [Analysis Services], validating
- classification accuracy [data mining]
- accuracy testing [data mining]
ms.assetid: bd24dd4a-624f-478a-9c94-b1361e857680
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 13d55fe9e4837bdacb248ddb63aad8b4064a88a9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48179770"
---
# <a name="choose-an-accuracy-chart-type-and-set-chart-options"></a>Auswählen eines Genauigkeitsdiagrammtyps Festlegen von Diagrammoptionen
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] stellt mehrere Methoden zum Bestimmen der Gültigkeit Ihrer Miningmodelle bereit. Der Typ des Genauigkeitsdiagramms, das Sie für jedes Modell oder jede Struktur erstellen können, hängt von diesen Faktoren ab:  
  
-   Dem Algorithmustyp, der verwendet wurde, um das Modell zu erstellen  
  
-   Dem Datentyp des vorhersagbaren Attributs  
  
-   Der Anzahl der zu messenden vorhersagbaren Attribute  
  
 In diesem Thema findet sich eine Übersicht über die verschiedenen Genauigkeitsdiagramme.  
  
 **Hinweis** Diagramme und ihre Definitionen werden nicht gespeichert. Wenn Sie das Fenster schließen, das ein Diagramm enthält, müssen Sie das Diagramm erneut erstellen.  
  
## <a name="accuracy-chart-types"></a>Genauigkeitsdiagrammtypen  
 Abhängig vom ausgewählten Diagrammtyp können Sie weitere Optionen konfigurieren, um das Diagramm zu durchsuchen oder das Diagramm in die Zwischenablage zu kopieren und mit den Daten in Excel zu arbeiten.  
  
#### <a name="lift-chart"></a>Prognosegütediagramm  
 Nachdem Sie die Optionen für das Modell konfiguriert und die Daten getestet haben, klicken Sie auf die Registerkarte **Prognosegütediagramm** , um die Ergebnisse anzuzeigen. Sie können das Diagramm auch in die Zwischenablage kopieren oder Details einzelner Trendlinien oder Datenpunkte in der Mininglegende anzeigen.  
  
#### <a name="profit-chart"></a>Gewinndiagramm  
 Nachdem Sie die Optionen für das Modell und die Testdaten konfiguriert haben, klicken Sie auf die Registerkarte **Prognosegütediagramm** , wählen Sie **Gewinndiagramm** in der Liste **Diagrammtyp** aus, um die Optionen für das Gewinndiagramm festzulegen, und klicken Sie anschließend auf **OK** , um die Ergebnisse anzuzeigen.  
  
 Sie können das Dialogfeld **Gewinndiagrammeinstellungen** beliebig oft verwenden, um verschiedene Kostenoptionen auszuprobieren und das Diagramm erneut anzuzeigen. Die Mininglegende enthält ausführliche Informationen über den geschätzten Gewinn für jedes Modell. Sie können auch das Diagramm und den Inhalt der Mininglegende in die Zwischenablage kopieren, um in Excel damit zu arbeiten.  
  
#### <a name="scatter-plot"></a>Punktdiagramm  
 Wenn Sie den entsprechenden Modelltyp ausgewählt haben, ist bei Klicken auf die Registerkarte **Prognosegütediagramm** als Diagrammtyp automatisch **Punktdiagramm** festgelegt, und ein Punktdiagramm wird angezeigt. Eine weitere Konfiguration ist nicht möglich. Sie können das Diagramm auch in die Zwischenablage kopieren und als Grafik in Excel oder in eine andere Anwendung einfügen.  
  
#### <a name="classification-matrix"></a>Klassifikationsmatrix  
 Für eine Klassifikationsmatrix wählen Sie auf der Registerkarte **Eingabeauswahl** die Modelle und Testdaten aus und klicken anschließend auf die Registerkarte **Klassifikationsmatrix** , um die Ergebnisse anzuzeigen.  
  
 Der Inhalt einer Klassifikationsmatrix ist bei allen Modelltypen gleich und kann nicht konfiguriert werden. Sie können die Daten im Diagramm in die Zwischenablage kopieren, um sie in Excel zu verwenden.  
  
#### <a name="cross-validation-report"></a>Bericht für die übergreifende Überprüfung  
 Um einen Kreuzvalidierungsbericht zu erstellen, wählen Sie zunächst eine Miningstruktur oder ein Miningmodell im Projektmappen-Explorer aus. Klicken Sie anschließend auf die Registerkarte **Kreuzvalidierung** , konfigurieren Sie alle relevanten Optionen, und klicken Sie dann auf **Ergebnisse abrufen** , um den Bericht zu generieren. Eine weitere Konfiguration ist nicht möglich.  
  
 Das Format des Kreuzvalidierungsberichts ist bei allen Modelltypen gleich und kann nicht konfiguriert werden. Der Inhalt des Berichts ist jedoch abhängig vom analysierten Modelltyp und vom Datentyp des vorhersagbaren Attributs unterschiedlich. Sie können die Ergebnisse des Berichts auch in die Zwischenablage kopieren, um in Excel mit den Daten zu arbeiten.  
  
  
