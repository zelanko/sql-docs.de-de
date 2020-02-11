---
title: Neue Volltext-Stopp Liste (Seite "Allgemein") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplist.general.f1
ms.assetid: 97f8e82d-82ab-4525-91c9-1ee3ae217309
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: eca5e82b9d23709b45949cfe6af9022f1243ef08
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62774212"
---
# <a name="new-full-text-stoplist-general-page"></a>Neue Volltext-Stoppliste (Seite 'Allgemein')
  In diesem Dialogfeld können Sie eine neue Volltext-Stoppliste erstellen. Eine *Stoppliste* ist eine Sammlung häufig verwendeter Wörter, die als *Stoppwörter*bezeichnet werden. Diese werden bei der Volltextindizierung für Tabellen, denen die Stoppliste zugewiesen wurde, weggelassen. Weitere Informationen finden sie unter [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](../relational-databases/search/full-text-search.md).  
  
 **So erstellen Sie eine Stoppliste mit SQL Server Management Studio**  
  
-   [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a>Tastatur  
 **Name der Volltext-Stoppliste**  
 Geben Sie hier den Namen für die Volltext-Stoppliste ein.  
  
 **Besitzer**  
 Geben Sie den Besitzer der Volltext-Stoppliste an. Wenn Sie sich selbst, d. h. den aktuellen Benutzer, als Besitzer angeben möchten, lassen Sie dieses Feld leer.  
  
 Klicken Sie auf die Schaltfläche zum Durchsuchen, um einen anderen Benutzer auszuwählen.  
  
### <a name="create-stoplist-options"></a>Optionen zur Stopplistenerstellung  
 Klicken Sie auf eine der folgenden Optionen:  
  
 **Leere Stoppliste erstellen**  
 Die neue Stoppliste enthält keine Stoppwörter.  
  
 **Aus der Systemstoppliste erstellen**  
 Die neue Stoppliste wird aus der Stoppliste erstellt, die standardmäßig in der [Ressourcendatenbank](../relational-databases/databases/resource-database.md)enthalten ist.  
  
 **Aus vorhandener Volltext-Stoppliste erstellen**  
 Die neue Stoppliste wird durch Kopieren einer vorhandenen Stoppliste erstellt.  
  
 **Quelldatenbank**  
 Gibt den Namen der Datenbank an, zu der die vorhandene Stoppliste gehört. Standardmäßig ist die aktuelle Datenbank ausgewählt. Sie können optional eine andere Datenbank in der Liste auswählen.  
  
 **Quellstoppliste**  
 Gibt den Namen einer vorhandenen Stoppliste an. Wählen Sie aus der Liste der verfügbaren Stoppliste eine Stoppliste aus, die als Quelle verwendet werden soll. Die verfügbaren Stopplisten werden in der Reihenfolge aufgelistet, in der sie im Objekt-Explorer angezeigt werden.  
  
 Wenn eine in den Stoppwörtern der Quellstoppliste angegebene Sprache in der aktuellen Datenbank nicht registriert ist, wird CREATE FULLTEXT STOPLIST erfolgreich ausgeführt. Allerdings werden Warnungen zurückgegeben, und die entsprechenden Stoppwörter werden nicht hinzugefügt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)   
 [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](../relational-databases/search/full-text-search.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
  
