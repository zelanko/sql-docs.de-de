---
title: Angeben von Partitionen und Bereitstellungsoptionen für Rollen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
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
manager: craigg
ms.openlocfilehash: 66c2683bd383ebd3d0a9278cb008b6909dc80007
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62726274"
---
# <a name="specifying-partition-and-role-deployment-options"></a>Angeben von Bereitstellungsoptionen für Partitionen und Rollen
  Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Bereitstellungs-Assistent liest die Bereitstellungsoptionen für Partitionen und Rollen aus der \< *Projektname*> .deploymentoptions-Datei. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] erstellt diese Datei, wenn Sie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt erstellen. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] verwendet die Bereitstellungsoptionen für Partitionen und Rollen des aktuellen Projekts, wenn die \< *Projektname*> .deploymentoptions-Datei erstellt wird. Weitere Informationen zu den Konfigurationseinstellungen finden Sie unter [Grundlegendes zu den zum Erstellen des Bereitstellungsskripts verwendeten Eingabedateien](deployment-script-files-input-used-to-create-deployment-script.md).  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a>Überprüfen der Bereitstellungsoptionen für Partitionen und Rollen  
 Die Bereitstellungsoptionen in der \< *Projektname*> .deploymentoptions Datei umfassen Folgendes:  
  
 **Bereitstellungsoptionen für Partitionen**  
 Die \< *Projektname*> .deploymentoptions-Datei gibt an, ob vorhandene Partitionen in der Zieldatenbank beibehalten oder überschrieben (Standardeinstellung). Wenn vorhandene Partitionen beibehalten werden, werden nur neue Partitionen bereitgestellt, und der Partitions- bzw. Aggregationsentwurf in allen vorhandenen Measuregruppen wird nicht geändert.  
  
> [!NOTE]  
>  Wird die Measuregruppe, in der die Partition vorhanden ist, gelöscht, wird die Partition automatisch gelöscht.  
  
 **Bereitstellungsoptionen für Rollen**  
 Die \< *Projektname*> .deploymentoptions-Datei gibt eine der folgenden Optionen für die Bereitstellung:  
  
-   Vorhandene Rollen und Rollenelemente in der Zieldatenbank werden beibehalten, und nur neue Rollen und Rollenelemente werden bereitgestellt.  
  
-   Alle in der Zieldatenbank vorhandenen Rollen und Elemente werden durch die bereitgestellten Rollen und Elemente ersetzt.  
  
-   Vorhandene Rollen und Rollenelemente in der Zieldatenbank werden beibehalten, neue Rollen werden nicht bereitgestellt.  
  
-   **Hinweis:** Wenn vorhandene Rollen und Elemente beibehalten werden, werden die Berechtigungen, die diesen Rollen zugeordnet sind, zurückgesetzt. Sicherheitsberechtigungen sind in den Objekten enthalten, die sie sichern, und nicht in den Sicherheitsrollen, denen sie zugeordnet sind. Weitere Informationen zum Arbeiten mit diesem Verhalten mithilfe des Assistenten für Analysis Service-Bereitstellung finden Sie unter "Beibehalten von Rollen und Mitglieder" in der Microsoft Knowledge Base.  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a>Ändern der Bereitstellungsoptionen für Partitionen und Rollen  
 Möglicherweise müssen Sie die Bereitstellung der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt mit anderen Partitions- und Rollenoptionen als denen, die in der \< *Projektname*> .deploymentoptions-Datei. Angenommen, Sie vorhandene Partitionen, Rollen und Mitglieder der Rolle, anstatt zu ersetzen alle vorhandenen Partitionen, Rollen und Elemente, wie angegeben in beibehalten möchten die \< *Projektname*> .deploymentoptions-Datei.  
  
 So ändern Sie die Bereitstellung von Partitionen und Rollen in einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt die Partitions- und rolleneinstellungen Einstellungen innerhalb des Projekts kann nicht geändert werden, da die  *\<Projektname >* **Eigenschaftenseiten**  im Dialogfeld [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] diese Optionen nicht angezeigt. Wenn Sie die Bereitstellungsoptionen für Rollen und Partitionen ändern möchten, müssen Sie ändern, dass diese Informationen in den \< *Projektname*> .deploymentoptions-Datei selbst. Das folgende Verfahren beschreibt, wie so ändern Sie die Bereitstellungsoptionen für Partitionen und Rollen in der \< *Projektname*> .deploymentoptions-Datei.  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a>So ändern Sie die Bereitstellung von Partitionen und Rollen, nachdem die Eingabedateien generiert wurden  
  
-   Führen Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] interaktiv aus, und geben Sie auf der Seite **Bereitstellungsoptionen für Partitionen und Rollen** neue Bereitstellungsoptionen für die Partitionen und Rollen an.  
  
     -oder-  
  
-   Führen Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] an der Eingabeaufforderung aus, und legen Sie fest, dass der Assistent im Antwortdateimodus ausgeführt wird. Weitere Informationen zum Antwortdateimodus finden Sie unter [Ausführen des Bereitstellungs-Assistenten für Analysis Services](running-the-analysis-services-deployment-wizard.md).  
  
     -oder-  
  
-   Öffnen der \< *Projektname*> .deploymentoptions in einem Text-Editor, und manuell die Optionen ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Angeben des Installationszieles](deployment-script-files-specifying-the-installation-target.md)   
 [Angeben der Konfigurationseinstellungen für die Lösungsbereitstellung](deployment-script-files-solution-deployment-config-settings.md)   
 [Angeben von Verarbeitungsoptionen](deployment-script-files-specifying-processing-options.md)  
  
  
