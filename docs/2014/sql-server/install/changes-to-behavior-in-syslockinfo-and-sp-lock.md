---
title: Änderungen am Verhalten in syslockinfo und sp_lock | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 65ace190004cab911dd8996642720620eba94935
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85045156"
---
# <a name="changes-to-behavior-in-syslockinfo-and-sp_lock"></a>Änderungen am Verhalten von 'syslockinfo' und 'sp_lock'
  **syslockinfo** und **sp_lock** können unerwartete Werte zurückgeben. Sie können auch zusätzliche Zeilen zurückgeben, während vorherige Versionen von **syslockinfo** und **sp_lock** maximal zwei Zeilen pro Sperr Ressource zurückgegeben haben.  
  
 Um auf Informationen von **syslockinfo** zuzugreifen oder **sp_lock** auszuführen, ist die View Server State-Berechtigung auf dem Server erforderlich.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>BESCHREIBUNG  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] werden die Spalten **rsc_objid** und **rsc_indid** in **syslockinfo** und die Spalten **objID** und **indid** in **sp_lock** die Objekt-ID und die Index-ID konsistent zurückgeben. In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] kann der Wert 0 (null) zurückgegeben werden.  
  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] geben **syslockinfo** und **sp_lock** in einer einzelnen Transaktion maximal zwei Zeilen für eine bestimmte Sperr Ressource zurück. Wenn die Sperrenpartitionierung aktiviert ist, werden ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] möglicherweise mehrere Zeilen für dieselbe Ressource zurückgegeben, die unter einer Transaktion ausgeführt wird. Möglicherweise werden bis zu n + 1 Zeilen zurückgegeben, wobei N die Anzahl der CPUs ist. Außerdem können die GRANTED-Anforderung und die WAITING-Anforderung jetzt für dieselbe Ressource angezeigt werden, was in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] nicht möglich war.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
