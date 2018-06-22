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
ms.topic: article
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ea0784932246de16020ce35ff8ff60c0388eafef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150640"
---
# <a name="ole-automation-procedures-server-configuration-option"></a>OLE-Automatisierungsprozeduren (Serverkonfigurationsoption)
  Verwenden Sie die `Ole Automation Procedures`-Option zum Angeben, ob OLE-Automatisierungsobjekte in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Batches instantiiert werden können. Diese Option kann auch mithilfe der richtlinienbasierten Verwaltung oder der gespeicherten Prozedur **sp_configure** konfiguriert werden. Weitere Informationen finden Sie unter [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
 Die `Ole Automation Procedures` -Option kann auf die folgenden Werte festgelegt werden.  
  
 0  
 OLE-Automatisierungsprozeduren sind deaktiviert. Standardeinstellung für neue Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 1  
 OLE-Automatisierungsprozeduren sind aktiviert.  
  
 Wenn OLE-Automatisierungsprozeduren aktiviert sind, startet ein Aufruf von **sp_OACreate** die freigegebene OLE-Ausführungsumgebung.  
  
 Der aktuelle Wert der die `Ole Automation Procedures` Option angezeigt und mit nicht geändert werden kann, die **Sp_configure** gespeicherten Systemprozedur.  
  
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
  
  
