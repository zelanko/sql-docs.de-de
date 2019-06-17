---
title: Hinzufügen einer Datenquellensicht für Callcenterdaten (Datamining-Lernprogramm für fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a448e7e4-dbd1-4d31-90bc-4d4a1c23b352
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 5da7978db04b0fdf6e1d4f7740857fc5c0cf90ed
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62823300"
---
# <a name="adding-a-data-source-view-for-call-center-data-intermediate-data-mining-tutorial"></a>Hinzufügen einer Datenquellensicht für Callcenterdaten (Data Mining-Lernprogramm für Fortgeschrittene)
  In dieser Aufgabe fügen Sie eine Datenquellensicht hinzu, mit der auf Callcenterdaten zugegriffen wird. Die gleichen Daten werden verwendet, um sowohl das ursprüngliche neuronale Netzwerkmodell zum Durchsuchen als auch das logistische Regressionsmodell zum Schreiben von Empfehlungen zu erstellen.  
  
 Sie verwenden den Datenquellensicht-Designer auch dazu, eine Spalte für den Wochentag hinzuzufügen. Dies ist hilfreich, da Sie aus Erfahrung wissen, dass sich Muster im Hinblick auf Anfrufaufkommen wie auch Dienstqualität wiederholen, die den Rhythmus von Werktagen und Wochenende wiederspiegeln, auch wenn die Quelldaten alle Callcenterdaten nach Datum verfolgen.  
  
## <a name="procedures"></a>Vorgehensweisen  
  
#### <a name="to-add-a-data-source-view"></a>So fügen Sie eine Datenquellensicht hinzu  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **Datenquellensichten**, und wählen Sie **neue Datenquellensicht**.  
  
     Der Datenquellensicht-Assistent wird geöffnet.  
  
2.  Klicken Sie auf der Seite **Willkommen beim Datenquellensicht-Assistenten** auf **Weiter**.  
  
3.  Auf der **Vybrat Zdroj DAT** Seite **relationale Datenquellen**, wählen die [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] -Datenquelle. Wenn Sie nicht über diese Datenquelle verfügen, finden Sie unter [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md). Klicken Sie auf **Weiter**.  
  
4.  Auf der **Tabellen und Sichten auswählen** Seite, wählen Sie in der folgende Tabelle aus, und klicken Sie dann auf den Pfeil nach rechts, um sie der Datenquellensicht hinzuzufügen:  
  
    -   **FactCallCenter (dbo)**  
  
    -   **DimDate**  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der **Abschließen des Assistenten** Seite standardmäßig den Namen die Datenquellensicht [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Ändern Sie den Namen in **CallCenter**, und klicken Sie dann auf **Fertig stellen**.  
  
     Datenquellensicht-Designer wird geöffnet und zeigt die **CallCenter** -Datenquellensicht.  
  
7.  Mit der rechten Maustaste im Bereich Datenquellensicht, und wählen **Tabellen hinzufügen/entfernen**. Wählen Sie die Tabelle, **DimDate** , und klicken Sie auf **OK**.  
  
     Eine Beziehung sollte zwischen automatisch hinzugefügt werden die `DateKey` Spalten in jeder Tabelle. Verwenden Sie diese Beziehung zum Abrufen der Spalte **EnglishDayNameOfWeek**, aus der **DimDate** Tabelle, und es in Ihr Modell verwenden.  
  
8.  Im Datenquellensicht-Designer mit der Maustaste in der Tabelle, **FactCallCenter**, und wählen Sie **neue benannte Berechnung**.  
  
     In der **benannte Berechnung erstellen** Dialogfeld geben die folgenden Werte:  
  
    |||  
    |-|-|  
    |**Spaltenname**|DayOfWeek (TagderWoche)|  
    |**Beschreibung**|Abrufen des Wochentags aus der DimDate-Tabelle|  
    |**expression**|`(SELECT EnglishDayNameOfWeek AS DayOfWeek FROM DimDate where FactCallCenter.DateKey = DimDate.DateKey)`|  
  
     Um sicherzustellen, dass der Ausdruck die Daten erstellt. Sie benötigen, mit der rechten Maustaste in der Tabelle **FactCallCenter**, und wählen Sie dann **Stichprobenoptionen**.  
  
9. Nehmen Sie sich kurz Zeit, die verfügbaren Daten durchzusehen, um ihre Verwendung im Data Mining besser verstehen zu können:  
  
|Spaltenname|Enthält|  
|-----------------|--------------|  
|FactCallCenterID|Ein beim Importieren der Daten in das Data Warehouse erstellter willkürlicher Schlüssel.<br /><br /> Diese Spalte identifiziert eindeutige Datensätze und sollte als Fallschlüssel für das Data Mining-Modell verwendet werden.|  
|DateKey|Das Datum des Callcentervorgangs, ausgedrückt als ganze Zahl. Ganzzahlige Datumsschlüssel werden oft in Data Warehouses verwendet. Möglicherweise möchten Sie diese Daten für die Gruppierung nach Datumswerten aber im Format Datum/Uhrzeit abrufen.<br /><br /> Beachten Sie, dass Datumsangaben nicht eindeutig sind, da der Hersteller einen separaten Bericht für jede einzelne Schicht eines Arbeitstages ausgibt.|  
|WageType|Gibt an, ob der Tag ein Arbeitstag, ein Wochenende oder ein Feiertag war.<br /><br /> Es ist möglich, dass es ein Unterschied in der Qualität des Kundendiensts an Wochenenden und Wochentage daher Sie diese Spalte als Eingabe verwenden.|  
|Shift|Gibt die Schicht an, für die Anrufe aufgezeichnet werden. Dieses Callcenter teilt den Arbeitstag in vier Schichten: Uhr, Mitternacht, Nachmittag 1 und PM2.<br /><br /> Es ist möglich, dass die Schicht die Qualität des Kundendiensts beeinflusst. Daher verwenden Sie diese Spalte als Eingabe.|  
|LevelOneOperators|Gibt die Anzahl der Ebene 1 arbeitenden Operatoren auf.<br /><br /> Callcenter-Mitarbeiter beginnen auf Ebene 1; diese Mitarbeiter sind also nicht sehr erfahren.|  
|LevelTwoOperators|Gibt die Anzahl der arbeitenden Operatoren auf Ebene 2 an.<br /><br /> Ein Mitarbeiter muss eine bestimmte Anzahl von Arbeitsstunden protokollieren, um sich als Operator auf Ebene 2 zu qualifizieren.|  
|TotalOperators|Die Gesamtzahl der arbeitenden Telefonisten während der Schicht.|  
|Aufrufe|Anzahl der Anrufe, die während der Schicht empfangen werden.|  
|AutomaticResponses|Die Anzahl der Anrufe, die vollständig über die automatisierte Anrufabwicklung (Interactive Voice Response, IVR) bearbeitet wurden.|  
|Orders|Die Anzahl der Aufträge, die durch die Anrufe abgeschlossen wurden.|  
|IssuesRaised|Die Anzahl der Probleme, die aus Anrufen hervorgingen und einer Nachbearbeitung bedürfen.|  
|AverageTimePerIssue|Die durchschnittliche Zeit, die erforderlich ist, um einen eingehenden Anruf zu bearbeiten.|  
|ServiceGrade|Eine Metrik, die die allgemeine Qualität der Dienst gibt an, gemessen als die *Abbruchrate* der gesamten Schicht misst. Je höher die Abbruchrate, desto wahrscheinlicher ist es, dass Kunden unzufrieden sind und potenzielle Aufträge verloren gehen.|  
  
 Beachten Sie, dass die Daten vier verschiedene Spalten enthalten, die auf einer einzelnen Datumsspalte basieren: `WageType`, **DayOfWeek**, `Shift`, und `DateKey`. Gewöhnlich ist es beim Data Mining nicht empfehlenswert, mehrere von den gleichen Daten abgeleitete Spalten zu verwenden, da die Werte zu stark miteinander korrelieren und so andere Muster verdecken können.  
  
 Allerdings werden nicht dazu verwendet `DateKey` im Modell, da er zu viele eindeutige Werte enthält. Es gibt keine direkte Beziehung zwischen `Shift` und **DayOfWeek**, und `WageType` und **DayOfWeek** beziehen sich nur teilweise. Wenn Ihnen die Kollinearität Sorgen bereitet, könnten Sie die Struktur mit allen verfügbaren Spalten erstellen und dann in jedem Modell andere Spalten ignorieren und die Auswirkungen überprüfen.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Erstellen einer Struktur des neuronalen Netzwerks und eines Warenkorbmodells &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellsichten in mehrdimensionalen Modellen](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
