---
title: Aktualisieren von Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
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
author: Minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cdd9e34e57694efc1234a2f0245833596644cb73
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68889185"
---
# <a name="upgrade-analysis-services"></a>Aktualisieren von Analysis Services
  Verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup zum Ausführen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Upgrades. Ausführliche Informationen zum Upgrade [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von im SharePoint-Modus finden Sie unter [Upgrade PowerPivot für SharePoint](upgrade-power-pivot-for-sharepoint.md). Weitere Informationen zum Aktualisieren einer vorhandenen SQL Server Instanz finden Sie unter [Upgrade auf SQL Server 2014 mit dem Installations-Assistenten &#40;Setup&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md).  
  
## <a name="known-upgrade-issues"></a>Bekannte Upgradeprobleme  
 Überprüfen Sie [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]vor dem Upgrade auf Folgendes:  
  
-   [Anmerkungen zu dieser Version von SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).  
  
-   Informationen zu den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Features und Funktionen, die eingestellt, veraltet oder geändert wurden, finden Sie unter [Analysis Services Abwärtskompatibilität](https://docs.microsoft.com/analysis-services/analysis-services-backward-compatibility).  
  
## <a name="pre-upgrade-checklist"></a>Prüfliste vor der Aktualisierung  
 Lesen Sie vor dem Upgrade die folgenden Informationen:  
  
-   [Unterstützte Versions- und Editionsupgrades](supported-version-and-edition-upgrades.md)  
  
-   [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Überprüfen der Parameter für die Systemkonfigurationsprüfung](check-parameters-for-the-system-configuration-checker.md)  
  
-   [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
-   [Sichern und Wiederherstellen von Analysis Services-Datenbanken](https://docs.microsoft.com/analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases)  
  
-   [Verwenden von Upgrade Advisor zur Vorbereitung auf Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)  
  
## <a name="upgrading-analysis-services"></a>Aktualisieren von Analysis Services  
 Sie können Server und Daten auf verschiedene Art und Weise aktualisieren:  
  
-   Ein direktes **Upgrade** ersetzt die vorhandenen Programmdateien durch [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Programmdateien. Datenbanken verbleiben am gleichen Ort. Programmordner werden aktualisiert, um den neuen Namen widerzuspiegeln.  
  
-   Bei einem parallelen **Upgrade** handelt es sich um eine Neuinstallation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] auf dem gleichen Computer, auf dem bereits eine Analysis Services Instanz vorhanden ist. Sie können Datenbanken zur neuen Instanz auf dem gleichen Computer verschoben und dann die alte Version deinstallieren, wenn Sie sie nicht mehr verwenden.  
  
-   Sie können auch Analysis Services auf neuer Hardware installieren und dann vorhandene Datenbanken zu diesem Server migrieren.  
  
## <a name="in-place-upgrade"></a>Direktes Upgrade  
 Sie können eine vorhandene Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aktualisieren und im Rahmen des Upgradevorgangs vorhandene Datenbanken automatisch von der alten Instanz zur neuen Instanz migrieren. Da die Metadaten und die binären Daten zwischen den beiden Versionen kompatibel sind, behalten Sie die Daten nach dem Upgrade bei, und es ist nicht nötig, eine manuelle Datenmigration durchzuführen.  
  
 Um eine vorhandene Instanz zu aktualisieren, führen Sie das Setup aus, und geben Sie den Namen der vorhandenen Instanz als Namen für die neue Instanz an.  
  
## <a name="upgrading-databases"></a>Datenbankupgrades  
 Datenbanken, die in früheren Versionen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erstellt wurden, werden auf dem aktualisierten Server unter einer älteren Einstellung für den Datenbank-Kompatibilitätsgrad ausgeführt. Datenbanken, die in den folgenden Versionen erstellt wurden, verfügen über den Datenbank-Kompatibilitätsgrad 105. Sie können den Kompatibilitätsgrad ändern, wenn Sie Funktionen verwenden möchten, die einen neueren Datenbank-Kompatibilitätsgrad erfordern. Andernfalls können Sie die Datenbanken auf dem aktualisierten Server mithilfe der ursprünglichen Einstellungen ausführen. Weitere Informationen finden Sie unter [Festlegen des Kompatibilitäts Grad einer mehrdimensionalen Datenbank &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/compatibility-level-of-a-multidimensional-database-analysis-services).  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von den-Editionen unterstützte Funktionen SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Planen einer SQL Server Installation](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Grundlegendes zur Microsoft OLAP-Architektur](https://docs.microsoft.com/analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-architecture)   
 [UpgradePowerPivot für SharePoint](upgrade-power-pivot-for-sharepoint.md)   
 [Installieren von Analysis Services im mehrdimensionalen und Data Mining-Modus](../../sql-server/install/install-analysis-services-in-multidimensional-and-data-mining-mode.md)   
 [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
