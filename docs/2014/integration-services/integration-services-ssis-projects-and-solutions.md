---
title: Integration Services-Projekte (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Integration Services], creating
- folders [Integration Services], projects
- files [Integration Services], projects
- folders [Integration Services]
- projects [Integration Services], about projects
ms.assetid: 28ea8120-0a79-4029-93f0-07d521b32bee
caps.latest.revision: 59
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c012e6802465df8db1060bebc47920e834620d40
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148881"
---
# <a name="integration-services-ssis-projects"></a>Integration Services-Projekte (SSIS)
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stellt [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] für die Entwicklung von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paketen bereit.  
  
 Wenn Sie Pakete auf einer [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbank oder im [!INCLUDE[ssIS](../includes/ssis-md.md)]-Paketspeicher bereitstellen, verwenden Sie den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Dienst, um die Pakete zu verwalten. Der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst steht nur in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]zur Verfügung. Weitere Informationen über den Dienst finden Sie unter [Integration Services-Dienst &#40;SSIS-Dienst&#41;](service/integration-services-service-ssis-service.md). Weitere Informationen zur Bereitstellung von Paketen finden Sie unter [Paketbereitstellung &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).  
  
 Wenn Sie [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekte auf dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Server bereitstellen, verwenden Sie Transact-SQL-Sichten und gespeicherte Prozeduren in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], um die Projekte zu verwalten. Weitere Informationen zur Projektbereitstellung finden Sie unter [Bereitstellung von Projekten und Paketen](packages/deploy-integration-services-ssis-projects-and-packages.md). Weitere Informationen über den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Server finden Sie unter [Integration Services-Dienst &#40;SSIS-Dienst&#41;](catalog/integration-services-ssis-server-and-catalog.md).  
  
 Eine Übersicht über [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] und [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] finden Sie unter [Integration Services- und Studio-Umgebungen &#40;SSIS&#41;](integration-services-ssis-development-and-management-tools.md).  
  
## <a name="understanding-integration-services-projects"></a>Grundlegendes zu Integration Services-Projekten  
 Ein Projekt ist ein Container, in dem Sie [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Pakete entwickeln.  
  
 In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]werden in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekten die mit dem Paket verknüpften Dateien gespeichert und gruppiert. Beispielsweise enthält ein Projekt die zum Erstellen einer bestimmten ETL-Projektmappe (Extract, Transfer, And Load) erforderlichen Dateien.  
  
 Vor dem Erstellen eines [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekts sollten Sie sich mit den grundlegenden Inhalten dieser Art von Projekten vertraut machen. Wenn Sie die Inhalte eines Projekts verstanden haben, können Sie ein [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt erstellen und verwenden.  
  
### <a name="folders-in-integration-services-projects"></a>Ordner in SQL Server Integration Services-Projekten  
 Im folgenden Diagramm werden die Ordner in einem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]veranschaulicht.  
  
 ![Ordner in einem Integration Services-Projekt](media/solutionexplorer.gif "Folders in an Integration Services project")  
  
 In der folgende Tabelle werden die Ordner in einem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt beschrieben.  
  
|Ordner|Description|  
|------------|-----------------|  
|[!INCLUDE[ssIS](../includes/ssis-md.md)] Pakete|Enthält Pakete. Weitere Informationen finden Sie unter [Integration Services-Pakete &#40;SSIS&#41;](../../2014/integration-services/integration-services-ssis-packages.md).|  
|Sonstiges|Enthält Dateien, die sich von Paketdateien unterscheiden.|  
  
### <a name="files-in-integration-services-projects"></a>Dateien in SQL Server Integration Services-Projekten  
 Wenn Sie einer Projektmappe ein neues oder vorhandenes [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt hinzufügen, erstellt [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] Projektdateien mit den Erweiterungen DTPROJ, DTPROJ.USER und DATABASE.  
  
-   Die DTPROJ-Datei enthält Informationen zu Projektkonfigurationen und Elementen wie Pakete.  
  
-   Die DTPROJ.USER-Datei enthält Informationen zu Ihren Einstellungen für das Verwenden dieses Projekts.  
  
-   Die DATABASE-Datei enthält Informationen, die [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] zum Öffnen des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekts benötigt.  
  
## <a name="understanding-solutions"></a>Grundlegendes zu Projektmappen  
 Eine Projektmappe ist ein Container, in dem die Projekte gruppiert und verwaltet werden, die Sie zum Entwickeln von End-to-End-Unternehmenslösungen verwenden. Mithilfe einer Projektmappe können Sie mehrere Projekte als Einheit verwalten und zusammenhängende Projekte für eine Unternehmenslösung zusammenbringen.  
  
 Projektmappen können unterschiedliche Projekttypen enthalten. Wenn Sie [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer zum Erstellen eines [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Pakets verwenden, arbeiten Sie in einem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt in einer von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]bereitgestellten Projektmappe.  
  
 Wenn Sie eine neue Projektmappe erstellen, fügt [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] dem Projektmappen-Explorer einen Projektmappenordner hinzu und erstellt Dateien mit den Dateierweiterungen „.sln“ und „.suo“.  
  
-   Die SLN-Datei enthält Informationen zur Projektmappenkonfiguration und führt die Projekte in der Projektmappe auf.  
  
-   Die SUO-Datei enthält Informationen zu Ihren Einstellungen für das Verwenden der Projektmappe.  
  
 Zwar wird von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] beim Erstellen eines neuen Projekts automatisch eine Projektmappe erstellt, jedoch können Sie auch eine leere Projektmappe erstellen und später Projekte hinzufügen.  
  
> [!NOTE]  
>  Wenn Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ein neues [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt erstellen, wird die Projektmappe standardmäßig nicht im Bereich **Projektexplorer** angezeigt. Um dieses Standardverhalten zu ändern, klicken Sie im Menü **Extras** auf **Optionen**. Erweitern Sie im Dialogfeld **Optionen** den Eintrag **Projekte und Projektmappen**, und klicken Sie dann auf **Allgemein**. Wählen Sie auf der Seite **Allgemein** die Option **Projektmappe immer anzeigen**aus.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Hinzufügen oder Entfernen eines Integration Services-Projekts in einer Projektmappe](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)  
  
 [Erstellen eines neuen SQL Server Integration Services-Projekts](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
 [Hinzufügen eines Elements zu einem Integration Services-Projekt](../../2014/integration-services/add-an-item-to-an-integration-services-project.md)  
  
 [Kopieren von Projektelementen](../../2014/integration-services/copy-project-items.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [Entwicklung eines Integration Services-Projekts](../../2014/integration-services/development-of-an-integration-services-project.md)  
  
  