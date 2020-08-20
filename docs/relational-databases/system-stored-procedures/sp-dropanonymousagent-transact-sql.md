---
description: sp_dropanonymousagent (Transact-SQL)
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
ms.openlocfilehash: d6e687976dab6d526a2413260d2ad2f980001086
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474278"
---
# <a name="sp_dropanonymousagent-transact-sql"></a>sp_dropanonymousagent (Transact-SQL)

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Löscht einen anonymen Agent für die Replikationsüberwachung auf dem Verteiler vom Verleger. Diese gespeicherte Prozedur wird auf dem Verleger für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_dropanonymousagent [ @subid= ] sub_id    , [ @type= ] type  
```  
  
## <a name="arguments"></a>Argumente  
`[ @subid = ] sub_id` Der globale Bezeichner für ein anonymes Abonnement. *sub_id* ist vom Datentyp **uniqueidentifier**und hat keinen Standardwert. Dieser Bezeichner kann mit **sp_helppullsubscription**auf dem Abonnenten abgerufen werden. Der Wert im **subid** -Feld des zurückgegebenen Resultsets ist dieser globale Bezeichner.  
  
`[ @type = ] type` Der Abonnementtyp. *Type ist vom Datentyp* **int**und hat keinen Standardwert. Gültige Werte sind **1** oder **2**. Geben Sie **1**an, wenn die Momentaufnahme-oder Transaktions Replikation mit dem Verteilungs-Agent. Geben Sie **2**an, wenn die Mergereplikation die Merge-Agent verwendet.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_dropanonymousagent** wird bei allen Replikations Typen verwendet.  
  
 Diese gespeicherte Prozedur wird nur verwendet, um anonyme Abonnement-Agents zu löschen, und kann nicht verwendet werden, um bekannte Abonnements zu löschen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **db_owner** Fixed-Daten Bank Rolle in der Verteilungs Datenbank können **sp_dropanonymousagent**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
