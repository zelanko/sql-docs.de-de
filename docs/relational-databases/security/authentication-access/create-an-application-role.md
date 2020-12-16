---
title: Erstellen einer Anwendungsrolle | Microsoft-Dokumentation
description: Erstellen Sie eine Anwendungsrolle in SQL Server, indem Sie SQL Server Management Studio oder Transact-SQL verwenden, um den Zugriff auf eine Datenbank einzuschränken, der nicht von einer Anwendung ausgeht.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql13.swb.approle.general.f1
helpviewer_keywords:
- application roles [SQL Server], creating
ms.assetid: 6b8da1f5-3d8e-4f88-b111-b915788b06f1
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: df42c1651d460b0be7b0e2900338982168ebd597
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97468561"
---
# <a name="create-an-application-role"></a>Erstellen einer Anwendungsrolle
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  In diesem Thema wird beschrieben, wie Sie eine Anwendungsrolle in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]erstellen können. Mit Anwendungsrollen wird der Benutzerzugriff auf eine Datenbank bis auf Zugriffe über bestimmte Anwendungen eingeschränkt. Anwendungsrollen verfügen nicht über Benutzer, daher wird die Liste **Rollenmitglieder** nicht angezeigt, wenn **Anwendungsrolle** ausgewählt wird.  
  
> [!IMPORTANT]  
>  Beim Festlegen von Kennwörtern für Anwendungsrollen wird die Kennwortkomplexität überprüft. Anwendungen, die Anwendungsrollen aufrufen, müssen ihre Kennwörter speichern. Kennwörter für Anwendungsrollen sollten immer verschlüsselt gespeichert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So erstellen Sie eine Anwendungsrolle mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER ANY APPLICATION ROLE-Berechtigung in der Datenbank.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
##### <a name="to-create-an-application-role"></a>So erstellen Sie eine Anwendungsrolle  
  
1.  Erweitern Sie im Objekt-Explorer die Datenbank, in der Sie eine Anwendungsrolle erstellen möchten.  
  
2.  Erweitern Sie den Ordner **Sicherheit** .  
  
3.  Erweitern Sie den Ordner **Rollen** .  
  
4.  Klicken Sie mit der rechten Maustaste auf den Ordner **Anwendungsrollen**, und klicken Sie dann auf **Neue Anwendungsrolle...** .  
  
5.  Geben Sie in das Dialogfeld **Anwendungsrolle – Neu** auf der Seite **Allgemein** den Namen der neuen Anwendungsrolle in das Feld **Rollenname** ein.  
  
6.  Geben Sie im Feld **Standardschema** das Schema an, das Objekte besitzen soll, die von dieser Rolle durch Eingabe der Objektnamen erstellt wurden. Klicken Sie alternativ auf die Auslassungspunkte **(...)** , um das Dialogfeld **Schema suchen** zu öffnen.  
  
7.  Geben Sie im Feld **Kennwort** ein Kennwort für die neue Rolle ein. Geben Sie dieses Kennwort erneut im Feld **Kennwort bestätigen** ein.  
  
8.  Wählen Sie unter **Schemas im Besitz dieser Rolle** die Schemas aus, die diese Rolle besitzen soll, oder zeigen Sie sie an. Jedes Schema kann immer nur im Besitz eines einzelnen Schemas oder einer einzelnen Rolle sein.  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

### <a name="additional-options"></a>Zusätzliche Optionen  
 Im Dialogfeld **Anwendungsrolle – Neu** sind auch Optionen auf zwei zusätzlichen Seiten verfügbar: **Sicherungsfähige Elemente** und **Erweiterte Eigenschaften**.  
  
-   Auf der Seite **Sicherungsfähige Elemente** werden alle möglichen sicherungsfähigen Elemente und die Berechtigungen für diese sicherungsfähigen Elemente aufgelistet, die für die Anmeldung gewährt werden können.  
  
-   Mithilfe der Seite **Erweiterte Eigenschaften** können Sie Datenbankbenutzern benutzerdefinierte Eigenschaften hinzufügen.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-an-application-role"></a>So erstellen Sie eine Anwendungsrolle  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- Creates an application role called "weekly_receipts" that has the password "987Gbv876sPYY5m23" and "Sales" as its default schema.  
  
    CREATE APPLICATION ROLE weekly_receipts   
        WITH PASSWORD = '987G^bv876sPY)Y5m23'   
        , DEFAULT_SCHEMA = Sales;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../../t-sql/statements/create-application-role-transact-sql.md).  
  
  
