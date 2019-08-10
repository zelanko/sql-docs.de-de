---
title: Hinzufügen einer Datenquellen Sicht für Callcenterdaten (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
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
ms.openlocfilehash: 04f930c42b0e41a9f10b35d10295a38e8dac7490
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68888684"
---
# <a name="adding-a-data-source-view-for-call-center-data-intermediate-data-mining-tutorial"></a>Hinzufügen einer Datenquellensicht für Callcenterdaten (Data Mining-Lernprogramm für Fortgeschrittene)
  In dieser Aufgabe fügen Sie eine Datenquellensicht hinzu, mit der auf Callcenterdaten zugegriffen wird. Die gleichen Daten werden verwendet, um sowohl das ursprüngliche neuronale Netzwerkmodell zum Durchsuchen als auch das logistische Regressionsmodell zum Schreiben von Empfehlungen zu erstellen.  
  
 Sie verwenden den Datenquellensicht-Designer auch dazu, eine Spalte für den Wochentag hinzuzufügen. Dies ist hilfreich, da Sie aus Erfahrung wissen, dass sich Muster im Hinblick auf Anfrufaufkommen wie auch Dienstqualität wiederholen, die den Rhythmus von Werktagen und Wochenende wiederspiegeln, auch wenn die Quelldaten alle Callcenterdaten nach Datum verfolgen.  
  
## <a name="procedures"></a>Vorgehensweisen  
  
#### <a name="to-add-a-data-source-view"></a>So fügen Sie eine Datenquellensicht hinzu  
  
1.  Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf **Datenquellen Sichten**, und wählen Sie **neue Datenquellen Sicht**aus.  
  
     Der Datenquellensicht-Assistent wird geöffnet.  
  
2.  Klicken Sie auf der Seite **Willkommen beim Datenquellensicht-Assistenten** auf **Weiter**.  
  
3.  Wählen Sie auf der Seite **Datenquelle auswählen** unter **relationale Datenquellen**die [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] Datenquelle aus. Wenn Sie nicht über diese Datenquelle verfügen, finden Sie weitere Informationen unter [Tutorial zu Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md). Klicken Sie auf **Weiter**.  
  
4.  Wählen Sie auf der Seite **Tabellen und Sichten auswählen** die folgende Tabelle aus, und klicken Sie dann auf den Pfeil nach rechts, um Sie der Datenquellen Sicht hinzuzufügen:  
  
    -   **FactCallCenter (dbo)**  
  
    -   **DimDate**  
  
5.  Klicken Sie auf **Weiter**.  
  
6.  Auf der Seite **Assistenten abschließen** wird die Datenquellen Sicht standardmäßig benannt [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]. Ändern Sie den Namen in **Callcenter**, und klicken Sie dann auf **Fertig**stellen.  
  
     Der Datenquellen Sicht-Designer wird geöffnet, um die **Callcenter** -Datenquellen Sicht anzuzeigen.  
  
7.  Klicken Sie mit der rechten Maustaste in den Bereich Datenquellen Sicht, und wählen Sie **Tabellen hinzufügen/entfernen**aus. Wählen Sie die Tabelle **DimDate** aus, und klicken Sie auf **OK**.  
  
     Zwischen den `DateKey` Spalten in jeder Tabelle sollte automatisch eine Beziehung hinzugefügt werden. Sie verwenden diese Beziehung, um die Spalte " **englischen daynameofweek**" aus der Tabelle " **DimDate** " zu erhalten und in Ihrem Modell zu verwenden.  
  
8.  Klicken Sie im Datenquellen Sicht-Designer mit der rechten Maustaste auf die Tabelle **FactCallCenter**, und wählen Sie **neue benannte Berechnung**aus.  
  
     Geben Sie im Dialogfeld **benannte Berechnung erstellen** die folgenden Werte ein:  
  
    |||  
    |-|-|  
    |**Spaltenname**|DayOfWeek (TagderWoche)|  
    |**Beschreibung**|Abrufen des Wochentags aus der DimDate-Tabelle|  
    |**expression**|`(SELECT EnglishDayNameOfWeek AS DayOfWeek FROM DimDate where FactCallCenter.DateKey = DimDate.DateKey)`|  
  
     Um zu überprüfen, ob der Ausdruck die benötigten Daten erstellt, klicken Sie mit der rechten Maustaste auf die Tabelle **FactCallCenter**, und wählen Sie dann **Daten durchsuchen**aus.  
  
9. Nehmen Sie sich kurz Zeit, die verfügbaren Daten durchzusehen, um ihre Verwendung im Data Mining besser verstehen zu können:  
  
|Spaltenname|Enthält|  
|-----------------|--------------|  
|FactCallCenterID|Ein beim Importieren der Daten in das Data Warehouse erstellter willkürlicher Schlüssel.<br /><br /> Diese Spalte identifiziert eindeutige Datensätze und sollte als Fallschlüssel für das Data Mining-Modell verwendet werden.|  
|DateKey|Das Datum des Callcentervorgangs, ausgedrückt als ganze Zahl. Ganzzahlige Datumsschlüssel werden oft in Data Warehouses verwendet. Möglicherweise möchten Sie diese Daten für die Gruppierung nach Datumswerten aber im Format Datum/Uhrzeit abrufen.<br /><br /> Beachten Sie, dass Datumsangaben nicht eindeutig sind, da der Hersteller einen separaten Bericht für jede einzelne Schicht eines Arbeitstages ausgibt.|  
|WageType|Gibt an, ob der Tag ein Wochentag, ein Wochenende oder ein Feiertag ist.<br /><br /> Es ist möglich, dass es einen Unterschied in der Quality of Customer Service am Wochenende gegenüber Wochentagen gibt, sodass Sie diese Spalte als Eingabe verwenden.|  
|Shift|Gibt die Schicht an, für die Anrufe aufgezeichnet werden. Dieser Callcenter teilt den Arbeitstag in vier Verschiebungen auf: AM, PM1, PM2 und Mitternacht.<br /><br /> Es ist möglich, dass die Schicht die Qualität des Kundendiensts beeinflusst. Daher verwenden Sie diese Spalte als Eingabe.|  
|LevelOneOperators|Gibt die Anzahl der Operatoren auf Ebene 1 an.<br /><br /> Callcenter-Mitarbeiter beginnen auf Ebene 1; diese Mitarbeiter sind also nicht sehr erfahren.|  
|LevelTwoOperators|Gibt die Anzahl der arbeitenden Operatoren auf Ebene 2 an.<br /><br /> Ein Mitarbeiter muss eine bestimmte Anzahl von Arbeitsstunden protokollieren, um sich als Operator auf Ebene 2 zu qualifizieren.|  
|TotalOperators|Die Gesamtzahl der arbeitenden Telefonisten während der Schicht.|  
|Aufrufe|Anzahl der Anrufe, die während der Schicht empfangen werden.|  
|AutomaticResponses|Die Anzahl der Anrufe, die vollständig über die automatisierte Anrufabwicklung (Interactive Voice Response, IVR) bearbeitet wurden.|  
|Orders|Die Anzahl der Aufträge, die durch die Anrufe abgeschlossen wurden.|  
|IssuesRaised|Die Anzahl der Probleme, die aus Anrufen hervorgingen und einer Nachbearbeitung bedürfen.|  
|AverageTimePerIssue|Die durchschnittliche Zeit, die erforderlich ist, um einen eingehenden Anruf zu bearbeiten.|  
|ServiceGrade|Eine Metrik, die die allgemeine Quality of Service angibt, gemessen als Abbruch *Rate* für die gesamte Schicht. Je höher die Abbruchrate, desto wahrscheinlicher ist es, dass Kunden unzufrieden sind und potenzielle Aufträge verloren gehen.|  
  
 Beachten Sie, dass die Daten vier verschiedene Spalten enthalten, die auf einer einzelnen Datums Spalte `WageType`basieren:, **dayospweek** `Shift`, `DateKey`und. Gewöhnlich ist es beim Data Mining nicht empfehlenswert, mehrere von den gleichen Daten abgeleitete Spalten zu verwenden, da die Werte zu stark miteinander korrelieren und so andere Muster verdecken können.  
  
 Im Modell wird jedoch nicht verwendet `DateKey` , da es zu viele eindeutige Werte enthält. Es gibt keine direkte Beziehung zwischen `Shift` und **dayof** `WageType` Week, und und **dayof Week** sind nur teilweise verwandt. Wenn Ihnen die Kollinearität Sorgen bereitet, könnten Sie die Struktur mit allen verfügbaren Spalten erstellen und dann in jedem Modell andere Spalten ignorieren und die Auswirkungen überprüfen.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Erstellen einer neuronalen Netzwerkstruktur und &#40;eines Data Mining-Data Mining-Lernprogramms&#41;](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellsichten in mehrdimensionalen Modellen](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
