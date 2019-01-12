---
title: Sp_vupgrade_replication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_vupgrade_replication_TSQL
- sp_vupgrade_replication
helpviewer_keywords:
- sp_vupgrade_replication
ms.assetid: d2c0ed66-07d1-4adc-82e5-a654376879bc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0e21e07cb9c81b65cccafda2e938057cd16f96b4
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54124410"
---
# <a name="spvupgradereplication-transact-sql"></a>sp_vupgrade_replication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wird vom Setup-Programm aktiviert, wenn ein Update für einen Replikationsserver durchgeführt wird. Aktualisiert bei Bedarf Schema- und Systemdaten, um die Replikation auf der aktuellen Produktebene zu unterstützen. Erstellt neue Replikationssystemobjekte in System- und Benutzerdatenbanken. Diese gespeicherte Prozedur wird auf dem Computer ausgeführt, auf dem das Replikationsupgrade erfolgen soll.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_vupgrade_replication [ [@login=] 'login' ]  
    [ , [ @password= ] 'password' ]  
    [ , [ @ver_old= ] 'old_version' ]  
    [ , [ @force_remove= ] 'force_removal' ]  
    [ , [ @security_mode= ] security_mode ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@login=**] **"**_Anmeldung_**"**  
 Gibt den Anmeldenamen des Systemadministrators an, der verwendet werden soll, wenn neue Systemobjekte in der Verteilungsdatenbank erstellt werden. *login* ist vom Datentyp **sysname**und hat den Standardwert NULL. Dieser Parameter ist nicht erforderlich, wenn *Security_mode* nastaven NA hodnotu **1**, d. h. auf Windows-Authentifizierung.  
  
> [!NOTE]  
>  Dieser Parameter wird ignoriert, wenn Sie ein Upgrade auf [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höhere Versionen durchführen.  
  
 [  **@password=**] **"**_Kennwort_**"**  
 Ist das Systemadministratorkennwort zu verwenden, wenn neue Systemobjekte in der Verteilungsdatenbank zu erstellen. *Kennwort* ist **Sysname**, hat den Standardwert **''** (leere Zeichenfolge). Dieser Parameter ist nicht erforderlich, wenn *Security_mode* nastaven NA hodnotu **1**, d. h. auf Windows-Authentifizierung.  
  
> [!NOTE]  
>  Dieser Parameter wird ignoriert, wenn Sie ein Upgrade auf SQL durchführen [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen.  
  
 [  **@ver_old=**] **"**_Old_version_**"**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 Diese gespeicherte Prozedur ist als veraltet markiert und wird in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entfernt.  
  
 [  **@force_remove=**] **"**_Force_removal_**"**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@security_mode=**] **"**_Security_mode_**"**  
 Gibt den Anmeldungssicherheitsmodus an, der verwendet werden soll, wenn neue Systemobjekte in der Verteilungsdatenbank erstellt werden. *Security_mode* ist **Bit** hat den Standardwert des **0**. Wenn **0**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung verwendet werden. Wenn **1**, Windows-Authentifizierung verwendet werden.  
  
> [!NOTE]  
>  Dieser Parameter wird ignoriert, wenn Sie ein Upgrade auf [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höhere Versionen durchführen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_vupgrade_replication** wird verwendet, wenn alle Arten der Replikation zu aktualisieren.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_vupgrade_replication**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Überprüfen von replizierten Daten](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
