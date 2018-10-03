---
title: SQL Server Integration Services (SSIS)-Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 67a74b8b9958eb52426a4f2bc8f36cd14c005f87
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074995"
---
# <a name="integration-services-ssis-server"></a>Integration Services (SSIS)-Server
  Nachdem Sie Pakete und Konfigurationen in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]entworfen und getestet haben, können Sie die Projekte, die die Pakete enthalten, auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server bereitstellen.  
  
 Der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Server stellt eine Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] dar, die als Host für die `SSISDB`-Datenbank fungiert. Die Datenbank speichert die folgenden Objekte: Pakete, Projekte, Parameter, Berechtigungen, Servereigenschaften und Verwendungsverlauf.  
  
 Die `SSISDB`-Datenbank macht die Objektinformationen in öffentlichen Sichten verfügbar, die Sie abfragen können. Die Datenbank stellt auch gespeicherte Prozeduren bereit, die Sie aufrufen können, um die Objekte zu verwalten.  
  
 Bevor Sie die Projekte auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Server bereitstellen können, müssen Sie den `SSISDB`-Katalog erstellen.  
  
 Eine Übersicht über die Funktionen des SSISDB-Katalogs finden Sie unter [SSIS-Katalog](ssis-catalog.md).  
  
## <a name="high-availability"></a>Hohe Verfügbarkeit  
 Wie andere Benutzerdatenbanken, die `SSISDB` -Datenbank unterstützt die datenbankspiegelung und Replikation. Weitere Informationen zur Spiegelung und Replikation finden Sie unter [Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Sie können auch die hohe Verfügbarkeit von SSISDB und die Inhalte bereitstellen, indem Sie die SSIS- und AlwaysOn-Verfügbarkeitsgruppen verwenden. Weitere Informationen finden Sie im folgenden Blogbeitrag von Matt Masson bei blogs.msdn.com: [SSIS mit AlwaysOn](http://go.microsoft.com/fwlink/?LinkId=255873).  
  
##  <a name="ssms"></a> Integration Services-Server in SQL Server Management Studio  
 Wenn Sie eine Verbindung mit einer Instanz des [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]s herstellen, die als Host für die `SSISDB`-Datenbank fungiert, werden die folgenden Objekte im Objekt-Explorer angezeigt:  
  
-   **SSISDB-Datenbank**  
  
     Die `SSISDB` Datenbank angezeigt wird, unter dem **Datenbanken** Knoten im Objekt-Explorer. Sie können die Sichten abfragen und die gespeicherten Prozeduren aufrufen, die zur Verwaltung des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Servers sowie der darauf gespeicherten Objekte verwendet werden.  
  
-   **Integration Services-Kataloge**  
  
     Unter dem Knoten **Integration Services-Kataloge** befinden sich Ordner für [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekte und -Umgebungen.  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Erstellen des SSIS-Katalogs](../create-the-ssis-catalog.md)  
  
-   [Anzeigen der Liste der auf dem Integration Services-Server gespeicherten Pakete](view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Bereitstellen von Projekten auf dem Integration Services-Server](../deploy-projects-to-integration-services-server.md)  
  
-   [Ausführen eines Pakets auf dem SSIS-Server mit SQL Server Management Studio](../run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Blogeintrag zu [SSIS mit AlwaysOn](http://go.microsoft.com/fwlink/?LinkId=255873)auf blogs.msdn.com.  
  
  
