---
title: sp_vupgrade_replication (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: aa15ada3a85a828133ca68a3c3c8ee43e365b344
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85722962"
---
# <a name="sp_vupgrade_replication-transact-sql"></a>sp_vupgrade_replication (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Wird vom Setup-Programm aktiviert, wenn ein Update für einen Replikationsserver durchgeführt wird. Aktualisiert bei Bedarf Schema- und Systemdaten, um die Replikation auf der aktuellen Produktebene zu unterstützen. Erstellt neue Replikationssystemobjekte in System- und Benutzerdatenbanken. Diese gespeicherte Prozedur wird auf dem Computer ausgeführt, auf dem das Replikationsupgrade erfolgen soll.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_vupgrade_replication [ [@login=] 'login' ]  
    [ , [ @password= ] 'password' ]  
    [ , [ @ver_old= ] 'old_version' ]  
    [ , [ @force_remove= ] 'force_removal' ]  
    [ , [ @security_mode= ] security_mode ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @login = ] 'login'`Der Anmelde Name des Systemadministrators, der beim Erstellen neuer Systemobjekte in der Verteilungs Datenbank verwendet werden soll. *login* ist vom Datentyp **sysname**und hat den Standardwert NULL. Dieser Parameter ist nicht erforderlich, wenn *security_mode* auf **1**festgelegt ist. Dies ist die Windows-Authentifizierung.  
  
> [!NOTE]  
>  Dieser Parameter wird ignoriert, wenn Sie ein Upgrade auf [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höhere Versionen durchführen.  
  
`[ @password = ] 'password'`Das Kennwort des Systemadministrators, das beim Erstellen neuer Systemobjekte in der Verteilungs Datenbank verwendet werden soll. *Password* ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist **' '** (leere Zeichenfolge). Dieser Parameter ist nicht erforderlich, wenn *security_mode* auf **1**festgelegt ist. Dies ist die Windows-Authentifizierung.  
  
> [!NOTE]  
>  Dieser Parameter wird ignoriert, wenn Sie ein Upgrade auf SQL [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und spätere Versionen durchführen.  
  
`[ @ver_old = ] 'old_version'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 Diese gespeicherte Prozedur ist als veraltet markiert und wird in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entfernt.  
  
`[ @force_remove = ] 'force_removal'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @security_mode = ] 'security_mode'`Der Anmelde Sicherheitsmodus, der beim Erstellen neuer Systemobjekte in der Verteilungs Datenbank verwendet werden soll. *security_mode* ist vom Typ **Bit** und hat den Standardwert **0**. Wenn der Wert **0**ist, wird die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung verwendet. Bei **1**wird die Windows-Authentifizierung verwendet.  
  
> [!NOTE]  
>  Dieser Parameter wird ignoriert, wenn Sie ein Upgrade auf [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] oder höhere Versionen durchführen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_vupgrade_replication** wird beim Aktualisieren aller Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_vupgrade_replication**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Replikations Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Überprüfen von replizierten Daten](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
