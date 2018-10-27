---
title: Mehrdimensionale Modelllösungsbereitstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services deployments, planning
- deploying [Analysis Services]
- deploying [Analysis Services], planning
ms.assetid: 7259c201-ff54-43e8-bda5-a6d51474e0e6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ab19949b3a05040285a11b6988614d34bf5f5ccf
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/26/2018
ms.locfileid: "50147435"
---
# <a name="multidimensional-model-solution-deployment"></a>Mehrdimensionale Modelllösungsbereitstellung
  Nachdem Sie die Entwicklung eines [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekts abgeschlossen haben, können Sie die Datenbank auf einem Analysis Services-Server bereitstellen. Analysis Services bietet sechs mögliche Bereitstellungsmethoden, die zum Umlagern der Datenbank auf einen Test- oder Produktionsserver verwendet werden können. Die Methoden werden nach ihren Vorteilen aufgelistet: AMO-Automatisierung, XMLA, Bereitstellungs-Assistent, Bereitstellungshilfsprogramm, Synchronisations-Assistent sowie Sicherung und Wiederherstellung.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Bereitstellungsmethoden](#bkmk_meth)  
  
 [Überlegungen zur Bereitstellung](#bkmk_considerations)  
  
 [Verwandte Aufgaben](#bkmk_rel)  
  
##  <a name="bkmk_meth"></a> Bereitstellungsmethoden  
  
|Methode|Description|Link|  
|------------|-----------------|----------|  
|**Analysis Management Objects (AMO)-Automatisierung**|AMO stellt eine programmgesteuerte Schnittstelle für den vollständigen Befehlssatz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]bereit, einschließlich Befehlen zur Bereitstellung von Projektmappen. Die AMO-Automatisierung bietet die flexibelste Möglichkeit zur Bereitstellung von Projektmappen, impliziert jedoch gleichzeitig einen gewissen Programmieraufwand.  Ein wichtiger Vorteil bei der Verwendung von AMO besteht darin, dass der SQL Server-Agent mit der AMO-Anwendung zum Ausführen einer Bereitstellung nach einem festgelegten Zeitplan verwendet werden kann.|[Entwickeln mit Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)|  
|**XMLA**|Verwenden Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , um ein XMLA-Skript der Metadaten einer vorhandenen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank zu erstellen, und führen Sie dieses Skript dann auf einem anderen Server aus, um die ursprüngliche Datenbank erneut zu erstellen. XMLA-Skripts können in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] einfach erstellt werden, indem Sie den Bereitstellungsprozess definieren, anschließend codieren und in einem XMLA-Skript speichern. Nachdem Sie das XMLA-Skript in einer Datei gespeichert haben, können Sie das Skript einfach gemäß einem Zeitplan ausführen oder das Skript in eine Anwendung einbetten, die eine direkte Verbindung mit einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]herstellt.<br /><br /> Sie können auch XMLA-Skripts auf einer vordefinierten Basis mithilfe des SQL Server-Agents ausführen, aber dabei bieten Ihnen XMLA-Skripts nicht dieselbe Flexibilität wie AMO. AMO stellt eine größere Bandbreite an Funktionalität bereit, indem es das gesamte Spektrum von Verwaltungsbefehlen hostet.|[Bereitstellen von Modelllösungen mit XMLA](deploy-model-solutions-using-xmla.md)|  
|**Bereitstellungs-Assistent**|Verwenden Sie den Bereitstellungs-Assistenten, um mithilfe der durch ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt generierten XML-Ausgabedateien die Metadaten des Projekts auf einem Zielserver bereitzustellen. Mit dem Bereitstellungs-Assistenten können Sie die Bereitstellung direkt in der [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datei ausführen, die während der Projekterstellung im Ausgabeverzeichnis erstellt wurde.<br /><br /> Der Hauptvorteil bei der Verwendung des Bereitstellungs-Assistenten von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] besteht in der Benutzerfreundlichkeit. Genauso wie ein XMLA-Skript zur späteren Verwendung in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]gespeichert werden kann, können Skripts des Bereitstellungs-Assistenten gespeichert werden. Der Bereitstellungs-Assistent kann sowohl interaktiv als auch mit dem Bereitstellungshilfsprogramm über die Eingabeaufforderung ausgeführt werden.|[Bereitstellen von Modelllösungen mithilfe des Bereitstellungs-Assistenten](deploy-model-solutions-using-the-deployment-wizard.md)|  
|**Bereitstellungshilfsprogramm**|Mit dem Bereitstellungshilfsprogramm kann die Analysis Services-Bereitstellungs-Engine über die Eingabeaufforderung gestartet werden.|[Bereitstellen von Modelllösungen mit dem Bereitstellungshilfsprogramm](deploy-model-solutions-with-the-deployment-utility.md)|  
|**Assistent zum Synchronisieren einer Datenbank**|Verwenden Sie den Assistenten zum Synchronisieren einer Datenbank, um die Metadaten und Daten zwischen zwei [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbanken zu synchronisieren.<br /><br /> Mithilfe des Synchronisations-Assistenten können Sie sowohl Daten als auch Metadaten von einem Quellserver auf einen Zielserver kopieren. Wenn der Zielserver keine Kopie der Datenbank enthält, die Sie bereitstellen möchten, wird eine neue Datenbank auf den Zielserver kopiert. Wenn auf dem Zielserver bereits eine Kopie derselben Datenbank vorhanden ist, wird die Datenbank auf dem Zielserver aktualisiert, damit sie die Metadaten und Daten der Quelldatenbank verwendet.|[Synchronisieren von Analysis Services-Datenbanken](synchronize-analysis-services-databases.md)|  
|**Sichern und Wiederherstellen**|Das Sichern stellt die einfachste Vorgehensweise zum Übertragen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbanken dar. Im Dialogfeld **Sichern** können Sie die Konfiguration der Optionen festlegen und anschließend die Sicherung über das Dialogfeld ausführen. Alternativ können Sie ein Skript erstellen, das Sie speichern und so oft wie nötig ausführen können.<br /><br /> Sichern und Wiederherstellen wird nicht so häufig verwendet wie die anderen Bereitstellungsmethoden, aber diese Methode stellt eine Möglichkeit zum schnellen Abschließen einer Bereitstellung mit minimalen Infrastrukturanforderungen dar.|[Sichern und Wiederherstellen von Analysis Services-Datenbanken](backup-and-restore-of-analysis-services-databases.md)|  
  
##  <a name="bkmk_considerations"></a> Überlegungen zur Bereitstellung  
 Bevor Sie ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt bereitstellen, sollten Sie überlegen, welche der folgenden Fragen auf Ihre Projektmappe zutreffen, und sich dann anhand der angegebenen Links über die richtige Vorgehensweise informieren:  
  
|Aspekt|Link zu weiteren Informationen|  
|-------------------|------------------------------|  
|Welche Hardware- und Softwareressourcen sind für diese Projektmappe erforderlich?|[Anforderungen und Überlegungen für die Bereitstellung von Analysis Services](requirements-and-considerations-for-analysis-services-deployment.md)|  
|Wie sollen verbundene Objekte außerhalb des [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projektbereichs, wie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete, Berichte oder relationale Datenbankschemas, bereitgestellt werden?||  
|Wie werden die Daten in der bereitgestellten [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank geladen und aktualisiert?<br /><br /> Wie werden die Metadaten (z.B. Berechnungen) in der bereitgestellten [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank aktualisiert?|[Bereitstellungsmethoden](#bkmk_meth) in diesem Thema.|  
|Sollen Benutzer über das Internet auf [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Daten zugreifen können?|[Konfigurieren von HTTP-Zugriff auf Analysis Services unter Internetinformationsdienste &#40;IIS&#41; 8.0](../instances/configure-http-access-to-analysis-services-on-iis-8-0.md)|  
|Soll ein kontinuierlicher Abfragezugriff auf [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Daten möglich sein?|[Anforderungen und Überlegungen für die Bereitstellung von Analysis Services](requirements-and-considerations-for-analysis-services-deployment.md)|  
|Sollen Objekte mithilfe von verknüpften Objekten oder Remotepartitionen in einer verteilten Umgebung bereitgestellt werden?|[Erstellen und Verwalten einer lokalen Partition &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md), [Erstellen und Verwalten einer Remotepartition &#40;Analysis Services&#41;](create-and-manage-a-remote-partition-analysis-services.md) und [Verknüpfte Measuregruppen](linked-measure-groups.md).|  
|Wie sollen die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Daten gesichert werden?|[Autorisieren des Zugriffs auf Objekte und Vorgänge &#40;Analysis Services&#41;](authorizing-access-to-objects-and-operations-analysis-services.md)|  
  
##  <a name="bkmk_rel"></a> Verwandte Aufgaben  
 [Anforderungen und Überlegungen für die Bereitstellung von Analysis Services](requirements-and-considerations-for-analysis-services-deployment.md)  
  
 [Bereitstellen von Modelllösungen mit XMLA](deploy-model-solutions-using-xmla.md)  
  
 [Bereitstellen von Modelllösungen mithilfe des Bereitstellungs-Assistenten](deploy-model-solutions-using-the-deployment-wizard.md)  
  
 [Bereitstellen von Modelllösungen mit dem Bereitstellungsprogramm](deploy-model-solutions-with-the-deployment-utility.md)  
  
  
