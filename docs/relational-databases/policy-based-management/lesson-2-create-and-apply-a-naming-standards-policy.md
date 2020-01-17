---
title: 'Lektion 2: Erstellen und Anwenden einer Richtlinie für Benennungsstandards'
description: In diesem Tutorial erfahren Sie, wie Sie eine Richtlinie für Benennungsstandards für die richtlinienbasierte Verwaltung in SQL Server erstellen und anwenden.
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.technology: security
ms.prod_service: database-engine
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 87e51f4e-156c-4def-8572-76a15075d75e
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ac5510320783c35c83f84118e9679da4fd351415
ms.sourcegitcommit: 035ad9197cb9799852ed705432740ad52e0a256d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75558695"
---
# <a name="lesson-2-create-and-apply-a-naming-standards-policy"></a>Lektion 2: Erstellen und Anwenden einer Richtlinie für Benennungsstandards
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Einige Typen von richtlinienbasierten Verwaltungsrichtlinien können Trigger erstellen, um die zukünftige Einhaltung der Richtlinie zu erzwingen. In dieser Lektion erstellen Sie eine Richtlinie, die einen Benennungsstandard für Tabellen erzwingt. Anschließend testen Sie die Richtlinie, indem Sie versuchen, eine Tabelle zu erstellen, die gegen die Richtlinie verstößt.  


## <a name="prerequisites"></a>Voraussetzungen
Zur Durchführung dieses Tutorials benötigen Sie SQL Server Management Studio sowie Zugriff auf einen Server, auf dem SQL-Server ausgeführt wird.

