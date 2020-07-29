---
title: Überprüfen von Abfragen
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 3782141ec728483157890264f86a45087e1d2c7d
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008117"
---
# <a name="verify-queries-visual-database-tools"></a>Überprüfen von Abfragen (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Um Probleme zu vermeiden, können Sie die erstellte Abfrage auf richtige Syntax überprüfen. Diese Option ist insbesondere dann nützlich, wenn Sie Anweisungen im [SQL-Bereich](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)eingeben.  
  
Einige Hinweise, die beim Überprüfen von Abfragen bedacht werden sollten:  
  
-   Eine Anweisung kann gültig und daher problemlos überprüfbar sein, auch wenn sie sich im **Diagrammbereich** und **Kriterienbereich**nicht darstellen lässt.  
  
-   Bei einer SQL-Überprüfung werden einige, aber möglicherweise nicht alle SQL-Fehler erkannt. Wenn eine Abfrage einen bei der SQL-Überprüfung nicht erkannten Fehler enthält, erkennt die Datenbank den Fehler beim Ausführen der Abfrage.  
  
-   Abfragen, die Parameter enthalten, können nicht überprüft werden.  
  
### <a name="to-verify-an-sql-statement"></a>So überprüfen Sie eine SQL-Anweisung  
  
-   Klicken Sie mit der rechten Maustaste in den **SQL-Bereich**, und wählen Sie im Kontextmenü den Befehl **SQL-Syntax überprüfen** aus.  
  
## <a name="see-also"></a>Weitere Informationen  
[Ausführen von Abfragen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/run-queries-visual-database-tools.md)  
[Ausführen grundlegender Vorgänge mit Abfragen &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
