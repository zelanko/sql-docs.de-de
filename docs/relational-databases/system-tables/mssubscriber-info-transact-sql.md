---
title: MSsubscriber_info (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
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
ms.openlocfilehash: 45065f7cde525d65997df2c97c972d684cadd90f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68139822"
---
# <a name="mssubscriber_info-transact-sql"></a>MSsubscriber_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSsubscriber_info** Tabelle enthält eine Zeile für jedes Verleger/Abonnenten-Paar, für das Abonnements vom lokalen Verteiler per pushübertragung übermittelt werden. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
 **Hinweis** Diese Systemtabelle wurde als veraltet markiert und wird zur Unterstützung früherer Versionen von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]beibehalten.  
  
## <a name="definition"></a>Definition  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Gebers**|**sysname**|Der Name des Verlegers.|  
|**Abonnenten**|**sysname**|Den Namen des Abonnenten.|  
|**type**|**tinyint**|Der Abonnententyp:<br /><br /> **0** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnent.<br /><br /> **1** = ODBC-Datenquelle.|  
|**Anmel**|**sysname**|Der Anmelde Name [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für die Authentifizierung. Wird verschlüsselt gespeichert, wenn der Abonnent mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierungsmodus hinzugefügt wird.|  
|**password**|**nvarchar (524)**|Das Kennwort für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung. Wird verschlüsselt gespeichert, wenn der Abonnent mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierungsmodus hinzugefügt wird.|  
|**Beschreibung**|**nvarchar(255)**|Die Beschreibung des Abonnenten.|  
|**security_mode**|**int**|Der implementierte Sicherheitsmodus:<br /><br /> **0** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung.<br /><br /> **1** =  1[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
