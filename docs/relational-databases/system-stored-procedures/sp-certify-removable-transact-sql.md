---
title: sp_certify_removable (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_certify_removable_TSQL
- sp_certify_removable
dev_langs:
- TSQL
helpviewer_keywords:
- sp_certify_removable
ms.assetid: ca12767f-0ae5-4652-b523-c23473f100a1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b873931c5d09f3c54f61e872f8ea6646408c1a04
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715964"
---
# <a name="sp_certify_removable-transact-sql"></a>sp_certify_removable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Überprüft, ob eine Datenbank für die Verteilung auf austauschbaren Medien ordnungsgemäß konfiguriert ist, und meldet dem Benutzer alle Probleme.  
  
> **WICHTIG!** [! Fügen Sie stattdessen[ssnotedepfuturevermeide](../../t-sql/statements/create-database-sql-server-transact-sql.md) ein.  
  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_certify_removable [ @dbname= ] 'dbname'  
     [ , [ @autofix = ] 'auto' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @dbname = ] 'dbname'`Gibt die Datenbank an, die überprüft werden soll. *dbname* ist vom **Datentyp vom Datentyp sysname**.  
  
`[ @autofix = ] 'auto'`Übergibt den Besitz der Datenbank und aller Datenbankobjekte an den Systemadministrator und löscht alle vom Benutzer erstellten Datenbankbenutzer und nicht standardmäßigen Berechtigungen. *Auto* ist vom Datentyp **nvarchar (4)** und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn die Datenbank ordnungsgemäß konfiguriert ist, führt **sp_certify_removable** folgende Schritte aus:  
  
-   Legt den Offlinemodus für die Datenbank fest, sodass Dateien kopiert werden können.  
  
-   Aktualisiert die Statistik für alle Tabellen und meldet Besitz- oder Benutzerprobleme.  
  
-   Markiert die Datendateigruppen als schreibgeschützt, damit diese Dateien auf schreibgeschützte Medien kopiert werden können.  
  
 Der Systemadministrator muss der Besitzer der Datenbank und aller Datenbankobjekte sein. Der Systemadministrator ist ein bekannter Benutzer, der auf allen Servern vorhanden ist, auf denen ausgeführt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird und die vorhanden sein können, wenn die Datenbank später verteilt und installiert wird.  
  
 Wenn Sie **sp_certify_removable** ohne den **automatischen** Wert ausführen und Informationen zu einer der folgenden Bedingungen zurückgibt:  
  
-   Der Systemadministrator ist nicht der Datenbankbesitzer.  
  
-   Beliebige vom Benutzer erstellte Benutzer sind bereits vorhanden.  
  
-   Der Systemadministrator besitzt nicht alle Objekte in der Datenbank.  
  
-   Es wurden von den Standardwerten abweichende Berechtigungen erteilt.  
  
 Sie können diese Bedingungen mithilfe der folgenden Möglichkeiten korrigieren:  
  
-   Verwenden Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tools und Prozeduren, und führen Sie **sp_certify_removable** dann erneut aus.  
  
-   Führen Sie **sp_certify_removable** nur mit dem **automatischen** Wert aus.  
  
 Beachten Sie, dass diese gespeicherte Prozedur nur Benutzer und Benutzerberechtigungen überprüft. Sie können der Datenbank Gruppen hinzufügen und diesen Berechtigungen erteilen. Weitere Informationen finden Sie unter [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)konfigurieren.  
  
## <a name="permissions"></a>Berechtigungen  
 Ausführungs Berechtigungen sind auf Mitglieder der festen Server Rolle **sysadmin** beschränkt.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird überprüft, ob die `inventory`-Datenbank für das Entfernen vorbereitet ist.  
  
```  
EXEC sp_certify_removable inventory, AUTO;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_create_removable &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-create-removable-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_dbremove &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dbremove-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
