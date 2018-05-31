---
title: Intelligente Abfrageverarbeitung in SQL-Datenbanken von Microsoft | Microsoft-Dokumentation
description: Features zur intelligenten Abfrageverarbeitung, die die Abfrageleistung in SQL Server und in Azure SQL-Datenbank verbessern
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords: ''
ms.assetid: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 7786fd048f1698c90f379450b31e0bac3457706e
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2018
ms.locfileid: "34455766"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>Intelligente Abfrageverarbeitung in SQL-Datenbanken
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

Die Featurefamilie **Intelligente Abfrageverarbeitung** enthält Features mit weitreichenden Auswirkungen, die die Leistung vorhandener Workloads mit minimalem Implementierungsaufwand verbessern.   Darin enthalten sind Verbesserungen bereits vorhandener Konstrukte und die Einführung adaptiver Methoden und Funktionen.  

## <a name="adaptive-query-processing"></a>Adaptive Abfrageverarbeitung
Innerhalb der Featurefamilie für intelligente Abfrageverarbeitung wurde in SQL Server 2017 und Azure SQL-Datenbank die Featurefamilie für adaptive Abfrageverarbeitung eingeführt. Hierdurch wurden neue Funktionen für die Abfrageverarbeitung hinzugefügt, die Optimierungsstrategien für die Bedingungen der Runtime Ihrer Anwendungsarbeitsauslastung anwenden:
- **Adaptive Joins im Batchmodus** Dieses Feature ermöglicht Ihrem Plan, während der Ausführung mithilfe eines einzelnen zwischengespeicherten Plans dynamisch zu einer besseren Joinstrategie zu wechseln.
- **Feedback zur Speicherzuweisung im Batchmodus** Dieses Feature berechnet den tatsächlich benötigten Speicherplatz für eine Abfrage und aktualisiert anschließend den Zuweisungswert für den zwischengespeicherten Plan. Hierdurch werden exzessive Speicherzuweisungen reduziert, die die Parallelität beeinflussen, und zu gering geschätzte Speicherzuweisungen behoben, die zu teuren Überläufen auf den Datenträger führen.
- **Verschachtelte Ausführung mit Tabellenwertfunktionen mit mehreren Anweisungen** Bei der verschachtelten Ausführung verwenden Sie die tatsächliche Zeilenanzahl aus der Funktion, um besser informierte Entscheidungen zum Downstream-Abfrageplan zu treffen. 

Weitere Informationen zur adaptiven Abfrageverarbeitung finden Sie unter [Adaptive Abfrageverarbeitung in SQL-Datenbanken](../../relational-databases/performance/adaptive-query-processing.md).

## <a name="see-also"></a>Siehe auch
[Leistungscenter für SQL Server-Datenbankmodul und Azure SQL-Datenbank](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)     
[Leitfaden zur Architektur der Abfrageverarbeitung](../../relational-databases/query-processing-architecture-guide.md)    
[Referenz zu logischen und physischen Showplanoperatoren](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
[Joins](../../relational-databases/performance/joins.md)    
[Veranschaulichung der adaptiven Abfrageverarbeitung](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md)        
