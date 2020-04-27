---
title: Angeben von Konfigurationseinstellungen für die Lösungs Bereitstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, configuration settings
- input files [Analysis Services]
- configuration options [Analysis Services]
- Analysis Services deployments, configuration settings
- deploying [Analysis Services], configuration settings
ms.assetid: 953814a3-85ef-40cc-b46a-d532aa7a6569
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8addba32560e136f68e538240f4fce01f826355e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66075267"
---
# <a name="specifying-configuration-settings-for-solution-deployment"></a>Angeben der Konfigurationseinstellungen für die Lösungsbereitstellung
  Der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Bereitstellungs-Assistent liest die Bereitstellungs Optionen für Partitionen und Rollen, die Sie im Bereitstellungs Skript verwenden, aus dem \< *Projektnamen*>. configsettings-Datei. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]erstellt diese Datei, wenn Sie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt erstellen. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]verwendet die Konfigurationseinstellungen des aktuellen Projekts, um den \< *Projektnamen*>. configsettings-Datei zu erstellen.  
  
## <a name="reviewing-the-configuration-settings-for-deployment"></a>Überprüfen der Konfigurationseinstellungen für die Bereitstellung  
 Im folgenden finden Sie die Konfigurationseinstellungen, die \<im *Projektnamen*>. configsettings-Datei gespeichert sind:  
  
-   **Datenquellen-Verbindungszeichenfolgen** Hierbei handelt es sich um die Verbindungszeichenfolgen für die jeweiligen Datenquellen basierend auf den im [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt angegebenen Werten. Die Benutzer-ID und das Kennwort werden stets aus der Verbindungszeichenfolge entfernt, bevor die restliche Zeichenfolge in dieser Datei gespeichert wird. Wenn jedoch die Bereitstellung durch den Bereitstellungs-Assistenten direkt auf einer Analysis Services-Instanz erfolgt, können Sie die entsprechenden Informationen zur Benutzer-ID und zum Kennwort im Assistenten hinzufügen, um eine erfolgreiche Verarbeitung der Bereitstellungsdatenbank zu ermöglichen. Diese Verbindungsinformationen werden nicht direkt im Bereitstellungsskript gespeichert, wenn ein solches vom Bereitstellungs-Assistenten gespeichert wird.  
  
-   **Identitätswechselkonten** Diese Einstellung gibt den Benutzernamen an, unter dem in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Anweisungen in den einzelnen Datenquellen ausgeführt werden. Wird kein Identitätswechselkonto angegeben, verwendet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] zum Ausführen von Anweisungen das Anmeldekonto. Wenn das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Anmeldekonto über Berechtigungen direkt in der Datenquelle verfügt, haben alle Datenbankadministratoren in allen Datenbanken in der Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] über das Anmeldekonto Zugriff auf die Datenquelle. Wenn ein Benutzerkonto und ein Kennwort angegeben sind, werden diese Informationen stets entfernt, bevor die Identitätswechselinformationen in dieser Datei gespeichert werden. Wenn jedoch die Bereitstellung durch den Bereitstellungs-Assistenten direkt auf einer Analysis Services-Instanz erfolgt, können Sie die entsprechenden Informationen zur Benutzer-ID und zum Kennwort im Assistenten hinzufügen, um eine erfolgreiche Verarbeitung der Bereitstellungsdatenbank zu ermöglichen. Diese Identitätswechselinformationen werden nicht direkt im Bereitstellungsskript gespeichert, wenn ein solches vom Bereitstellungs-Assistenten gespeichert wird.  
  
-   **Schlüsselfehler-Protokolldateien** Diese Einstellung gibt den Dateinamen und Pfad der Schlüsselfehler-Protokolldatei für jeden Cube und für jede Measuregruppe, Partition und Dimension in der Datenbank an.  
  
-   **Speicherorte** Diese Einstellung gibt den Speicherort für jeden Cube, jede Measuregruppe und Partition in der Datenbank an. Wird für ein Objekt kein Wert angegeben, verwendet der Bereitstellungs-Assistent für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] den Standardspeicherort für das Objekt. Partitionen verwenden beispielsweise den Speicherort für die Measuregruppe, Measuregruppen verwenden den Speicherort für den Cube, und Cubes verwenden den Standardspeicherort für Objekte in der Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Als Speicherort kann ein lokaler Pfad oder ein UNC-Pfad (Universal Naming Convention) angegeben werden.  
  
-   **Berichtsserver** Diese Einstellung gibt den Berichtsserver und Ordnerspeicherort für jede in den einzelnen Cubes in der Datenbank definierte Berichtsaktion an.  
  
## <a name="modifying-the-configuration-settings-for-deployment"></a>Ändern der Konfigurationseinstellungen für die Bereitstellung  
 In einigen Fällen müssen Sie das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Projekt möglicherweise mit anderen Konfigurationseinstellungen bereitstellen, als im \< *Projektnamen*>. configsettings-Datei gespeichert. Vielleicht möchten Sie die Verbindungszeichenfolge für eine oder mehrere Datenquellen ändern oder Speicherorte für bestimmte Partitionen oder Measuregruppen angeben.  
  
 Um die Bereitstellung von Partitionen und Rollen in einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt zu ändern, müssen Sie diese Informationen \<im *Projektnamen*>. configsettings-Datei ändern, wie im folgenden Verfahren beschrieben. Die Partitions-und Rollen Einstellungen können nicht innerhalb des Projekts geändert werden, da diese Optionen im Dialogfeld * \<Projektname>* **Eigenschaften Seiten** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] nicht angezeigt werden.  
  
> [!NOTE]  
>  Konfigurationseinstellungen können für alle Objekte oder nur für neu erstellte Objekte gelten. Wenden Sie Konfigurationseinstellungen nur dann auf neu erstellte Objekte an, wenn Sie für eine bereits früher bereitgestellte [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank zusätzliche Objekte bereitstellen und vorhandene Objekte nicht überschreiben möchten. Um anzugeben, ob Konfigurationseinstellungen für alle Objekte oder nur für neu erstellte Objekte gelten, legen Sie diese Option \<in der *Projektname*>. deploymentoptions-Datei fest. Weitere Informationen finden Sie unter [Angeben von Bereitstellungsoptionen für Partitionen und Rollen](deployment-script-files-partition-and-role-deployment-options.md).  
  
#### <a name="to-change-configuration-settings-after-the-input-files-have-been-generated"></a>So ändern Sie Konfigurationseinstellungen, nachdem die Eingabedateien generiert wurden  
  
-   Führen Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] interaktiv aus, und geben Sie auf der Seite **Konfigurationseinstellungen** die Konfigurationseinstellungen für die Objekte an, die bereitgestellt werden.  
  
     - oder -  
  
-   Führen Sie den Bereitstellungs-Assistenten für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] an der Eingabeaufforderung aus, und legen Sie fest, dass der Assistent im Antwortdateimodus ausgeführt wird. Weitere Informationen zum Antwortdateimodus finden Sie unter [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).  
  
     - oder -  
  
-   Ändern Sie \<den *Projektnamen*>. configsettings-Datei, indem Sie einen beliebigen Text-Editor verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben des Installations Ziels](deployment-script-files-specifying-the-installation-target.md)   
 [Angeben von Bereitstellungs Optionen für Partitionen und Rollen](deployment-script-files-partition-and-role-deployment-options.md)   
 [Angeben von Verarbeitungsoptionen](deployment-script-files-specifying-processing-options.md)  
  
  
