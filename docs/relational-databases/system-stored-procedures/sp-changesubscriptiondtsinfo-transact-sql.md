---
title: Sp_changesubscriptiondtsinfo (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 04587ac4015719bb8a525754d7c0d9e36790b2b6
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52783372"
---
# <a name="spchangesubscriptiondtsinfo-transact-sql"></a>sp_changesubscriptiondtsinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die DTS-Paketeigenschaften (Data Transformation Services) eines Abonnements. Diese gespeicherte Prozedur wird auf dem Abonnenten für die Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changesubscriptiondtsinfo [ [ @job_id = ] job_id ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] 'dts_package_location' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@job_id=**] *Job_id*  
 Die Auftrags-ID des Verteilungs-Agents für das Pushabonnement. *Job_id* ist **varbinary(16)**, hat keinen Standardwert. Um die Verteilungsauftrags-ID zu ermitteln, führen Sie **Sp_helpsubscription** oder **Sp_helppullsubscription**.  
  
 [ **@dts_package_name**=] **"***Dts_package_name***"**  
 Gibt den Namen des DTS-Pakets an. *Dts_package_name* ist eine **Sysname**, hat den Standardwert NULL. Beispielsweise geben Sie ein Paket mit dem Namen **DTSPub_Package**, geben Sie `@dts_package_name = N'DTSPub_Package'`.  
  
 [ **@dts_package_password**=] **"***Dts_package_password***"**  
 Gibt das Kennwort für das Paket an. *Dts_package_password* ist **Sysname** hat den Standardwert NULL, der angibt, dass die Kennworteigenschaft ist, werden nicht geändert.  
  
> [!NOTE]  
>  Ein DTS-Paket muss über ein Kennwort verfügen.  
  
 [ **@dts_package_location**=] **"***Dts_package_location***"**  
 Gibt den Paketspeicherort an. *Dts_package_location* ist eine **nvarchar(12)**, hat den Standardwert NULL, der angibt, dass der Speicherort des Pakets ist, werden nicht geändert. Der Speicherort des Pakets kann geändert werden, um **Verteiler** oder **Abonnenten**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_changesubscriptiondtsinfo** wird verwendet, für Momentaufnahme- und Transaktionsreplikation, die nur für Pushabonnements geeignet sind.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** festen Serverrolle **Db_owner** feste Datenbankrolle oder der Ersteller des Abonnements kann ausführen **Sp_changesubscriptiondtsinfo**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
