---
title: Ändern Sie Anwendungen so Bigint-Werte von sysperfinfo.cntr_value erwartet | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: ced1e07b5423dcdc7c13d24e8528a2b6ac240aaa
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66093963"
---
# <a name="modify-applications-to-expect-bigint-values-from-sysperfinfocntrvalue"></a>Ändern von Anwendungen, damit bigint-Werte von 'sysperfinfo.cntr_value' erwartet werden
  Gibt Sysperfinfo einen `bigint` Wert für die Cntr_value-Spalte.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Durch Ändern der Anwendungen, die sysperfinfo verwenden, können Sie sicherstellen, dass sie die `bigint`-Werte der cntr_value-Spalte verarbeiten können.  
  
> [!NOTE]  
>  Sysperfinfo ist eine kompatibilitätssicht. Sie sollten stattdessen die dynamische Verwaltungssicht sys.dm_os_performance_counter verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
