---
title: Article Options for Transactional Replication | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 992b479ea0867aef1ca75e42cc865db2cc5a735f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63268652"
---
# <a name="article-options-for-transactional-replication"></a>Artikeloptionen für die Transaktionsreplikation
  Für Artikel in Transaktionsveröffentlichungen stehen eine Reihe von Optionen zur Verfügung. Bei der Transaktionsreplikation haben Sie folgende Möglichkeiten:  
  
-   Sie können angeben, wie Änderungen vom Verleger an Abonnenten weitergegeben werden. Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](transactional-articles-specify-how-changes-are-propagated.md)  
  
-   Sie können angeben, dass die Ausführung einer gespeicherten Prozedur repliziert wird. Dies ist bei der Replikation der Ergebnisse von wartungsorientierten gespeicherten Prozeduren hilfreich, die sich möglicherweise auf große Datenmengen auswirken. Weitere Informationen finden Sie unter [Publishing Stored Procedure Execution in Transactional Replication](publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Sie können Schemaoptionen angeben, beispielsweise ob Einschränkungen und Trigger auf den Abonnenten kopiert werden. Weitere Informationen finden Sie unter [Angeben von Schemaoptionen](../publish/specify-schema-options.md).  
  
-   Sie können Zeilenfilter und Spaltenfilter verwenden. Das Filtern von Tabellenartikeln ermöglicht es Ihnen, Datenpartitionen zu erstellen, die veröffentlicht werden können. Weitere Informationen finden Sie unter [Filtern von veröffentlichten Daten](../publish/filter-published-data.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von Daten und Datenbankobjekten](../publish/publish-data-and-database-objects.md)  
  
  
