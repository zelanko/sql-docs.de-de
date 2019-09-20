---
title: Definieren und Ändern eines Spaltenfilters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server replication], column
- modifying filters, column
- modifying filters
- column filters [SQL Server replication]
ms.assetid: d7c3186a-9a8c-45d8-ab34-05beec4c26dd
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 761c6b6bd1c92e7dd22cc231e46417b4b971a614
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70846601"
---
# <a name="define-and-modify-a-column-filter"></a>Definieren und Ändern eines Spaltenfilters
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)]Spaltenfilter definiert und geändert werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
-   **So definieren und ändern Sie einen Spaltenfilter mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a> Einschränkungen  
  
-   Einige Spalten können nicht gefiltert werden. Weitere Informationen dazu finden Sie unter [Filtern von veröffentlichten Daten](../../../relational-databases/replication/publish/filter-published-data.md). Wenn Sie einen Spaltenfilter ändern, nachdem Abonnements initialisiert wurden, müssen Sie eine neue Momentaufnahme generieren. Außerdem müssen nach der Änderung alle Abonnements erneut initialisiert werden. Weitere Informationen zum Ändern von Eigenschaften finden Sie unter [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 Spaltenfilter werden auf der Seite **Artikel** des Assistenten für neue Veröffentlichung definiert. Weitere Informationen zum Verwenden des Assistenten für neue Veröffentlichung finden Sie unter [Erstellen einer Veröffentlichung](../../../relational-databases/replication/publish/create-a-publication.md).  
  
 Zum Definieren und Ändern der Spaltenfilter steht die Seite **Artikel** des Dialogfelds **Veröffentlichungseigenschaften – \<Veröffentlichung>** zur Verfügung. Weitere Informationen zu Veröffentlichungs- und Artikeleigenschaften finden Sie unter [Anzeigen und Ändern von Veröffentlichungseigenschaften](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### <a name="to-define-a-column-filter"></a>So definieren Sie einen Spaltenfilter  
  
1.  Erweitern Sie im Bereich **Zu veröffentlichende Objekte** auf der Seite **Artikel** des Assistenten für neue Veröffentlichung die zu filternde Tabelle.  
  
2.  Klicken Sie auf die Kontrollkästchen für alle Spalten, die herausgefiltert werden sollen, um deren Markierung aufzuheben.  
  
#### <a name="to-modify-column-filtering"></a>So ändern Sie die Spaltenfilterung  
  
1.  Erweitern Sie im Bereich **Zu veröffentlichende Objekte** auf der Seite **Artikel** des Dialogfelds **Veröffentlichungseigenschaften – \<Veröffentlichung>** die zu filternde Tabelle.  
  
2.  Klicken Sie auf die Kontrollkästchen für alle Spalten, die herausgefiltert werden sollen, um deren Markierung aufzuheben, und stellen Sie sicher, dass die Kontrollkästchen für die Spalten, die im Artikel enthalten sein sollen, markiert sind.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 Während der Erstellung von Tabellenartikeln können Sie definieren, welche Spalten in den Artikel aufgenommen werden sollen. Nachdem der Artikel definiert wurde, können Sie die Spalten noch ändern. Gefilterte Spalten können mithilfe gespeicherter Replikationsprozeduren programmgesteuert definiert und geändert werden.  
  
> [!NOTE]  
>  Im Folgenden wird davon ausgegangen, dass sich die zugrunde liegende Tabelle nicht geändert hat. Informationen zur Replikation von DDL-Änderungen (Data Definition Language, Datendefinitionssprache) an veröffentlichten Tabellen finden Sie unter [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-snapshot-or-transactional-publication"></a>So definieren Sie einen Spaltenfilter für einen in einer Momentaufnahme- oder einer Transaktionsveröffentlichung veröffentlichten Artikel  
  
1.  Definieren Sie den zu filternden Artikel. Weitere Informationen finden Sie unter [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)aus. Damit werden die Spalten definiert, die in den Artikel aufgenommen oder daraus entfernt werden sollen.  
  
    -   Wenn nur einige wenige Spalten aus einer viele Spalten umfassenden Tabelle veröffentlicht werden sollen, führen Sie [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) einmal für jede hinzuzufügende Spalte aus. Geben Sie für **\@column** den Spaltennamen und für **\@operation** den Wert **add** an.  
  
    -   Wenn die meisten Spalten einer umfangreichen Tabelle veröffentlicht werden sollen, führen Sie [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) unter Angabe des Werts **null** für **\@column** und des Werts **add** für **\@operation** aus, um alle Spalten hinzuzufügen. Führen Sie dann für jede auszuschließende Spalte einmal [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) aus. Geben Sie dabei für **\@operation** den Wert **drop** und für **\@column** den Namen der auszuschließenden Spalte an.  
  
3.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)aus. Geben Sie für **\@publication** den Namen der Veröffentlichung und für **\@article** den Namen des gefilterten Artikels an. Damit werden die Synchronisierungsobjekte für den gefilterten Artikel erstellt.  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a>So ändern Sie einen Spaltenfilter, um zusätzliche Spalten in einen Artikel aufzunehmen, der in einer Momentaufnahme- oder Transaktionsveröffentlichung veröffentlicht wurde  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) einmal für jede zu hinzuzufügende Spalte aus. Geben Sie für **\@column** den Spaltennamen und für **\@operation** den Wert **add** an.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)aus. Geben Sie für **\@publication** den Namen der Veröffentlichung und für **\@article** den Namen des gefilterten Artikels an. Wenn für die Veröffentlichung Abonnements vorhanden sind, geben Sie für **\@change_active** den Wert **1** an. Damit werden die Synchronisierungsobjekte für den gefilterten Artikel erneut erstellt.  
  
