---
title: Verwalten von Identitätsspalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- identity values [SQL Server replication]
- merge replication [SQL Server replication], identity range management
- publishing [SQL Server replication], identity columns
- transactional replication, identity range management
- identity columns [SQL Server], replication
ms.assetid: 98892836-cf63-494a-bd5d-6577d9810ddf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1b9a7b28c288ef80d24fb67479727d94c3c09fa5
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060525"
---
# <a name="manage-identity-columns"></a>Verwalten von Identitätsspalten
  In diesem Thema wird beschrieben, wie Identitätsspalten in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]verwaltet werden. Wenn Einfügungen von Abonnenten zurück auf den Verleger repliziert werden, müssen Identitätsspalten verwaltet werden, um zu verhindern, dass der gleiche Identitätswert sowohl dem Abonnenten als auch dem Verleger zugewiesen wird. Die Replikation kann Identitätsbereiche automatisch verwalten, oder Sie können sich dafür entscheiden, Identitätsbereiche manuell zu verwalten.  Informationen über die von der Replikation zur Verfügung gestellten Verwaltungsoptionen für Identitätsbereiche finden Sie unter [Replizieren von Identitätsspalten](replicate-identity-columns.md).  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Empfehlungen  
  
-   Wird eine Tabelle in mehr als einer Veröffentlichung veröffentlicht, müssen Sie für diese Veröffentlichungen die gleichen Verwaltungsoptionen für Identitätsbereiche angeben. Weitere Informationen finden Sie unter „Veröffentlichen von Tabellen in mehreren Veröffentlichungen“ in [Veröffentlichen von Daten und Datenbankobjekten](publish-data-and-database-objects.md).  
  
-   Weitere Informationen zu einer automatisch inkrementierten Zahl, die in mehreren Tabellen verwendet oder aus Anwendungen aufgerufen werden kann, ohne dass auf eine Tabelle verwiesen wird, finden Sie unter [Sequenznummern](../../sequence-numbers/sequence-numbers.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Geben Sie auf der Registerkarte **Eigenschaften** des Dialog Felds **Artikeleigenschaften- \<Article> ** für den Assistenten für neue Veröffentlichung eine Verwaltungs Option für Identitäts Spalten an. Weitere Informationen zum Zugreifen auf diesen Assistenten finden Sie unter [Erstellen einer Veröffentlichung](create-a-publication.md). Führen Sie im Assistenten für neue Veröffentlichung folgende Aktionen aus:  
  
-   Wenn Sie auf der Seite **Veröffentlichungstyp** die Option **Mergeveröffentlichung** oder **Transaktionsveröffentlichung mit aktualisierbaren Abonnements** auswählen, wählen Sie die automatische oder manuelle Identitätsbereichsverwaltung aus (automatisch, die Standardeinstellung, wird empfohlen). Nach dem Veröffentlichen der Tabelle kann die Eigenschaft nicht geändert werden. Es können jedoch andere, verbundene Eigenschaften geändert werden.  
  
-   Wenn Sie andere Veröffentlichungstypen auswählen, legen Sie die manuelle Identitätsbereichsverwaltung fest.  
  
 Ändern Sie Identitäts Bereiche und Schwellenwerte auf der Registerkarte **Eigenschaften** der **Artikel \<Article> Eigenschaften**, die im Dialogfeld **Veröffentlichungs Eigenschaften- \<Publication> ** verfügbar sind. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](view-and-modify-publication-properties.md).  
  
#### <a name="to-specify-an-identity-column-management-option"></a>So geben Sie eine Verwaltungsoption für Identitätsspalten an  
  
1.  Wenn auf dem Verleger eine Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt wird, die älter als [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]ist, wählen Sie im Assistenten für neue Veröffentlichung auf der Seite **Veröffentlichungstyp** die Option **Mergeveröffentlichung** oder **Transaktionsveröffentlichung mit aktualisierbaren Abonnements**aus.  
  
2.  Wählen Sie auf der Seite **Artikel** eine Tabelle mit einer Identitätsspalte aus.  
  
