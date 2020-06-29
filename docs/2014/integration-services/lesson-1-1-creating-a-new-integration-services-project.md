---
title: 'Schritt 1: Erstellen eines neuen Integration Services-Projekts | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c96b23a8807741429eaee00dace7c22f1cd540c5
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85436227"
---
# <a name="step-1-creating-a-new-integration-services-project"></a>Schritt 1: Erstellen eines neuen Integration Services-Projekts
  Der erste Schritt beim Erstellen eines Pakets in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ist das Erstellen eines [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekts. Dieses Projekt enthält die Vorlagen für die Objekte, die Sie in einer Datentransformationslösung verwenden: Datenquellen, Datenquellensichten und Pakete.  
  
 Die Pakete, die Sie in diesem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Lernprogramm erstellen, interpretieren die Werte gebietsschemabezogener Daten. Wenn Ihr Computer nicht für die Verwendung der Ländereinstellung Englisch (USA) konfiguriert ist, müssen Sie zusätzliche Eigenschaften im Paket festlegen. Die Pakete, die Sie in den Lektionen 2 bis 5 verwenden, werden aus dem in Lektion 1 erstellten Paket kopiert, sodass Sie keine gebietsschemabezogenen Eigenschaften in dem kopierten Paket aktualisieren müssen.  
  
> [!NOTE]  
>  Dieses Lernprogramm erfordert Microsoft SQL Server Data Tools.  
>   
>  Weitere Informationen zum Installieren von SQL Server Data Tools finden Sie unter [Herunterladen von SQL Server Data Tools](https://msdn.microsoft.com/data/hh297027).  
  
### <a name="to-create-a-new-integration-services-project"></a>So erstellen Sie ein neues Integration Services-Projekt  
  
1.  Zeigen Sie im Menü **Start** auf **Alle Programme**, dann auf **Microsoft SQL Server**, und klicken Sie auf **SQL Server Data Tools**.  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie auf **Projekt** , um ein neues [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt zu erstellen.  
  
3.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Business Intelligence** unter **Installierte Vorlagen**, und wählen Sie im Bereich **Vorlagen** die Option **Integration Services-Projekt** aus.  
  
4.  Ändern Sie im Feld **Name** den Standardnamen in **SSIS Tutorial**. Deaktivieren Sie optional das Kontrollkästchen **Projektmappenverzeichnis erstellen** .  
  
5.  Akzeptieren Sie den Standardspeicherort, oder klicken Sie auf **Durchsuchen** , um nach dem Ordner zu suchen, den Sie verwenden möchten. Klicken Sie im Dialogfeld **Projektspeicherort** auf den Ordner und anschließend auf **Ordner auswählen**.  
  
6.  Klicken Sie auf **OK**.  
  
     Standardmäßig wird ein leeres Paket mit dem Namen **Package.dtsx**erstellt und Ihrem Projekt unter SSIS-Pakete hinzugefügt.  
  
7.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Package.dtsx**, klicken Sie auf **Umbenennen**, und benennen Sie das Standardpaket in **Lesson 1.dtsx**um.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Schritt 2: Hinzufügen und Konfigurieren eines Verbindungs-Managers für Flatfiles](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
  
