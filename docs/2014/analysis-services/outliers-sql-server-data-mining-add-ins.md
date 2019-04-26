---
title: Ausreißer (SQL Server Data Mining-Add-ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exceptions [data mining]
- data preparation
- outliers [data mining]
- data cleaning
ms.assetid: e6fa7c62-4005-4792-9211-3b699377a517
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0771c953875e9871c53892bc14a3e2a537060833
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62743621"
---
# <a name="outliers-sql-server-data-mining-add-ins"></a>Ausreißer (SQL Server Data Mining-Add-Ins)
  ![Ausreißer-Assistenten im Data Mining-Menüband](media/dmc-outliers.gif "Ausreißerentfernungs-Assistenten im Data Mining-Menüband")  
  
 Ein *Ausreißer* bedeutet, dass einen Datenwert, der für jede der folgenden Gründe problematisch ist:  
  
-   Der Wert liegt außerhalb des erwarteten Bereichs.  
  
-   Daten wurden möglicherweise falsch eingegeben.  
  
-   Der Wert fehlt.  
  
-   Daten enthalten ein Leerzeichen oder eine andere NULL-Zeichenfolge.  
  
-   Der Wert ist genau, liegt aber so weit außerhalb der Verteilung, dass er das Modell erheblich beeinträchtigen kann.  
  
 Mit dem Data Mining-Client für Excel können Sie diese Daten ermitteln und dann die Werte aktualisieren oder unterdrücken. Sie können z. B. Ausreißer durch ein arithmetisches Mittel ersetzen oder die Zeilen löschen, die potentiell falsche Werte enthalten.  
  
## <a name="handling-outliers"></a>Ausreißerbehandlung  
 Die **Ausreißerentfernungs** Assistent bietet mehrere Tools, um Ausreißer zu behandeln:  
  
-   Zunächst können Sie die Daten untersuchen, um die Verteilung von Werten und die Beziehung zwischen Ausreißern und anderen Daten besser zu verstehen.  
  
     Beispielsweise können Sie die **Stichprobenoptionen** Task, um zu überprüfen und beheben Sie die Werte. Die **Ausreißerentfernungs** Assistenten zeigt außerdem ein Diagramm, das entweder eine Linie oder ein Balkendiagramm, hilft Ihnen die Verteilung aller Werte zu verstehen.  
  
-   Als Nächstes können Sie die **Ausreißer** Assistenten, um Ausreißer entfernt oder geändert. Die zu verwendende Methode hängt davon ab, ob die Werte diskret oder kontinuierlich sind.  
  
     Der Assistent stellt diskrete Werte in einem Balkendiagramm dar, wobei jeder Balken für einen bestimmten Wert und die Höhe des Balkens für die Anzahl der Fälle für jeden Wert steht. Durch Bewegen des Schwellenwert-Schiebereglers im Diagramm können Sie die Balken verkürzen, die Gruppen mit ungewöhnlichen oder potentiell schlechten Werten darstellen.  
  
-   Der Assistent zeigt kontinuierliche Werte entweder in einem Balkendiagramm oder in einem Liniendiagramm an. Im Liniendiagramm wird der Wert auf der X-Achse und die Anzahl der Werte auf der Y-Achse dargestellt.  
  
     Sie können steuern, ob entfernt, oder behalten Sie die Werte am unteren und oberen Ende des Diagramms durch Ändern der **mindestens** und **maximale** Werte oder die Schieberegler. Beim Ändern der Minimum- und Maximumwerte werden die unterdrückten Daten im Diagramm schattiert dargestellt.  
  
 Nachdem Sie ausgewählt haben, mit welchen Ausreißern Sie arbeiten möchten, können Sie im Assistenten festlegen, wie die Ausreißer verarbeitet werden sollen. Sie können die Zeilen mit den Ausreißerwerten löschen oder einen Ersatzwert angeben, wie z. B. einen Mittelwert, eine Null oder einen anderen Wert Ihrer Wahl.  
  
 Schließlich bietet der Assistent einige Optionen zum Anzeigen der neuen Daten. Sie können die ursprünglichen Daten durch die neuen Werte ersetzen, der Tabelle eine neue Spalte mit den neuen Werten hinzufügen oder ein neues Arbeitsblatt erstellen, das die aktualisierten Daten enthält.  
  
### <a name="using-the-outlier-wizard"></a>Verwenden des Ausreißerentfernungs-Assistenten  
  
1.  In der **Data Mining** des Menübands, klicken Sie auf **Daten bereinigen**, und wählen Sie **Ausreißer**.  
  
2.  In der **Quelldaten auswählen** Dialogfeld Wählen Sie eine Excel-Datentabelle oder einen Bereich von Zellen, und klicken Sie auf **Weiter**.  
  
    > [!WARNING]  
    >  Sie können keine der **Ausreißer** Assistenten auf externe Daten, es sei denn, Sie ihn zunächst nach Excel kopieren.  
  
3.  In der **Spalte auswählen** wählen Sie im Dialogfeld eine **einzelne** Spalte.  
  
     Klicken Sie auf **Weiter**.  
  
4.  In der **Schwellenwerte angeben** Dialogfeld überprüfen Sie die Verteilung der Daten.  
  
    -   Wenn die Spalte diskrete Werte enthält, zeigt der Assistent ein Histogramm an, das die Anzahl für jeden diskreten Wert enthält.  
  
         Vorausgesetzt, dass Ausreißer selten auftreten, filtern, indem Sie ändern die **mindestens** Wert.  
  
    -   Wenn die Spalte numerische Daten enthält, können Sie klicken die **als diskrete Werte anzeigen** Schaltfläche oder die **als numerische Werte anzeigen** Schaltfläche zum Wechseln zwischen die Werten in einem Balken- oder Liniendiagramm anzeigen.  
  
5.  In der **Schwellenwerte angeben** Dialogfeld Wählen Sie den Bereich der Daten, die Sie einen minimalen und maximalen Wert eingeben, oder indem Sie die Schieberegler ziehen beibehalten möchten. Klicken Sie auf **Weiter**.  
  
6.  In der **Ausreißerbehandlung** Dialogfeld Feld angeben, ob die Werte gelöscht oder ersetzt werden sollen, und klicken Sie auf **Weiter**.  
  
7.  In der **Ziel auswählen** Dialogfeld geben die neuen Daten gespeichert werden sollen.  
  
### <a name="related-options"></a>Zugehörige Optionen  
 Der Assistent bietet folgende Optionen:  
  
|**Optionen**|**Anmerkung**|  
|-----------------|-----------------|  
|**Wählen Sie Spalte**|Sie können nur mit jeweils einer Spalte arbeiten.|  
|**Umgang mit Schwellenwerten angeben**|Legen Sie einen Schwellenwert mit **mindestens** um Werte auszuschließen, die in weniger Zeilen als der Schwellenwert gefunden werden.<br /><br /> Zunächst den Wert in **minimale** ist gleich dem Wert mit den wenigsten Zeilen, und Sie können nicht als das Minimum niedriger als dieser Wert.|  
|**Ausreißerbehandlung**|Wenn Sie Ausreißer löschen möchten, können Sie die Daten im aktuellen Arbeitsblatt ändern oder eine Kopie der Daten in einem neuen Arbeitsblatt erstellen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Durchsuchen von Daten &#40;SQL Server Data Mining-Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md)  
  
  
