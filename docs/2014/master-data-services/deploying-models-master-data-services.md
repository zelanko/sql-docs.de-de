---
title: Bereitstellen von Modellen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], about deployment packages
- deployment packages [Master Data Services]
ms.assetid: 30085c08-034f-4efe-80fe-408f9091ff5c
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 58f946f89691a6e26ba4402166b8ad725e7a977c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52761782"
---
# <a name="deploying-models-master-data-services"></a>Bereitstellen von Modellen (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ist ein Paket eine XML-Datei, die eine zur Bereitstellung geeignete Modellstruktur enthält und optional Daten vom Modell. Verschieben Sie Kopien von Modellen mithilfe von Modellpaketen von einer MDS-Umgebung in eine andere oder erstellen Sie damit neue Modelle in der vorhandenen MDS-Umgebung.  
  
> [!IMPORTANT]  
>  Pakete können nur in der Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] bereitgestellt werden, in der sie erstellt wurden. Dies bedeutet, dass in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] erstellte Pakete nicht in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] oder höher bereitgestellt werden können.  
  
## <a name="tools-for-deploying-models"></a>Tools zum Bereitstellen von Modellen  
 Sie können je nach Anforderungen mithilfe eines der drei Tools mit Modellpaketen arbeiten.  
  
-   **MDSModelDeploy-Tool**: Verwenden Sie zum Erstellen und Bereitstellen von modellobjekten und Daten, die das Tool MDSModelDeploy.exe. Wenn Sie bei der Installation von MDS den Standardpfad ausgewählt haben, befindet sich dieses Tool auf *Laufwerk*: \Programme\Microsoft SQL Server\120\Master Data Services\Configuration.  
  
-   **Modellbereitstellungs-Assistenten**: Zum Erstellen und Bereitstellen von Paketen, die nur die Modellstruktur enthalten, verwenden Sie den Assistenten in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web-Anwendung. Sie können diesen Assistenten nicht zur Bereitstellung von Daten verwenden.  
  
-   **Modellpaket-Editor**: Um ein modellpaket zu bearbeiten, verwenden Sie die ModelPackageEditor.exe, die der Modellpaketeditor-Assistent wird gestartet. Sie verwenden diesen Assistenten, um ein Paket zu bearbeiten, das vom MDSModelDeploy-Tool oder dem Modellbereitstellungs-Assistenten erstellt wurde. Wenn Sie bei der Installation von MDS den Standardpfad ausgewählt haben, befindet sich dieses Tool auf *Laufwerk*: \Programme\Microsoft SQL Server\120\Master Data Services\Configuration.  
  
> [!IMPORTANT]  
>  Sie können das MDSDeployModel verwenden, um ein neues Modell oder einen Modellklon zu erstellen oder um ein vorhandenes Modell einschließlich Daten zu aktualisieren. Wenn Sie das MDSModelDeploy-Tool verwenden, um ein vorhandenes Modell inklusive Daten zu aktualisieren, und das Paket keine Entität, kein Attribut oder kein Element enthält, die bzw. das im Zielmodell enthalten ist, wird diese Entität bzw. dieses Attribut oder Element von MDSModelDeploy nicht aus dem Modell gelöscht.  
  
## <a name="what-packages-contain"></a>Inhalte von Paketen  
 Ein Modellpaket ist eine XML-Datei, die mit der Erweiterung .pkg gespeichert wird. Wenn Sie ein Bereitstellungspaket erstellen, können Sie entscheiden, ob Daten eingeschlossen werden oder nicht. Wenn Sie entscheiden, Daten einzuschließen, müssen Sie eine Version der einzuschließenden Daten auswählen.  
  
 Alle Modellobjekte sind in einem Paket enthalten. Diese Objekte sind:  
  
-   Entitäten  
  
-   Attribute  
  
-   Attributgruppen  
  
-   Hierarchien  
  
-   Auflistungen  
  
-   Geschäftsregeln  
  
-   Versionsflags  
  
-   Abonnementsichten  
  
 Benutzerdefinierte Metadaten, Dateiattribute sowie Benutzer- und Gruppenberechtigungen sind nicht eingeschlossen. Nachdem Sie ein Modell bereitgestellt haben, müssen diese manuell aktualisiert werden.  
  
## <a name="sample-packages"></a>Beispielpakete  
 In der Installation von [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]sind Beispielpaketdateien enthalten. Diese Paketdateien sind Installationsverzeichnis von [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]im Unterverzeichnis Master Data Services\Samples\Packages gespeichert. Wenn Sie diese Beispielspakete mithilfe des Tools MDSModelDeploy bereitstellen, werden Beispielmodelle erstellt und mit Daten aufgefüllt.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Erstellen Sie mit dem Tool MDSModelDeploy ein neues Bereitstellungspaket mit Modellobjekten und/oder Daten.|[Erstellen eines Modellbereitstellungspakets mit MDSModelDeploy](../../2014/master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|Erstellen Sie nur mit dem Assistenten ein neues Bereitstellungspaket mit Modellobjekten.|[Erstellen eines Modellbereitstellungspakets mithilfe des Assistenten](../../2014/master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)|  
|Stellen Sie mit dem Tool MDSModelDeploy ein Paket mit Modellobjekten und Daten bereit.|[Bereitstellen eines Modellbereitstellungspakets mit MDSModelDeploy](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|Stellen Sie nur mit dem Assistenten ein Paket Modellobjekte bereit.|[Bereitstellen eines Modellbereitstellungspakets mithilfe des Assistenten](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)|  
|Bearbeiten Sie ein Modellbereitstellungspaket, um ausgewählte Teile eines Modells und nicht das ganze Modell bereitzustellen.|[Bearbeiten eines Modellbereitstellungspakets](../../2014/master-data-services/edit-a-model-deployment-package.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Optionen für Modellbereitstellung &#40;Master Data Services&#41;](model-deployment-options-master-data-services.md)  
  
  
