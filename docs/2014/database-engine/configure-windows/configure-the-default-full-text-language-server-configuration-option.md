---
title: Konfigurieren der Serverkonfigurationsoption „Volltext-Standardsprache“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- languages [full-text search]
- default full-text language option
ms.assetid: 0fa8785b-0830-4a52-aff5-fcf8268b72fc
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ec0736326a4da0708d125bfc480996d54bb86c8a
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935729"
---
# <a name="configure-the-default-full-text-language-server-configuration-option"></a>Konfigurieren der Serverkonfigurationsoption Volltext-Standardsprache
  In diesem Thema wird beschrieben, wie die `default full-text language` Server Konfigurationsoption in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von oder konfiguriert wird [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] . Mit der- `default full-text language` Option wird ein Standard sprach Wert für Volltextindizes angegeben. Für alle Daten, die Volltextindizes aufweisen, wird eine linguistische Analyse ausgeführt, die von der Sprache der Daten abhängt. Der Standardwert für diese Option ist die Sprache des Servers. Bei einer lokalisierten Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die `default full-text language` Option von Setup auf die Sprache des Servers festgelegt, wenn eine entsprechende Entsprechung vorhanden ist. Bei einer nicht lokalisierten Version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird Englisch für die Option `default full-text language` verwendet.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
     [Security](#Security)  
  
-   **So konfigurieren Sie die Option Volltext-Standardsprache mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Nachverfolgung:**  [Nach dem Konfigurieren der Option „Volltext-Standardsprache“](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Der Wert der `default full-text language` Option wird in einem Volltextindex verwendet, wenn für eine Spalte keine Sprache über die Option language **language_term** in der CREATE FULLTEXT INDEX-Anweisung oder der ALTER FULLTEXT INDEX-Anweisung angegeben wird. Wenn die Volltext-Standardsprache nicht unterstützt wird oder das Sprachanalysepaket nicht verfügbar ist, schlägt die CREATE- oder ALTER-Operation fehl, und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt eine Fehlermeldung zurück, die besagt, dass die angegebene Sprache ungültig ist.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Diese Option ist eine erweiterte Option und sollte ausschließlich von einem erfahrenen Datenbankadministrator oder einem zertifizierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Techniker geändert werden.  
  
-   Die `default full-text language` Option erfordert einen LCID-Wert. Eine Liste mit unterstützten LCIDs und den dazugehörigen Sprachen finden Sie unter [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)konfiguriert wird. Andere Sprachen können beispielsweise von unabhängigen Softwareherstellern verfügbar sein. Wenn keine spezielle Sprache gefunden wird, schaltet die Volltextsuch-Engine automatisch in die primäre Sprache.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Die Ausführungsberechtigungen für **sp_configure** ohne Parameter oder nur mit dem ersten Parameter werden standardmäßig allen Benutzern erteilt. Zum Ausführen von **sp_configure** mit beiden Parametern zum Ändern einer Konfigurationsoption oder zum Ausführen der RECONFIGURE-Anweisung muss einem Benutzer die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-the-default-full-text-language-option"></a>So konfigurieren Sie die Option Volltext-Standardsprache  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf einen Server, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie auf den **Erweitert** -Knoten.  
  
3.  Verwenden Sie unter Verschiedenes die Option **Volltext-Standardsprache** , um einen Wert für die Standardsprache für volltextindizierte Spalten anzugeben.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-configure-the-default-full-text-language-option"></a>So konfigurieren Sie die Option Volltext-Standardsprache  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. In diesem Beispiel wird gezeigt, wie [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) verwendet wird, um den Wert der Option `default full-text` auf Holländisch (`1043`) festzulegen.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'default full-text language', 1043 ;  
GO  
RECONFIGURE  
GO  
  
```  
  
 Weitere Informationen finden Sie unter [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)angezeigt oder konfiguriert wird.  
  
##  <a name="follow-up-after-you-configure-the-default-full-text-language-option"></a><a name="FollowUp"></a>Nächster Schritt: Nach dem Konfigurieren der Option „Volltext-Standardsprache“  
 Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
  
