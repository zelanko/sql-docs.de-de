---
title: Erstellen einer Anwendungsrolle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.approle.general.f1
helpviewer_keywords:
- application roles [SQL Server], creating
ms.assetid: 6b8da1f5-3d8e-4f88-b111-b915788b06f1
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 9a46c83c497c8eaeba3873bafef399f924506916
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076260"
---
# <a name="create-an-application-role"></a>Erstellen einer Anwendungsrolle
  In diesem Thema wird beschrieben, wie Sie eine Anwendungsrolle in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]erstellen können. Mit Anwendungsrollen wird der Benutzerzugriff auf eine Datenbank bis auf Zugriffe über bestimmte Anwendungen eingeschränkt. Anwendungsrollen verfügen nicht über Benutzer, daher wird die Liste **Rollenmitglieder** nicht angezeigt, wenn **Anwendungsrolle** ausgewählt wird.  
  
> [!IMPORTANT]  
>  Beim Festlegen von Kennwörtern für Anwendungsrollen wird die Kennwortkomplexität überprüft. Anwendungen, die Anwendungsrollen aufrufen, müssen ihre Kennwörter speichern. Kennwörter für Anwendungsrollen sollten immer verschlüsselt gespeichert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So erstellen Sie eine Anwendungsrolle mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER ANY APPLICATION ROLE-Berechtigung in der Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
##### <a name="to-create-an-application-role"></a>So erstellen Sie eine Anwendungsrolle  
  
1.  Erweitern Sie im Objekt-Explorer die Datenbank, in der Sie eine Anwendungsrolle erstellen möchten.  
  
2.  Erweitern Sie den Ordner **Sicherheit** .  
  
3.  Erweitern Sie den Ordner **Rollen** .  
  
4.  Klicken Sie mit der rechten Maustaste auf den Ordner **Anwendungsrollen** , und klicken Sie dann auf **Neue Anwendungsrolle…**.  
  
5.  Geben Sie in das Dialogfeld **Anwendungsrolle - Neu** auf der Seite **Allgemein**den neuen Namen der neuen Anwendungsrolle in das Feld **Rollenname** ein.  
  
6.  Geben Sie im Feld **Standardschema** das Schema an, das Objekte besitzen soll, die von dieser Rolle durch Eingabe der Objektnamen erstellt wurden. Klicken Sie alternativ auf die Auslassungspunkte **(…)** , um das Dialogfeld **Schema suchen** zu öffnen.  
  
7.  Geben Sie im Feld **Kennwort** ein Kennwort für die neue Rolle ein. Geben Sie im Feld **Kennwort bestätigen** das Kennwort erneut ein.  
  
8.  Wählen Sie unter **Schemas im Besitz dieser Rolle**die Schemas aus, die diese Rolle besitzen soll, oder zeigen Sie sie an. Jedes Schema kann immer nur im Besitz eines einzelnen Schemas oder einer einzelnen Rolle sein.  
  
9. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a>Zusätzliche Optionen  
 Das Dialogfeld **Anwendungsrolle - Neu** verfügt zudem über Optionen auf zwei zusätzlichen Seiten: **Sicherungsfähige Elemente** und **Erweiterte Eigenschaften**.  
  
-   Auf der Seite **Sicherungsfähige Elemente** werden alle möglichen sicherungsfähigen Elemente und die Berechtigungen für diese sicherungsfähigen Elemente aufgelistet, die für die Anmeldung gewährt werden können.  
  
-   Mithilfe der Seite **Erweiterte Eigenschaften** können Sie Datenbankbenutzern benutzerdefinierte Eigenschaften hinzufügen.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-an-application-role"></a>So erstellen Sie eine Anwendungsrolle  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- Creates an application role called "weekly_receipts" that has the password "987Gbv876sPYY5m23" and "Sales" as its default schema.  
  
    CREATE APPLICATION ROLE weekly_receipts   
        WITH PASSWORD = '987G^bv876sPY)Y5m23'   
        , DEFAULT_SCHEMA = Sales;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-application-role-transact-sql).  
  
  