3.  Klicken Sie auf **Artikeleigenschaften**und anschließend auf **Eigenschaften des hervorgehobenen Artikels festlegen**.  
  
4.  Legen Sie auf der Registerkarte **Eigenschaften** des Dialog Felds **Artikel \<Article> Eigenschaften-** im Abschnitt **Identitäts Bereichs Verwaltung** die Eigenschaft **Identitäts Bereiche automatisch verwalten** auf **automatisch** oder **manuell** (bei Verlegern, auf denen oder höher ausgeführt [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] wird) oder auf **true** oder **false** fest (bei Verlegern, auf denen eine Version von vor ausgeführt wird [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ).  
  
5.  Wenn Sie in Schritt 4 **Automatisch** oder **Wahr** ausgewählt haben, geben Sie Werte für die Optionen der folgenden Tabelle ein. Weitere Informationen zum Verwenden dieser Einstellungen finden Sie im Abschnitt „Zuweisen von Identitätsbereichen“ unter [Replizieren von Identitätsspalten](replicate-identity-columns.md).  
  
    |Option|Wert|BESCHREIBUNG|  
    |------------|-----------|-----------------|  
    |**Bereichsgröße auf dem Verleger**|Ganze Zahl für die Bereichsgröße (z. B. 20000).|Weitere Informationen finden Sie im Abschnitt „Zuweisen von Identitätsbereichen“ von [Replizieren von Identitätsspalten](replicate-identity-columns.md).|  
    |**Bereichsgröße auf dem Abonnenten**|Ganze Zahl für die Bereichsgröße (z. B. 10000).|Weitere Informationen finden Sie im Abschnitt „Zuweisen von Identitätsbereichen“ von [Replizieren von Identitätsspalten](replicate-identity-columns.md).|  
    |**Prozentsatz für Bereichsschwellenwert**|Ganze Zahl für Schwellenwert in Prozent (z. B. 90 entspricht 90 %)|Der Prozentsatz der Identitätswerte, die in einem Knoten insgesamt verwendet werden, bevor ein neuer Identitätsbereich zugewiesen wird.<br /><br /> Hinweis: Der Wert muss angeben werden, er wird jedoch nur von Abonnenten verwendet, die Abonnements mit verzögertem Update über eine Warteschlange verwenden, und von Abonnenten für Mergeveröffentlichungen, auf denen [!INCLUDE[ssEW](../../../includes/ssew-md.md)] oder frühere Versionen von anderen SQL Server-Editionen ausgeführt werden. Weitere Informationen finden Sie im Abschnitt „Zuweisen von Identitätsbereichen“ in [Replizieren von Identitätsspalten](replicate-identity-columns.md).|  
    |**Anfangswert des nächsten Bereichs**|Wert für ganze Zahl. Schreibgeschützt.|Der Wert, bei dem der nächste Bereich beginnt. Wenn der aktuelle Bereich z. B. 5001-6000 lautet, liegt dieser Wert bei 6001.|  
    |**Maximaler Identitätswert**|Wert für ganze Zahl. Schreibgeschützt.|Der größte Wert für die Identitätsspalte. Er wird durch den Basisdatentyp der Spalte bestimmt.|  
    |**Inkrement**|Wert für ganze Zahl. Schreibgeschützt.|Die Zahl, um die sich eine Identitätsspalte bei jeder Einfügung erhöhen oder verringern sollte: in der Regel auf 1 festgelegt.|  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-modify-identity-ranges-and-thresholds-after-a-table-is-published"></a>So ändern Sie Identitätsbereiche und Schwellenwerte nach dem Veröffentlichen einer Tabelle  
  
1.  Wählen Sie im Dialogfeld **Veröffentlichungs Eigenschaften- \<Publication> ** auf der Seite **Artikel** eine Tabelle mit einer Identitäts Spalte aus.  
  
2.  Klicken Sie auf **Artikeleigenschaften**und anschließend auf **Eigenschaften des hervorgehobenen Artikels festlegen**.  
  
3.  Geben Sie auf der Registerkarte **Eigenschaften** des Dialog Felds **Artikeleigenschaften- \<Article> ** im Abschnitt **Identitäts Bereichs Verwaltung** Werte für eine oder mehrere der folgenden Eigenschaften ein: **Bereichs Größe des Herausgebers**, **Größe des Abonnenten Bereichs**und **Prozentsatz für Bereichs Schwellenwert**.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Klicken Sie im Dialogfeld **Veröffentlichungs Eigenschaften \<Publication> -** auf **OK** .  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Wenn ein Artikel erstellt wird, können Sie mithilfe gespeicherter Replikationsprozeduren Verwaltungsoptionen für Identitätsbereiche angeben.  
  
#### <a name="to-enable-automatic-identity-range-management-when-defining-articles-for-a-transactional-publication"></a>So aktivieren Sie die automatische Identitätsbereichsverwaltung beim Definieren von Artikeln für eine Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus. Wenn die zu veröffentlichende Quell Tabelle eine Identitäts Spalte aufweist, geben Sie den Wert **Auto** für ** \@ identityrangemanagementoption**, den dem Verleger zugewiesenen Bereich von Identitäts Werten für ** \@ pub_identity_range**, den Bereich der Identitäts Werte, die den einzelnen Abonnenten für ** \@ identity_range**zugewiesen sind, und den Prozentsatz der gesamten Identitäts Werte an, die verwendet werden, bevor ein neuer Identitäts Bereich für den ** \@ Schwellenwert**zugewiesen wird. Weitere Informationen zum Definieren von Artikeln finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
    > [!NOTE]  
    >  Vergewissern Sie sich, dass der Datentyp der Identitätsspalte groß genug ist, um den gesamten, allen Abonnenten zugewiesenen Identitätsbereich zu unterstützen.  
  
#### <a name="to-disable-automatic-identity-range-management-when-defining-articles-for-a-transactional-publication"></a>So deaktivieren Sie die automatische Identitätsbereichsverwaltung beim Definieren von Artikeln für eine Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus. Geben Sie den Wert **Manual** für ** \@ identityrangemanagementoption**an. Weitere Informationen zum Definieren von Artikeln finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
2.  Weisen Sie auf dem Abonnenten Identitätsartikelspalten Bereiche zu, um zu verhindern, dass für Updateabonnenten Konflikte auftreten. Weitere Informationen finden Sie im Abschnitt zum Zuweisen von Bereichen bei der manuellen Verwaltung von Identitätsbereichen im Thema [Replizieren von Identitätsspalten](replicate-identity-columns.md).  
  
#### <a name="to-enable-automatic-identity-range-management-when-defining-articles-for-a-merge-publication"></a>So aktivieren Sie die automatische Identitätsbereichsverwaltung beim Definieren von Artikeln für eine Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)aus. Wenn die zu veröffentlichende Quell Tabelle eine Identitäts Spalte aufweist, geben Sie den Wert **Auto** für ** \@ identityrangemanagementoption**, den Bereich der Identitäts Werte, der einem Server Abonnement für ** \@ pub_identity_range**zugewiesen ist, den Bereich der Identitäts Werte, die dem Verleger und jedem Client Abonnement für ** \@ identity_range**zugewiesen sind, und den Prozentsatz der gesamten Identitäts Werte an, die verwendet werden, bevor ein neuer Identitäts ** \@ Bereich für** Weitere Informationen dazu, wann neue Identitätsbereiche zugewiesen werden, finden Sie im Abschnitt zum Zuweisen von Identitätsbereichen im Thema [Replizieren von Identitätsspalten](replicate-identity-columns.md). Weitere Informationen zum Definieren von Artikeln finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
    > [!NOTE]  
    >  Vergewissern Sie sich, dass der Datentyp der Identitätsspalte groß genug ist, um den gesamten, allen Abonnenten zugewiesenen Identitätsbereich zu unterstützen. Dies gilt besonders bei Abonnenten mit Serverabonnements.  
  
#### <a name="to-disable-automatic-identity-range-management-when-defining-articles-for-a-merge-publication"></a>So deaktivieren Sie die automatische Identitätsbereichsverwaltung beim Definieren von Artikeln für eine Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)aus. Geben Sie einen der folgenden Werte für die ** \@ identityrangemanagementoption**an:  
  
    -   **manual** &ndash; Identitätsbereiche müssen manuell für Updateabonnenten zugewiesen werden.  
  
    -   **none** &ndash; Identitätsspalten auf dem Verleger werden auf dem Abonnenten nicht als Identitätsspalten definiert.  
  
     Weitere Informationen zum Definieren von Artikeln finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
2.  Weisen Sie auf dem Abonnenten Identitätsartikelspalten Bereiche zu, um zu verhindern, dass für Updateabonnenten Konflikte auftreten.  
  
#### <a name="to-change-automatic-identity-range-management-settings-for-an-existing-article-in-a-snapshot-or-transactional-publication"></a>So ändern Sie die Einstellungen für die automatische Identitätsbereichsverwaltung für einen vorhandenen Artikel in einer Momentaufnahme- oder Transaktionsveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql) aus, und achten Sie auf den Wert von **identityrangemanagementoption** im Resultset. Ist dieser Wert **0**, ist die automatische Identitätsbereichsverwaltung nicht aktiviert.  
  
2.  Wenn der Wert von **identityrangemanagementoption** im Resultset **1**ist, ändern Sie die Einstellungen wie folgt:  
  
    -   Um die zugewiesenen Identitätsbereiche zu ändern, führen Sie [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie den Wert **identity_range** oder **pub_identity_range** für die ** \@ Eigenschaft** und den neuen Bereichs Wert für ** \@ Wert**an.  
  
    -   Um den Schwellenwert zu ändern, bei dessen Überschreiten neue Identitätsbereiche zugewiesen werden, führen Sie [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie den Wert **Schwellen** Wert für die ** \@ Eigenschaft** und den neuen Schwellenwert für ** \@ Wert**an.  
  
#### <a name="to-change-automatic-identity-range-management-settings-for-an-existing-article-in-a-merge-publication"></a>So ändern Sie die Einstellungen für die automatische Identitätsbereichsverwaltung für einen vorhandenen Artikel in einer Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql) aus, und achten Sie auf den Wert von **identity_support** im Resultset. Ist dieser Wert **0**, ist die automatische Identitätsbereichsverwaltung nicht aktiviert.  
  
2.  Wenn der Wert von **identity_support** im Resultset **1**ist, ändern Sie die Einstellungen wie folgt:  
  
    -   Um die zugewiesenen Identitätsbereiche zu ändern, führen Sie [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie den Wert **identity_range** oder **pub_identity_range** für die ** \@ Eigenschaft** und den neuen Bereichs Wert für ** \@ Wert**an.  
  
    -   Um den Schwellenwert zu ändern, bei dessen Überschreiten neue Identitätsbereiche zugewiesen werden, führen Sie [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie den Wert **Schwellen** Wert für die ** \@ Eigenschaft** und den neuen Schwellenwert für ** \@ Wert**an. Weitere Informationen dazu, wann neue Identitätsbereiche zugewiesen werden, finden Sie im Abschnitt zum Zuweisen von Identitätsbereichen im Thema [Replizieren von Identitätsspalten](replicate-identity-columns.md).  
  
    -   Um die automatische Verwaltung von Identitätsbereichen zu deaktivieren, führen Sie [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) auf dem Verleger für die Veröffentlichungsdatenbank aus. Geben Sie den Wert **identityrangemanagementoption** für die ** \@ Eigenschaft** und entweder **manuell** oder **None** für ** \@ value**an.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Peer-zu-Peer-Transaktions Replikation](../transactional/peer-to-peer-transactional-replication.md)   
 [Konzepte für gespeicherte System Prozeduren von](../concepts/replication-system-stored-procedures-concepts.md)   
 [Replizieren von Identitäts Spalten](replicate-identity-columns.md)  
  
  
