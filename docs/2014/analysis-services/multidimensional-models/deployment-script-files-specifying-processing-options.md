---
title: Angeben von Verarbeitungsoptionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services deployments, processing options
- input files [Analysis Services]
- deploying [Analysis Services], processing options
- modifying processing options
- Analysis Services Deployment Wizard, processing options
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ea766d26034b9ee0d1fcefbd215f41c19da1f9ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075228"
---
# <a name="specifying-processing-options"></a>Angeben von Verarbeitungsoptionen
  Der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Bereitstellungs-Assistent liest die Verarbeitungsoptionen \<aus der Datei *Project Name*>. deploymentoptions. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erstellt diese Datei, wenn Sie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt erstellen. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]verwendet die Verarbeitungsoptionen, die auf der Seite **Bereitstellung** \<des * \<Dialog Felds Projektname>* **Eigenschaften Seiten** angegeben werden, um den *Projektnamen*>. deploymentoptions-Datei zu erstellen.  
  
## <a name="reviewing-the-processing-options-for-deployment"></a>Überprüfen der Verarbeitungsoptionen für die Bereitstellung  
 Die Konfigurationseinstellungen, die in \<der *Projektname*>. deploymentoptions-Datei gespeichert sind, lauten wie folgt:  
  
-   **Verarbeitungsmethode** Mit dieser Einstellung wird gesteuert, ob die bereitgestellten Objekte nach der Bereitstellung verarbeitet werden und welche Art von Verarbeitung ausgeführt wird. Es stehen drei Verarbeitungsoptionen zur Verfügung:  
  
    -   Standardverarbeitung (Standardeinstellung)  
  
    -   Vollständige Verarbeitung  
  
    -   Keine  
  
-   **Optionen** für die Rück schreibe Tabelle Wenn das Rück schreiben im [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt aktiviert ist, wird durch diese Einstellung definiert, wie das Rück schreiben behandelt wird. Es sind drei Rückschreibetabellenoptionen verfügbar:  
  
    -   Wenn eine Rückschreibetabelle vorhanden ist, wird diese standardmäßig verwendet. Ist keine Rückschreibetabelle vorhanden, wird eine neue Rückschreibetabelle erstellt.  
  
    -   Wenn bereits eine Rückschreibetabelle vorhanden ist, kann die Bereitstellung nicht durchgeführt werden. Ist keine Rückschreibetabelle vorhanden, wird eine neue Rückschreibetabelle erstellt.  
  
    -   Unabhängig davon, ob bereits eine Rückschreibetabelle vorhanden ist, wird eine neue Rückschreibetabelle erstellt. In diesem Fall löscht der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die vorhandene Tabelle und ersetzt sie durch eine neue Rückschreibetabelle.  
  
-   **Transaktions Bereitstellung** Mit dieser Einstellung wird gesteuert, ob die Bereitstellung von Metadatenänderungen und Verarbeitungs Befehlen in einer einzelnen Transaktion oder in separaten Transaktionen erfolgt.  
  
    -   Wenn diese Option auf `True` (Standard) festgelegt ist, stellt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] alle Metadatenänderungen und alle Verarbeitungsbefehle in einer einzelnen Transaktion bereit.  
  
    -   Ist diese Option `False`, stellt [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] die Metadatenänderungen in einer einzelnen Transaktion und jeden Verarbeitungsbefehl jeweils in einer eigenen Transaktion bereit.  
  
## <a name="modifying-the-processing-options-for-deployment"></a>Ändern der Verarbeitungsoptionen für die Bereitstellung  
 Allerdings müssen Sie das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt möglicherweise mit anderen Verarbeitungsoptionen bereitstellen, als diejenigen, \<die in der *Projektname*>. deploymentoptions-Datei gespeichert sind. Vielleicht sollen alle Objekte vollständig oder mithilfe der Standardverarbeitungsoption oder überhaupt nicht verarbeitet werden. Wenn die Cubes oder Dimensionen für den Schreibzugriff aktiviert sind, können Sie angeben, ob eine neue oder eine vorhandene Rückschreibetabelle verwendet werden soll.  
  
 Wenn Sie die bei der Bereitstellung zu verwendenden Verarbeitungsoptionen ändern möchten, können Sie entweder das Projekt bearbeiten und neu erstellen, oder Sie ändern mithilfe einer der im Folgenden beschriebenen Prozedur die Verarbeitungsoptionen in der Eingabedatei.  
  
#### <a name="to-change-processing-options-after-the-input-files-have-been-generated"></a>So ändern Sie Verarbeitungsoptionen, nachdem die Eingabedateien generiert wurden  
  
-   Führen Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] interaktiv aus. Geben Sie auf der Seite **Verarbeitungsoptionen** die Verarbeitungsoptionen für das bereitzustellende Projekt an.  
  
     Oder  
  
-   Führen Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] an der Eingabeaufforderung aus, und legen Sie fest, dass der Assistent im Antwortdateimodus ausgeführt wird. Weitere Informationen zum Antwortdateimodus finden Sie unter [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).  
  
     Oder  
  
-   Ändern Sie \<den *Projektnamen*>. deploymentoptions-Datei, indem Sie einen beliebigen Text-Editor verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben des Installations Ziels](deployment-script-files-specifying-the-installation-target.md)   
 [Angeben von Bereitstellungs Optionen für Partitionen und Rollen](deployment-script-files-partition-and-role-deployment-options.md)   
 [Angeben der Konfigurationseinstellungen für die Lösungsbereitstellung](deployment-script-files-solution-deployment-config-settings.md)  
  
  
