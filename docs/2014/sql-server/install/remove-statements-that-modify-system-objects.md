---
title: Entfernen von Anweisungen, mit denen Systemobjekte geändert werden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- direct system catalog updates [SQL Server]
- system catalogs [SQL Server]
ms.assetid: 221b46c2-c27e-4df8-bd8c-8b990d6d5e98
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 526181bc4bf7ab81df2eaa25f19e7627c9b7af10
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059157"
---
# <a name="remove-statements-that-modify-system-objects"></a>Entfernen von Anweisungen, mit denen Systemobjekte geändert werden
  Der Upgrade Advisor hat Anweisungen erkannt, die den Systemkatalog aktualisieren. Das direkte Aktualisieren von Systemkatalogen ist nicht zulässig. Ändern Sie Ihre SQL-Skripts, sodass sie offizielle und dokumentierte APIs verwenden.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Das direkte Aktualisieren von Systemkatalogen ist nicht zulässig. Jeder Versuch generiert die folgende Fehlermeldung:  
  
 `Server: Msg 259, Level 16, State 1, Line 1`  
  
 `Ad hoc updates to system catalogs are not allowed.`  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Ändern Sie Ihre SQL-Skripts, sodass sie offizielle und dokumentierte APIs verwenden. Verwenden Sie z. b. ALTER DATABASE *database_name* Set Emergency, anstatt eine Update-Anweisung für die **sysdatabase** -Systemtabelle ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](https://docs.microsoft.com/sql/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
