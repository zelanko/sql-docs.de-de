---
title: Anzeigen der Definition einer gespeicherten Prozedur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.technology: stored-procedures
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [SQL Server], viewing
- definition of stored procedure
- viewing stored procedures
- displaying stored procedures
ms.assetid: 93318587-a0c5-4788-946f-3b5dc8372ea9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 09737f1b9764680e67dbb0bbefb2d0ec86df71e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37288406"
---
# <a name="view-the-definition-of-a-stored-procedure"></a>Anzeigen der Definition einer gespeicherten Prozedur
    
##  <a name="Top"></a> Sie können die Definition einer gespeicherten Prozedur in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] mit Objekt-Explorer-Menüoptionen oder im Abfrage-Editor mit [!INCLUDE[tsql](../../includes/tsql-md.md)]anzeigen. In diesem Thema wird beschrieben, wie die Definition der Prozedur im Objekt-Explorer und mit einer gespeicherten Systemprozedur, Systemfunktion und der Objektkatalogsicht im Abfrage-Editor angezeigt wird.  
  
-   **Vorbereitungen:**  [Sicherheit](#Security)  
  
-   **Anzeigen der Definition einer Prozedur unter Verwendung von:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Gespeicherte Systemprozedur: `sp_helptext`  
 Erfordert die Mitgliedschaft in der **public** -Rolle. Definitionen von Systemobjekten sind öffentlich sichtbar. Die Definition von Benutzerobjekten ist für den Objektbesitzer sichtbar oder für Berechtigte, die über eine der folgenden Berechtigungen verfügen: ALTER, CONTROL, TAKE OWNERSHIP oder VIEW DEFINITION.  
  
 Systemfunktion: `OBJECT_DEFINITION`  
 Definitionen von Systemobjekten sind öffentlich sichtbar. Die Definition von Benutzerobjekten ist für den Objektbesitzer sichtbar oder für Berechtigte, die über eine der folgenden Berechtigungen verfügen: ALTER, CONTROL, TAKE OWNERSHIP oder VIEW DEFINITION. Über diese Berechtigungen verfügen implizit Mitglieder der festen Datenbankrollen **db_owner**, **db_ddladmin**und **db_securityadmin** .  
  
 Objektkatalogsicht: `sys.sql_modules`  
 Die Sichtbarkeit der Metadaten in Katalogsichten ist auf sicherungsfähige Elemente eingeschränkt, bei denen der Benutzer entweder der Besitzer ist oder für die dem Benutzer eine Berechtigung erteilt wurde. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).  
  
##  <a name="Procedures"></a> Anzeigen der Definition einer gespeicherten Prozedur  
 Sie können eine der folgenden Anwendungen verwenden:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 **So zeigen Sie die Definition einer Prozedur im Objekt-Explorer an**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **Datenbanken**, erweitern Sie die Datenbank, zu der die Prozedur gehört, und erweitern Sie dann **Programmierbarkeit**.  
  
3.  Erweitern Sie **Gespeicherte Prozeduren**, klicken Sie mit der rechten Maustaste auf die Prozedur, und klicken Sie anschließend auf **Skript für gespeicherte Prozeduren als**. Klicken Sie dann auf eine der folgenden Optionen: **Create To**, **Alter To**oder **Drop and Create in**.  
  
4.  Wählen Sie **Neues Abfrage-Editor-Fenster**aus. Daraufhin wird die Prozedurdefinition angezeigt.  
  
###  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So zeigen Sie die Definition einer Prozedur im Abfrage-Editor an**  
  
 Gespeicherte Systemprozedur: `sp_helptext`  
 1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie auf der Symbolleiste auf **Neue Abfrage**.  
  
3.  Geben Sie im Abfragefenster die folgende Anweisung, die `sp_helptext` gespeicherten Systemprozedur. Ändern Sie den Datenbanknamen und den Namen der gespeicherten Prozedur so, dass diese auf die gewünschte Datenbank und die gespeicherte Prozedur verweisen.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_helptext N'AdventureWorks2012.dbo.uspLogError';  
    ```  
  
 Systemfunktion: `OBJECT_DEFINITION`  
 1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie auf der Symbolleiste auf **Neue Abfrage**.  
  
3.  Geben Sie im Abfragefenster die folgenden Anweisungen ein, die die `OBJECT_DEFINITION`-Systemfunktion verwenden: Ändern Sie den Datenbanknamen und den Namen der gespeicherten Prozedur so, dass diese auf die gewünschte Datenbank und die gespeicherte Prozedur verweisen.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT OBJECT_DEFINITION (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
 Objektkatalogsicht: `sys.sql_modules`  
 1.  Stellen Sie im Objekt-Explorer eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie auf der Symbolleiste auf **Neue Abfrage**.  
  
3.  Geben Sie im Abfragefenster die folgenden Anweisungen, mit denen die `sys.sql_modules` -Katalogsicht angezeigt. Ändern Sie den Datenbanknamen und den Namen der gespeicherten Prozedur so, dass diese auf die gewünschte Datenbank und die gespeicherte Prozedur verweisen.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT definition  
    FROM sys.sql_modules  
    WHERE object_id = (OBJECT_ID(N'AdventureWorks2012.dbo.uspLogError'));  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer gespeicherten Prozedur](create-a-stored-procedure.md)   
 [Ändern einer gespeicherten Prozedur](modify-a-stored-procedure.md)   
 [Löschen einer gespeicherten Prozedur](delete-a-stored-procedure.md)   
 [Umbenennen einer gespeicherten Prozedur](rename-a-stored-procedure.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-definition-transact-sql)   
 [sys.sql_modules &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-modules-transact-sql)   
 [sp_helptext &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helptext-transact-sql)   
 [OBJECT_ID &#40;Transact-SQL&#41;](/sql/t-sql/functions/object-id-transact-sql)  
  
  
