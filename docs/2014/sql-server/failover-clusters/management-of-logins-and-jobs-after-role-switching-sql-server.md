---
title: Verwaltung von Anmeldenamen und Aufträgen nach einem Rollenwechsel (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- role switching [SQL Server]
ms.assetid: fc2fc949-746f-40c7-b5d4-3fd51ccfbd7b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 870243a5ee69f6058fdc34597ccd4a78b93859e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63252858"
---
# <a name="management-of-logins-and-jobs-after-role-switching-sql-server"></a>Verwaltung von Anmeldenamen und Aufträgen nach einem Rollenwechsel (SQL Server)
  Beim Bereitstellen einer Lösung für hohe Verfügbarkeit oder Notfall Wiederherstellung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für eine-Datenbank ist es wichtig, relevante Informationen, die für die Datenbank in der **Master** -oder **msdb** -Datenbank gespeichert sind, zu reproduzieren. Zu relevanten Informationen gehören normalerweise die Aufträge der primären/Prinzipaldatenbank sowie die Anmeldenamen der Benutzer oder Prozesse, die eine Verbindung mit der Datenbank herstellen müssen. Diese Informationen sollten auf jeder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz dupliziert werden, die eine sekundäre/Spiegeldatenbank hostet. Nach dem Rollenwechsel sollten die Informationen möglichst in der neuen primären/Prinzipaldatenbank programmgesteuert reproduziert werden.  
  
## <a name="logins"></a>Anmeldungen  
 Anmeldenamen, denen eine Berechtigung für den Zugriff auf die Prinzipaldatenbank zugewiesen wurde, sollten auf jeder Serverinstanz reproduziert werden, die eine Kopie der Datenbank hostet. Wenn die primäre/Prinzipalrolle gewechselt wird, können ausschließlich Benutzer, deren Anmeldenamen auf der neuen primären/Prinzipalserverinstanz enthalten sind, auf die neue primäre/Prinzipaldatenbank zugreifen. Benutzer, deren Anmeldenamen nicht auf der neuen primären/Prinzipalserverinstanz definiert wurden, sind verwaist und können nicht auf die Datenbank zugreifen.  
  
 Wenn ein Benutzer verwaist ist, erstellen Sie den Anmeldenamen auf der neuen primären/Prinzipalserverinstanz und führen [sp_change_users_login](/sql/relational-databases/system-stored-procedures/sp-change-users-login-transact-sql)aus. Weitere Informationen finden Sie unter [Problembehandlung bei verwaisten Benutzern &#40;SQL Server&#41;](troubleshoot-orphaned-users-sql-server.md)aus.  
  
###  <a name="SSauthentication"></a> Anmeldenamen von Anwendungen, die die SQL Server-Authentifizierung oder eine lokale Windows-Anmeldung verwenden  
 Wenn eine Anwendung die SQL Server-Authentifizierung oder eine lokale Windows-Anmeldung verwendet, können nicht übereinstimmende SIDs verhindern, dass der Anmeldename der Anwendung auf einer Remoteinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aufgelöst wird. Aufgrund der nicht übereinstimmenden SIDs wird der Anmeldename auf der Remoteserverinstanz als verwaister Benutzer behandelt. Dieses Problem kann auftreten, wenn von einer Anwendung nach einem Failover eine Verbindung mit einer gespiegelten oder Protokollversand-Datenbank hergestellt wird bzw. wenn eine Verbindung mit einer Replikationsabonnenten-Datenbank hergestellt wird, die von einer Sicherung initialisiert wurde.  
  
 Um dieses Problem zu vermeiden, sollten Sie Vorbeugemaßnahmen ergreifen, wenn Sie eine solche Anwendung für die Verwendung einer Datenbank einrichten, die auf einer Remoteinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gehostet wird. Eine Vorbeugungsmaßnahme besteht darin, die Anmeldenamen und Kennwörter von der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf die Remoteinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu übertragen. Weitere Informationen zur Vermeidung dieses Problems finden Sie im KB-Artikel 918992 [Übertragen von Benutzernamen und Kennwörtern zwischen Instanzen von SQL Server](https://support.microsoft.com/kb/918992/).  
  
> [!NOTE]  
>  Dieses Problem betrifft lokale Windows-Konten auf unterschiedlichen Computern. Bei Domänenkonten tritt das Problem jedoch nicht auf, da die SID auf allen Computern identisch ist.  
  
 Weitere Informationen finden Sie unter [Verwaiste Benutzer bei Datenbankspiegelung und Protokollversand](https://blogs.msdn.com/b/sqlserverfaq/archive/2009/04/13/orphaned-users-with-database-mirroring-and-log-shipping.aspx) (Blog zur Datenbank-Engine).  
  
## <a name="jobs"></a>Aufträge  
 Aufträge, wie z. B. Sicherungsaufträge, erfordern besondere Aufmerksamkeit. Nach einem Rollenwechsel muss der Datenbankbesitzer oder der Systemadministrator die Aufträge für die neue primäre/Prinzipaldatenbank gewöhnlich erneut erstellen.  
  
 Wenn die frühere primäre/Prinzipalserverinstanz verfügbar ist, sollten Sie die ursprünglichen Aufträge auf dieser Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]löschen. Sie sollten beachten, dass Aufträge in der aktuellen Spiegeldatenbank fehlerhaft sind, weil sich die Datenbank im Status RESTORING befindet und dadurch nicht verfügbar ist.  
  
> [!NOTE]  
>  Unterschiedliche Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind möglicherweise anders konfiguriert und verfügen u. U. über abweichende Laufwerkbuchstaben. Bei den Aufträgen für die einzelnen Partner müssen derartige Unterschiede berücksichtigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Metadaten beim Bereitstellen einer Datenbank auf einer anderen Serverinstanz &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)   
 [Problembehandlung bei verwaisten Benutzern &#40;SQL Server&#41;](troubleshoot-orphaned-users-sql-server.md)  
  
  
