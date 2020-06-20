---
title: Entfernen von Anweisungen, die Systemobjekte löschen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d9e8fbfd4a436e87cee413d95468ccf5dd36b9dd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059181"
---
# <a name="remove-statements-that-drop-system-objects"></a>Entfernen Sie Anweisungen, mit denen Systemobjekte gelöscht werden
  Der Upgrade Advisor hat Anweisungen erkannt, die Systemobjekte löschen. System Objekte, einschließlich erweiterter gespeicherter Prozeduren, werden in der schreibgeschützten **Ressourcen** Datenbank (mssqlsystemresource) bereitgestellt und können nicht gelöscht werden. Ändern Sie Ihre Anwendungen, sodass sie EXECUTE-Berechtigungen für Systemobjekte aufheben oder verweigern.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 Anweisungen wie DROP TABLE, DROP PROCEDURE und **sp_dropextendedproc** können nicht zum Entfernen von System Objekten verwendet werden, da diese Objekte in der schreibgeschützten **Ressourcen** Datenbank bereitgestellt werden.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Entfernen Sie alle Anweisungen, mit denen Systemobjekte aus Ihren Anwendungen gelöscht werden. Ändern Sie Ihre Anwendungen, sodass sie EXECUTE-Berechtigungen für Systemobjekte aufheben oder verweigern. Alternativ können Sie auch das Tool zur Oberflächenkonfiguration (Surface Area Configuration, SAC) verwenden, um einige dieser Objekte zu deaktivieren. Beispielsweise kann die erweiterte gespeicherte Prozedur **xp_cmdshell** mit dem SAC-Tool deaktiviert oder aktiviert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
