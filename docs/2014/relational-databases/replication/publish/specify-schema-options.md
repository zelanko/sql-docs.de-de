---
title: Angeben von Schemaoptionen | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- schemas [SQL Server replication], options
- articles [SQL Server replication], transactional replication options
- articles [SQL Server replication], merge replication options
- articles [SQL Server replication], schema options
ms.assetid: 1f85a479-bd6e-4023-abf7-7435a7e5b567
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 52064cc189dc62152814436d2d11326a74c89ff6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85005238"
---
# <a name="specify-schema-options"></a>Angeben von Schemaoptionen
  In diesem Thema wird beschrieben, wie Schemaoptionen in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]festgelegt werden. Beim Veröffentlichen einer Tabelle oder einer Sicht können Sie die Objekterstellungsoptionen steuern, die für das veröffentlichte Objekt repliziert werden. Sie können diesen Option festlegen, wenn der Artikel erstellt wird, und auch zu einem späteren Zeitpunkt ändern. Wenn Sie diese Optionen für einen Artikel nicht explizit festlegen, wird eine Standardgruppe von Optionen definiert.  
  
> [!NOTE]  
>  Die Standardschemaoptionen bei der Verwendung von gespeicherten Replikationsprozeduren können sich von den Standardoptionen unterscheiden, wenn Artikel mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]hinzugefügt werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Empfehlungen](#Recommendations)  
  
-   **So geben Sie Schemaoptionen an mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Wenn Sie Schemaoptionen ändern, nachdem eine Veröffentlichung erstellt wurde, müssen Sie eine neue Momentaufnahme generieren.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Eine umfassende Liste der Schema Optionen finden Sie unter dem ** \@ schema_option** -Parameter [sp_addarticle &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) und [sp_addmergearticle &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Geben Sie auf der Registerkarte **Eigenschaften** des Dialog Felds **Artikeleigenschaften- \<Article> ** die Schema Optionen an, z. b. ob Einschränkungen und Trigger auf Abonnenten kopiert werden sollen. Diese Registerkarte ist im Assistenten für neue Veröffentlichung und im Dialogfeld **Veröffentlichungs \<Publication> Eigenschaften-** verfügbar. Weitere Informationen zum Verwenden des Assistenten sowie Zugriff auf das Dialogfeld finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md) und [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-schema-options"></a>So geben Sie Schemaoptionen an  
  
1.  Wählen Sie auf der Seite **Artikel** des Assistenten für neue Veröffentlichung oder im Dialogfeld **Veröffentlichungs Eigenschaften \<Publication> -** einen Artikel aus, und klicken Sie dann auf **Artikeleigenschaften**.  
  
2.  Wählen Sie aus, auf welche Artikel die Änderungen der Schemaoptionen angewendet werden sollen:  
  
    -   Klicken Sie auf **Eigenschaften des hervorgehobenen \<ObjectType> Artikels festlegen** , um das Dialogfeld **Artikeleigenschaften- \<ObjectName> ** zu starten. in diesem Dialogfeld vorgenommene Eigenschaften Änderungen werden nur auf das Objekt angewendet, das im Objektbereich auf der Seite **Artikel** hervorgehoben ist.  
  
    -   Klicken Sie auf **Eigenschaften aller \<ObjectType> Artikel festlegen** , um das Dialogfeld **Eigenschaften für alle \<ObjectType> Artikel** zu öffnen. in diesem Dialogfeld vorgenommene Eigenschafts Änderungen werden auf alle Objekte dieses Typs im Objektbereich auf der Seite " **Artikel** " angewendet, einschließlich derjenigen, die noch nicht für die Veröffentlichung ausgewählt wurden.  
  
        > [!NOTE]  
        >  Im Dialogfeld **Eigenschaften für alle \<ObjectType> Artikel** vorgenommene Eigenschaften Änderungen überschreiben alle zuvor im Dialogfeld **Artikeleigenschaften \<ObjectName> -** vorgenommenen Änderungen. Wenn Sie beispielsweise sowohl mehrere Standardwerte für alle Artikel eines Objekttyps als auch bestimmte Eigenschaften für einzelne Objekte festlegen möchten, legen Sie zuerst die Standardwerte für alle Artikel fest. Legen Sie anschließend die Eigenschaften für die einzelnen Objekte fest.  
  
3.  Geben Sie auf der Registerkarte **Eigenschaften** des Dialog Felds **Artikeleigenschaften- \<Article> ** in den Abschnitten **Objekte und Einstellungen in Abonnent** und **Zielobjekt** kopieren Werte für die Optionen an.  
  
4.  Ändern Sie die Eigenschaften nach Bedarf, und klicken Sie dann auf **OK**.  
  
5.  Wenn Sie sich im Dialogfeld **Veröffentlichungs Eigenschaften \<Publication> -** befinden, klicken Sie auf **OK** , um das Dialogfeld zu speichern und zu schließen.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Schemaoptionen werden als hexadezimaler Wert angegeben, der das [| (Bitweise OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) -Ergebnis einer oder mehrerer Optionen ist. Weitere Informationen finden Sie unter [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) und [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql).  
  
> [!NOTE]  
>  Sie müssen Schemaoptionswerte vor dem Ausführen eines bitweisen Vorgangs von **binary** in **int** konvertieren. Weitere Informationen finden Sie unter [CAST und CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-snapshot-or-transactional-publication"></a>So geben Sie Schemaoptionen an, wenn Sie einen Artikel für eine Momentaufnahme- oder Transaktionsveröffentlichung definieren  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus. Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört, für die ** \@ Veröffentlichung**, den Namen des Artikels für den ** \@ Artikel**, das Datenbankobjekt, das veröffentlicht wird, für ** \@ source_object**, den Typ des Datenbankobjekts für den ** \@ Typ**und [| (Bitweises OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) Ergebnis von mindestens einer Schema Option für ** \@ schema_option**. Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
#### <a name="to-specify-schema-options-when-defining-an-article-for-a-merge-publication"></a>So geben Sie Schemaoptionen an, wenn Sie einen Artikel für eine Mergeveröffentlichung definieren  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)aus. Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört, für die ** \@ Veröffentlichung**, den Namen des Artikels für den ** \@ Artikel, das**Datenbankobjekt, das veröffentlicht wird, für ** \@ source_object**und [| (Bitweises OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) Ergebnis von mindestens einer Schema Option für ** \@ schema_option**. Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-snapshot-or-transactional-publication"></a>So ändern Sie Schemaoptionen für einen Artikel in einer Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)aus. Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört ** \@ , und den** Namen des Artikels für den ** \@ Artikel**an. Notieren Sie den Wert der **schema_option** -Spalte im Resultset.  
  
2.  Führen Sie einen [& (Bitweise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql)-Vorgang mit dem Wert aus Schritt 1 und dem gewünschten Wert für die Schemaoption aus, um festzustellen, ob die Option festgelegt ist.  
  
    -   Wenn das Ergebnis **0**ist, ist die Option nicht festgelegt.  
  
    -   Wenn das Ergebnis der Optionswert ist, ist die Option bereits festgelegt.  
  
3.  Wenn die Option nicht festgelegt ist, führen Sie einen [| (Bitweisen OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) -Vorgang mit dem Wert aus Schritt 1 und dem gewünschten Wert für die Schemaoption aus.  
  
4.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql)aus. Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört, für die ** \@ Veröffentlichung**, den Namen des Artikels für den ** \@ Artikel**, den Wert **schema_option** für die- ** \@ Eigenschaft**und das hexadezimale Ergebnis aus Schritt 3 für ** \@ value**an.  
  
5.  Führen Sie den Momentaufnahme-Agent zum Generieren einer neuen Momentaufnahme aus. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
#### <a name="to-change-schema-options-for-an-existing-article-in-a-merge-publication"></a>So ändern Sie Schemaoptionen für einen vorhandenen Artikel in einer Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)aus. Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört ** \@ , und den** Namen des Artikels für den ** \@ Artikel**an. Notieren Sie den Wert der **schema_option** -Spalte im Resultset.  
  
2.  Führen Sie einen [& (Bitweise AND)](/sql/t-sql/language-elements/bitwise-and-transact-sql)-Vorgang mit dem Wert aus Schritt 1 und dem gewünschten Wert für die Schemaoption aus, um festzustellen, ob die Option festgelegt ist.  
  
    -   Wenn das Ergebnis **0**ist, ist die Option nicht festgelegt.  
  
    -   Wenn das Ergebnis der Optionswert ist, ist die Option bereits festgelegt.  
  
3.  Wenn die Option nicht festgelegt ist, führen Sie einen [| (Bitweisen OR)](/sql/t-sql/language-elements/bitwise-or-transact-sql) -Vorgang mit dem Wert aus Schritt 1 und dem gewünschten Wert für die Schemaoption aus.  
  
4.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)aus. Geben Sie den Namen der Veröffentlichung, zu der der Artikel gehört, für die ** \@ Veröffentlichung**, den Namen des Artikels für den ** \@ Artikel**, den Wert **schema_option** für die- ** \@ Eigenschaft**und das hexadezimale Ergebnis aus Schritt 3 für ** \@ value**an.  
  
5.  Führen Sie den Momentaufnahme-Agent zum Generieren einer neuen Momentaufnahme aus. Weitere Informationen finden Sie unter [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von Daten und Datenbankobjekten](publish-data-and-database-objects.md)   
 [Article Options for Transactional Replication](../transactional/article-options-for-transactional-replication.md)  
  
  
