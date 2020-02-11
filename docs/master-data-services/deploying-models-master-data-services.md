---
title: Bereitstellen von Modellen
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deployment packages [Master Data Services], about deployment packages
- deployment packages [Master Data Services]
ms.assetid: 30085c08-034f-4efe-80fe-408f9091ff5c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1fa740ec21867c07b2e39b9743234dd3c8121551
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728292"
---
# <a name="deploying-models-master-data-services"></a>Bereitstellen von Modellen (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ist ein Paket eine XML-Datei, die eine zur Bereitstellung geeignete Modellstruktur enthält und optional Daten vom Modell. Verschieben Sie Kopien von Modellen mithilfe von Modellpaketen von einer MDS-Umgebung in eine andere oder erstellen Sie damit neue Modelle in der vorhandenen MDS-Umgebung.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]Das **Tool mdsmodelbereitstellung** ist abwärts kompatibel mit den in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] oder höher erstellten Paketen.  
  
## <a name="tools-for-deploying-models"></a>Tools zum Bereitstellen von Modellen  
 Sie können je nach Anforderungen mithilfe eines der drei Tools mit Modellpaketen arbeiten.  
  
-   **Mdsmodelbereitstellungs-Tool**: zum Erstellen und Bereitstellen von Modell Objekten und-Daten verwenden Sie das Tool "mdsmodelbereitstellungs. exe". Falls Sie bei der Installation von MDS den Standardpfad ausgewählt haben, finden Sie dieses Tool unter folgendem Pfad *Laufwerk*:\Programme\Microsoft SQL Server\130\Master Data Services\Configuration.  
  
-   **Modellbereitstellungs-Assistent**: zum Erstellen und Bereitstellen von Paketen der Modellstruktur verwenden Sie den Assistenten [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] in der-Webanwendung. Sie können diesen Assistenten nicht zur Bereitstellung von Daten verwenden.  
  
-   **Modell Paket-Editor**: um ein Modell Paket zu bearbeiten, verwenden Sie "modelpackageeditor. exe", mit dem der modellpaketeditor-Assistent gestartet wird. Sie verwenden diesen Assistenten, um ein Paket zu bearbeiten, das vom MDSModelDeploy-Tool oder dem Modellbereitstellungs-Assistenten erstellt wurde. Falls Sie bei der Installation von MDS den Standardpfad ausgewählt haben, finden Sie dieses Tool unter folgendem Pfad *Laufwerk*:\Programme\Microsoft SQL Server\130\Master Data Services\Configuration.  
  
> [!IMPORTANT]  
>  Mit dem MDSModelDeploy-Tool können Sie ein neues Modell oder einen Modellklon erstellen oder ein vorhandenes Modell einschließlich seiner Daten aktualisieren. Wenn Sie das MDSModelDeploy-Tool verwenden, um ein vorhandenes Modell inklusive Daten zu aktualisieren, und das Paket keine Entität, kein Attribut oder kein Element enthält, die bzw. das im Zielmodell enthalten ist, wird diese Entität bzw. dieses Attribut oder Element von MDSModelDeploy nicht aus dem Modell gelöscht.  
  
## <a name="what-packages-contain"></a>Inhalte von Paketen  
 Ein Modellpaket ist eine XML-Datei, die mit der Erweiterung .pkg gespeichert wird. Wenn Sie ein Bereitstellungspaket erstellen, können Sie entscheiden, ob Daten eingeschlossen werden oder nicht. Wenn Sie entscheiden, Daten einzuschließen, müssen Sie eine Version der einzuschließenden Daten auswählen.  
  
 Alle Modellobjekte sind in einem Paket enthalten. Diese Objekte sind:  
  
-   Entitäten  
  
-   Attributes  
  
-   Attributgruppen  
  
-   Hierarchien  
  
-   Auflistungen  
  
-   Geschäftsregeln  
  
-   Versionsflags  
  
-   Abonnementsichten  
  
 Dateiattribute sowie Benutzer- und Gruppenberechtigungen sind nicht eingeschlossen. Nachdem Sie ein Modell bereitgestellt haben, müssen diese manuell aktualisiert werden.  
  
## <a name="sample-packages"></a>Beispielpakete  
 In der Installation von [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]sind Beispielpaketdateien enthalten. Diese Paketdateien sind Installationsverzeichnis von [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]im Unterverzeichnis Master Data Services\Samples\Packages gespeichert. Wenn Sie diese Beispielspakete mithilfe des Tools MDSModelDeploy bereitstellen, werden Beispielmodelle erstellt und mit Daten aufgefüllt.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Erstellen Sie mit dem Tool MDSModelDeploy ein neues Bereitstellungspaket mit Modellobjekten und/oder Daten.|[Erstellen eines Modellbereitstellungspakets mit MDSModelDeploy](../master-data-services/create-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|Erstellen Sie nur mit dem Assistenten ein neues Bereitstellungspaket mit Modellobjekten.|[Erstellen eines Modellbereitstellungspakets mithilfe des Assistenten](../master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)|  
|Stellen Sie mit dem Tool MDSModelDeploy ein Paket mit Modellobjekten und Daten bereit.|[Bereitstellen eines Modellbereitstellungspakets mit MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)|  
|Stellen Sie nur mit dem Assistenten ein Paket Modellobjekte bereit.|[Bereitstellen eines Modellbereitstellungspakets mithilfe des Assistenten](../master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)|  
|Bearbeiten Sie ein Modellbereitstellungspaket, um ausgewählte Teile eines Modells und nicht das ganze Modell bereitzustellen.|[Bearbeiten eines Modellbereitstellungspakets](../master-data-services/edit-a-model-deployment-package.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Modell Bereitstellungs Optionen &#40;Master Data Services&#41;](../master-data-services/model-deployment-options-master-data-services.md)  
  
  
