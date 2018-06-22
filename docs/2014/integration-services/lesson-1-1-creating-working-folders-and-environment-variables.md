---
title: 'Schritt 1: Erstellen von Arbeitsordnern und Umgebungsvariablen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45091ba2-ea3d-4399-9814-489d812b42cc
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b28c191bb07ca9898c594de82dee6b27592786f9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056281"
---
# <a name="step-1-creating-working-folders-and-environment-variables"></a>Schritt 1: Erstellen von Arbeitsordnern und Umgebungsvariablen
  In dieser Aufgabe erstellen Sie den Arbeitsordner (C:\DeploymentTutorial) und die neuen Systemumgebungsvariablen (`DataTransfer` und `LoadXMLData`), die in späteren Lernprogrammaufgaben verwendet werden.  
  
 Der Arbeitsordner befindet sich im Stamm von Laufwerk C. Bei Bedarf können Sie ein anderes Laufwerk bzw. einen anderen Speicherort verwenden. Sie müssen sich diesen Speicherort jedoch notieren und immer dann verwenden, wenn im Lernprogramm auf den Speicherort des Arbeitsordners DeploymentTutorial verwiesen wird.  
  
 In einer späteren Lektion stellen Sie Pakete bereit, die im Dateisystem in der sysssispackages-Tabelle der msdb-Datenbank von[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] gespeichert werden. Idealerweise erfolgt die Bereitstellung der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Pakete auf einem anderen Computer. Falls dies nicht möglich ist, können Sie dennoch viel von diesem Lernprogramm profitieren, indem Sie die Pakete auf einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf dem lokalen Computer bereitstellen. Die Umgebungsvariablen, die auf dem lokalen Computer und dem Zielcomputer verwendet werden, weisen die gleichen Variablennamen auf, doch werden unterschiedliche Werte in den Variablen gespeichert. So verweist z. B. der Wert der `DataTransfer` -Umgebungsvariablen auf dem lokalen Computer auf den Ordner C:\DeploymentTutorial, während die `DataTransfer` -Umgebungsvariable auf dem Zielcomputer auf den Ordner C:\DeploymentTutorialInstall verweist.  
  
 Wenn Sie eine Bereitstellung auf dem lokalen Computer planen, müssen Sie nur einen Satz von Umgebungsvariablen erstellen. Es ist jedoch erforderlich, den Wert der Umgebungsvariablen vor der lokalen Bereitstellung auf einen geeigneten Wert zu aktualisieren.  
  
 Wenn Sie planen, die Pakete auf einem anderen Computer bereitzustellen, müssen Sie zwei Sätze von Umgebungsvariablen erstellen: einen Satz für den lokalen Computer und einen Satz für den Zielcomputer. Zum jetzigen Zeitpunkt können Sie nur die Variablen für den Quellcomputer erstellen. Die Variablen für den Zielcomputer müssen später erstellt werden. Sie können die Pakete jedoch erst auf dem Zielcomputer installieren, wenn sowohl der Ordner als auch die Umgebungsvariablen auf dem Zielcomputer verfügbar sind.  
  
### <a name="to-create-the-local-working-folder"></a>So erstellen Sie den lokalen Arbeitsordner  
  
1.  Klicken Sie mit der rechten Maustaste auf das Menü Start, und klicken Sie dann auf Suchen.  
  
2.  Klicken Sie auf **Lokaler Datenträger (C:)**.  
  
3.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie anschließend auf **Ordner**.  
  
4.  Neuen Ordner zum Umbenennen `DeploymentTutorial`.  
  
### <a name="to-create-local-environment-variables"></a>So erstellen Sie lokale Umgebungsvariablen  
  
1.  Klicken Sie im Menü **Start** auf **Systemsteuerung**.  
  
2.  Doppelklicken Sie in der Systemsteuerung auf **System**.  
  
3.  Klicken Sie im Dialogfeld **Systemeigenschaften** auf die Registerkarte **Erweitert** , und klicken Sie dann auf **Umgebungsvariablen**.  
  
4.  Klicken Sie im Dialogfeld **Umgebungsvariablen** im Bereich **Systemvariablen** auf **Neu**.  
  
5.  In der **neue Systemvariable** Geben Sie im Dialogfeld `DataTransfer` in der **Variablenname** Feld und `C:\DeploymentTutorial\datatransferconfig.dtsconfig` in der **Variablenwert** Feld.  
  
6.  Klicken Sie auf **OK**.  
  
7.  Klicken Sie auf **neu** erneut, und geben `LoadXMLData` in der **Variablenname** Feld und `C:\DeploymentTutorial\loadxmldataconfig.dtsconfig` in der **Variablenwert** Feld.  
  
8.  Klicken Sie auf **OK** , um das Dialogfeld **Umgebungsvariablen** zu beenden.  
  
9. Klicken Sie auf **OK** , um das Dialogfeld **Systemeigenschaften** zu beenden.  
  
10. Führen Sie optional einen Neustart des Computers aus. Wenn Sie den Computer nicht neu starten, wird der Name der neuen Variablen nicht im Paketkonfigurations-Assistenten angezeigt, kann jedoch verwendet werden.  
  
### <a name="to-create-destination-environment-variables"></a>So erstellen Sie Zielumgebungsvariablen  
  
1.  Klicken Sie im Menü **Start** auf **Systemsteuerung**.  
  
2.  Doppelklicken Sie in der Systemsteuerung auf **System**.  
  
3.  Klicken Sie im Dialogfeld **Systemeigenschaften** auf die Registerkarte **Erweitert** , und klicken Sie dann auf **Umgebungsvariablen**.  
  
4.  Klicken Sie im Dialogfeld **Umgebungsvariablen** unter **Systemvariablen** auf **Neu**.  
  
5.  In der **neue Systemvariablen** Geben Sie im Dialogfeld `DataTransfer` in der **Variablenname** Feld und `C:\DeploymentTutorialInstall\datatransferconfig.dtsconfig` in der **Variablenwert** Feld.  
  
6.  Klicken Sie auf **OK**.  
  
7.  Klicken Sie auf **neu** erneut, und geben `LoadXMLData` in der **Variablenname** Feld und `C:\DeploymentTutorialInstall\loadxmldataconfig.dtsconfig` in der **Variablenwert** Feld.  
  
8.  Klicken Sie auf **OK** , um das Dialogfeld **Umgebungsvariablen** zu beenden.  
  
9. Klicken Sie auf **OK** , um das Dialogfeld **Systemeigenschaften** zu beenden.  
  
10. Führen Sie optional einen Neustart des Computers aus.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Schritt 2: Erstellen des Bereitstellungsprojekts](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
![Integration Services (kleines Symbol)](media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben Sie mit Integration Services** <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
  