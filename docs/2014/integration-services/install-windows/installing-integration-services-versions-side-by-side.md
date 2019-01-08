---
title: Interoperabilität und Koexistenz (Integrationsservices) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- interoperability and coexistence [Integration Services]
- Integration Services, interoperability and coexistence
ms.assetid: edfbcd56-012f-462e-a542-95491394fda9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0af7cfe8119c6ceb879c75ffee4497e62997f77f
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53355887"
---
# <a name="interoperability-and-coexistence-integration-services"></a>Interoperabilität und Koexistenz (Integration Services)
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services (SSIS) können gleichzeitig mit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services und [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services verwendet werden.  
  
## <a name="features-and-differences"></a>Funktionen und Unterschiede  
 In der folgenden Tabelle sind einige Unterschiede zwischen der aktuellen und der früheren Version von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]aufgelistet.  
  
|Funktion|[!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)]|[!INCLUDE[ssISversion11](../../includes/ssisversion11-md.md)]|[!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)]|  
|-------------|-------------------------------|---------------------------------|---------------------------------|  
|Entwicklungsumgebung|[SQL Server 2014 Data Tools – Business Intelligence für Visual Studio 2012 CTP 2](https://www.microsoft.com/download/details.aspx?id=40736)<br /><br /> [SQL Server 2014 Data Tools – Business Intelligence für Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=42313)|[SQL Server Datatools für Visual Studio 2010](https://msdn.microsoft.com/library/hh500335\(v=vs.103\).aspx)<br /><br /> [SQL Server Data Tools – Business Intelligence für Visual Studio 2012](https://www.microsoft.com/download/details.aspx?id=36843)|Business Intelligence Development Studio ([!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)])|  
|Verwaltungsumgebung|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
|Hauptsystemtabelle in msdb zum Speichern von Paketen|sysssispackages|sysssispackages|sysssispackages|  
|Eingabeaufforderungs-Haupthilfsprogramm zum Ausführen von Paketen|**dtexec** (dtexec.exe), Version 2014|**dtexec** (dtexec.exe), Version 2012|**dtexec** (dtexec.exe), Version 2008|  
|Standard-Stammdateisystemordner|C:\Programme\Microsoft SQL Server\120\DTS|C:\Programme\Microsoft SQL Server\110\DTS|C:\Programme\Microsoft SQL Server\100\DTS|  
|Standard-Stammregistrierungsschlüssel|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\120\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\110\SSIS|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS|  
  
## <a name="side-by-side-compatibility-issues"></a>Kompatibilitätsprobleme bei paralleler Ausführung  
 Wenn [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services gleichzeitig mit [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services und [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services installiert sind, können Sie folgende Tasks durchführen:  
  
-   **Entwerfen Sie Pakete in SQL Server-Datentools**. Entwickeln und verwalten Sie Pakete auf der Basis entsprechender Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mit den folgenden Tools.  
  
    -   Verwenden Sie die [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]-Version von Business Intelligence Development Studio zum Entwickeln und Verwalten von Paketen, die auf [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] basieren.  
  
    -   Entwickeln und verwalten Sie Pakete auf der Basis von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] mit der [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] -Version von [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
    -   Entwickeln und verwalten Sie Pakete auf der Basis von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit der [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] -Version von [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)].  
  
-   **Laden und Ausführen von Paketen** Sie können Pakete, die in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]entwickelt wurden, in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]laden und ausführen. Wenn Sie das Paket einem vorhandenen Projekt hinzufügen, wird das Paket permanent auf das Format aktualisiert, das von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services verwendet wird. Wenn Sie die Paketdatei in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]öffnen, wird das Paket vorübergehend auf das Format aktualisiert, das von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services verwendet wird. Wenn Sie die Änderungen am Paket speichern, wird das Paket dauerhaft aktualisiert. Nachdem Sie ein Paket in dem Format gespeichert haben, das von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services verwendet wird, kann es nicht mehr mit der entsprechenden [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] - oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] -Version von Business Intelligence Development Studio geöffnet und nicht mehr mit den entsprechenden [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services- oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services-Tools ausgeführt werden.  
  
-   **Verwalten von Paketen in SQL Server Management Studio**. Sie können keine Verbindung zu einer Instanz der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Dienstes mit der [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] - oder der [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] -Version von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]herstellen. Mit der [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] -Version von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] können Sie keine Verbindung zu einer Instanz der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] - oder [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version des [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]-Diensts herstellen. Mit der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version von [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] können Sie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete in einer Instanz von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] oder [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]verwalten. Sie müssen jedoch die Dienstkonfigurationsdatei ändern, um die Instanz von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] der Liste der von dem Dienst verwalteten Speicherorte hinzuzufügen. Weitere Informationen finden Sie unter [Konfigurieren des Integration Services-Diensts &#40;SSIS-Dienst&#41;](../service/integration-services-service-ssis-service.md).  
  
-   **Speichern von Paketen in SQL Server**. Sie können Pakete in den nachfolgend angegebenen Datenbanken speichern.  
  
    |Paketformat|Datenbank|  
    |--------------------|--------------|  
    |[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services|Msdb-Datenbank einer Instanz von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
    |[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services|Msdb-Datenbank einer Instanz von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|  
    |[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services|Msdb-Datenbank einer Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
     In einer Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]können Sie Pakete aus einer Instanz von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]importieren, Sie können jedoch keine Pakete in eine Instanz von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]exportieren.  
  
     In einer Instanz von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] oder einer Instanz von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]können Sie weder Pakete aus einer Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]importieren noch Pakete in eine entsprechende Instanz exportieren.  
  
-   **Ausführen von Paketen**. Sie können [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Integration Services und [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Integration Services-Pakete ausführen, indem Sie Version [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version des **dtexec** -Hilfsprogramms oder des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent verwenden. Wenn ein in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] oder [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] entwickeltes Paket mit einem [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]Integration Services-Tool geladen wird, wird das Paket vom Tool vorübergehend in das von [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] verwendete Paketformat konvertiert. Wenn das [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] - oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] -Paket Probleme aufweist, die eine erfolgreiche Konvertierung verhindern, kann das [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Integration Services-Tool das Paket erst ausführen, wenn diese Probleme behoben wurden. Weitere Informationen finden Sie unter [Upgrade Integration Services Packages](upgrade-integration-services-packages.md).  
  
  
