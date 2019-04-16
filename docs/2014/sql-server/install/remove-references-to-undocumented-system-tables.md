---
title: Entfernen Sie Verweise auf nicht dokumentierte Systemtabellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- undocumented system tables [SQL Server]
- system tables [SQL Server]
ms.assetid: 010b1236-2219-4bf4-a6db-e3fc3abfa37a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0c2c25120191b88abcf177723749aa5c46ba44ff
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59582553"
---
# <a name="remove-references-to-undocumented-system-tables"></a>Entfernen von Verweisen auf nicht dokumentierte Systemtabellen
  Viele Systemtabellen, die in früheren Versionen nicht dokumentiert waren, haben sich geändert oder sind nicht mehr vorhanden. Daher kann ihre Verwendung nach einem Upgrade zu Fehlern führen. Da der Upgrade Advisor nach Verweisen auf Systemtabellennamen sucht, enthält sein Bericht Verweise auf alle Benutzertabellen, die dieselben Namen wie Systemtabellen haben.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
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
  
|Statt|Verwenden Sie|  
|----------------|---------|  
|**sysfulltextnotify**|**TableFulltextPendingChanges** Eigenschaft der OBJECTPROPERTYEX-Funktion.|  
|**syslocks**|**Sys. dm_tran_locks** dynamische verwaltungssicht oder Sp_lock, oder die **sys.syslockinfo** -kompatibilitätssicht angezeigt.|  
|**sysproperties**|**Sys. extended_properties** -Katalogsicht oder der **Fn_listextendedproperty** Funktion|  
|**sysxlogins**|**Sys. server_principals** Katalogsicht oder **Syslogins** -kompatibilitätssicht angezeigt.|  
|alle **Spt_** Tabellen|Kein Ersatz verfügbar|  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
