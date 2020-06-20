---
title: Angeben von Artikeltypen (Replikationsprogrammierung mit Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- articles [SQL Server replication], transactional replication options
- articles [SQL Server replication], merge replication options
- stored procedures [SQL Server replication], publishing
ms.assetid: d7effbac-c45b-423f-97ae-fd426b1050ba
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7864825891203530bf30015471ca22a1daccf9b9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060342"
---
# <a name="specify-article-types-replication-transact-sql-programming"></a>Angeben von Artikeltypen (Replikationsprogrammierung mit Transact-SQL)
  Die Standardartikeltypen für die Replikation sind Tabellen. Sie können aber auch andere Datenbankobjekte als Artikel veröffentlichen, einschließlich Sichten, gespeicherte Prozeduren, benutzerdefinierte Funktionen und die Ausführung von gespeicherten Prozeduren. Sie können gespeicherte Replikationsprozeduren verwenden, um einen Artikeltyp beim Definieren eines Artikels programmgesteuert anzugeben. Welche Prozeduren Sie verwenden, hängt vom Typ der Replikation und des Artikels ab.  
  
> [!NOTE]  
>  Beim Definieren von Artikeln für Tabellen, Sichten und gespeicherte Prozeduren gibt die Bezeichnung schema only an, dass nur die Objektdefinition repliziert wird.  
  
### <a name="to-publish-a-table-article-in-a-transactional-or-snapshot-publication"></a>So veröffentlichen Sie einen Tabellenartikel in einer Transaktions- oder Momentaufnahmeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus. Geben Sie einen der folgenden Werte für ** \@ Typ** an, um den Typ des Artikels zu definieren:  
  
    -   **logbased** &ndash; ein protokollbasierter Tabellenartikel, der der Standard für die Transaktions- und Momentaufnahmereplikation ist. Die Replikation generiert automatisch die gespeicherte Prozedur, die für das horizontale Filtern verwendet wird, sowie die Sicht, die einen vertikal gefilterten Artikel definiert.  
  
    -   **logbased manualfilter** : ein Protokoll basierter, horizontal gefilterter Artikel, in dem die gespeicherte Prozedur für das horizontale Filtern manuell vom Benutzer erstellt und definiert und für ** \@ Filter**angegeben wird. Weitere Informationen finden Sie unter [Definieren oder Ändern eines statischen Zeilenfilters](define-and-modify-a-static-row-filter.md).  
  
    -   **logbased manualview** : ein Protokoll basierter, vertikal gefilterter Artikel, in dem die Sicht, die den vertikal gefilterten Artikel definiert, vom Benutzer erstellt und definiert und für ** \@ sync_object**angegeben wird. Weitere Informationen finden Sie unter [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) und [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
    -   **logbased manualboth** : ein Protokoll basierter, horizontal und vertikal gefilterter Artikel, in dem sowohl die gespeicherte Prozedur für das horizontale Filtern als auch die Sicht, die den vertikal gefilterten Artikel definiert, vom Benutzer erstellt und definiert und für ** \@ Filter** bzw. ** \@ sync_object**angegeben wird. Weitere Informationen finden Sie unter [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) und [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
     Damit wird ein neuer Artikel für die Veröffentlichung definiert. Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
2.  Führen Sie für **logbased manualboth** -Artikel und **logbased manualfilter** -Artikel [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) aus, um die gespeicherte Filterprozedur für einen horizontal gefilterten Artikel zu generieren. Weitere Informationen finden Sie unter [Definieren oder Ändern eines statischen Zeilenfilters](define-and-modify-a-static-row-filter.md).  
  
3.  Führen Sie für Artikel vom Typ **logbased manualboth**, **logbased manualview**und **logbased manualfilter**[sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) aus, um die Sicht zu generieren, die den vertikal gefilterten Artikel definiert. Weitere Informationen finden Sie unter [Definieren und Ändern eines Spaltenfilters](define-and-modify-a-column-filter.md).  
  
### <a name="to-publish-a-view-or-indexed-view-article-in-a-transactional-or-snapshot-publication"></a>So veröffentlichen Sie einen Artikel für eine Sicht oder eine indizierte Sicht in einer Transaktions- oder Momentaufnahmeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus. Geben Sie einen der folgenden Werte für ** \@ Typ** an, um den Typ des Artikels zu definieren:  
  
    -   **indexed view logbased** &ndash; ein Artikel für eine protokollbasierte, indizierte Sicht. Die Replikation generiert automatisch die gespeicherte Prozedur, die für das horizontale Filtern verwendet wird, sowie die Sicht, die einen vertikal gefilterten Artikel definiert.  
  
    -   **view schema only** &ndash; ein Artikel für eine Sicht vom Typ schema only. Die Basistabelle muss ebenfalls repliziert werden.  
  
    -   **indexed view schema only** &ndash; ein Artikel für eine indizierte Sicht vom Typ schema only. Die Basistabelle muss ebenfalls repliziert werden.  
  
    -   **indizierte Sicht logbased manualfilter** -ein Protokoll basierter, horizontal gefilterter Artikel für eine indizierte Sicht, in dem die gespeicherte Prozedur für das horizontale Filtern manuell vom Benutzer erstellt und definiert und für ** \@ Filter**angegeben wird. Weitere Informationen finden Sie unter [Definieren oder Ändern eines statischen Zeilenfilters](define-and-modify-a-static-row-filter.md).  
  
    -   **indizierte Sicht logbased manualview** : ein Protokoll basierter, gefilterter Artikel für eine indizierte Sicht, in dem die Sicht, die einen vertikal gefilterten Artikel definiert, vom Benutzer erstellt und definiert und für ** \@ sync_object**angegeben wird. Weitere Informationen finden Sie unter [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) und [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
    -   **indizierte Sicht logbased manualboth** : ein Protokoll basierter, gefilterter Artikel für eine indizierte Sicht, in dem sowohl die gespeicherte Prozedur für das horizontale Filtern als auch die Sicht, die einen vertikal gefilterten Artikel definiert, vom Benutzer erstellt und definiert und für ** \@ Filter** bzw. ** \@ sync_object**angegeben wird. Weitere Informationen finden Sie unter [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md) und [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
     Damit wird ein neuer Artikel für die Veröffentlichung definiert. Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
2.  Führen Sie für **logbased manualboth** -Artikel und **logbased manualfilter** -Artikel [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) aus, um die gespeicherte Filterprozedur für einen horizontal gefilterten Artikel zu generieren. Weitere Informationen finden Sie unter [Definieren oder Ändern eines statischen Zeilenfilters](define-and-modify-a-static-row-filter.md).  
  
3.  Führen Sie für Artikel vom Typ **logbased manualboth**, **logbased manualview**und **logbased manualfilter**[sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) aus, um die Sicht zu generieren, die den vertikal gefilterten Artikel definiert. Weitere Informationen finden Sie unter [Definieren und Ändern eines Spaltenfilters](define-and-modify-a-column-filter.md).  
  
### <a name="to-publish-a-stored-procedure-stored-procedure-execution-or-user-defined-function-article-in-a-transactional-or-snapshot-publication"></a>So veröffentlichen Sie einen Artikel für eine gespeicherte Prozedur, für die Ausführung einer gespeicherten Prozedur oder für eine benutzerdefinierte Funktion in einer Transaktions- oder Momentaufnahmeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)aus. Geben Sie einen der folgenden Werte für ** \@ Typ** an, um den Typ des Artikels zu definieren:  
  
    -   **proc schema only** &ndash; ein Artikel für eine gespeicherte Prozedur vom Typ schema only.  
  
    -   **proc exec** &ndash; repliziert die Ausführung der gespeicherten Prozedur auf alle Abonnenten des Artikels. Weitere Informationen finden Sie unter [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **serializable proc exec** &ndash; repliziert die Ausführung der gespeicherten Prozedur nur, wenn die Prozedur im Kontext einer serialisierbaren Transaktion ausgeführt wird. Weitere Informationen finden Sie unter [Publishing Stored Procedure Execution in Transactional Replication](../transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
    -   **func schema only** &ndash; ein Artikel für eine benutzerdefinierte Funktion vom Typ schema only.  
  
     Damit wird ein neuer Artikel für die Veröffentlichung definiert. Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
### <a name="to-publish-a-table-or-view-article-in-a-merge-publication"></a>So veröffentlichen Sie einen Tabellen- oder Sichtartikel in einer Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)aus. Geben Sie einen der folgenden Werte für ** \@ Typ** an, um den Typ des Artikels zu definieren:  
  
    -   **table** &ndash; ein Tabellenartikel.  
  
    -   **indexed view schema only** &ndash; ein Artikel für eine indizierte Sicht vom Typ schema only.  
  
    -   **view schema only** &ndash; ein Artikel für eine Sicht vom Typ schema only.  
  
     Damit wird ein neuer Artikel für die Veröffentlichung definiert. Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
### <a name="to-publish-a-stored-procedure-or-user-defined-function-article-in-a-merge-publication"></a>So veröffentlichen Sie einen Artikel für eine gespeicherte Prozedur oder eine benutzerdefinierte Funktion in einer Mergeveröffentlichung  
  
1.  Führen Sie auf dem Verleger für die Veröffentlichungsdatenbank [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql)aus. Geben Sie einen der folgenden Werte für ** \@ Typ** an, um den Typ des Artikels zu definieren:  
  
    -   **func schema only** &ndash; ein Artikel für eine benutzerdefinierte Funktion vom Typ schema only.  
  
    -   **proc schema only** &ndash; ein Artikel für eine gespeicherte Prozedur vom Typ schema only.  
  
     Damit wird ein neuer Artikel für die Veröffentlichung definiert. Weitere Informationen finden Sie unter [Definieren eines Artikels](define-an-article.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konzepte für gespeicherte System Prozeduren von](../concepts/replication-system-stored-procedures-concepts.md)   
 [Veröffentlichen von Daten und Datenbankobjekten](publish-data-and-database-objects.md)  
  
  
