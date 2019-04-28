---
title: Entfernen Sie Anweisungen, die Systemobjekte ändern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- direct system catalog updates [SQL Server]
- system catalogs [SQL Server]
ms.assetid: 221b46c2-c27e-4df8-bd8c-8b990d6d5e98
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ebc7288bd7c72ce76df69d11c7a9fb0771764fca
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856143"
---
# <a name="remove-statements-that-modify-system-objects"></a>Entfernen von Anweisungen, mit denen Systemobjekte geändert werden
  Der Upgrade Advisor hat Anweisungen erkannt, die den Systemkatalog aktualisieren. Das direkte Aktualisieren von Systemkatalogen ist nicht zulässig. Ändern Sie Ihre SQL-Skripts, sodass sie offizielle und dokumentierte APIs verwenden.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Das direkte Aktualisieren von Systemkatalogen ist nicht zulässig. Jeder Versuch generiert die folgende Fehlermeldung:  
  
 `Server: Msg 259, Level 16, State 1, Line 1`  
  
 `Ad hoc updates to system catalogs are not allowed.`  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie Ihre SQL-Skripts, sodass sie offizielle und dokumentierte APIs verwenden. Verwenden Sie beispielsweise ALTER DATABASE *Database_name* SET EMERGENCY, statt eine UPDATE-Anweisung für die **Sysdatabases** -Systemtabelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
