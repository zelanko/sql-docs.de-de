---
title: sp_markpendingschemachange (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_markpendingschemachange
- sp_markpendingschemachange_TSQL
helpviewer_keywords:
- sp_markpendingschemachange
ms.assetid: 01100309-7bef-4154-85bf-f18489577e37
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 91fb437d0b280f8739f0c6d1b6b90efeb73ab3c0
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831022"
---
# <a name="sp_markpendingschemachange-transact-sql"></a>sp_markpendingschemachange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wird für die Unterstützung von Mergeveröffentlichungen verwendet, indem ein Administrator die Möglichkeit erhält, bestimmte ausstehende Schemaänderungen auszulassen, sodass sie nicht repliziert werden. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
> [!CAUTION]  
>  Diese gespeicherte Prozedur kann zur Folge haben, dass Schemaänderungen nicht repliziert werden. Sie sollte nur zur Problembehandlung verwendet werden, nachdem andere Methoden, wie z. B. die erneute Initialisierung, bereits versucht wurden oder die Leistung zu stark einschränken.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_markpendingschemachange [@publication = ] 'publication'  
    [ , [ @schemaversion = ] schemaversion ]  
    [ , [ @status = ] 'status' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @schemaversion = ] schemaversion`Identifiziert eine ausstehende Schema Änderung. *Schema Version* ist vom Datentyp **int**und hat den Standardwert **0**. Verwenden Sie [sp_enumeratependingschemachanges &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-enumeratependingschemachanges-transact-sql.md) , um die ausstehenden Schema Änderungen für die Veröffentlichung aufzulisten.  
  
`[ @status = ] 'status'`Gibt an, ob eine ausstehende Schema Änderung ausgelassen wird. der *Status* ist " **nvarchar (10)** " mit dem Standardwert " **aktiv**". Wenn der Wert von *Status* **übersprungen**lautet, wird die ausgewählte Schema Änderung nicht repliziert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_markpendingschemachange** wird bei der Mergereplikation verwendet.  
  
 **sp_markpendingschemachange** ist eine gespeicherte Prozedur für die Unterstützung der Mergereplikation und sollte nur verwendet werden, wenn andere Korrekturmaßnahmen, wie z. b. die erneute Initialisierung, die Situation nicht beheben konnten oder zu teuer in Bezug auf die Leistung sind.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_markpendingschemachange**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sysmergeschemachange &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/sysmergeschemachange-transact-sql.md)  
  
  
