---
title: Entfernen von Verweisen auf nicht dokumentierte Systemtabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system tables [SQL Server]
- system tables [SQL Server]
ms.assetid: 010b1236-2219-4bf4-a6db-e3fc3abfa37a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 45c38038ee3d3214e4303c0ddbe0110be926c37e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059201"
---
# <a name="remove-references-to-undocumented-system-tables"></a>Entfernen von Verweisen auf nicht dokumentierte Systemtabellen
  Viele Systemtabellen, die in früheren Versionen nicht dokumentiert waren, haben sich geändert oder sind nicht mehr vorhanden. Daher kann ihre Verwendung nach einem Upgrade zu Fehlern führen. Da der Upgrade Advisor nach Verweisen auf Systemtabellennamen sucht, enthält sein Bericht Verweise auf alle Benutzertabellen, die dieselben Namen wie Systemtabellen haben.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Die folgenden nicht dokumentierten Systemtabellen wurden entfernt:  
  
-   **spt_datatype_info**  
  
-   **spt_datatype_info_ext**  
  
-   **spt_provider_types**  
  
-   **spt_server_info**  
  
-   **spt_values**  
  
-   **sysfulltextnotify**  
  
-   **syslocks**  
  
-   **sysproperties**  
  
-   **sysprotects_aux**  
  
-   **sysprotects_view**  
  
-   **SYSREMOTE_CATALOGS**  
  
-   **SYSREMOTE_COLUMN_PRIVILEGES**  
  
-   **SYSREMOTE_COLUMNS**  
  
-   **SYSREMOTE_FOREIGN_KEYS**  
  
-   **SYSREMOTE_INDEXES**  
  
-   **SYSREMOTE_PRIMARY_KEYS**  
  
-   **SYSREMOTE_PROVIDER_TYPES**  
  
-   **SYSREMOTE_SCHEMATA**  
  
-   **SYSREMOTE_STATISTICS**  
  
-   **SYSREMOTE_TABLE_PRIVILEGES**  
  
-   **SYSREMOTE_TABLES**  
  
-   **SYSREMOTE_VIEWS**  
  
-   **syssegments**  
  
-   **sysxlogins**  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie die Anwendungen entsprechend der folgenden Tabelle.  
  
|Statt|Zweck|  
|----------------|---------|  
|**sysfulltextnotify**|Die **tablefulltextpdingchanges** -Eigenschaft der OBJECTPROPERTYEX-Funktion.|  
|**syslocks**|dynamische Verwaltungs Sicht **sys. dm_tran_locks** oder sp_lock oder die **sys.sysLockInfo** -Kompatibilitäts Sicht.|  
|**sysproperties**|**sys. extended_properties** -Katalog Sicht oder die **fn_listextendedproperty** -Funktion|  
|**sysxlogins**|**sys. server_principals** -Katalog Sicht oder **syslogins** -Kompatibilitäts Sicht.|  
|alle **spt_** Tabellen|Kein Ersatz verfügbar|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
