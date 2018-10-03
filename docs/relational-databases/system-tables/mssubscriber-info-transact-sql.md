---
title: MSsubscriber_info (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSsubscriber_info_TSQL
- MSsubscriber_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_info system table
ms.assetid: 5ca22f41-6020-4f72-8110-e69baf3447cb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d510f63bb0a5873cb7967b24a5793bc24bcddf9d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741150"
---
# <a name="mssubscriberinfo-transact-sql"></a>MSsubscriber_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSsubscriber_info** -Tabelle enthält eine Zeile für jedes Verleger/Abonnent-Paar, die Abonnements aus dem lokalen Verteiler abgelegt wird. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
 **Beachten Sie** diese Systemtabelle wurde als veraltet markiert und ist weiterhin für die Unterstützung früherer Versionen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="definition"></a>Definition  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Der Name des Verlegers.|  
|**subscriber**|**sysname**|Den Namen des Abonnenten.|  
|**type**|**tinyint**|Der Abonnententyp:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten.<br /><br /> **1** = ODBC-Datenquelle.|  
|**login**|**sysname**|Der Anmeldename für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung. Wird verschlüsselt gespeichert, wenn der Abonnent mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierungsmodus hinzugefügt wird.|  
|**password**|**nvarchar(524)**|Das Kennwort für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung. Wird verschlüsselt gespeichert, wenn der Abonnent mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierungsmodus hinzugefügt wird.|  
|**description**|**nvarchar(255)**|Die Beschreibung des Abonnenten.|  
|**security_mode**|**int**|Der implementierte Sicherheitsmodus:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
