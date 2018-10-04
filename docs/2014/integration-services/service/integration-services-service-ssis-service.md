---
title: Integration Services-Dienst (SSIS-Dienst) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services service, about Integration Services service
- SQL Server Integration Services service
- service [Integration Services],about Integration Services service
- service [Integration Services]
- SQL Server Integration Services, service
ms.assetid: 2c785b3b-4a0c-4df7-b5cd-23756dc87842
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4f2c1f5f17f55244787bf4f79949008be79088fe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48119420"
---
# <a name="integration-services-service-ssis-service"></a>Integration Services-Dienst (SSIS-Dienst)
  In den Themen in diesem Abschnitt wird der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst, ein Windows-Dienst zum Verwalten von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen, erläutert. Dieser Dienst ist nicht erforderlich, um Integration Services-Pakete zu erstellen, zu speichern und auszuführen. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] unterstützt den [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst für die Abwärtskompatibilität mit früheren Versionen von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] speichert [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Objekte, Einstellungen und operative Daten in der `SSISDB`-Datenbank für Projekte, die mithilfe des Projektbereitstellungsmodells auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Server bereitgestellt wurden. Der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Server, bei dem es sich um eine Instanz der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank-Engine handelt, hostet die Datenbank. Weitere Informationen zur Verschlüsselung finden Sie unter [SSIS-Katalog](../catalog/ssis-catalog.md). Weitere Informationen zum Bereitstellen eines Projekts auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server, finden Sie unter [Bereitstellen von Paketen auf dem Integration Services-Server](../deploy-projects-to-integration-services-server.md).  
  
## <a name="management-capabilities"></a>Managementfunktionen  
 Der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst ist ein Windows-Dienst zur Verwaltung von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen. Der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst steht nur in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]zur Verfügung.  
  
 Beim Ausführen des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienstes stehen folgende Verwaltungsfunktionen zur Verfügung:  
  
-   Starten von lokal und remote gespeicherten Paketen  
  
-   Beenden von lokal und remote ausgeführten Paketen  
  
-   Überwachen von lokal und remote ausgeführten Paketen  
  
-   Importieren und Exportieren von Paketen  
  
-   Verwalten des Paketspeichers  
  
-   Anpassen von Speicherordnern  
  
-   Beenden von ausgeführten Paketen beim Beenden des Dienstes  
  
-   Anzeigen des Windows-Ereignisprotokolls  
  
-   Herstellen von Verbindungen mit mehreren [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Servern  
  
## <a name="startup-type-for-integration-services-service"></a>Starttyp für Integration Services-Dienst  
 Der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst wird zusammen mit der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Komponente von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installiert. Standardmäßig wird der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst gestartet, und der Starttyp des Dienstes ist auf automatisch festgelegt. Der Dienst muss ausgeführt werden, damit die im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketspeicher gespeicherten Pakete überwacht werden. Als [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paketspeicher können entweder die msdb-Datenbank einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder die dazu bestimmten Ordner des Dateisystems dienen.  
  
 Der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienst ist nicht erforderlich, wenn Sie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete lediglich entwerfen und ausführen möchten. Der Dienst ist jedoch zum Auflisten und Überwachen von Paketen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]erforderlich.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Festlegen der Eigenschaften des Integration Services-Diensts](../set-the-properties-of-the-integration-services-service.md)  
  
-   [Anzeigen von Ereignissen für den Integration Services-Dienst](../view-events-for-the-integration-services-service.md)  
  
  
