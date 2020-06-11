---
title: Angeben von Bereitstellungs Optionen für Partitionen und Rollen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input files [Analysis Services]
- partitions [Analysis Services], deployment options
- Analysis Services deployments, roles
- Analysis Services deployments, partitions
- Analysis Services Deployment Wizard, roles
- Analysis Services Deployment Wizard, partitions
- deploying [Analysis Services], roles
- roles [Analysis Services], deployment options
- deploying [Analysis Services], partitions
- modifying role deployments
- modifying partition deployments
ms.assetid: e9b9ca57-a5cc-4fc0-87b5-305257038d56
author: minewiskan
ms.author: owend
ms.openlocfilehash: f4f2f5bb2f3f39636541d5aea5b931b1dcc72534
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546862"
---
# <a name="specifying-partition-and-role-deployment-options"></a>Angeben von Bereitstellungsoptionen für Partitionen und Rollen
  Der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Bereitstellungs-Assistent liest die Bereitstellungs Optionen für Partitionen und Rollen aus der \<*project name*> Datei ". deploymentoptions". [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erstellt diese Datei, wenn Sie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt erstellen. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]verwendet die Bereitstellungs Optionen für Partitionen und Rollen des aktuellen Projekts, wenn die \<*project name*> Datei. deploymentoptions erstellt wird. Weitere Informationen zu den Konfigurationseinstellungen finden Sie unter [Grundlegendes zu den zum Erstellen des Bereitstellungsskripts verwendeten Eingabedateien](deployment-script-files-input-used-to-create-deployment-script.md).  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a>Überprüfen der Bereitstellungsoptionen für Partitionen und Rollen  
 Die Bereitstellungs Optionen in der \<*project name*> Datei. deploymentoptions umfassen Folgendes:  
  
 **Bereitstellungsoptionen für Partitionen**  
 Die \<*project name*> Datei. deploymentoptions gibt an, ob vorhandene Partitionen in der Zieldatenbank beibehalten oder überschrieben (Standard) werden. Wenn vorhandene Partitionen beibehalten werden, werden nur neue Partitionen bereitgestellt, und der Partitions- bzw. Aggregationsentwurf in allen vorhandenen Measuregruppen wird nicht geändert.  
  
> [!NOTE]  
>  Wird die Measuregruppe, in der die Partition vorhanden ist, gelöscht, wird die Partition automatisch gelöscht.  
  
 **Bereitstellungsoptionen für Rollen**  
 Die \<*project name*> Datei. deploymentoptions gibt eine der folgenden Optionen für die Rollen Bereitstellung an:  
  
-   Vorhandene Rollen und Rollenelemente in der Zieldatenbank werden beibehalten, und nur neue Rollen und Rollenelemente werden bereitgestellt.  
  
-   Alle in der Zieldatenbank vorhandenen Rollen und Elemente werden durch die bereitgestellten Rollen und Elemente ersetzt.  
  
-   Vorhandene Rollen und Rollenelemente in der Zieldatenbank werden beibehalten, neue Rollen werden nicht bereitgestellt.  
  
-   **Hinweis:** Wenn vorhandene Rollen und Elemente beibehalten werden, werden die Berechtigungen, die diesen Rollen zugeordnet sind, zurückgesetzt. Sicherheitsberechtigungen sind in den Objekten enthalten, die sie sichern, und nicht in den Sicherheitsrollen, denen sie zugeordnet sind. Weitere Informationen zum Arbeiten mit diesem Verhalten mithilfe des Bereitstellungs-Assistenten für Analysis Services finden Sie unter "beibehalten von Rollen und Mitgliedern" in der Microsoft Knowledge Base.  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a>Ändern der Bereitstellungsoptionen für Partitionen und Rollen  
 Möglicherweise müssen Sie das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt mit anderen Partitions-und Rollen Optionen bereitstellen, als in der \<*project name*> Datei. deploymentoptions gespeichert sind. Beispielsweise möchten Sie möglicherweise vorhandene Partitionen, Rollen und Rollen Mitglieder beibehalten, anstatt alle vorhandenen Partitionen, Rollen und Member wie in der \<*project name*> Datei. deploymentoptions angegeben zu ersetzen.  
  
 Wenn Sie die Bereitstellung von Partitionen und Rollen in einem-Projekt ändern möchten [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , können Sie die Partitions-und Rollen Einstellungen innerhalb des Projekts nicht ändern, da *\<project name>* Diese Optionen im Dialogfeld **Eigenschaften Seiten** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] nicht angezeigt werden. Wenn Sie die Bereitstellungs Optionen für Rollen und Partitionen ändern möchten, müssen Sie diese Informationen in der \<*project name*> Datei. deploymentoptions selbst ändern. Im folgenden Verfahren wird beschrieben, wie die Bereitstellungs Optionen für Partitionen und Rollen in der \<*project name*> Datei ". deploymentoptions" geändert werden.  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a>So ändern Sie die Bereitstellung von Partitionen und Rollen, nachdem die Eingabedateien generiert wurden  
  
-   Führen Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] interaktiv aus, und geben Sie auf der Seite **Bereitstellungsoptionen für Partitionen und Rollen** neue Bereitstellungsoptionen für die Partitionen und Rollen an.  
  
     - oder -  
  
-   Führen Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] an der Eingabeaufforderung aus, und legen Sie fest, dass der Assistent im Antwortdateimodus ausgeführt wird. (Weitere Informationen zum Antwortdatei Modus finden Sie unter [Ausführen des Bereitstellungs-Assistenten für Analysis Services](running-the-analysis-services-deployment-wizard.md).)  
  
     - oder -  
  
-   Öffnen Sie die \<*project name*> deploymentoptions in einem beliebigen Text-Editor, und ändern Sie die Optionen manuell.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben des Installations Ziels](deployment-script-files-specifying-the-installation-target.md)   
 [Angeben von Konfigurationseinstellungen für die Lösungs Bereitstellung](deployment-script-files-solution-deployment-config-settings.md)   
 [Angeben von Verarbeitungsoptionen](deployment-script-files-specifying-processing-options.md)  
  
  
