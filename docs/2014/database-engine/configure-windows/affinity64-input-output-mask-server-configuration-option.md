---
title: affinity64 I/O mask (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- processor affinity [SQL Server]
- binding processors [SQL Server]
- affinity64 I/O mask option
ms.assetid: d304eae7-5116-40ee-a0fa-0a3c0bc20c01
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0cb0e6dd4b14a3f5584dcd7ec920ee16e0241a64
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148173"
---
# <a name="affinity64-input-output-mask-server-configuration-option"></a>affinity64 I/O mask (Serverkonfigurationsoption)
  Die Option **affinity64 I/O mask** bindet die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenträger-E/A an eine bestimmte Teilmenge der CPUs. Diese Option verhält sich ähnlich wie die Option **affinity I/O mask** . Verwenden Sie **affinity I/O mask** , um die ersten 32 Prozessoren zu binden, und mit **affinity64 I/O mask** binden Sie die restlichen Prozessoren auf dem Computer. Wenn Sie **affinity64 I/O mask**neu konfigurieren, müssen Sie die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neu starten. Diese Option wird nur in der 64-Bit-Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Affinity I/O Mask (Serverkonfigurationsoption)](affinity-input-output-mask-server-configuration-option.md)   
 [Überwachen der Ressourcenverwendung &#40;Systemmonitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
