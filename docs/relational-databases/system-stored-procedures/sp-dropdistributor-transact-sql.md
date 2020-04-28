---
title: sp_dropdistributor (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdistributor
- sp_dropdistributor_TSQL
helpviewer_keywords:
- sp_dropdistributor
ms.assetid: 0644032f-5ff0-4718-8dde-321bc9967a03
author: stevestein
ms.author: sstein
ms.openlocfilehash: a82a3bedf78eb69dfc4a1736e212164341077601
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "72304976"
---
# <a name="sp_dropdistributor-transact-sql"></a>sp_dropdistributor (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Deinstalliert den Verteiler. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank mit Ausnahme der Verteilungsdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropdistributor [ [ @no_checks= ] no_checks ]   
    [ , [ @ignore_distributor= ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @no_checks = ] no_checks`Gibt an, ob nach abhängigen Objekten gesucht werden soll, bevor der Verteiler gelöscht wird. *no_checks* ist vom Typ **Bit**. der Standardwert ist 0.  
  
 Wenn der Wert **0**ist, wird **sp_dropdistributor** überprüft, um sicherzustellen, dass alle Veröffentlichungs-und Verteilungs Objekte zusätzlich zum Verteiler gelöscht wurden.  
  
 Bei **1**werden von **sp_dropdistributor** alle Veröffentlichungs-und Verteilungs Objekte gelöscht, bevor der Verteiler deinstalliert wird.  
  
`[ @ignore_distributor = ] ignore_distributor`Gibt an, ob diese gespeicherte Prozedur ausgeführt wird, ohne eine Verbindung mit dem Verteiler herzustellen. *ignore_distributor* ist vom Typ **Bit**. der Standardwert ist **0**.  
  
 Bei **0**wird **sp_dropdistributor** eine Verbindung mit dem Verteiler hergestellt und alle Replikations Objekte entfernt. Wenn **sp_dropdistributor** keine Verbindung mit dem Verteiler herstellen kann, schlägt die gespeicherte Prozedur fehl.  
  
 Wenn der Wert **1**ist, wird keine Verbindung mit dem Verteiler hergestellt, und die Replikations Objekte werden nicht entfernt. Diese Möglichkeit wird verwendet, wenn der Verteiler deinstalliert wird oder dauerhaft offline ist. Die Objekte für diesen Verleger werden auf dem Verteiler nicht entfernt, bis der Verteiler zu einem späteren Zeitpunkt neu installiert wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_dropdistributor** wird bei allen Replikations Typen verwendet.  
  
 Wenn andere Verleger-oder Verteilungs Objekte auf dem Server vorhanden sind, schlägt **sp_dropdistributor** fehl, es sei denn ** \@, no_checks** ist auf **1**festgelegt.  
  
 Diese gespeicherte Prozedur muss ausgeführt werden, nachdem die Verteilungs Datenbank durch Ausführen von **sp_dropdistributiondb**gelöscht wurde.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistributor-trans_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_dropdistributor**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichung und Verteilung deaktivieren](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sp_adddistributor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md)   
 [sp_changedistributor_property &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
