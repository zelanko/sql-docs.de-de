---
description: Erstellen von Volltextsuchabfragen (Visual Database Tools)
title: Erstellen von Volltextsuchabfragen
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 25d6b063d6ae801ce26a3a353a75bf29a10b0237
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038918"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>Erstellen von Volltextsuchabfragen (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
In Volltextsuchen werden mit dem CONTAINS-Prädikat Zeilen gefunden, die in einer bestimmten Spalte den angegebenen Text enthalten. Volltextsuchen sind nur bei Spalten möglich, die aktive Volltextindizes haben. Wenn Sie versuchen, die CONTAINS-Klausel in einer Spalte zu verwenden, für die es zurzeit keinen aktiven Volltextindex gibt, wird ein Fehler angezeigt. Weitere Informationen zu Volltextindizes und der CONTAINS-Klausel finden Sie unter [Volltextsuche (SQL Server)](../../relational-databases/search/full-text-search.md) und [CONTAINS (Transact-SQL)](../../t-sql/queries/contains-transact-sql.md).  
  
### <a name="to-create-a-full-text-search-query"></a>So erstellen Sie eine Volltextsuchabfrage  
  
1.  Öffnen Sie im Projektmappen-Explorer eine Abfrage, oder erstellen Sie eine neue Abfrage.  
  
2.  Verwenden Sie in der WHERE-Klausel der Abfrage die CONTAINS-Funktion, um eine Volltextspalte zu durchsuchen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Unterstützte Abfragetypen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Themen zur Vorgehensweise: Entwerfen von Abfragen und Sichten &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Ausführen grundlegender Vorgänge mit Abfragen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
