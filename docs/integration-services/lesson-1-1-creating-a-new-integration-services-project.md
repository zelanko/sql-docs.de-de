---
title: 'Schritt 1: Erstellen eines neuen Integration Services-Projekts | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/03/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 74e56788741b36e68884db823fa46eb24856081e
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "71296129"
---
# <a name="lesson-1-1-create-a-new-integration-services-project"></a>Lektion 1-1: Erstellen eines neuen SQL Server Integration Services-Projekts

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Der erste Schritt beim Erstellen eines Pakets in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ist das Erstellen eines [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekts. Dieses Beispielprojekt enthält Vorlagen für die Datenquellen, Datenquellensichten und Pakete, aus denen eine Datentransformationslösung besteht.  
  
Die Pakete, die Sie in diesem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Tutorial erstellen, interpretieren die Werte von gebietsschemabezogenen Daten. Wenn Ihr Computer nicht für die Verwendung der Ländereinstellung **Englisch (USA)** konfiguriert ist, müssen Sie zusätzliche Eigenschaften im Paket festlegen. 

Die Pakete, die Sie in den Lektionen 2 bis 6 verwenden, werden aus dem Paket kopiert, das Sie in dieser Lektion erstellen.  
  
> [!NOTE]  
> Machen Sie sich, falls noch nicht geschehen, mit den [Anforderungen für Lektion 1](../integration-services/lesson-1-create-a-project-and-basic-package-with-ssis.md#prerequisites) vertraut.

## <a name="create-a-new-integration-services-project"></a>Erstellen eines neuen SQL Server Integration Services-Projekts  
  
1.  Suchen Sie im Windows-**Startmenü** nach **Visual Studio (SSDT)** , und wählen Sie es aus.  
  
2.  Wählen Sie in Visual Studio den Befehl **Datei** > **Neu** > **Projekt** aus, um ein neues [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt zu erstellen.  
  
3.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Business Intelligence** unter **Installiert**, und wählen Sie im Bereich **Vorlagen** die Option **Integration Services-Projekt** aus.  
  
4.  Ändern Sie im Feld **Name** den Standardnamen in **SSIS Tutorial**. Um einen Ordner zu verwenden, der bereits vorhanden ist, deaktivieren Sie das Kontrollkästchen **Verzeichnis für Projektmappe erstellen**.  
  
5.  Übernehmen Sie den Standardspeicherort, oder wählen Sie **Durchsuchen** aus, um zu dem Ordner zu navigieren, den Sie verwenden möchten. Wählen Sie im Dialogfeld **Projektspeicherort** den Ordner und anschließend **Ordner auswählen** aus.  
  
6.  Klicken Sie auf **OK**.  
  
    Standardmäßig wird ein leeres Paket mit dem Namen **Package.dtsx** erstellt und Ihrem Projekt unter **SSIS-Pakete** hinzugefügt.  
  
7.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **Package.dtsx**, wählen Sie **Umbenennen** aus, und benennen Sie das Standardpaket in **Lesson 1.dtsx** um.  
  
## <a name="go-to-next-task"></a>Weiter zur nächsten Aufgabe
[Schritt 2: Hinzufügen und Konfigurieren eines Verbindungs-Managers für Flatfiles](../integration-services/lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
