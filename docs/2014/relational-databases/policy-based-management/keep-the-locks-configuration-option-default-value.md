---
title: Beibehalten des Standardwerts für die Konfigurationsoption „locks“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: f214f05b-5f0b-4786-b2ad-b8b4b6e58d72
caps.latest.revision: 12
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d2ef15536a79b5e67de7907ce6a8bdf5595c49f4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280860"
---
# <a name="keep-the-locks-configuration-option-default-value"></a>Beibehalten des Standardwerts für die Konfigurationsoption 'locks'
  Diese Regel überprüft den Wert der Konfigurationsoption Sperren. Durch diese Option wird die maximale Anzahl verfügbarer Sperren festgelegt. Diese schränkt ein, wie viel Arbeitsspeicher [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] für Sperren verwendet. In der Standardeinstellung 0 kann [!INCLUDE[ssDE](../../includes/ssde-md.md)] Sperrstrukturen je nach Systemanforderungen dynamisch zuordnen bzw. deren Zuordnung aufheben.  
  
 Wenn Sperren einen Wert ungleich 0 (null) hat, werden Stapelverarbeitungsaufträge angehalten, und es wird eine Fehlermeldung angezeigt, dass keine Sperren vorhanden sind, wenn der angegebene Wert überschritten wird.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Verwenden Sie die gespeicherte Systemprozedur sp_configure, um den Wert von Sperren mithilfe der folgenden Anweisung auf die Standardeinstellung zu ändern:  
  
```  
EXEC sp_configure 'locks', 0;  
```  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Konfigurieren der Serverkonfigurationsoption Sperren](../../database-engine/configure-windows/configure-the-locks-server-configuration-option.md)  
  
 [sys.dm_tran_locks &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql)  
  
 [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql)  
  
 [Microsoft Knowledge Base-Artikel 271509](http://go.microsoft.com/fwlink/?linkid=117788)  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
