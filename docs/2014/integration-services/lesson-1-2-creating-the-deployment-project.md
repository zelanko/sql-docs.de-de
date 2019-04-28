---
title: 'Schritt 2: Erstellen des Bereitstellungsprojekts | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 59990fe2-7036-4e9c-8efc-6ece9e66eda7
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6f5b0cc2c86ef483a7e2b2c0f5dccba21383641f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62891847"
---
# <a name="step-2-creating-the-deployment-project"></a>Schritt 2: Erstellen des Bereitstellungsprojekts
  In [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]ist die bereitstellbare Einheit ein [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt. Bevor Sie Pakete bereitstellen können, müssen Sie ein neues [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt erstellen und diesem Projekt alle Pakete und Hilfsdateien hinzufügen, die mit den Paketen bereitgestellt werden sollen.  
  
### <a name="to-create-the-integration-services-project"></a>So erstellen Sie das Integration Services-Projekt  
  
1.  Klicken Sie auf **Start**und zeigen sie auf **Alle Programme**. Klicken Sie nun auf **Microsoft SQL Server**und anschließend auf **SQL Server Data Tools**.  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie anschließend auf **Projekt** , um ein neues [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt zu erstellen.  
  
3.  Wählen Sie im Bereich **Vorlagen** des Dialogfelds **Neues Projekt** die Option **Integration Services-Projekt** aus.  
  
4.  Ändern Sie im Feld **Name** den Standardnamen in **Deployment Tutorial**. Deaktivieren Sie optional das Kontrollkästchen **Projektmappenverzeichnis erstellen** .  
  
5.  Übernehmen Sie den Standardspeicherort, oder klicken Sie auf **Durchsuchen** , um nach dem gewünschten Ordner zu suchen.  
  
6.  Klicken Sie im Dialogfeld **Projektspeicherort** auf den Ordner und anschließend auf **Öffnen**.  
  
7.  Klicken Sie auf **OK**.  
  
8.  Standardmäßig wird ein leeres Paket mit dem Namen Package.dtsx erstellt und dem Projekt hinzugefügt. Sie verwenden dieses Paket jedoch nicht, sondern fügen dem Projekt vorhandene Pakete hinzu. Da alle Pakete in einem Projekt bei der Bereitstellung berücksichtigt werden, sollten Sie Package.dtsx löschen. Klicken Sie dazu mit der rechten Maustaste auf das Paket und anschließend auf **Löschen**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Schritt 3: Hinzufügen von Paketen und weiteren Dateien](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
![Integration Services (kleines Symbol)](media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Integration Services-Projekte &#40;SSIS&#41;](integration-services-ssis-projects-and-solutions.md)  
  
  
