---
title: Ausreißer (SQL Server Data Mining-Add-Ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
ms.openlocfilehash: 3043c8f63433396f059f5c456512ad4ba2bffd93
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66072136"
---
# <a name="outliers-sql-server-data-mining-add-ins"></a>Ausreißer (SQL Server Data Mining-Add-Ins)
  ![Ausreißer-Assistent (Data Mining-Menüband)](media/dmc-outliers.gif "Ausreißer-Assistent (Data Mining-Menüband)")  
  
 Ein *Ausreißer* bedeutet einen Datenwert, der aus einem der folgenden Gründe problematisch ist:  
  
-   Der Wert liegt außerhalb des erwarteten Bereichs.  
  
-   Daten wurden möglicherweise falsch eingegeben.  
  
-   Der Wert fehlt.  
  
-   Daten enthalten ein Leerzeichen oder eine andere NULL-Zeichenfolge.  
  
-   Der Wert ist genau, liegt aber so weit außerhalb der Verteilung, dass er das Modell erheblich beeinträchtigen kann.  
  
 Mit dem Data Mining-Client für Excel können Sie diese Daten ermitteln und dann die Werte aktualisieren oder unterdrücken. Sie können z. B. Ausreißer durch ein arithmetisches Mittel ersetzen oder die Zeilen löschen, die potentiell falsche Werte enthalten.  
  
## <a name="handling-outliers"></a>Ausreißerbehandlung  
 Der **ausreißerentfernungs** -Assistent bietet mehrere Tools, mit denen Ausreißer entsprechend behandelt werden können:  
  
-   Zunächst können Sie die Daten untersuchen, um die Verteilung von Werten und die Beziehung zwischen Ausreißern und anderen Daten besser zu verstehen.  
  
     Beispielsweise können Sie den Task " **Daten durchsuchen** " verwenden, um die Werte zu überprüfen und zu korrigieren. Der **ausreißerentfernungs** -Assistent zeigt außerdem ein Diagramm an, entweder ein Linien-oder Balkendiagramm, um Ihnen das Verständnis der Verteilung aller Werte zu erleichtern.  
  
-   Als nächstes können Sie mit dem **ausreißerausreißerassistenten** Ausreißer entfernen oder ändern. Die zu verwendende Methode hängt davon ab, ob die Werte diskret oder kontinuierlich sind.  
  
     Der Assistent stellt diskrete Werte in einem Balkendiagramm dar, wobei jeder Balken für einen bestimmten Wert und die Höhe des Balkens für die Anzahl der Fälle für jeden Wert steht. Durch Bewegen des Schwellenwert-Schiebereglers im Diagramm können Sie die Balken verkürzen, die Gruppen mit ungewöhnlichen oder potentiell schlechten Werten darstellen.  
  
-   Der Assistent zeigt kontinuierliche Werte entweder in einem Balkendiagramm oder in einem Liniendiagramm an. Im Liniendiagramm wird der Wert auf der X-Achse und die Anzahl der Werte auf der Y-Achse dargestellt.  
  
     Sie können steuern, ob die Werte am unteren und am Ende des Diagramms entfernt oder beibehalten werden sollen, indem Sie die **minimalen** und **maximalen** Werte ändern oder die Balken verschieben. Beim Ändern der Minimum- und Maximumwerte werden die unterdrückten Daten im Diagramm schattiert dargestellt.  
  
 Nachdem Sie ausgewählt haben, mit welchen Ausreißern Sie arbeiten möchten, können Sie im Assistenten festlegen, wie die Ausreißer verarbeitet werden sollen. Sie können die Zeilen mit den Ausreißerwerten löschen oder einen Ersatzwert angeben, wie z. B. einen Mittelwert, eine Null oder einen anderen Wert Ihrer Wahl.  
  
 Schließlich bietet der Assistent einige Optionen zum Anzeigen der neuen Daten. Sie können die ursprünglichen Daten durch die neuen Werte ersetzen, der Tabelle eine neue Spalte mit den neuen Werten hinzufügen oder ein neues Arbeitsblatt erstellen, das die aktualisierten Daten enthält.  
  
### <a name="using-the-outlier-wizard"></a>Verwenden des Ausreißerentfernungs-Assistenten  
  
1.  Klicken Sie im **Data Mining** -Menüband auf **Daten bereinigen**, und wählen Sie **Ausreißer**aus.  
  
2.  Wählen Sie im Dialogfeld **Quelldaten auswählen** eine Excel-Datentabelle oder einen Zellbereich aus, und klicken Sie auf **weiter**.  
  
    > [!WARNING]  
    >  Sie können den **Ausreißer** -Assistenten nicht für externe Daten verwenden, es sei denn, Sie kopieren ihn zuerst in Excel.  
  
3.  Wählen Sie im Dialogfeld **Spalte auswählen** eine **einzelne** Spalte aus.  
  
     Klicken Sie auf **Weiter**.  
  
4.  Überprüfen Sie im Dialogfeld **Schwellenwerte angeben** die Verteilung der Daten.  
  
    -   Wenn die Spalte diskrete Werte enthält, zeigt der Assistent ein Histogramm an, das die Anzahl für jeden diskreten Wert enthält.  
  
         Wenn es sich bei Ausreißern um seltene Werte handelt, können Sie diese filtern, indem Sie den **Minimal** Wert ändern.  
  
    -   Wenn die Spalte numerische Daten enthält, können Sie auf die Schaltfläche **als diskret anzeigen** oder auf die Schaltfläche **als numerisch anzeigen** klicken, um zwischen dem Anzeigen der Werte in einem Balkendiagramm oder einem Liniendiagramm zu wechseln.  
  
5.  Wählen Sie im Dialogfeld **Schwellenwerte angeben** den Datenbereich aus, den Sie aufbewahren möchten, indem Sie einen minimal-und Höchstwert eingeben, oder indem Sie die Schieberegler ziehen. Klicken Sie auf **Weiter**.  
  
6.  Geben Sie im Dialogfeld **ausreißerbehandlung** an, ob die Werte gelöscht oder ersetzt werden sollen, und klicken Sie auf **weiter**.  
  
7.  Geben Sie im Dialogfeld **Ziel auswählen** an, wo die neuen Daten gespeichert werden sollen.  
  
### <a name="related-options"></a>Zugehörige Optionen  
 Der Assistent bietet folgende Optionen:  
  
|**Optionen**|**Comment**|  
|-----------------|-----------------|  
|**Spalte auswählen**|Sie können nur mit jeweils einer Spalte arbeiten.|  
|**Umgang mit Schwellenwerten angeben**|Legen Sie einen Schwellenwert mithilfe von **Minimal** fest, um Werte auszuschließen, die in weniger Zeilen als der Schwellenwert gefunden werden.<br /><br /> Anfänglich ist der Wert **Minimal** gleich dem Wert mit den wenigsten Zeilen, und Sie können den Minimalwert nicht unterschreiten.|  
|**Ausreißerbehandlung**|Wenn Sie Ausreißer löschen möchten, können Sie die Daten im aktuellen Arbeitsblatt ändern oder eine Kopie der Daten in einem neuen Arbeitsblatt erstellen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Durchsuchen von Daten &#40;SQL Server Data Mining-Add-ins&#41;](explore-data-sql-server-data-mining-add-ins.md)  
  
  
