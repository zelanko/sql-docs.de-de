---
title: Ändern Sie Anwendungen erwarten von Bigint-Werte von sysperfinfo.cntr_value | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sysperfinfo
- bigint values [SQL Server]
ms.assetid: b0345303-6e9a-4078-8148-6e1bce207b8c
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 436e4d7dc8f1e4a98cfab2b0f2ce2c77576950f8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056858"
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
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
