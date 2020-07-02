---
title: sp_dropanonymousagent (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropanonymousagent
- sp_dropanonymousagent_TSQL
helpviewer_keywords:
- sp_dropanonymousagent
ms.assetid: 4cb96efa-9358-44a3-a8ee-a7e181bed089
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: 8c9a025beaf1d9701411668a13fa78273105d30c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717326"
---
# <a name="sp_dropanonymousagent-transact-sql"></a>sp_dropanonymousagent (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Löscht einen anonymen Agent für die Replikationsüberwachung auf dem Verteiler vom Verleger. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_dropanonymousagent [ @subid= ] sub_id    , [ @type= ] type  
```  
  
## <a name="arguments"></a>Argumente  
`[ @subid = ] sub_id`Der globale Bezeichner für ein anonymes Abonnement. *sub_id* ist vom Datentyp **uniqueidentifier**und hat keinen Standardwert. Dieser Bezeichner kann mit **sp_helppullsubscription**auf dem Abonnenten abgerufen werden. Der Wert im **subid** -Feld des zurückgegebenen Resultsets ist dieser globale Bezeichner.  
  
`[ @type = ] type`Der Abonnementtyp. *Type ist vom Datentyp* **int**und hat keinen Standardwert. Gültige Werte sind **1** oder **2**. Geben Sie **1**an, wenn die Momentaufnahme-oder Transaktions Replikation mit dem Verteilungs-Agent. Geben Sie **2**an, wenn die Mergereplikation die Merge-Agent verwendet.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_dropanonymousagent** wird bei allen Replikations Typen verwendet.  
  
 Diese gespeicherte Prozedur wird nur verwendet, um anonyme Abonnement-Agents zu löschen, und kann nicht verwendet werden, um bekannte Abonnements zu löschen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **db_owner** Fixed-Daten Bank Rolle in der Verteilungs Datenbank können **sp_dropanonymousagent**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
