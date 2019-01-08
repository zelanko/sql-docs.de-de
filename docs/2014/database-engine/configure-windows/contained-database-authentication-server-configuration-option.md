---
title: Serverkonfigurationsoption „Contained Database Authentication“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- contained_database_authentication_TSQL
- contained database authentication
helpviewer_keywords:
- contained database, enabling
- contained database authentication option
ms.assetid: b80768d2-ac20-4035-a335-d9adb74b3f6e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 60b0cca44cae7e71e538fe87d5912a044209d06d
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52641381"
---
# <a name="contained-database-authentication-server-configuration-option"></a>Contained Database Authentication (Serverkonfigurationsoption)
  Verwenden Sie die **contained database authentication** -Option, um in der Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]eigenständige Datenbanken zu aktivieren.  
  
 Mit dieser Serveroption können Sie **contained database authentication**steuern.  
  
-   Wenn **contained database authentication** für die Instanz deaktiviert (0) ist, können keine eigenständigen Datenbanken erstellt oder an das [!INCLUDE[ssDE](../../includes/ssde-md.md)]angefügt werden.  
  
-   Wenn **contained database authentication** für die Instanz aktiviert (1) ist, können eigenständige Datenbanken erstellt oder an das [!INCLUDE[ssDE](../../includes/ssde-md.md)]angefügt werden.  
  
 Eine eigenständige Datenbank schließt alle erforderlichen Datenbankeinstellungen und Metadaten zum Definieren der Datenbank ein, und ihre Konfiguration ist nicht von der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Instanz abhängig, in der die Datenbank installiert ist. Benutzer können eine Verbindung mit der Datenbank herstellen, ohne dass sie bei der Anmeldung auf der [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Ebene eine Authentifizierung durchführen. Das Isolieren der Datenbank von der Datenbank-Engine ermöglicht das einfache Verschieben der Datenbank in eine andere Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dadurch, dass alle Datenbankeinstellungen in der Datenbank enthalten sind, können Datenbankbesitzer sämtliche Konfigurationseinstellungen für die Datenbank verwalten. Weitere Informationen zu eigenständigen Datenbanken finden Sie unter [Eigenständige Datenbanken](../../relational-databases/databases/contained-databases.md).  
  
 Wenn eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz über eigenständige Datenbanken verfügt, kann die Einstellung **contained database authentication** mit der **RECONFIGURE WITH OVERRIDE** -Anweisung auf 0 festgelegt werden. Indem **contained database authentication** auf 0 festgelegt wird, wird die Authentifizierung eigenständiger Datenbanken für diese Datenbanken deaktiviert.  
  
> [!IMPORTANT]  
>  Wenn eigenständige Datenbanken aktiviert sind, können Datenbankbenutzer mit der Berechtigung ALTER ANY USER, wie z. B. Mitglieder der Rollen db_owner und db_accessadmin Zugriff auf Datenbanken gewähren und auf diese Weise auch Zugriff auf die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gewähren. Das bedeutet, dass die Kontrolle über den Zugriff zum Server nicht mehr auf Mitglieder der festen Serverrollen „sysadmin“ und „securityadmin“ sowie Zugangsdaten mit den Serverebenenberechtigungen CONTROL SERVER und ALTER ANY LOGIN beschränkt ist. Bevor Sie eigenständige Datenbanken zulassen, sollten Sie die Risiken kennen, die eigenständige Datenbanken mit sich bringen. Weitere Informationen finden Sie unter [Security Best Practices with Contained Databases](../../relational-databases/databases/security-best-practices-with-contained-databases.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden enthaltene Datenbanken für die [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz aktiviert.  
  
```tsql  
sp_configure 'contained database authentication', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
