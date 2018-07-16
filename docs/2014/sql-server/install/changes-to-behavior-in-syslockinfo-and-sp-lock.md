---
title: Änderungen am Verhalten von ' syslockinfo ' und ' sp_lock ' | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
caps.latest.revision: 27
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eb410a4c65d9b626290297fce85ddf2fe20c08d6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295860"
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
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
