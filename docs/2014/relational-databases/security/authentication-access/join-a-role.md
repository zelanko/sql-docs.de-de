---
title: Verknüpfen einer Rolle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/14/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASEUSER.MEMBERSHIP.F1
helpviewer_keywords:
- adding a member to a role
- join a role
ms.assetid: 05c8d10d-5823-46c6-8b1a-81722da6a42b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: d1c846f7ed60bbecac64021e9a881312e1f1f64c
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54134120"
---
# <a name="join-a-role"></a>Verknüpfen einer Rolle
  In diesem Thema wird beschrieben, wie Rollen in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]Anmeldenamen und Datenbankbenutzern zugewiesen werden. Für die effiziente Verwaltung von Berechtigungen in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwenden Sie Rollen. Weisen Sie Rollen Berechtigungen zu, und fügen Sie den Rollen dann Benutzer und Anmeldenamen hinzu, oder entfernen Sie solche. Bei Verwendung von Rollen müssen Berechtigungen nicht für jeden Benutzer einzeln verwaltet werden.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt vier Typen von Rollen.  
  
-   Feste Serverrollen  
  
-   Benutzerdefinierte Serverrollen  
  
-   Feste Datenbankrollen  
  
-   Benutzerdefinierte Datenbankrollen  
  
 Die festen Rollen sind in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]automatisch verfügbar. Feste Rollen verfügen über die erforderlichen Berechtigungen zum Ausführen häufiger Tasks. Weitere Informationen zu festen Rollen finden Sie unter den folgenden Links: Benutzerdefinierte Rollen werden von Ihnen erstellt und können mit den von Ihnen ausgewählten Berechtigungen angepasst werden. Weitere Informationen zu benutzerdefinierten Rollen finden Sie unter den folgenden Links:  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Sicherheit](#Security)  
  
-   **Zuweisen von Rollen zu Anmeldenamen und Datenbankbenutzern mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Durch das Ändern des Namens einer Datenbankrolle werden die ID-Nummer, der Besitzer oder Berechtigungen der Rolle nicht geändert.  
  
-   Datenbankrollen werden in den Katalogsichten sys.database_role_members und sys.database_principals angezeigt.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert `ALTER ANY ROLE` -Berechtigung für die Datenbank `ALTER` -Berechtigung für die Rolle oder die Mitgliedschaft in **Db_securityadmin**.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a>So fügen Sie einer festen Serverrolle ein Mitglied hinzu  
  
1.  Erweitern Sie im Objekt-Explorer den Server, für den Sie eine feste Serverrolle bearbeiten möchten.  
  
2.  Erweitern Sie den Ordner **Sicherheit** .  
  
3.  Erweitern Sie den Ordner **Serverrollen** .  
  
4.  Klicken Sie mit der rechten Maustaste auf die Rolle, die Sie bearbeiten möchten, und wählen Sie anschließend **Eigenschaften**aus.  
  
5.  In der **Serverrolleneigenschaften –**_Server_role_name_ Dialogfeld auf die **Mitglieder** auf **hinzufügen**.  
  
6.  Geben Sie im Dialogfeld **Serveranmeldenamen oder -rolle auswählen** unter **Geben Sie die Namen der auszuwählenden Objekte ein (Beispiele)** den Anmeldenamen oder die Serverrolle ein, den bzw. die Sie dieser Serverrolle hinzufügen möchten. Alternativ können Sie auf **Durchsuchen** klicken und verfügbare Objekte im Dialogfeld **Nach Objekten suchen** auswählen. Klicken Sie auf **OK** zum Zurückgeben der **Serverrolleneigenschaften –**_Server_role_name_ Dialogfeld.  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a>So fügen Sie einer benutzerdefinierten Datenbankrolle ein Mitglied hinzu  
  
1.  Erweitern Sie im Objekt-Explorer den Server, für den Sie eine benutzerdefinierte Datenbankrolle bearbeiten möchten.  
  
2.  Erweitern Sie den Ordner **Datenbanken** .  
  
3.  Erweitern Sie die Datenbank, in der Sie eine benutzerdefinierte Datenbankrolle bearbeiten möchten.  
  
4.  Erweitern Sie den Ordner **Sicherheit** .  
  
5.  Erweitern Sie den Ordner **Rollen** .  
  
6.  Erweitern Sie den Ordner **Serverrollen** .  
  
7.  Klicken Sie mit der rechten Maustaste auf die Rolle, die Sie bearbeiten möchten, und wählen Sie anschließend **Eigenschaften**aus.  
  
8.  In der **Eigenschaften der Datenbankrolle -**_Database_role_name_ Dialogfeld die **allgemeine** auf **hinzufügen**.  
  
9. Geben Sie im Dialogfeld **Datenbankbenutzer oder -rolle auswählen** unter **Geben Sie die Namen der auszuwählenden Objekte ein (Beispiele)** den Anmeldenamen oder die Datenbankrolle ein, den bzw. die Sie dieser Datenbankrolle hinzufügen möchten. Alternativ können Sie auf **Durchsuchen** klicken und verfügbare Objekte im Dialogfeld **Nach Objekten suchen** auswählen. Klicken Sie auf **OK** zum Zurückgeben der **Eigenschaften der Datenbankrolle -**_Database_role_name_ Dialogfeld.  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a>So fügen Sie einer festen Serverrolle ein Mitglied hinzu  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    ALTER SERVER ROLE diskadmin ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [ALTER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-role-transact-sql).  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a>So fügen Sie einer benutzerdefinierten Datenbankrolle ein Mitglied hinzu  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    ALTER ROLE Marketing ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_addrolemember &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addrolemember-transact-sql).  
  
## <a name="see-also"></a>Siehe auch  
 [Rollen auf Serverebene](server-level-roles.md)   
 [Rollen auf Datenbankebene](../authentication-access/database-level-roles.md)   
 [Anwendungsrollen](../authentication-access/application-roles.md)  
  
  
