---
title: Interoperabilität und Koexistenz (Integration Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interoperability and coexistence [Integration Services]
- Integration Services, interoperability and coexistence
ms.assetid: edfbcd56-012f-462e-a542-95491394fda9
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: d0db34c7b894dc7b92ad6061d4f3c53c1cd2dbe9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048292"
---
# <a name="interoperability-and-coexistence-integration-services"></a>Interoperabilität und Koexistenz (Integration Services)
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services (SSIS) können gleichzeitig mit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services und [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services verwendet werden.  
  
## <a name="features-and-differences"></a>Funktionen und Unterschiede  
 In der folgenden Tabelle sind einige Unterschiede zwischen der aktuellen und der früheren Version von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] aufgelistet.  
  
|Funktion|[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]|[!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]|[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]|  
|-------------|-------------------------------|---------------------------------|---------------------------------|  
|Entwicklungsumgebung|[SQL Server 2014 Data Tools – Business Intelligence für Visual Studio 2012 CTP 2](http://www.microsoft.com/download/details.aspx?id=40736)<br /><br /> [SQL Server 2014 Data Tools - Business Intelligence für Visual Studio 2013](http://www.microsoft.com/download/details.aspx?id=42313)|[SQL Server Data Tools für Visual Studio 2010](http://msdn.microsoft.com/library/hh500335\(v=vs.103\).aspx)<br /><br /> [SQL Server Data Tools – Business Intelligence für Visual Studio 2012](http://www.microsoft.com/download/details.aspx?id=36843)|Business Intelligence Development Studio ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)])|  
|Verwaltungsumgebung|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
|Hauptsystemtabelle in msdb zum Speichern von Paketen|sysssispackages|sysssispackages|sysssispackages|  
|Eingabeaufforderungs-Haupthilfsprogramm zum Ausführen von Paketen|**dtexec** (dtexec.exe), Version 2014|**dtexec** (dtexec.exe), Version 2012|**dtexec** (dtexec.exe), Version 2008|  
|Standard-Stammdateisystemordner|C:\Programme\Microsoft SQL Server\120\DTS|C:\Programme\Microsoft SQL Server\110\DTS|C:\Programme\Microsoft SQL Server\100\DTS|  
|Standard-Stammregistrierungsschlüssel|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS|  
  
## <a name="side-by-side-compatibility-issues"></a>Kompatibilitätsprobleme bei paralleler Ausführung  
 Wenn [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services gleichzeitig mit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services und [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services installiert sind, können Sie folgende Tasks durchführen:  
  
-   **Entwerfen Sie Pakete in SQL Server-Datentools**. Entwickeln und verwalten Sie Pakete auf der Basis entsprechender Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit den folgenden Tools.  
  
    -   Verwenden der [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Version von Business Intelligence Development Studio zum Entwickeln und verwalten Sie Pakete auf der Grundlage von [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]  
  
    -   Verwenden der [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Version [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] zu entwickeln und verwalten Sie Pakete auf der Grundlage von [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
    -   Verwenden der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Version [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] zu entwickeln und verwalten Sie Pakete auf der Grundlage von [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
-   **Laden und Ausführen von Paketen** Sie laden und Ausführen von Paketen, die im entwickelt wurden [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Version [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Wenn Sie das Paket einem vorhandenen Projekt hinzufügen, wird das Paket permanent auf das Format aktualisiert, das von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services verwendet wird. Wenn Sie die Paketdatei in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] öffnen, wird das Paket vorübergehend auf das Format aktualisiert, das von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services verwendet wird. Wenn Sie die Änderungen am Paket speichern, wird das Paket dauerhaft aktualisiert. Nach dem Speichern in das Format, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services verwendet, die Pakete können nicht mehr geöffnet werden, in der entsprechenden [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] -Version von Business Intelligence Development Studio ausführen, die mit den entsprechenden [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integrationsservices oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services-Tools.  
  
-   **Verwalten von Paketen in SQL Server Management Studio**. Sie können keine Verbindung mit einer Instanz von der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Version von der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienstes mit der [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Version von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Sie können keine Verbindung mit einer Instanz von der [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder die [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Version von der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Diensts von der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Version des [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Mit der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Version von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] können Sie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete in einer Instanz von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] oder [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwalten. Sie müssen jedoch die Dienstkonfigurationsdatei ändern, um die Instanz von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] der Liste der von dem Dienst verwalteten Speicherorte hinzuzufügen. Weitere Informationen finden Sie unter [Konfigurieren des Integration Services-Diensts &#40;SSIS-Dienst&#41;](../service/integration-services-service-ssis-service.md).  
  
-   **Speichern von Paketen in SQL Server**. Sie können Pakete in den nachfolgend angegebenen Datenbanken speichern.  
  
    |Paketformat|Datenbank|  
    |--------------------|--------------|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integrationsservices|Msdb-Datenbank einer Instanz von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
    |[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integrationsservices|Msdb-Datenbank einer Instanz von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|  
    |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integrationsservices|Msdb-Datenbank einer Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
     In einer Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], Sie können Pakete importieren, von einer Instanz von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder von einer Instanz von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], aber Sie können Pakete exportieren, mit einer Instanz von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder mit einer Instanz von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
     In einer Instanz von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder einer Instanz von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] können Sie weder Pakete aus einer Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] importieren noch Pakete in eine entsprechende Instanz exportieren.  
  
-   **Ausführen von Paketen**. Ausführen können [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services und [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services-Paketen mithilfe der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Version der **Dtexec** Hilfsprogramm oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Wenn eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services-Tool lädt ein Paket, das entwickelt wurde [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], das Tool vorübergehend konvertiert wird, im Arbeitsspeicher, der das Paket Paketformat, die [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] verwendet. Wenn die [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Paket Probleme aufweist, die eine erfolgreiche Konvertierung verhindern, können die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services-Tool das Paket erst ausführen, diese Probleme behoben wurden. Weitere Informationen finden Sie unter [Upgrade Integration Services Packages](upgrade-integration-services-packages.md).  
  
  