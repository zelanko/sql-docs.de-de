---
title: Änderungen am Verhalten von ' syslockinfo ' und ' sp_lock ' | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: e8c6534449ffc4e89efcd49c943726bf6ecd9f26
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66096644"
---
# <a name="changes-to-behavior-in-syslockinfo-and-splock"></a>Änderungen am Verhalten von 'syslockinfo' und 'sp_lock'
  **Syslockinfo** und **Sp_lock** möglicherweise unerwartete Werte zurück. Sie können auch zusätzliche Zeilen zurückgeben, während vorherige Versionen von **Syslockinfo** und **Sp_lock** maximal zwei Zeilen je Lock-Ressource zurückgegeben.  
  
 Um den Zugriff auf Informationen von **Syslockinfo** oder führen Sie **Sp_lock** erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], **Rsc_objid** und **Rsc_indid** Spalten in **Syslockinfo** und **Objid** und **Indid**  Spalten in **Sp_lock** konsistent zurückgeben die Objekt-ID und index-ID In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] kann der Wert 0 (null) zurückgegeben werden.  
  
 In [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], **Syslockinfo** und **Sp_lock** maximal zwei Zeilen für eine bestimmte Lock-Ressource in einer einzelnen Transaktion zurückgeben. Wenn die Sperrenpartitionierung aktiviert ist, werden ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] möglicherweise mehrere Zeilen für dieselbe Ressource zurückgegeben, die unter einer Transaktion ausgeführt wird. Gibt es möglicherweise bis zu N + 1 Zeilen zurückgegeben, wobei N die Anzahl der CPUs ist. Außerdem können die GRANTED-Anforderung und die WAITING-Anforderung jetzt für dieselbe Ressource angezeigt werden, was in [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] nicht möglich war.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgrade-Probleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
