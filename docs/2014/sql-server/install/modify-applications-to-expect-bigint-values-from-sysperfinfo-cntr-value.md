---
title: Ändern Sie die Anwendungen so, dass bigint-Werte von sysperfinfo. cntr_value erwartet werden. Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 108a9b981debc95e182b16847c39a03d4b242088
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012209"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntr_value"></a>Ändern von Anwendungen, damit bigint-Werte von 'sysperfinfo.cntr_value' erwartet werden
  sysperfinfo gibt einen `bigint` Wert für die cntr_value Spalte zurück.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Durch Ändern der Anwendungen, die sysperfinfo verwenden, können Sie sicherstellen, dass sie die `bigint`-Werte der cntr_value-Spalte verarbeiten können.  
  
> [!NOTE]  
>  sysperfinfo ist eine Kompatibilitäts Ansicht. Sie sollten stattdessen die dynamische Verwaltungssicht sys.dm_os_performance_counter verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
