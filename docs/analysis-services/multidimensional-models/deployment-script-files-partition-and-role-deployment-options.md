---
title: Angeben von Partitionen und Bereitstellungsoptionen für Rollen | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8bd62cc5fef3ef13dede85c06b28b0501a83de2f
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52513909"
---
# <a name="deployment-script-files---partition-and-role-deployment-options"></a>Bereitstellungsskriptdateien – Bereitstellungsoptionen für Partitionen und Rollen
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Bereitstellungs-Assistent liest die Bereitstellungsoptionen für Partitionen und Rollen aus der \< *Projektname*> .deploymentoptions-Datei. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] erstellt diese Datei, wenn Sie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt erstellen. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] verwendet die Bereitstellungsoptionen für Partitionen und Rollen des aktuellen Projekts, wenn die \< *Projektname*> .deploymentoptions-Datei erstellt wird. Weitere Informationen zu den Konfigurationseinstellungen finden Sie unter [Grundlegendes zu den zum Erstellen des Bereitstellungsskripts verwendeten Eingabedateien](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md).  
  
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
  
-   Führen Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] an der Eingabeaufforderung aus, und legen Sie fest, dass der Assistent im Antwortdateimodus ausgeführt wird. Weitere Informationen zum Antwortdateimodus finden Sie unter [Ausführen des Bereitstellungs-Assistenten für Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md).  
  
     -oder-  
  
-   Öffnen der \< *Projektname*> .deploymentoptions in einem Text-Editor, und manuell die Optionen ändern. Die Optionen für PartitionDeployment sind DeployPartitions, RetainPartitions. Die Optionen für RoleDeployment sind DeployRolesAndMembers, DeployRolesRetainMembers, RetainRoles.
  
## <a name="see-also"></a>Siehe auch  
 [Angeben des Installationszieles](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)   
 [Angeben der Konfigurationseinstellungen für die Lösungsbereitstellung](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)   
 [Angeben von Verarbeitungsoptionen](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
  
