---
title: Article Options for Transactional Replication | Microsoft-Dokumentation
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
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
caps.latest.revision: 29
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 8a39b04efd82147a695c744958a29aae5f449dd2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050080"
---
# <a name="article-options-for-transactional-replication"></a>Artikeloptionen für die Transaktionsreplikation
  Für Artikel in Transaktionsveröffentlichungen stehen eine Reihe von Optionen zur Verfügung. Bei der Transaktionsreplikation haben Sie folgende Möglichkeiten:  
  
-   Sie können angeben, wie Änderungen vom Verleger an Abonnenten weitergegeben werden. Weitere Informationen finden Sie unter [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](transactional-articles-specify-how-changes-are-propagated.md)  
  
-   Sie können angeben, dass die Ausführung einer gespeicherten Prozedur repliziert wird. Dies ist bei der Replikation der Ergebnisse von wartungsorientierten gespeicherten Prozeduren hilfreich, die sich möglicherweise auf große Datenmengen auswirken. Weitere Informationen finden Sie unter [Publishing Stored Procedure Execution in Transactional Replication](publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Sie können Schemaoptionen angeben, beispielsweise ob Einschränkungen und Trigger auf den Abonnenten kopiert werden. Weitere Informationen finden Sie unter [Angeben von Schemaoptionen](../publish/specify-schema-options.md).  
  
-   Sie können Zeilenfilter und Spaltenfilter verwenden. Das Filtern von Tabellenartikeln ermöglicht es Ihnen, Datenpartitionen zu erstellen, die veröffentlicht werden können. Weitere Informationen finden Sie unter [Filtern von veröffentlichten Daten](../publish/filter-published-data.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von Daten und Datenbankobjekten](../publish/publish-data-and-database-objects.md)  
  
  