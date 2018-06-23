---
title: Veröffentlichungen mit Oracle (Übersicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- publishing [SQL Server replication], Oracle publishing
- snapshot replication [SQL Server], Oracle publishing
- Oracle publishing [SQL Server replication]
- transactional replication, Oracle publishing
- Oracle publishing [SQL Server replication], about Oracle publishing
ms.assetid: 2e013259-0022-4897-a08d-5f8deb880fa8
caps.latest.revision: 39
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 595547640aa5fb2647208cf092448d691ea92027
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160188"
---
# <a name="oracle-publishing-overview"></a>Oracle Publishing Overview
  Mit [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]können Sie Oracle-Verleger in Ihre Replikationstopologie einbinden (ab Oracle Version 9i). Verlegerserver können auf einem beliebigen von Oracle unterstützten Hardware- und Betriebssystem bereitgestellt werden. Die Funktion basiert auf der viel benutzten Momentaufnahme- und Transaktionsreplikation von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und bietet eine ähnliche Leistung und Benutzerfreundlichkeit.  
  
 Das Veröffentlichen mit Oracle ist veraltet. Die heterogene Replikation an Nicht-SQL Server-Abonnenten ist veraltet. Um Daten zu verschieben, erstellen Sie Lösungen mit Change Data Capture und [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="snapshot-replication-for-oracle"></a>Momentaufnahmereplikation für Oracle  
 Oracle-Momentaufnahmeveröffentlichungen werden auf ähnliche Weise implementiert wie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Momentaufnahmeveröffentlichungen. Wenn der Momentaufnahme-Agent für eine Oracle-Veröffentlichung ausgeführt wird, stellt er eine Verbindung mit dem Oracle-Verleger her und verarbeitet die einzelnen Tabellen in der Veröffentlichung. Bei der Verarbeitung der einzelnen Tabellen ruft der Agent die Tabellenzeilen ab und erstellt Schemaskripts, die dann in der Momentaufnahmefreigabe der Veröffentlichung gespeichert werden. Der gesamte Datensatz wird jedes Mal erstellt, wenn der Momentaufnahme-Agent ausgeführt wird. Demzufolge werden den Oracle-Tabellen keine Änderungsprotokollierungstrigger hinzugefügt (wie es bei der Transaktionsreplikation der Fall ist). Die Momentaufnahmereplikation stellt eine praktische Möglichkeit zur Datenmigration dar, bei der das Verlegersystem nur minimal beeinträchtigt wird.  
  
## <a name="transactional-replication-for-oracle"></a>Transaktionsreplikation für Oracle  
 Transaktionsreplikationen bei Oracle werden mithilfe der Architektur für die Transaktionsveröffentlichung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]implementiert. Änderungen werden jedoch über eine Kombination aus Datenbanktriggern auf der Oracle-Datenbank und Protokolllese-Agents verfolgt. Abonnenten einer Oracle-Transaktionsveröffentlichung werden automatisch mithilfe der Momentaufnahmereplikation initialisiert. Nachfolgende Änderungen werden protokolliert und über den Protokolllese-Agent an die Abonnenten geliefert.  
  
 Wenn eine Oracle-Veröffentlichung erstellt wird, werden Trigger und Nachverfolgungstabellen für jede veröffentlichte Tabelle innerhalb der Oracle-Datenbank erstellt. Wenn Datenänderungen an den veröffentlichten Tabellen vorgenommen wurden, werden die Datenbanktrigger in den Tabellen ausgelöst und Informationen in die Replikations-Nachverfolgungstabelle für jede geänderte Zeile eingefügt. Der Protokolllese-Agent auf dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verleger verschiebt anschließend die Informationen bezüglich der Datenänderungen von den Nachverfolgungstabellen in die Verteilungsdatenbank auf dem Verleger. Schließlich verschiebt der Verteilungs-Agent, wie bei der standardmäßigen Transaktionsreplikation, Änderungen vom Verleger auf die Abonnenten.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren eines Oracle-Verlegers](configure-an-oracle-publisher.md)   
 [Begriffe im Zusammenhang mit dem Veröffentlichen von Oracle-Daten](glossary-of-terms-for-oracle-publishing.md)   
 [Heterogene Datenbankreplikation](heterogeneous-database-replication.md)  
  
  