---
title: Erstellen von Volltextsuchabfragen (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3963876ce326529fd2538adc2d303d218406a924
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059292"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>Erstellen von Volltextsuchabfragen (Visual Database Tools)
  In Volltextsuchen werden mit dem CONTAINS-Prädikat Zeilen gefunden, die in einer bestimmten Spalte den angegebenen Text enthalten. Volltextsuchen sind nur bei Spalten möglich, die aktive Volltextindizes haben. Wenn Sie versuchen, die CONTAINS-Klausel in einer Spalte zu verwenden, für die es zurzeit keinen aktiven Volltextindex gibt, wird ein Fehler angezeigt. Weitere Informationen zu Volltextindizes und der CONTAINS-Klausel, finden Sie unter [Volltextsuche](../../relational-databases/search/full-text-search.md) und [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).  
  
### <a name="to-create-a-full-text-search-query"></a>So erstellen Sie eine Volltextsuchabfrage  
  
1.  Öffnen Sie im Projektmappen-Explorer eine Abfrage, oder erstellen Sie eine neue Abfrage.  
  
2.  Verwenden Sie in der WHERE-Klausel der Abfrage die CONTAINS-Funktion, um eine Volltextspalte zu durchsuchen.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützte Abfragetypen &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Entwerfen von Abfragen und Sichten Gewusst-wie-Themen &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Ausführen grundlegender Vorgänge mit Abfragen &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
