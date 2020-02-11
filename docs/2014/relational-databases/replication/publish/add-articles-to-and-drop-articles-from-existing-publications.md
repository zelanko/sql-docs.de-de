---
title: Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], dropping
- deleting articles
- removing articles
- dropping articles
- adding articles
- administering replication, articles
- publications [SQL Server replication], adding and dropping articles
- articles [SQL Server replication], adding
ms.assetid: b148e907-e1f2-483b-bdb2-59ea596efceb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 523891f2f0005c7f6e6752e5d16d3680f680fdfa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73882337"
---
# <a name="add-articles-to-and-drop-articles-from-existing-publications"></a>Hinzufügen und Löschen von Artikeln aus vorhandenen Veröffentlichungen
  Nachdem eine Veröffentlichung erstellt wurde, können ihr Artikel hinzugefügt oder Artikel aus der Veröffentlichung gelöscht werden. Während das Hinzufügen von Artikeln jederzeit erfolgen kann, hängen die Schritte zum Löschen von Artikeln vom jeweiligen Replikationstyp und dem Zeitpunkt ab, zu dem der Artikel gelöscht wird.  
  
## <a name="adding-articles"></a>Hinzufügen von Artikeln  
 Hinzufügen eines Artikels beinhaltet Folgendes: Hinzufügen des Artikels zur Veröffentlichung; Erstellen einer neuen Momentaufnahme für die Veröffentlichung und Synchronisieren des Abonnements zum Zuweisen des Schemas und der Daten für den neuen Artikel.  
  
> [!NOTE]
>  Wenn Sie einer Mergeveröffentlichung einen Artikel hinzufügen und ein vorhandener Artikel von diesem neuen Artikel abhängt, müssen Sie mithilfe des ** \@processing_order** -Parameters von [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) und [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql)eine Verarbeitungsreihenfolge für beide Artikel angeben. Angenommen, Sie veröffentlichen eine Tabelle, aber Sie veröffentlichen keine Funktion, die auf die Tabelle verweist. Wenn Sie die Funktion nicht veröffentlichen, kann die Tabelle nicht auf dem Abonnenten erstellt werden. Wenn Sie die Funktion einer Veröffentlichung hinzufügen, geben Sie einen Wert von **1** für den **\@processing_order**-Parameter von **sp_addmergearticle**, und geben Sie einen Wert von **2** für den **\@processing_order**-Parameter von **sp_changemergearticle** an. Geben Sie dann den Tabellennamen für den **\@article**-Parameter an. Durch diese Verarbeitungsreihenfolge wird sichergestellt, dass Sie die Funktion auf dem Abonnenten vor der Tabelle erstellen, die davon abhängt. Sie können unterschiedliche Nummern für die einzelnen Artikel verwenden, dabei muss jedoch die Nummer für die Funktion kleiner als die Nummer der Tabelle sein.  
  
