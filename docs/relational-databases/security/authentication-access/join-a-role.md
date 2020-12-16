---
title: Verknüpfen einer Rolle | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie Konten oder Datenbankbenutzern in SQL Server mithilfe von SQL Server Management Studio oder Transact-SQL Rollen zuweisen. Verwenden Sie Rollen, um Berechtigungen zu verwalten.
ms.custom: ''
ms.date: 07/14/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL13.SWB.DATABASEUSER.MEMBERSHIP.F1
helpviewer_keywords:
- adding a member to a role
- join a role
ms.assetid: 05c8d10d-5823-46c6-8b1a-81722da6a42b
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 46d97f8d8e8313bc3fe63a83c4d2187704be802b
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97460004"
---
# <a name="join-a-role"></a>Verknüpfen einer Rolle
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
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
  
     [Security](#Security)  
  
-   **Zuweisen von Rollen zu Anmeldenamen und Datenbankbenutzern mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Durch das Ändern des Namens einer Datenbankrolle werden die ID-Nummer, der Besitzer oder Berechtigungen der Rolle nicht geändert.  
  
-   Datenbankrollen werden in den Katalogsichten sys.database_role_members und sys.database_principals angezeigt.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die **ALTER ANY ROLE** -Berechtigung für die Datenbank, die **ALTER** -Berechtigung für die Rolle oder die Mitgliedschaft in **db_securityadmin**.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a>So fügen Sie einer festen Serverrolle ein Mitglied hinzu  
  
1.  Erweitern Sie im Objekt-Explorer den Server, für den Sie eine feste Serverrolle bearbeiten möchten.  
  
2.  Erweitern Sie den Ordner **Sicherheit** .  
  
3.  Erweitern Sie den Ordner **Serverrollen** .  
  
4.  Klicken Sie mit der rechten Maustaste auf die Rolle, die Sie bearbeiten möchten, und wählen Sie anschließend **Eigenschaften** aus.  
  
5.  Klicken Sie im Dialogfeld **Serverrolleneigenschaften –** _server\_role\_name_ auf der Seite **Mitglieder** auf **Hinzufügen**.  
  
6.  Geben Sie im Dialogfeld **Serveranmeldenamen oder -rolle auswählen** unter **Geben Sie die Namen der auszuwählenden Objekte ein (Beispiele)** den Anmeldenamen oder die Serverrolle ein, den bzw. die Sie dieser Serverrolle hinzufügen möchten. Alternativ können Sie auf **Durchsuchen** klicken und verfügbare Objekte im Dialogfeld **Nach Objekten suchen** auswählen. Klicken Sie auf **OK**, um zum Dialogfeld **Serverrolleneigenschaften –** _server\_role\_name_ zurückzukehren.  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a>So fügen Sie einer benutzerdefinierten Datenbankrolle ein Mitglied hinzu  
  
1.  Erweitern Sie im Objekt-Explorer den Server, für den Sie eine benutzerdefinierte Datenbankrolle bearbeiten möchten.  
  
2.  Erweitern Sie den Ordner **Datenbanken** .  
  
3.  Erweitern Sie die Datenbank, in der Sie eine benutzerdefinierte Datenbankrolle bearbeiten möchten.  
  
4.  Erweitern Sie den Ordner **Sicherheit** .  
  
5.  Erweitern Sie den Ordner **Rollen** .  
  
6.  Erweitern Sie den Ordner **Serverrollen** .  
  
7.  Klicken Sie mit der rechten Maustaste auf die Rolle, die Sie bearbeiten möchten, und wählen Sie anschließend **Eigenschaften** aus.  
  
8.  Klicken Sie im Dialogfeld **Datenbankrolleneigenschaften –** _database\_role\_name_ auf der Seite **Allgemein** auf **Hinzufügen**.  
  
9. Geben Sie im Dialogfeld **Datenbankbenutzer oder -rolle auswählen** unter **Geben Sie die Namen der auszuwählenden Objekte ein (Beispiele)** den Anmeldenamen oder die Datenbankrolle ein, den bzw. die Sie dieser Datenbankrolle hinzufügen möchten. Alternativ können Sie auf **Durchsuchen** klicken und verfügbare Objekte im Dialogfeld **Nach Objekten suchen** auswählen. Klicken Sie auf **OK**, um zum Dialogfeld **Datenbankrolleneigenschaften –** _database\_role\_name_ zurückzukehren.  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a>So fügen Sie einer festen Serverrolle ein Mitglied hinzu  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    ALTER SERVER ROLE diskadmin ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [ALTER ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-role-transact-sql.md).  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a>So fügen Sie einer benutzerdefinierten Datenbankrolle ein Mitglied hinzu  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    ALTER ROLE Marketing ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_addrolemember &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rollen auf Serverebene](../../../relational-databases/security/authentication-access/server-level-roles.md)   
 [Rollen auf Datenbankebene](../../../relational-databases/security/authentication-access/database-level-roles.md)   
 [Anwendungsrollen](../../../relational-databases/security/authentication-access/application-roles.md)  
  
  
