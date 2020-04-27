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
manager: craigg
ms.openlocfilehash: b9b36013f13360a2afcf9546cd1e286b35ae4acd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66075354"
---
# <a name="specifying-partition-and-role-deployment-options"></a>Angeben von Bereitstellungsoptionen für Partitionen und Rollen
  Der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Bereitstellungs-Assistent für liest die Bereitstellungs Optionen für \<Partitionen und Rollen aus der Datei *Project Name*>. deploymentoptions. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erstellt diese Datei, wenn Sie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt erstellen. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]verwendet die Bereitstellungs Optionen für Partitionen und Rollen des aktuellen Projekts, \<wenn der *Projektname*>. deploymentoptions-Datei erstellt wird. Weitere Informationen zu den Konfigurationseinstellungen finden Sie unter [Grundlegendes zu den zum Erstellen des Bereitstellungsskripts verwendeten Eingabedateien](deployment-script-files-input-used-to-create-deployment-script.md).  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a>Überprüfen der Bereitstellungsoptionen für Partitionen und Rollen  
 Die Bereitstellungs Optionen in \<der Datei *Project Name*>. deploymentoptions umfassen Folgendes:  
  
 **Bereitstellungsoptionen für Partitionen**  
 Der \< *Projektname*>. deploymentoptions-Datei gibt an, ob vorhandene Partitionen in der Zieldatenbank beibehalten oder überschrieben (Standard) werden. Wenn vorhandene Partitionen beibehalten werden, werden nur neue Partitionen bereitgestellt, und der Partitions- bzw. Aggregationsentwurf in allen vorhandenen Measuregruppen wird nicht geändert.  
  
> [!NOTE]  
>  Wird die Measuregruppe, in der die Partition vorhanden ist, gelöscht, wird die Partition automatisch gelöscht.  
  
 **Bereitstellungsoptionen für Rollen**  
 Der \< *Projektname*>. deploymentoptions-Datei gibt eine der folgenden Optionen für die Rollen Bereitstellung an:  
  
-   Vorhandene Rollen und Rollenelemente in der Zieldatenbank werden beibehalten, und nur neue Rollen und Rollenelemente werden bereitgestellt.  
  
-   Alle in der Zieldatenbank vorhandenen Rollen und Elemente werden durch die bereitgestellten Rollen und Elemente ersetzt.  
  
-   Vorhandene Rollen und Rollenelemente in der Zieldatenbank werden beibehalten, neue Rollen werden nicht bereitgestellt.  
  
-   **Hinweis:** Wenn vorhandene Rollen und Elemente beibehalten werden, werden die Berechtigungen, die diesen Rollen zugeordnet sind, zurückgesetzt. Sicherheitsberechtigungen sind in den Objekten enthalten, die sie sichern, und nicht in den Sicherheitsrollen, denen sie zugeordnet sind. Weitere Informationen zum Arbeiten mit diesem Verhalten mithilfe des Bereitstellungs-Assistenten für Analysis Services finden Sie unter "beibehalten von Rollen und Mitgliedern" in der Microsoft Knowledge Base.  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a>Ändern der Bereitstellungsoptionen für Partitionen und Rollen  
 Möglicherweise müssen Sie das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt mit anderen Partitions-und Rollen Optionen bereitstellen, als diejenigen \<, die in der *Projektname*>. deploymentoptions-Datei gespeichert sind. Beispielsweise möchten Sie möglicherweise vorhandene Partitionen, Rollen und Rollen Mitglieder beibehalten, anstatt alle vorhandenen Partitionen, Rollen und Member zu ersetzen, wie in der \< *Projektname*>. deploymentoptions-Datei angegeben.  
  
 Um die Bereitstellung von Partitionen und Rollen in einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt zu ändern, können Sie die Partitions-und Rollen Einstellungen innerhalb des Projekts nicht ändern, da im Dialogfeld [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] * \<Projektname>* **Eigenschaften Seiten** in diese Optionen nicht angezeigt werden. Wenn Sie die Bereitstellungs Optionen für Rollen und Partitionen ändern möchten, müssen Sie diese Informationen innerhalb des \< *Projekt namens*>. deploymentoptions-Datei selbst ändern. Im folgenden Verfahren wird beschrieben, wie die Bereitstellungs Optionen für Partitionen und Rollen \<innerhalb des *Projekt namens*>. deploymentoptions-Datei geändert werden.  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a>So ändern Sie die Bereitstellung von Partitionen und Rollen, nachdem die Eingabedateien generiert wurden  
  
-   Führen Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] interaktiv aus, und geben Sie auf der Seite **Bereitstellungsoptionen für Partitionen und Rollen** neue Bereitstellungsoptionen für die Partitionen und Rollen an.  
  
     - oder -  
  
-   Führen Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] an der Eingabeaufforderung aus, und legen Sie fest, dass der Assistent im Antwortdateimodus ausgeführt wird. (Weitere Informationen zum Antwortdatei Modus finden Sie unter [Ausführen des Bereitstellungs-Assistenten für Analysis Services](running-the-analysis-services-deployment-wizard.md).)  
  
     - oder -  
  
-   Öffnen Sie \<den *Projektnamen*>. deploymentoptions in einem beliebigen Text-Editor, und ändern Sie die Optionen manuell.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben des Installations Ziels](deployment-script-files-specifying-the-installation-target.md)   
 [Angeben von Konfigurationseinstellungen für die Lösungs Bereitstellung](deployment-script-files-solution-deployment-config-settings.md)   
 [Angeben von Verarbeitungsoptionen](deployment-script-files-specifying-processing-options.md)  
  
  
