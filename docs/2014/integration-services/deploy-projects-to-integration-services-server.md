---
title: Bereitstellen von Projekten auf Integration Services Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6e9402f4-4d50-49ff-820d-65a77829c4a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 186a0633b168c551514705a0494b63f080884373
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437487"
---
# <a name="deploy-projects-to-integration-services-server"></a>Deploy Projects to Integration Services Server
  In der aktuellen Version von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]können Sie Projekte auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server bereitstellen. Der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server ermöglicht es Ihnen, Pakete zu verwalten und auszuführen sowie mit Umgebungen Laufzeitwerte für Pakete zu konfigurieren.  
  
 Weitere Informationen zu Umgebungen finden Sie unter [Erstellen und Zuordnen einer Serverumgebung](../../2014/integration-services/create-and-map-a-server-environment.md).  
  
> [!NOTE]  
>  Wie in vorherigen Versionen von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]können Sie auch in der aktuellen Version Pakete auf einer SQL Server-Instanz bereitstellen und den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst zum Ausführen und Verwalten der Pakete verwenden. Sie verwenden das Paketbereitstellungsmodell. Weitere Informationen finden Sie unter [Paket Bereitstellung &#40;SSIS-&#41;](packages/legacy-package-deployment-ssis.md).  
  
 Um auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server ein Projekt bereitzustellen, führen Sie die folgenden Tasks aus:  
  
1.  Erstellen Sie einen SSISDB-Katalog, falls noch nicht geschehen. Weitere Informationen finden Sie unter [Erstellen des SSIS-Katalogs](catalog/ssis-catalog.md).  
  
2.  Konvertieren Sie das Projekt mit dem Assistenten für die Konvertierung von **Integration Services-Projekten** ins Projektbereitstellungsmodell. Weitere Informationen finden Sie in den folgenden Anweisungen: [So konvertieren Sie ein Projekt in das Projektbereitstellungsmodell](#convert).  
  
    -   Wenn Sie das Projekt in [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)]erstellt haben, verwendet das Projekt standardmäßig das Projektbereitstellungsmodell.  
  
    -   Wenn Sie das Projekt in einer früheren Version von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]erstellt haben, konvertieren Sie das Projekt nach dem Öffnen der Projektdatei in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]in das Projektbereitstellungsmodell.  
  
        > [!NOTE]  
        >  Wenn das Projekt mindestens eine Datenquelle enthält, werden die Datenquellen entfernt, wenn die Projektkonvertierung abgeschlossen wird. Fügen Sie einen Verbindungs-Manager auf Projektebene hinzu, um eine Verbindung mit einer Datenquelle herzustellen, die von den Paketen im Projekt gemeinsam genutzt werden kann. Weitere Informationen finden Sie unter [Hinzufügen, Löschen oder Freigeben eines Verbindungs-Managers in einem Paket](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)  
  
         Abhängig davon, ob Sie den Assistenten zum Konvertieren von **Integration Services-Projekten** von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oder von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ausführen, führt der Assistent unterschiedliche Konvertierungstasks aus.  
  
        -   Wenn Sie den Assistenten über [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ausführen, werden die im Projekt enthaltenen Pakete von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 2005, 2008 oder 2008 R2 in das Format konvertiert, das von der aktuellen Version von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]verwendet wird. Ein Update des ursprünglichen Projekts (.dtproj) und der Paketdateien (.dtsx) wird durchgeführt.  
  
        -   Wenn Sie den Assistenten über [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ausführen, generiert der Assistent eine Projektbereitstellungsdatei (.ispac) von den Paketen und Konfigurationen, die im Projekt enthalten sind. Ein Update der Originalpaketdateien (.dtsx) wird nicht durchgeführt.  
  
             Sie können eine vorhandene Datei auswählen oder eine neue Datei erstellen (auf der Assistentenseite für das **Auswahlziel**).  
  
             Zur Aktualisierung von Paketdateien bei der Konvertierung eines Projekts führen Sie den **Assistenten für die Konvertierung von Integration Services-Projekten** über [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]aus. Wenn Paketdateien unabhängig von einer Projektkonvertierung aktualisiert werden sollen, führen Sie den Assistenten zum Konvertieren von **Integration Services-Projekten** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] aus, und führen Sie dann den **SSIS-Paketupgrade-Assistenten**aus. Wenn Sie die Paketdateien getrennt aktualisieren, stellen Sie sicher, dass Sie die Änderungen speichern. Andernfalls werden bei der Konvertierung des Projekts in das Projektbereitstellungsmodell alle nicht gespeicherten Änderungen am Paket nicht konvertiert.  
  
     Weitere Informationen zum Upgraden von Paketen finden Sie unter [Upgraden von Integration Services-Paketen](install-windows/upgrade-integration-services-packages.md) und [Upgraden von Integration Services-Paketen mit dem SSIS-Paketupgrade-Assistenten](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).  
  