3.  Führen Sie den Auftrag des Momentaufnahme-Agents für die Veröffentlichung erneut aus, um eine aktualisierte Momentaufnahme zu erstellen.  
  
4.  Erneutes Initialisieren von Abonnements Weitere Informationen finden Sie unter [Erneutes Initialisieren von Abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-snapshot-or-transactional-publication"></a>So ändern Sie einen Spaltenfilter, um Spalten aus einem Artikel zu entfernen, der in einer Momentaufnahme- oder Transaktionsveröffentlichung veröffentlicht wurde  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) einmal für jede zu entfernende Spalte aus. Geben Sie für **\@column** den Spaltennamen und für **\@operation** den Wert **drop** an.  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)aus. Geben Sie für **\@publication** den Namen der Veröffentlichung und für **\@article** den Namen des gefilterten Artikels an. Wenn für die Veröffentlichung Abonnements vorhanden sind, geben Sie für **\@change_active** den Wert **1** an. Damit werden die Synchronisierungsobjekte für den gefilterten Artikel erneut erstellt.  
  
3.  Führen Sie den Auftrag des Momentaufnahme-Agents für die Veröffentlichung erneut aus, um eine aktualisierte Momentaufnahme zu erstellen.  
  
4.  Erneutes Initialisieren von Abonnements Weitere Informationen finden Sie unter [Erneutes Initialisieren von Abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### <a name="to-define-a-column-filter-for-an-article-published-in-a-merge-publication"></a>So definieren Sie einen Spaltenfilter für einen Artikel, der in einer Mergeveröffentlichung veröffentlicht wurde  
  
1.  Definieren Sie den zu filternden Artikel. Weitere Informationen finden Sie unter [Definieren eines Artikels](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md)aus. Damit werden die Spalten definiert, die in den Artikel aufgenommen oder daraus entfernt werden sollen.  
  
    -   Wenn nur einige wenige Spalten aus einer viele Spalten umfassenden Tabelle veröffentlicht werden sollen, führen Sie [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) einmal für jede hinzuzufügende Spalte aus. Geben Sie für **\@column** den Spaltennamen und für **\@operation** den Wert **add** an.  
  
    -   Wenn die meisten Spalten einer umfangreichen Tabelle veröffentlicht werden sollen, führen Sie [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) unter Angabe des Werts **null** für **\@column** und des Werts **add** für **\@operation** aus, um alle Spalten hinzuzufügen. Führen Sie dann für jede auszuschließende Spalten einmal [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) aus. Geben Sie dabei für **\@operation** den Wert **drop** und für **\@column** den Namen der auszuschließenden Spalte an.  
  
#### <a name="to-change-a-column-filter-to-include-additional-columns-for-an-article-published-in-a-merge-publication"></a>So ändern Sie einen Spaltenfilter, um zusätzliche Spalten in einen Artikel aufzunehmen, der in einer Mergeveröffentlichung veröffentlicht wurde  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) einmal für jede zu hinzuzufügende Spalte aus. Geben Sie für **\@column** den Spaltennamen, für **\@operation** den Wert **add** und sowohl für **\@force_invalidate_snapshot** als auch für **\@force_reinit_subscription** den Wert **1** an.  
  
2.  Führen Sie den Auftrag des Momentaufnahme-Agents für die Veröffentlichung erneut aus, um eine aktualisierte Momentaufnahme zu erstellen.  
  
3.  Erneutes Initialisieren von Abonnements Weitere Informationen finden Sie unter [Erneutes Initialisieren von Abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### <a name="to-change-a-column-filter-to-remove-columns-for-an-article-published-in-a-merge-publication"></a>So ändern Sie einen Spaltenfilter, um Spalten aus einem Artikel zu entfernen, der in einer Mergeveröffentlichung veröffentlicht wurde  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) einmal für jede zu entfernende Spalte aus. Geben Sie für **\@column** den Spaltennamen, für **\@operation** den Wert **drop** und sowohl für **\@force_invalidate_snapshot** als auch für **\@force_reinit_subscription** den Wert **1** an.  
  
2.  Führen Sie den Auftrag des Momentaufnahme-Agents für die Veröffentlichung erneut aus, um eine aktualisierte Momentaufnahme zu erstellen.  
  
3.  Erneutes Initialisieren von Abonnements Weitere Informationen finden Sie unter [Erneutes Initialisieren von Abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
###  <a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 In diesem Beispiel für Transaktionsreplikation wird die Spalte `DaysToManufacture` aus einem Artikel entfernt, der auf der Tabelle `Product` basiert.  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-colu_1.sql)]  
  
 In diesem Beispiel für eine Mergereplikation wird die Spalte `CreditCardApprovalCode` aus einem Artikel entfernt, der auf der Tabelle `SalesOrderHeader` basiert.  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-colu_2.sql)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Filtern von veröffentlichten Daten](../../../relational-databases/replication/publish/filter-published-data.md)   
 [Filtern veröffentlichter Daten für die Mergereplikation](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)  
  
  
