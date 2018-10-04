---
title: 'Schritt 1: Erstellen des Bereitstellungs-Hilfsprogramms | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 1ff4dcff-89b3-4b99-a725-5f7963e98abf
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b2bbae058a0e3ecacaa4be9204a822451e1a0602
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48216006"
---
# <a name="step-1-building-the-deployment-utility"></a>Schritt 1: Erstellen des Bereitstellungs-Hilfsprogramms
  In dieser Aufgabe konfigurieren und erstellen Sie ein Bereitstellungsprogramm für das Deployment Tutorial-Projekt.  
  
 Vor dem Erstellen des Bereitstellungshilfsprogramms müssen Sie die Eigenschaften des Deployment Tutorial-Projekts ändern. Sie können diese Eigenschaften im Dialogfeld **Deployment Tutorial-Eigenschaftenseiten** konfigurieren. In diesem Dialogfeld müssen Sie die Fähigkeit aktivieren, Konfigurationen während der Bereitstellung zu aktualisieren, und angeben, dass beim Erstellungsvorgang ein Bereitstellungshilfsprogramm generiert werden soll. Nach dem Festlegen der Eigenschaften erstellen Sie das Projekt.  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] stellt eine Reihe von Fenstern zum Debuggen von Paketen bereit. Sie können Fehler-, Warn- und Informationsmeldungen anzeigen, den Status von Paketen zur Laufzeit nachverfolgen oder den Fortschritt und die Ergebnisse von Erstellungsvorgängen anzeigen. In dieser Lektion verwenden Sie das Ausgabefenster, um den Fortschritt und die Ergebnisse beim Erstellen des Bereitstellungshilfsprogramms anzuzeigen.  
  
### <a name="to-set-the-deployment-utility-properties"></a>So legen Sie die Eigenschaften des Bereitstellungshilfsprogramms fest  
  
1.  Wenn [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] noch nicht geöffnet ist, klicken Sie auf **Start**, zeigen Sie auf **Alle Programme**, zeigen Sie auf **Microsoft SQL Server 2005**, und klicken Sie dann auf **Business Intelligence Development Studio**.  
  
2.  Klicken Sie im Menü **Datei** auf **Öffnen**&gt; **Projekt/Projektmappe**. Wählen Sie den Ordner **Deployment Tutorial** aus, klicken Sie auf **Öffnen**und anschließend doppelt auf **Deployment Tutorial.sln**.  
  
3.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf „Deployment Tutorial“ und anschließend auf **Eigenschaften**.  
  
4.  Erweitern Sie im Dialogfeld **Deployment Tutorial-Eigenschaftenseiten** den Knoten Konfigurationseigenschaften, und klicken Sie auf Bereitstellungshilfsprogramm.  
  
5.  Im rechten Bereich die **Deployment Tutorial-Eigenschaftenseiten** Dialogfeld überprüfen Sie, ob `AllowConfigurationChanges` nastaven NA hodnotu `true`legen `CreateDeploymentUtility` zu `true`, und aktualisieren Sie optional den Standardwert `DeploymentOutputPath`.  
  
6.  Klicken Sie auf **OK**.  
  
### <a name="to-build-the-deployment-utility"></a>So erstellen Sie das Bereitstellungshilfsprogramm  
  
1.  Klicken Sie im Projektmappen-Explorer auf **Deployment Tutorial**.  
  
2.  Klicken Sie im Menü **Ansicht** auf **Ausgabe**. Das Ausgabefenster befindet sich standardmäßig in der unteren linken Ecke von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
3.  Klicken Sie im Menü **Erstellen** auf **Deployment Tutorial erstellen**.  
  
4.  Überprüfen Sie im Ausgabefenster die folgenden Informationen:  
  
     Erstellung gestartet: SQL Integration Services-Projekt: Inkrementell ...  
  
     Bereitstellungshilfsprogramm wird erstellt...  
  
     Das Bereitstellungshilfsprogramm wurde erstellt.  
  
     Erstellung abgeschlossen -- 0 Fehler, 0 Warnungen  
  
     ========== Erstellen: 0 erfolgreich, Fehler bei 0, 1 aktuell, 0 übersprungen ==========  
  
5.  Klicken Sie im Menü **Datei** auf **Beenden**. Wenn Sie zum Speichern der Änderungen an Deployment Tutorial-Elementen aufgefordert werden, klicken Sie auf **Ja**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Schritt 2: Überprüfen des Bereitstellungspakets](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
![Integration Services (kleines Symbol)](media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Bereitstellungs-Hilfsprogramms](../../2014/integration-services/create-a-deployment-utility.md)  
  
  
