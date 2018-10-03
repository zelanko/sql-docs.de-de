---
title: Nicht mehr unterstützte SQL Server-Funktionen in SQLServer 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 0678bfbc-5d3f-44f4-89c0-13e8e52404da
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0aec881fd3257a42151338953015a0d88b56ea8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48063840"
---
# <a name="discontinued-sql-server-features-in-sql-server-2014"></a>Nicht mehr unterstützte SQL Server-Funktionen in SQL Server 2014
  In diesem Thema werden die Funktionen beschrieben, die nach dem Upgrade auf [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] nicht mehr zur Verfügung stehen.  
  
## <a name="discontinued-features-in-includesssql14includessssql14-mdmd"></a>Nicht mehr unterstützte Funktionen in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Keine nicht mehr unterstützten Funktionen in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
## <a name="discontinued-features-in-includesssql11includessssql11-mdmd"></a>Nicht mehr unterstützte Funktionen in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="discontinued-active-directory-helper-service"></a>Eingestellter Hilfsdienst für Active Directory  
 Der Active Directory-Hilfsdienst und die zugehörigen Komponenten wurden entfernt. In der folgenden Tabelle werden die zugehörigen und somit entfernten Komponenten aufgeführt:  
  
|Kategorie|Nicht mehr unterstützte Funktion|Ersatz|  
|--------------|--------------------------|-----------------|  
|Gespeicherte Systemprozeduren|sp_ActiveDirectory_Obj<br /><br /> sp_ActiveDirectory_SCP<br /><br /> sp_ActiveDirectory_Start|Kein Ersatz verfügbar|  
  
## <a name="discontinued-features-in-sql-server-2008-r2"></a>Nicht mehr unterstützte Funktionen in SQL Server 2008 R2  
  
### <a name="64-bit-platform-support-in-reporting-services"></a>Unterstützung der 64-Bit-Plattform in Reporting Services  
 Ab [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Komponente keine Unterstützung mehr für Itanium-basierte Server unter Windows Server 2003 oder Windows Server 2003 R2. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt weiterhin andere 64-Bit-Betriebssysteme, einschließlich Windows Server°2008 für Itanium-basierte Systeme und Windows Server°2008°R2 für Itanium-basierte Systeme. Um von einer [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]-Installation mit [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] unter einer Itanium-basierten Systemedition von Windows Server 2003 oder Windows Server 2003 R2 auf [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] zu aktualisieren, müssen Sie zunächst das Betriebssystem aktualisieren.  
  
## <a name="discontinued-features-in-sql-server-2008"></a>Nicht mehr unterstützte Funktionen in SQL Server 2008  
  
### <a name="discontinued-sql-dmo-from-sql-server-express-installation"></a>Nicht mehr unterstütztes SQL-DMO aus der SQL Server Express-Installation  
 SQL-DMO für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] wurde aus [!INCLUDE[ssExpressEd10](../includes/ssexpressed10-md.md)] entfernt. Es wird empfohlen, Anwendungen, die diese Funktion derzeit nutzen, so schnell wie möglich zu ändern. Wenn Sie für die SQL-DMO unterstützen, müssen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express installieren Sie die Abwärtskompatibilitätskomponenten aus dem [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] feature Packs aus der [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=51230). Verwenden Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Objects (SMO) für neue Entwicklungen.  
  
### <a name="discontinued-option-for-web-assistant"></a>Nicht mehr unterstützte Option für Web-Assistent  
 Die Option `sp_configure` zur Aktivierung des Web-Assistenten wurde aus [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] entfernt. Stattdessen wird die Verwendung von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] empfohlen.  
  
### <a name="surface-area-configuration-tool"></a>Oberflächenkonfigurations-Tool  
 Das Oberflächen-Konfigurationstool nicht mehr für die [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Die folgende Tabelle zeigt, welche Elemente Sie zum Konfigurieren von Einstellungen, Optionen und Komponentenfunktionen in dieser Version verwenden können.  
  
|Ersatz-Einstellungen und Komponentenfunktionen|Vorgehensweise: Konfigurieren|  
|-------------------------------------------------|----------------------|  
|Protokolle, Verbindung und Startoptionen|Verwenden Sie den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Konfigurations-Manager.|  
|[!INCLUDE[ssDE](../includes/ssde-md.md)]-Funktionen|Verwenden Sie die richtlinienbasierte Verwaltung, die Eigenschafteneinstellungen in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder sp_Configure.|  
|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Funktionen|Verwenden Sie die Eigenschafteneinstellungen in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Enableintegratedsecurity-Eigenschaft|Verwenden Sie die Eigenschafteneinstellungen in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] – "Geplante Ereignisse und Berichtsübermittlung" und "Web und HTTP-Zugriff"|Bearbeiten Sie die Konfigurationsdatei RSReportServer.config.|  
|Befehlszeilenoptionen|In dieser Version nicht unterstützt|  
|SOAP und [!INCLUDE[ssSB](../includes/sssb-md.md)]-Endpunkte|Verwendung [CREATE ENDPOINT](/sql/t-sql/statements/create-endpoint-transact-sql)und [ALTER ENDPOINT](/sql/t-sql/statements/alter-endpoint-transact-sql).|  
  
### <a name="discontinued-command-prompt-parameters-for-sql-server-setup"></a>Nicht mehr unterstützte Eingabeaufforderungsparameter für das SQL Server-Setup  
 Die folgende Tabelle enthält die Eingabeaufforderungsparameter für das Setup aus früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], die in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] nicht unterstützt werden.  
  
|Nicht mehr unterstützter Parameter|Ersatzparameter|  
|----------------------------|---------------------------|  
|ADDLOCAL|/ACTION=Uninstall und /FUNKTIONEN|  
|DISABLENETWORKPROTOCOLS|/ TCPENABLED für TCP/IP<sup>1</sup>|  
|DISABLENETWORKPROTOCOLS|/ NPENABLED für Named Pipes<sup>1</sup>|  
|INSTALLSQLDATADIR|/SQLUSERDBDIR<br /><br /> /SQLUSERDBLOGDIR<br /><br /> /SQLBACKUPDIR<br /><br /> /SQLTEMPDBDIR<br /><br /> /SQLTEMPDBLOGDIR|  
|REINSTALL|Keine Entsprechung in dieser Version.|  
|REINSTALLMODE|Keine Entsprechung in dieser Version.|  
|REMOVE|/ACTION=Uninstall und /FUNKTIONEN|  
|SAMPLEDATABASE|Keine Entsprechung in dieser Version.|  
|SAVESYSDB|Keine Entsprechung in dieser Version.|  
|SKUUPGRADE<sup>2</sup>|Keine Entsprechung in dieser Version.|  
|UPGRADE|/ACTION=Upgrade und /FUNKTIONEN|  
|USESYSDB|Keine Entsprechung in dieser Version.|  
  
 <sup>1</sup>diesen Parameter nur für die Installation gültig sind.  
  
 <sup>2</sup>ab [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], geben Sie/Action = EditionUpgrade, um eine vorhandene Edition von aktualisieren [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf eine andere Edition und ohne die ursprünglichen Installationsmedien zu verwenden. Weitere Informationen zu unterstützten Versions- und Editionsupgrades finden Sie unter [Supported Version and Edition Upgrades](../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
 Weitere Informationen finden Sie unter [Installieren von SQL Server 2014 über die Eingabeaufforderung](../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
  
