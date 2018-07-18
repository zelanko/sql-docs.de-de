---
title: Volltext-Stopplisten-Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplistproperties.general.f1
- sql12.swb.fulltextsearch.ftstoplistproperties.schedule.f1
ms.assetid: 2e907f5b-0cf9-484a-afcf-a4e7f1e2f87f
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 3802396c3b2ff6d64aa439af07e7dba2f9b30c60
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37241290"
---
# <a name="full-text-stoplist-properties"></a>Volltext-Stopplisten-Eigenschaften
  Verwenden Sie dieses Dialogfeld, um einzelne Stoppwörter hinzuzufügen oder zu löschen, um alle Stoppwörter für eine bestimmte Sprache zu löschen oder um die aktuelle Stoppliste zu löschen. Ein Stoppwort ist ein häufig verwendetes Wort, das in eine Stoppliste aufgenommen wird. Die Stoppwörter in einer Stoppliste werden bei der Volltextindizierung für Tabellen, die diese Stoppliste verwenden, ausgelassen. Weitere Informationen finden sie unter [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](../relational-databases/search/full-text-search.md).  
  
 **SQL Server Management Studio verwenden, um Stopplisten-Eigenschaften zu ändern.**  
  
-   [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a>Tastatur  
 **Aktion**  
 Gibt die Aktion an, die Sie durchführen möchten.  
  
 **Stoppwort hinzufügen**  
 Fügt der Stoppliste ein häufig verwendetes Wort hinzu.  
  
 **Stoppwort löschen**  
 Löscht ein Stoppwort aus der Stoppliste.  
  
 **Alle Stoppwörter löschen**  
 Löscht alle Stoppwörter für eine bestimmte Sprache.  
  
 **Inhalt der Stoppliste löschen**  
 Löscht die Stoppliste, indem alle Stoppwörter für alle Sprachen gelöscht werden.  
  
 **Stoppwort**  
 Wenn Sie **Stoppwort hinzufügen** oder **Stoppwort löschen**ausgewählt haben, geben Sie das Stoppwort im Feld **Stoppwort** ein. Ein neues Stoppwort muss eindeutig sein; das heißt, es darf noch nicht in dieser Stoppliste für die Sprache, die Sie auswählen, enthalten sein.  
  
 **Volltext-Standardsprache**  
 Wenn Sie **Stoppwort hinzufügen**, **Stoppwort löschen**oder **Alle Stoppwörter löschen**ausgewählt haben, wählen Sie die Sprache des Stoppworts bzw. der Stoppwörter aus der Liste aus. Diese Liste umfasst alle Volltextsprachen, die von der Serverinstanz unterstützt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [sys.fulltext_stopwords &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)   
 [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](../relational-databases/search/full-text-search.md)   
 [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
