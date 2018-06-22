---
title: Aktualisieren von Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading databases
- databases [Analysis Services], upgrading
- installing Analysis Services, side-by-side installations
- Analysis Services upgrades
- Analysis Services upgrades, about upgrading Analysis Services
- SSAS, database migration
- upgrading Analysis Services
- installing Analysis Services, upgrading
- SSAS, upgrading
ms.assetid: a131d329-386e-4470-aaa9-ffcde4e5ec0c
caps.latest.revision: 63
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: dd4ae8ef0eb99859885dfbd33af284c843c282d4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048793"
---
# <a name="upgrade-analysis-services"></a>Aktualisieren von Analysis Services
  Verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup zum Ausführen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Upgrades. Ausführliche Informationen zum Aktualisieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im SharePoint-Modus finden Sie unter [Aktualisieren von PowerPivot für SharePoint](upgrade-power-pivot-for-sharepoint.md). Für Weitere Informationen zum Aktualisieren einer vorhandenen SQL Server-Instanz, finden Sie unter [ein Upgrade auf SQL Server 2014 mithilfe des Installations-Assistenten &#40;Setup&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md).  
  
## <a name="known-upgrade-issues"></a>Bekannte Upgradeprobleme  
 Lesen Sie vor dem Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]die folgenden Themen:  
  
-   [Versionsanmerkungen zu SQL Server 2014](http://go.microsoft.com/fwlink/?LinkID=296445).  
  
-   Informationen dazu, welche [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Features und Funktionen nicht mehr unterstützt, veraltet, oder geändert wurden finden Sie unter [Analysis Services Backward Compatibility](../../analysis-services/analysis-services-backward-compatibility.md).  
  
## <a name="pre-upgrade-checklist"></a>Prüfliste vor dem Upgrade  
 Lesen Sie vor dem Upgrade die folgenden Informationen:  
  
-   [Unterstützte Versions- und Editionsupgrades](supported-version-and-edition-upgrades.md)  
  
-   [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Überprüfen der Parameter für die Systemkonfigurationsprüfung](check-parameters-for-the-system-configuration-checker.md)  
  
-   [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [Sichern und Wiederherstellen von Analysis Services-Datenbanken](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)  
  
-   [Verwenden von Upgrade Advisor zur Vorbereitung auf Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
## <a name="upgrading-analysis-services"></a>Aktualisieren von Analysis Services  
 Sie können Server und Daten auf verschiedene Art und Weise aktualisieren:  
  
-   Ein **direktes Upgrade** ersetzt die vorhandenen durch Programmdateien [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Programmdateien. Datenbanken verbleiben am gleichen Ort. Programmordner werden aktualisiert, um den neuen Namen widerzuspiegeln.  
  
-   Ein **Side-by-Side-Upgrade** ist eine Neuinstallation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] auf demselben Computer, die eine vorhandene Analysis Services-Instanz verfügt. Sie können Datenbanken zur neuen Instanz auf dem gleichen Computer verschoben und dann die alte Version deinstallieren, wenn Sie sie nicht mehr verwenden.  
  
-   Sie können auch Analysis Services auf neuer Hardware installieren und dann vorhandene Datenbanken zu diesem Server migrieren.  
  
## <a name="in-place-upgrade"></a>Direktes Upgrade  
 Sie können eine vorhandene Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aktualisieren und als Teil des Upgradevorgangs vorhandene Datenbanken automatisch von der alten Instanz in die neue migrieren. Da die Metadaten und die binären Daten zwischen den beiden Versionen kompatibel sind, behalten Sie die Daten nach dem Upgrade bei, und es ist nicht nötig, eine manuelle Datenmigration durchzuführen.  
  
 Um eine vorhandene Instanz zu aktualisieren, führen Sie das Setup aus, und geben Sie den Namen der vorhandenen Instanz als Namen für die neue Instanz an.  
  
## <a name="upgrading-databases"></a>Datenbankupgrades  
 Datenbanken, die in früheren Versionen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellt wurden, werden auf dem aktualisierten Server unter einer älteren Einstellung für den Datenbank-Kompatibilitätsgrad ausgeführt. Datenbanken, die in den folgenden Versionen erstellt wurden, verfügen über den Datenbank-Kompatibilitätsgrad 105. Sie können den Kompatibilitätsgrad ändern, wenn Sie Funktionen verwenden möchten, die einen neueren Datenbank-Kompatibilitätsgrad erfordern. Andernfalls können Sie die Datenbanken auf dem aktualisierten Server mithilfe der ursprünglichen Einstellungen ausführen. Weitere Informationen finden Sie unter [legen Sie den Kompatibilitätsgrad einer mehrdimensionalen Datenbank &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services.md).  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Von den Editionen von SQLServer 2014 unterstützte Funktionen](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Planen einer SQL Server-Installation](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Grundlegendes zur Microsoft OLAP-Architektur](../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)   
 [Aktualisieren von PowerPivot für SharePoint](upgrade-power-pivot-for-sharepoint.md)   
 [Installieren von Analysis Services im mehrdimensionalen Modus und im Data Mining-Modus](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md)   
 [PowerPivot für SharePoint 2010-Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  