---
title: sp_changesubscriptiondtsinfo (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriptiondtsinfo
- sp_changesubscriptiondtsinfo_TSQL
helpviewer_keywords:
- sp_changesubscriptiondtsinfo
ms.assetid: 64fc085f-f81b-493b-b59a-ee6192d9736d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d721bf729d99a60a32693ddbe609cfcee01ba701
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85771370"
---
# <a name="sp_changesubscriptiondtsinfo-transact-sql"></a>sp_changesubscriptiondtsinfo (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Ändert die DTS-Paketeigenschaften (Data Transformation Services) eines Abonnements. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnement Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changesubscriptiondtsinfo [ [ @job_id = ] job_id ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] 'dts_package_location' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id`Die Auftrags-ID des Verteilungs-Agent für das Pushabonnement. *job_id* ist vom Datentyp **varbinary (16)** und hat keinen Standardwert. Führen Sie **sp_helpsubscription** oder **sp_helppullsubscription**aus, um die Verteilungs Auftrags-ID zu ermitteln.  
  
`[ @dts_package_name = ] 'dts_package_name'`Gibt den Namen des DTS-Pakets an. *dts_package_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn Sie z. b. ein Paket mit dem Namen **DTSPub_Package**angeben möchten, geben Sie an `@dts_package_name = N'DTSPub_Package'` .  
  
`[ @dts_package_password = ] 'dts_package_password'`Gibt das Kennwort für das Paket an. *dts_package_password* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL, der angibt, dass die Kenn Wort Eigenschaft unverändert bleiben soll.  
  
> [!NOTE]  
>  Ein DTS-Paket muss über ein Kennwort verfügen.  
  
`[ @dts_package_location = ] 'dts_package_location'`Gibt den Speicherort des Pakets an. *dts_package_location* ist vom Datentyp **nvarchar (12)** und hat den Standardwert NULL, womit angegeben wird, dass der Paket Speicherort unverändert bleiben soll. Der Speicherort des Pakets kann in **Verteiler** oder **Abonnent**geändert werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_changesubscriptiondtsinfo** wird für die Momentaufnahme-und Transaktions Replikation verwendet, bei denen es sich nur um Pushabonnements handelt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** oder der Ersteller des Abonnements können **sp_changesubscriptiondtsinfo**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
