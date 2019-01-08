---
title: Einführung in SQL Server Management Studio für Business Intelligence | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio for Integration Services
- SQL Server Management Studio for Reporting Services
- SQL Server Management Studio for Analysis Services
ms.assetid: ffaa77b7-03d0-4d7a-aa42-c5091a4f2ceb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ab38a4465ec03415f9c1d903419ccbe2b07e6a86
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52808472"
---
# <a name="introduction-to-sql-server-management-studio-for-business-intelligence"></a>Einführung in SQL Server Management Studio für Business Intelligence
  Verwenden Sie [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] für den Zugriff auf und die Verwaltung von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] und [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Obwohl alle drei Business Intelligence-Technologien auf [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]basieren, weichen die mit den jeweiligen Technologien verbundenen Verwaltungsaufgaben leicht voneinander ab.  
  
> [!NOTE]  
>  Verwenden Sie zum Erstellen und Ändern von Projektmappen in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]und [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]und nicht [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ist eine Entwicklungsumgebung, die auf [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[vsprvs](../includes/vsprvs-md.md)]basiert.  
  
## <a name="managing-analysis-services-solutions-using-sql-server-management-studio"></a>Verwalten von Analysis Services-Lösungen mit SQL Server Management Studio  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ermöglicht es Ihnen, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Objekte zu verwalten, beispielsweise Ausführen von Sicherungen und Verarbeiten von Objekten.  
  
 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] bietet ein [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Skriptprojekt, in dem Sie in Multidimensional Expressions (MDX), Data Mining Extensions (DMX) und XML for Analysis (XMLA) geschriebene Skripts entwickeln und speichern können. Sie verwenden [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Skriptprojekte, um Verwaltungsaufgaben auszuführen oder Objekte wie Datenbanken oder Cubes in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanzen neu zu erstellen. Sie können beispielsweise ein XMLA-Skript in einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Skriptprojekt entwickeln, das neue Objekte direkt auf einer vorhandenen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Instanz erstellt. Die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Skriptprojekte können als Teil einer Lösung gespeichert werden und mit dem Quellcodeverwaltungssystem integriert werden.  
  
 Weitere Informationen zur Verwendung von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], finden Sie unter [Analysis Services-Skriptprojekt in SQL Server Management Studio](../analysis-services/instances/analysis-services-scripts-project-in-sql-server-management-studio.md).  
  
## <a name="managing-integration-services-solutions-using-sql-server-management-studio"></a>Verwalten von Integration Services-Lösungen mit SQL Server Management Studio  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ermöglicht Ihnen die Verwendung des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Diensts, mit dem Sie Pakete verwalten und ausgeführte Pakete überwachen können. Zudem können Sie [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] zur Organisation von Paketen in Ordnern, zum Ausführen von Paketen, zum Im- und Exportieren von Paketen, zum Migrieren von DTS-Paketen (Data Transformation Services) sowie zum Aktualisieren von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paketen verwenden.  
  
## <a name="managing-reporting-services-projects-using-sql-server-management-studio"></a>Verwalten von Reporting Services-Projekten mit SQL Server Management Studio  
 Verwenden Sie SQL Server Management Studio zum Aktivieren von Reporting Services-Funktionen und zum Verwalten von Server und Datenbanken sowie von Rollen und Aufträgen.  
  
 Verwalten Sie freigegebene Zeitpläne mit dem Ordner Freigegebene Zeitpläne, und verwalten Sie Berichtsserver-Datenbanken (ReportServer, ReportServerTempdb). Sie können darüber hinaus eine RSExecRole-Rolle in der master-Systemdatenbank erstellen, wenn Sie eine Berichtsserver-Datenbank in eine neue oder andere SQL Server-Datenbank-Engine ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)]) verschieben. Weitere Informationen zu diesen Aufgaben finden Sie unter den folgenden Themen:  
  
-   [Reporting Services in SQL Server Management Studio (SSRS)](../reporting-services/tools/reporting-services-in-sql-server-management-studio-ssrs.md)  
  
-   [Verwalten eine Berichtsserver-Datenbank &#40;einheitlicher SSRS-Modus&#41;](../reporting-services/report-server/report-server-database-ssrs-native-mode.md)  
  
-   [Create the RSExecRole (Erstellen der Rolle RSExecRole)](../reporting-services/security/create-the-rsexecrole.md)  
  
 Zudem verwalten Sie den Server, indem Sie verschiedene Funktionen aktivieren und konfigurieren, Serverstandardwerte festlegen und Rollen und Aufträge verwalten. Weitere Informationen zu diesen Aufgaben finden Sie unter den folgenden Themen:  
  
-   [Festlegen von Berichtsservereigenschaften &#40;Management Studio&#41;](../reporting-services/tools/set-report-server-properties-management-studio.md)  
  
-   [Erstellen, Löschen oder Ändern einer Rolle &#40;Management Studio&#41;](../reporting-services/security/role-definitions-create-delete-or-modify.md)  
  
-   [Enable and Disable Client-Side Printing for Reporting Services (Aktivieren und Deaktivieren des clientseitige Drucks für Reporting Services)](../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen mehrdimensionaler Modelle mit SQL Server-Datentools &#40;SSDT&#41;](../analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)   
 [Reporting Services in SQL Server-Datentools &#40;SSDT&#41;](../reporting-services/tools/reporting-services-in-sql-server-data-tools-ssdt.md)  
  
  
