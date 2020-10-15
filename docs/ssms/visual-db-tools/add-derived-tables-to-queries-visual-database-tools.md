---
description: Hinzufügen abgeleiteter Tabellen zu Abfragen (Visual Database Tools)
title: Hinzufügen von abgeleiteten Tabellen zu Abfragen
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [Visual Database Tools]
- joins [SQL Server], derived tables
- table joins [SQL Server]
- derived tables
ms.assetid: 05f1ba1d-465f-4e36-84bb-21b963c9b8f9
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: ec4389810e09af78f61e99762dbb30862919f1d1
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037186"
---
# <a name="add-derived-tables-to-queries-visual-database-tools"></a>Hinzufügen abgeleiteter Tabellen zu Abfragen (Visual Database Tools)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Abgeleitete Tabellen stellen Resultsets dar, die als Tabellenquellen in einer Abfrage verwendet werden. Im **Diagrammbereich**können Sie einer Abfrage eine abgeleitete Tabelle hinzufügen.  
  
### <a name="to-add-a-derived-table-to-a-query"></a>So fügen Sie einer Abfrage eine abgeleitete Tabelle hinzu  
  
1.  Öffnen Sie eine vorhandene Abfrage, oder erstellen Sie eine neue Abfrage.  
  
2.  Klicken Sie mit der rechten Maustaste auf den **Diagrammbereich** , und wählen Sie **Neue abgeleitete Tabelle hinzufügen**aus.  
  
    Es wird eine neue Tabelle namens „derivedtbl_*N* “ hinzugefügt, und die SELECT-Anweisung der abgeleiteten Tabelle wird der FROM-Klausel der Abfrage hinzugefügt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Ausführen grundlegender Vorgänge mit Abfragen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[Erstellen von Abfragen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-queries-visual-database-tools.md)  
[Öffnen von Abfragen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/open-queries-visual-database-tools.md)  
[SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)  
