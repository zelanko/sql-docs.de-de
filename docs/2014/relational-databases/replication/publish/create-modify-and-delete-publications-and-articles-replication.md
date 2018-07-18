---
title: Erstellen, Ändern und Löschen von Veröffentlichungen und Artikeln (Replikation) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], creating
- articles [SQL Server replication], defining
ms.assetid: e66d06ec-a12b-444d-875b-77f958af2f21
caps.latest.revision: 35
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c362d75076a5d52a9696717cc866a4e7d195c5da
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197111"
---
# <a name="create-modify-and-delete-publications-and-articles-replication"></a>Erstellen, Ändern und Löschen von Veröffentlichungen und Artikeln (Replikation)
  Dieser Abschnitt der Dokumentation enthält Informationen zur Ausführung der Aufgaben, die das Erstellen von Veröffentlichungen und das Definieren von Artikeln betreffen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Create a Publication](create-a-publication.md)  
  
-   [Definieren eines Artikels](define-an-article.md)  
  
-   [Anzeigen und Ändern von Veröffentlichungseigenschaften](view-and-modify-publication-properties.md)  
  
-   [Anzeigen und Ändern von Artikeleigenschaften](view-and-modify-article-properties.md)  
  
-   [Löschen einer Veröffentlichung](delete-a-publication.md)  
  
-   [Löschen eines Artikels](delete-an-article.md)  
  
-   [Erstellen einer Veröffentlichung aus einer Oracle-Datenbank](create-a-publication-from-an-oracle-database.md)  
  
-   [Festlegen des Ablaufdatums für Abonnements](set-the-expiration-period-for-subscriptions.md)  
  
-   [Angeben von Schemaoptionen](specify-schema-options.md)  
  
-   [Replizieren von Schemaänderungen](replicate-schema-changes.md)  
  
-   [Verwalten von Identitätsspalten](manage-identity-columns.md)  
  
-   [Festlegen des Kompatibilitätsgrads von Mergeveröffentlichungen](set-the-compatibility-level-for-merge-publications.md)  
  
## <a name="snapshot-options"></a>Momentaufnahmeoptionen  
  
-   [Angeben des Momentaufnahmeformats &#40;SQL Server Management Studio&#41;](specify-snapshot-format-sql-server-management-studio.md)  
  
-   [Angeben eines alternativen Speicherortes für den Momentaufnahmeordner &#40;SQL Server Management Studio&#41;](specify-an-alternate-snapshot-folder-location-sql-server-management-studio.md)  
  
-   [Komprimieren von Momentaufnahmedateien &#40;SQL Server Management Studio&#41;](compress-snapshot-files-sql-server-management-studio.md)  
  
-   [Konfigurieren von Momentaufnahmeeigenschaften &#40;Replikationsprogrammierung mit Transact-SQL&#41;](configure-snapshot-properties-replication-transact-sql-programming.md)  
  
-   [Ausführen von Skripts vor und nach dem Anwenden einer Momentaufnahme &#40;SQL Server Management Studio&#41;](../execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   [Übermitteln einer Momentaufnahme über FTP](deliver-a-snapshot-through-ftp.md)  
  
## <a name="filtering-data"></a>Filtern von Daten  
  
-   [Definieren und Ändern eines Spaltenfilters](define-and-modify-a-column-filter.md)  
  
-   [Definieren und Ändern eines statischen Zeilenfilters](define-and-modify-a-static-row-filter.md)  
  
-   [Definieren und Ändern eines parametrisierten Zeilenfilters für einen Mergeartikel](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
-   [Optimieren von parametrisierten Zeilenfiltern](../merge/parameterized-filters-parameterized-row-filters.md)  
  
-   [Definieren und Ändern eines Verknüpfungsfilters zwischen Mergeartikeln](define-and-modify-a-join-filter-between-merge-articles.md)  
  
-   [Automatisches Generieren einer Reihe von Joinfiltern zwischen Mergeartikeln &#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md)  
  
## <a name="transactional-replication-options"></a>Transaktionsreplikationsoptionen  
  
-   [Festlegen der Propagierungsmethode für Datenänderungen an Transaktionsartikeln](set-the-propagation-method-for-data-changes-to-transactional-articles.md)  
  
-   [Aktivieren des Aktualisierens von Abonnements für Transaktionsveröffentlichungen](enable-updating-subscriptions-for-transactional-publications.md)  
  
-   [Festlegen der Konfliktlösungsoptionen für verzögerte Updates über eine Warteschlange &#40;SQL Server Management Studio&#41;](set-queued-updating-conflict-resolution-options-sql-server-management-studio.md)  
  
-   [Veröffentlichen der Ausführung einer gespeicherten Prozedur in einer Transaktionsveröffentlichung &#40;SQL Server Management Studio&#41;](publish-execution-of-stored-procedure-in-transactional-publication.md)  
  
## <a name="merge-replication-options"></a>Mergereplikationsoptionen  
  
-   [Definieren einer logischen Datensatzbeziehung zwischen Mergetabellenartikeln](define-a-logical-record-relationship-between-merge-table-articles.md)  
  
-   [Angeben der Verarbeitungsreihenfolge von Mergetabellenartikeln &#40;Replikationsprogrammierung mit Transact-SQL&#41;](specify-the-processing-order-of-merge-table-articles.md)  
  
-   [Angeben, dass ein neuer Mergetabellenartikel nur herunterladbar ist](specify-that-a-merge-table-article-is-download-only.md)  
  
-   [Angeben, dass Löschvorgänge für Mergeartikel nicht nachverfolgt werden sollen &#40;Replikationsprogrammierung mit Transact-SQL&#41;](specify-that-deletes-should-not-be-tracked-for-merge-articles.md)  
  
-   [Angeben der Konfliktnachverfolgungs- und -lösungsebene für Mergeartikel](specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md)  
  
-   [Angeben eines Mergeartikelkonfliktlösers](specify-a-merge-article-resolver.md)  
  
-   [Angeben von interaktiver Konfliktauflösung von Mergeartikeln](specify-interactive-conflict-resolution-for-merge-articles.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von Daten und Datenbankobjekten](publish-data-and-database-objects.md)  
  
  