- Installieren Sie [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installieren Sie die [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
  
## <a name="create-the-finance-database"></a>Erstellen der Datenbank „Finance“  
  
1.  Öffnen Sie ein Abfragefenster in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], und führen Sie die folgende Anweisung aus:  
  
    ```sql  
    CREATE DATABASE Finance ;  
    GO  
    ```  
  
2.  Klicken Sie im Objekt-Explorer auf **Datenbanken**, und drücken Sie anschließend F5, um die Liste der Datenbanken zu aktualisieren.  

## <a name="create-the-finance-tables-condition"></a>Erstellen der Tabellenbedingung „Finance“ 

1.  Erweitern Sie im Objekt-Explorer **Verwaltung**, erweitern Sie **Richtlinienverwaltung**, klicken Sie mit der rechten Maustaste auf **Bedingungen**und anschließend auf **Neue Bedingung**. 

   ![Neue Bedingung](Media/lesson-2-create-and-apply-a-naming-standards-policy/new-condition.png)
  
2.  Geben Sie im Dialogfeld **Neue Bedingung erstellen** im Feld **Name** den Namen **Finanz_Tabellen**ein.  
    1. Wählen Sie in der Liste **Facet** die Option **Mehrteiliger Name**aus. 
    1. Geben Sie im Bereich **Ausdruck** im Feld **Feld** die Option **\@Name** aus, wählen Sie im Feld **Operator** die Option **Like** aus, und geben Sie in das Feld **Wert** den Namen ```'fintbl%'``` ein, um zu erzwingen, dass alle Tabellennamen mit den Buchstaben **fintbl** anfangen.
    1. Geben Sie auf der Seite **Beschreibung** die Beschreibung **Finanz_Tabellen-Namen müssen mit fintbl beginnen**ein, und klicken Sie anschließend auf **OK** , um die Bedingung zu erstellen.  

    ![Tabellenbedingung „Finance“](Media/lesson-2-create-and-apply-a-naming-standards-policy/finance-tables-condition.png)
 
## <a name="create-the-finance-name-policy"></a>Erstellen der Richtlinie „Finance Name“  
  
1.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf **Richtlinien**und anschließend auf **Neue Richtlinie**.  

   ![Neue Richtlinie](Media/lesson-2-create-and-apply-a-naming-standards-policy/new-policy.png)
  
2.  Geben Sie im Dialogfeld **Neue Richtlinie erstellen** im Feld **Name** den Namen **Finanz_Name**ein.
    1. Wählen Sie in der Liste **Bedingung überprüfen** die Option **Finanz_Tabellen**aus. Diese befindet sich im Abschnitt **Mehrteiliger Name** . 
    1. Im Abschnitt **Für** wird eine Liste der Datenbankobjekte angezeigt, die diese Richtlinie anwenden könnten. Aktivieren Sie das Kontrollkästchen für **Jede Tabelle**.
    1. Wählen Sie in der Liste **Aktiviert** aus. (Das Feld **Aktiviert** gilt nicht für **bedarfsgesteuerte** Richtlinien.)
    1. Wählen Sie in der Liste **Auswertungsmodus** die Option **Bei Änderung: Verhindern**aus. Dadurch wird die Richtlinie erzwungen, indem ein Datenbanktrigger für die Datenbank Finanzen erstellt wird. 
    1. Wählen Sie in der Liste **Serverbeschränkung** die Option **Keine**aus. 
    1. Fügen Sie auf der Seite **Beschreibung** die Beschreibung „Tabellennamen in der Finance-Datenbank müssen "fintbl%" enthalten“ hinzu. 
    1. Kehren Sie zur Seite **Allgemein** zurück, erweitern Sie im Bereich **Jede Datenbank** den Eintrag **Jede**, und klicken Sie anschließend auf **Neue Bedingung**.

    ![Erstellen der neuen Richtlinie „Finance Name“](Media/lesson-2-create-and-apply-a-naming-standards-policy/create-new-policy-finance-name.png)
  
6.  Geben Sie im Dialogfeld **Neue Bedingung erstellen** im Feld **Name** den Namen **Finanz_Datenbank**ein.
    1. Vervollständigen Sie im Feld **Ausdruck** den Ausdruck so, dass er @Name = 'Finance' umfasst, und klicken Sie anschließend auf **OK**, um die Bedingungsseite zu schließen. 
  
    ![Erstellen der neuen Bedingung „finance database“](Media/lesson-2-create-and-apply-a-naming-standards-policy/create-new-condition.png)

    > [!NOTE]  
    > Sie müssen möglicherweise mit dem Cursor aus dem Feld **Wert** wechseln, um die Schaltfläche **OK** zu aktivieren.  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="create-the-finance-policy-category"></a>Erstellen der Richtlinienkategorie „Finance“  
  
1.  Erweitern Sie im Objekt-Explorer **Verwaltung**, klicken Sie mit der rechten Maustaste auf **Richtlinienverwaltung**und anschließend auf **Kategorien verwalten**.  

   ![Kategorien verwalten](Media/lesson-2-create-and-apply-a-naming-standards-policy/manage-categories.png)
  
2.  Geben Sie im Dialogfeld **Richtlinienkategorien verwalten** unter **Name**die Zeichenfolge **Finanzen** in das leere Feld ein, und deaktivieren Sie **Datenbankabonnements beauftragen**. **Datenbankabonnements beauftragen** zwingt jede Datenbank in der Instanz, die zu dieser Richtlinienkategorie gehörenden Richtlinien zu abonnieren. Für diese Lektion darf nur die Datenbank Finanzen die Richtlinie Finanz_Name abonnieren.  

    ![Richtlinienkategorien verwalten](Media/lesson-2-create-and-apply-a-naming-standards-policy/manage-policy-categories.png)
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

## <a name="subscribe-to-the-finance-policy-category"></a>Abonnieren der Richtlinienkategorie „Finance“  
  
1.  Erweitern Sie im Objekt-Explorer **Datenbanken**, klicken Sie mit der rechten Maustaste auf **Finanzen**, zeigen Sie auf **Richtlinien**, und klicken Sie anschließend auf **Kategorien**. 

   ![Finance-Richtlinienkategorien](Media/lesson-2-create-and-apply-a-naming-standards-policy/finance-categories.png)
  
2.  Aktivieren Sie das Kontrollkästchen **Abonniert** für die Kategorie **Finanzen** .  

   ![Finance-Richtlinie abonniert](Media/lesson-2-create-and-apply-a-naming-standards-policy/subscribe-to-finance.png)
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="test-the-enforcement-of-the-finance-name-policy"></a>Testen der Durchsetzung der Richtlinie „Finance Name“  
  
1.  Öffnen Sie ein Abfragefenster in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Führen Sie die folgenden Anweisungen aus, mit denen versucht wird, eine Tabelle zu erstellen, die gegen die Richtlinie **Finanz_Name** verstößt. Die Tabelle verstößt gegen die Richtlinie, da der Tabellenname nicht mit den Buchstaben **fintbl**beginnt.  
  
    ```sql  
    USE Finance ;  
    GO  
    CREATE TABLE NewTable  
    (Col1 int) ;  
    GO    
    ```  
  
    Beachten Sie, dass die Richtlinie das Erstellen der Tabelle verhindert und eine Informationsmeldung zurückgibt, die den Richtliniennamen liefert. 

   ```
     Policy 'Finance Name' has been violated by 'SQLSERVER:\SQL\SQL\SQL2017\Databases\Finance\Tables\dbo.NewTable'.
     This transaction will be rolled back.
     Policy condition: '@Name LIKE 'fintbl%''
     Policy description: 'Tables names in the Finance database must contain 'fintbl%''.
     Additional help: '' : ''
     Statement: 'CREATE TABLE NewTable  
         (Col1 int)'.
     Msg 515, Level 16, State 2, Procedure msdb.sys.sp_syspolicy_execute_policy, Line 69 [Batch Start Line 2]
     Cannot insert the value NULL into column 'target_query_expression', table 'msdb.dbo.syspolicy_policy_execution_history_details_internal'; column does not allow nulls. INSERT fails.
     The statement has been terminated.
   ``` 
  
2.  Um einen gültigen Namen anzugeben, ändern Sie den Code wie folgt, und führen Sie dann erneut die Anweisung aus.  
  
    ```sql  
    USE Finance ;  
    GO  
    CREATE TABLE fintblNewTable  
    (Col1 int) ;  
    GO    
    ```  
  
    Nun wird die Tabelle erstellt.  
  
## <a name="apply-the-policy-to-the-whole-server"></a>Übernehmen der Richtlinie für den ganzen Server  
  
1.  Momentan hat nur die Datenbank Finanzen die Richtlinienkategorie Finanzen abonniert. In vielen Fällen ist es einfacher, die Richtlinienkategorie für den ganzen Server zu übernehmen. Erweitern Sie im Objekt-Explorer **Verwaltung**, klicken Sie mit der rechten Maustaste auf **Richtlinienverwaltung**und anschließend auf **Kategorien verwalten**.  
  
2.  Suchen Sie im Dialogfeld **Richtlinienkategorien verwalten** nach der Kategorie „Finanzen“, und aktivieren Sie das Kontrollkästchen **Datenbankabonnements beauftragen** für die Kategorie „Finanzen“.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Nun gilt die Kategorie „Finanzen“ für alle Datenbanken, aber durch die von Ihnen erstellte Bedingung ist die Richtlinie „Finanz_Name“ nur auf die Datenbank „Finanzen“ beschränkt. Dieses Beispiel zeigt, wie Sie komplexe Kombinationen von Bedingungen verwenden können, um Richtlinien so zuzuweisen, dass sie für viele Server richtig übernommen werden.  
  
## <a name="summary"></a>Zusammenfassung  
Dieses Lernprogramm hat gezeigt, wie Sie Bedingungen, Richtlinien und Richtliniengruppen der richtlinienbasierten Verwaltung erstellen und die Kompatibilität der Ziele der richtlinienbasierten Verwaltung überprüfen können.  
  
## <a name="next"></a>Next (Weiter)  
Dieses Lernprogramm ist beendet. Um zum Anfang zurückzukehren, wechseln Sie zu [Tutorial: Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/tutorial-administering-servers-by-using-policy-based-management.md).  
  
Eine Liste der Tutorials finden Sie unter [Tutorials für SQL Server 2016](../../sql-server/tutorials-for-sql-server-2016.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
