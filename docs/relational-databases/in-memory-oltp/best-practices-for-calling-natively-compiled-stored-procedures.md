---
title: Bewährte Vorgehensweisen für systemintern kompilierte gespeicherte Prozeduren
description: Lernen Sie die Best Practices für nativ kompilierte gespeicherte Prozeduren kennen, die üblicherweise in leistungskritischen Teilen einer Anwendung zum Einsatz kommen.
ms.custom: seo-dt-2019
ms.date: 03/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694b
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e26440be66b89ff789890169751a18500f465c00
ms.sourcegitcommit: d56a834269132a83e5fe0a05b033936776cda8bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91529371"
---
# <a name="best-practices-for-calling-natively-compiled-stored-procedures"></a>Bewährte Vorgehensweisen für den Aufruf von systemintern kompilierten gespeicherten Prozeduren
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Für systemintern kompilierte gespeicherte Prozeduren gilt Folgendes:  
  
-   Sie werden üblicherweise in leistungskritischen Anwendungskomponenten verwendet.  
  
-   Sie werden häufig ausgeführt.  
  
-   Es wird erwartet, dass sie schnell sind.  
  
 Der Leistungsvorteil bei Verwendung einer systemintern kompilierten gespeicherten Prozedur nimmt mit der Anzahl der Zeilen und dem Umfang der Logik zu, die von der Prozedur verarbeitet werden. Beispielsweise lässt sich die Leistung einer nativ kompilierten gespeicherten Prozedur durch Verwendung einer oder mehrerer der folgenden Komponenten verbessern:  
  
-   Aggregation:  
  
-   Joins geschachtelter Schleifen.  
  
-   Auswahl-, Einfüge-, Update- und Löschvorgänge mit mehreren Anweisungen.  
  
-   Komplexe Ausdrücke.  
  
-   Prozedurale Logik, wie Bedingungsanweisungen und Schleifen.  
  
 Wenn Sie nur eine einzelne Zeile verarbeiten müssen, bietet eine systemintern kompilierte gespeicherte Prozedur u. U. keinen Leistungsvorteil.  
  
 Stellen Sie Folgendes sicher, um zu vermeiden, dass der Server Parameternamen zuordnen und Typen konvertieren muss:  
  
-   Gleichen Sie die Typen der an die Prozedur übergebenen Parameter mit den Typen in der Prozedurdefinition ab.  
  
-   Verwenden Sie Ordnungszahlparameter (namenlos), wenn Sie systemintern kompilierte gespeicherte Prozeduren aufrufen. Verwenden Sie für die effizienteste Ausführung keine benannten Parameter.  
  
 Ineffizienz in Parametern mit nativen kompilierten gespeicherten Prozeduren kann über das XEvent **natively_compiled_proc_slow_parameter_passing** erkannt werden:
 - Nicht übereinstimmende Typen: **reason=parameter_conversion**
 - Benannte Parameter: **reason=named_parameters**
 - Standardwerte: **reason=default** 
  
## <a name="see-also"></a>Weitere Informationen  
 [Nativ kompilierte gespeicherte Prozeduren](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