3.  Stellen Sie das Projekt auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Server bereit. Weitere Informationen finden Sie in den folgenden Anweisungen: So stellen Sie [ein Projekt auf dem Integration Services Server](#deploy)bereit.  
  
4.  (Optional) Erstellen Sie eine Umgebung für das bereitgestellte Projekt. Weitere Informationen finden Sie unter [Erstellen und Zuordnen einer Serverumgebung](../../2014/integration-services/create-and-map-a-server-environment.md).  
  
##  <a name="to-convert-a-project-to-the-project-deployment-model"></a><a name="convert"></a>So konvertieren Sie ein Projekt in das Projekt Bereitstellungs Modell  
  
1.  Öffnen Sie das Projekt in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], und klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt. Klicken Sie anschließend auf **In Projektbereitstellungsmodell konvertieren**.  
  
     - oder -  
  
     Klicken Sie im Objekt-Explorer in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]mit der rechten Maustaste auf den Knoten **Projekte** , und wählen Sie anschließend die Option **Pakete importieren**aus.  
  
2.  Schließen Sie den Assistenten ab. Weitere Informationen finden Sie unter [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md).  
  
##  <a name="to-deploy-a-project-to-the-integration-services-server"></a><a name="deploy"></a>So stellen Sie ein Projekt auf dem Integration Services Server bereit  
  
1.  Öffnen Sie das Projekt in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], und wählen Sie dann im Menü **Projekt** die Option **Bereitstellen** aus, um den **Bereitstellungs-Assistent für Integration Services**zu starten.  
  
     - oder -  
  
     Erweitern Sie in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]  >  Objekt-Explorer den Knoten **ssisdb** , und suchen Sie den Ordner Projekte für das Projekt, das Sie bereitstellen möchten. Klicken Sie mit der rechten Maustaste auf den Ordner **Projekte** , und klicken Sie anschließend auf **Projekt bereitstellen**.  
  
     - oder -  
  
     Führen Sie an der Eingabeaufforderung **isdeploymentwizard.exe** unter dem Pfad **%ProgramFiles%\Microsoft SQL Server\110\DTS\Binn**aus. Auf 64-Bit-Computern steht auch eine 32-Bit-Version des Tools unter **%ProgramFiles(x86)%\Microsoft SQL Server\100\DTS\Binn**zur Verfügung.  
  
2.  Klicken Sie auf der Seite **Quelle auswählen** auf **Projektbereitstellungsdatei** , um die Bereitstellungsdatei für das Projekt auszuwählen.  
  
     ODER  
  
     Klicken Sie auf **Integration Services-Katalog** , um ein Projekt auszuwählen, das bereits im SSISDB-Katalog bereitgestellt wurde.  
  
3.  Schließen Sie den Assistenten ab. Weitere Informationen finden Sie unter [Integration Services Deployment Wizard](../../2014/integration-services/integration-services-deployment-wizard.md).  
  
  
