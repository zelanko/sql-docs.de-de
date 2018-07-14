---
title: OLE-Automatisierungsprozeduren (Serverkonfigurationsoption) | Microsoft-Dokumentation
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
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
caps.latest.revision: 20
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a1f1feb6278c36f09c978f5f8f1ae6dbf9f64e60
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37205760"
---
# <a name="ole-automation-procedures-server-configuration-option"></a>OLE-Automatisierungsprozeduren (Serverkonfigurationsoption)
  Verwenden Sie die `Ole Automation Procedures`-Option zum Angeben, ob OLE-Automatisierungsobjekte in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Batches instantiiert werden können. Diese Option kann auch mithilfe der richtlinienbasierten Verwaltung oder der gespeicherten Prozedur **sp_configure** konfiguriert werden. Weitere Informationen finden Sie unter [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
 Die `Ole Automation Procedures` Option kann auf die folgenden Werte festgelegt werden.  
  
 0  
 OLE-Automatisierungsprozeduren sind deaktiviert. Standardeinstellung für neue Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 1  
 OLE-Automatisierungsprozeduren sind aktiviert.  
  
 Wenn OLE-Automatisierungsprozeduren aktiviert sind, startet ein Aufruf von **sp_OACreate** die freigegebene OLE-Ausführungsumgebung.  
  
 Der aktuelle Wert von der `Ole Automation Procedures` Option angezeigt und geändert werden kann, die **Sp_configure** gespeicherten Systemprozedur.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt, wie die aktuelle Einstellung von OLE-Automatisierungsprozeduren angezeigt werden kann.  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 Das folgende Beispiel zeigt, wie OLE-Automatisierungsprozeduren aktiviert werden.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Oberflächenkonfiguration](../../relational-databases/security/surface-area-configuration.md)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
