---
title: sp_refreshsubscriptions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_refreshsubscriptions
- sp_refreshsubscriptions_TSQL
helpviewer_keywords:
- sp_refreshsubscriptions
ms.assetid: 6cb9b1ce-1ce7-43ab-9451-201f79ed1ffa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 33e9094a7f08cc6b4929b36b2739aa4dda026e07
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828799"
---
# <a name="sp_refreshsubscriptions-transact-sql"></a>sp_refreshsubscriptions (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Hinzufügen von Abonnements zu neuen Artikeln für alle vorhandenen Abonnenten zu einer sofort aktualisierten Veröffentlichung. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_refreshsubscriptions [ @publication = ] 'publication'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Die Veröffentlichung, für die Abonnements aktualisiert werden sollen. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_refreshsubscriptions** wird bei der Momentaufnahme-, Transaktions-und Mergereplikation verwendet.  
  
 **sp_refreshsubscriptions** wird von **sp_addarticle** für eine sofort Aktualisier Ende Veröffentlichung aufgerufen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_refreshsubscriptions**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addarticle &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