1.  Zum Hinzufügen einzelner oder mehrerer Artikel stehen die folgenden Methoden zur Verfügung:  
  
    -   [Hinzufügen und Löschen von Artikeln aus einer Veröffentlichung &#40;SQL Server Management Studio&#41;](add-articles-to-and-drop-articles-from-a-publication.md)  
  
    -   [Definieren eines Artikels](define-an-article.md)  
  
2.  Nachdem Sie einer Veröffentlichung einen Artikel hinzugefügt haben, müssen Sie eine neue Momentaufnahme für die Veröffentlichung (sowie – bei Mergeveröffentlichungen mit parametrisierten Filtern – für alle Partitionen) erstellen. Der Verteilungs-Agent oder der Merge-Agent kopiert dann das Schema und die Daten für den neuen Artikel auf den Abonnenten (ohne dabei die gesamte Veröffentlichung neu zu initialisieren).  
  
    -   Informationen zum Erstellen einer Momentaufnahme finden Sie unter [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
    -   Informationen zum Erstellen einer neuen Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern finden Sie unter [Erstellen einer Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
3.  Synchronisieren Sie nach Abschluss der Momentaufnahmeerstellung das Abonnement, um das Schema und die Daten für den neuen Artikel zu kopieren.  
  
    -   Informationen zum Synchronisieren eines Pushabonnements finden Sie unter [Synchronize a Push Subscription](../synchronize-a-push-subscription.md).  
  
    -   Informationen zum Synchronisieren eines Pullabonnements finden Sie unter [Synchronize a Pull Subscription](../synchronize-a-pull-subscription.md).  
  
## <a name="dropping-articles"></a>Löschung von Artikeln  
 Artikel können jederzeit aus einer Veröffentlichung gelöscht werden, wobei jedoch Folgendes zu beachten ist:  
  
-   Durch das Löschen eines Artikels aus einer Veröffentlichung wird weder das Objekt aus der Veröffentlichungsdatenbank noch das zugehörige Objekt aus der Abonnementdatenbank entfernt. Verwenden Sie DROP \<Objekt>, um diese Objekte ggf. zu entfernen. Wenn Sie einen Artikel löschen möchten, der über Fremdschlüsseleinschränkungen mit anderen veröffentlichten Artikeln verknüpft ist, sollten Sie die Tabelle auf dem Abonnenten manuell oder mithilfe einer bedarfsgesteuerten Skriptausführung löschen. Geben Sie ein Skript an, dass die entsprechenden DROP \<Objekt>-Anweisungen enthält. Weitere Informationen finden Sie unter [Ausführen von Skripts während der Synchronisierung &#40;Replikationsprogrammierung mit Transact-SQL&#41;](../execute-scripts-during-synchronization-replication-transact-sql-programming.md).  
  
-   Bei Mergeveröffentlichungen mit einem Kompatibilitätsgrad von 90RTM oder höher können Artikel jederzeit gelöscht werden. Es ist jedoch eine neue Momentaufnahme erforderlich. Außerdem zu beachten:  
  
    -   Wenn der Artikel ein übergeordneter Artikel in einer Joinfilter- oder logischen Datensatzbeziehung ist, müssen zunächst die Beziehungen gelöscht werden, was eine erneute Initialisierung erforderlich macht.  
  
    -   Wenn der Artikel den letzten parametrisierten Filter in einer Veröffentlichung hat, müssen die Abonnements erneut initialisiert werden.  
  
-   Bei Mergeveröffentlichungen mit einem Kompatibilitätsgrad von unter 90RTM können Artikel ohne weiteres gelöscht werden, solange die Abonnements noch nicht zum ersten Mal synchronisiert wurden. Wird ein Artikel nach der Synchronisierung von Abonnements gelöscht, müssen die Abonnements gelöscht, neu erstellt und dann synchronisiert werden.  
  
-   Bei Momentaufnahme- oder Transaktionsveröffentlichungen können Artikel ohne weiteres gelöscht werden, solange noch keine Abonnements erstellt wurden. Wird ein Artikel nach der Erstellung von Abonnements gelöscht, müssen die Abonnements gelöscht, neu erstellt und dann synchronisiert werden. Weitere Informationen zum Löschen von Abonnements finden Sie unter [Abonnieren von Veröffentlichungen](../subscribe-to-publications.md) und [sp_dropsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql). **sp_dropsubscription** ermöglicht es Ihnen, einen einzelnen Artikel aus dem Abonnement anstelle des gesamten Abonnements zu löschen.  
  
1.  Das Löschen eines Artikels aus einer Veröffentlichung umfasst das eigentliche Löschen des Artikels und das Erstellen einer neuen Momentaufnahme für die Veröffentlichung. Durch das Löschen eines Artikels wird die aktuelle Momentaufnahme ungültig, sodass eine neue Momentaufnahme erstellt werden muss.  
  
    -   Informationen zum Löschen eines Artikels aus einer Veröffentlichung finden Sie unter [Hinzufügen und Löschen von Artikeln aus einer Veröffentlichung &#40;SQL Server Management Studio&#41;](add-articles-to-and-drop-articles-from-a-publication.md) oder [Löschen eines Artikels](delete-an-article.md).  
  
2.  Nachdem Sie einen Artikel aus einer Veröffentlichung gelöscht haben, müssen Sie eine neue Momentaufnahme für die Veröffentlichung (sowie – bei Mergeveröffentlichungen mit parametrisierten Filtern – für alle Partitionen) erstellen.  
  
    -   Informationen zum Erstellen einer Momentaufnahme finden Sie unter [Create and Apply the Initial Snapshot](../create-and-apply-the-initial-snapshot.md).  
  
    -   Informationen zum Erstellen einer neuen Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern finden Sie unter [Erstellen einer Momentaufnahme für eine Mergeveröffentlichung mit parametrisierten Filtern](../create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 Wie oben bereits erwähnt, müssen die Abonnements in einigen Fällen nach dem Löschen eines Artikels gelöscht und dann neu erstellt sowie synchronisiert werden. Weitere Informationen finden Sie unter [Abonnieren von Veröffentlichungen](../subscribe-to-publications.md) und [Synchronisieren von Daten](../synchronize-data.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Veröffentlichen von Daten und Datenbankobjekten](publish-data-and-database-objects.md)   
 [Abonnements erneut initialisieren](../reinitialize-subscriptions.md)   
 [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](make-schema-changes-on-publication-databases.md)  
  
  
