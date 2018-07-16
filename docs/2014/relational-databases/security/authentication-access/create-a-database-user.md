---
title: Erstellen eines Datenbankbenutzers | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.DATABASEUSER.GENERAL.F1
- sql12.swb.user.securables.f1
helpviewer_keywords:
- database users, creating
- creating users with Management Studio
- mapping users
- users [SQL Server], creating
- database user additions [SQL Server]
- database users, mapping
- CREATE USER [Management Studio]
- users [SQL Server], adding
- mapping database users
ms.assetid: 782798d3-9552-4514-9f58-e87be4b264e4
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b71bfa8857cb754cbab2fa983dea96cb45ea4ae0
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299970"
---
# <a name="create-a-database-user"></a>Erstellen eines Datenbankbenutzers
  In diesem Thema wird beschrieben, wie zum Erstellen eines Datenbankbenutzers, der diesen einem Anmeldenamen in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Der Datenbankbenutzer ist die Identität der Anmeldung, wenn er mit einer Datenbank verbunden ist. Der Datenbankbenutzer kann den gleichen Namen verwenden wie die Anmeldung, dies ist jedoch nicht erforderlich. In diesem Thema wird davon ausgegangen, dass in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]bereits eine Anmeldung vorhanden ist. Informationen dazu, wie Sie eine Anmeldung zu erstellen, finden Sie unter [erstellen Sie eine Anmeldung](create-a-login.md).  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Hintergrund](#Restrictions)  
  
     [Security](#Security)  
  
-   **Zum Erstellen eines Datenbankbenutzers mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Hintergrund  
 Ein Benutzer ist ein Sicherheitsprinzipal auf Datenbankebene. Anmeldungen müssen einem Datenbankbenutzer zugeordnet werden, damit eine Verbindung zu einer Datenbank hergestellt werden kann. Eine Anmeldung kann unterschiedlichen Datenbanken als unterschiedliche Benutzer zugeordnet werden, aber kann nur als ein Benutzer in jeder Datenbank zugeordnet werden. In einer teilweise eigenständigen Datenbank kann ein Benutzer erstellt werden, der über keinen Anmeldenamen verfügt. Weitere Informationen zu eigenständigen Datenbankbenutzern finden Sie unter [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql). Wenn in einer Datenbank Gastbenutzer aktiviert sind, kann eine Anmeldung, die keinem Datenbankbenutzer zugeordnet ist, als Gastbenutzer auf die Datenbank zugreifen.  
  
> [!IMPORTANT]  
>  Gastbenutzer sind normalerweise deaktiviert. Aktivieren Sie Gastbenutzer nur, wenn es notwendig ist.  
  
 Als Sicherheitsprinzipalen können Benutzern Berechtigungen gewährt werden. Die Datenbank ist der Bereich eines Benutzers. Um eine bestimmte Datenbank mit einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]zu verbinden, muss ein Anmeldename einem Datenbankbenutzer zugeordnet werden. Die Berechtigungen innerhalb der Datenbank werden dem Datenbankbenutzer, nicht dem Anmeldenamen, gewährt bzw. verweigert.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die `ALTER ANY USER`-Berechtigung für die Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
##### <a name="to-create-a-database-user"></a>So erstellen Sie einen Datenbankbenutzer  
  
1.  Erweitern Sie im Objekt-Explorer den Ordner **Datenbanken** .  
  
2.  Erweitern Sie die Datenbank, in der der neue Datenbankbenutzer erstellt werden soll.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Sicherheit** , zeigen Sie auf **Neu**, und klicken Sie dann auf **Benutzer**.  
  
4.  Wählen Sie im Dialogfeld **Datenbankbenutzer - Neu** auf der Seite **Allgemein** einen der folgenden Benutzertypen aus der Liste **Benutzertyp** aus: **SQL-Benutzer mit Anmeldename**, **SQL-Benutzer ohne Anmeldename**, **Benutzer, der einem Zertifikat zugeordnet ist**, **Benutzer, der einem asymmetrischen Schlüssel zugeordnet ist**oder **Windows-Benutzer**.  
  
5.  Geben Sie in das Feld **Benutzername** den Namen für den neuen Benutzer ein. Wenn Sie **Windows-Benutzer** aus der Liste **Benutzertyp** ausgewählt haben, können Sie zudem auf die Auslassungszeichen **(…)** klicken, um das Dialogfeld **Benutzer oder Gruppe auswählen** zu öffnen.  
  
6.  Geben Sie im Feld **Anmeldename** den Anmeldenamen für den Benutzer ein. Klicken Sie alternativ auf die Auslassungspunkte **(…)** , um das Dialogfeld **Anmeldenamen auswählen** zu öffnen. **Anmeldename** ist verfügbar, wenn Sie entweder **SQL-Benutzer mit Anmeldename** oder **Windows-Benutzer** aus der Liste **Benutzertyp** auswählen.  
  
7.  Im Feld **Standardschema** wird das Schema angegeben, das von diesem Benutzer erstellte Objekte besitzen wird. Klicken Sie alternativ auf die Auslassungspunkte **(…)** , um das Dialogfeld **Schema auswählen** zu öffnen. **Standardschema** ist verfügbar, wenn Sie entweder **SQL-Benutzer mit Anmeldename**, **SQL-Benutzer ohne Anmeldename**oder **Windows-Benutzer** aus der Liste **Benutzertyp** auswählen.  
  
8.  Geben Sie im Feld **Zertifikatsname** das Zertifikat an, das für den Datenbankbenutzer verwendet werden soll. Klicken Sie alternativ auf die Auslassungspunkte **(…)** , um das Dialogfeld **Zertifikat auswählen** zu öffnen. **Zertifikatname** ist verfügbar, wenn Sie die Option **Benutzer, der einem Zertifikat zugeordnet ist** aus der Liste **Benutzertyp** auswählen.  
  
9. Geben Sie im Feld **Asymmetrischer Schlüsselname**  den Schlüssel an, der für den Datenbankbenutzer verwendet werden soll. Klicken Sie alternativ auf die Auslassungspunkte **(…)** , um das Dialogfeld **Asymmetrischen Schlüssel auswählen** zu öffnen. Die Option für den **asymmetrischen Schlüsselnamen** ist verfügbar, wenn Sie die Option **Benutzer, der einem asymmetrischen Schlüssel zugeordnet ist** aus der Liste **Benutzertyp** auswählen.  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="additional-options"></a>Zusätzliche Optionen  
 Im Dialogfeld **Datenbankbenutzer - Neu** sind auch Optionen auf vier zusätzlichen Seiten verfügbar: **Schemas im Besitz**, **Mitgliedschaft**, **Sicherungsfähige Elemente**und **Erweiterte Eigenschaften**.  
  
-   Auf der Seite **Schemas im Besitz** werden alle möglichen Schemas aufgelistet, die dem neuen Datenbankbenutzer gehören können. Aktivieren oder deaktivieren Sie unter **Schemas im Besitz dieses Benutzers**die Kontrollkästchen, die sich neben den Schemas befinden, um einem Datenbankbenutzer Schemas hinzuzufügen oder diese von diesem zu entfernen.  
  
-   Auf der Seite **Mitgliedschaft** werden alle möglichen Datenbank-Mitgliedschaftsrollen aufgelistet, die dem neuen Datenbankbenutzer gehören können. Aktivieren oder deaktivieren Sie unter **Mitgliedschaft in Datenbankrolle**die Kontrollkästchen, die sich neben den Rollen befinden, um einem Datenbankbenutzer Rollen hinzuzufügen oder diese von diesem zu entfernen.  
  
-   Auf der Seite **Sicherungsfähige Elemente** werden alle möglichen sicherungsfähigen Elemente und die Berechtigungen für diese sicherungsfähigen Elemente aufgelistet, die für die Anmeldung gewährt werden können.  
  
-   Mithilfe der Seite **Erweiterte Eigenschaften** können Sie Datenbankbenutzern benutzerdefinierte Eigenschaften hinzufügen. Die folgenden Optionen sind auf dieser Seite verfügbar.  
  
     **Datenbank**  
     Zeigt den Namen der ausgewählten Datenbank an. Dieses Feld ist schreibgeschützt.  
  
     **Sortierung**  
     Zeigt die für die ausgewählte Datenbank verwendete Sortierung an. Dieses Feld ist schreibgeschützt.  
  
     **Eigenschaften**  
     Zeigt bzw. gibt die erweiterten Eigenschaften für das Objekt an. Jede erweiterte Eigenschaft besteht aus einem aus Name und Wert bestehenden Paar von Metadaten, das dem Objekt zugeordnet ist.  
  
     **Auslassungspunkte (…)**  
     Klicken Sie auf die Auslassungszeichen **(…)** hinter **Wert** , um das Dialogfeld **Wert für erweiterte Eigenschaft** zu öffnen. Geben Sie den Wert der erweiterten Eigenschaft an diesem größeren Speicherort ein, bzw. zeigen Sie ihn an. Weitere Informationen finden Sie unter [Wert für erweiterte Eigenschaft (Dialogfeld)](http://msdn.microsoft.com/library/ms189353.aspx).  
  
     **Delete**  
     Entfernt die ausgewählte erweiterte Eigenschaft.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-database-user"></a>So erstellen Sie einen Datenbankbenutzer  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- Creates the login AbolrousHazem with password '340$Uuxwp7Mcxo7Khy'.  
    CREATE LOGIN AbolrousHazem   
        WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
    GO  
  
    -- Creates a database user for the login created above.  
    CREATE USER AbolrousHazem FOR LOGIN AbolrousHazem;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).  
  
## <a name="see-also"></a>Siehe auch  
 
  [Prinzipale &amp;#40;Datenbank-Engine&amp;#41;](principals-database-engine.md)  
  
  
