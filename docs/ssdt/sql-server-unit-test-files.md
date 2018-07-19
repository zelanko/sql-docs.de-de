---
title: SQL Server-Komponententestdateien | Microsoft-Dokumentation
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cee093c9-b97d-4fb0-b80f-806d071259dc
caps.latest.revision: 9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e23304a429b77bcb4a5fc6a4c1001f2f28cf7885
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094237"
---
# <a name="sql-server-unit-test-files"></a>SQL Server-Komponententestdateien
SQL Server-Komponententests werden wie Komponententests für verwalteten Code in Testprojekten angelegt. Die Elemente, aus denen sich ein SQL Server-Komponententest zusammensetzt, können im **Projektmappen-Explorer** in der Hierarchie eines Testprojekts angezeigt werden.  
  
Ein SQL Server-Komponententest besteht aus mehreren Elementen, die in verschiedenen Dateien enthalten sind. In der folgenden Tabelle sind die Dateien beschrieben, die in einem SQL Server-Komponententest zusammenwirken.  
  
|**File**|**Beschreibung**|  
|------------|-------------------|  
|CS- oder VB-Datei|Diese Quellcodedatei enthält eine mit dem [TestClass]-Attribut ergänzte Klasse. Die Klasse enthält eine einzelne Testmethode für jeden enthaltenen SQL Server-Komponententest. Diese Methoden werden mit dem [TestMethod]-Attribut ergänzt.<br /><br />Jede Testmethode enthält den geeigneten Code zum Ausführen des Transact\-SQL-Testskripts. Dieser Code wird bei der Erstellung der Testmethoden generiert und kann geändert werden.<br /><br />**HINWEIS**: Wenn Sie im **Projektmappen-Explorer** auf die Datei doppelklicken, wird die Testklasse im SQL Server-Komponententest-Designer geöffnet. Um die CS- oder VB-Datei zu öffnen und den Quellcode anzuzeigen, klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf die Datei und klicken dann auf **Code anzeigen**.|  
|RESX-Datei|Diese Ressourcendatei enthält die Transact\-SQL-Skripts für alle Tests in der zugehörigen CS- oder VB-Datei. Die Skriptgruppe umfasst das Vortestskript, das Testskript sowie das Nachtestskript. Die Ressourcendatei enthält editierbare XML. Die Ressourcendatei wird in die Testassembly kompiliert.<br /><br />Zum Erstellen des Transact\-SQL-Skriptcodes können Sie den **SQL Server-Komponententest-Designer** verwenden. Weitere Informationen zu den Skripts, die in SQL Server-Komponententests verwendet werden, finden Sie unter [Skripts in SQL Server-Komponententests](../ssdt/scripts-in-sql-server-unit-tests.md).|  
|"App.config"|In dieser Datei werden die Datenbankverbindungszeichenfolgen für das Testprojekt sowie weitere Konfigurationseinstellungen für SQL Server-Komponententests gespeichert, beispielsweise das Befehlstimeout. Weitere Informationen finden Sie unter [Skripts in SQL Server-Komponententests](../ssdt/scripts-in-sql-server-unit-tests.md).|  
|"SQLDatabaseSetup.cs" oder "SQLDatabaseSetup.vb"|Die Datei enthält eine Klasse, die die Testumgebung für alle SQL Server-Komponententests im Testprojekt vorbereitet. Auf der Grundlage der Konfigurationseinstellungen in der Datei „app.config“ kann ein SQL Server-Datenbankprojekt in der Testdatenbank bereitgestellt werden.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Erstellen und Definieren von SQL Server-Komponententests](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[Erstellen und Definieren von SQL Server-Komponententests](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[Überprüfen des Datenbankcodes mithilfe von SQL Server-Komponententests](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
[Skripts in SQL Server-Komponententests](../ssdt/scripts-in-sql-server-unit-tests.md)  
  
