---
title: Bewährte Vorgehensweisen für den Aufruf von systemintern kompilierten gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694bb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 39f88ef6c0b39bb51e4c1ba54388b37e04983b00
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050325"
---
# <a name="best-practices-for-calling-natively-compiled-stored-procedures"></a>Bewährte Vorgehensweisen für den Aufruf von systemintern kompilierten gespeicherten Prozeduren
  Für systemintern kompilierte gespeicherte Prozeduren gilt Folgendes:  
  
-   Sie werden üblicherweise in leistungskritischen Anwendungskomponenten verwendet.  
  
-   Sie werden häufig ausgeführt.  
  
-   Sie zeichnen sich erwartungsgemäß durch eine sehr schnelle Ausführung aus.  
  
 Der Leistungsvorteil bei Verwendung einer systemintern kompilierten gespeicherten Prozedur nimmt mit der Anzahl der Zeilen und dem Umfang der Logik zu, die von der Prozedur verarbeitet werden. Beispielsweise lässt sich die Leistung einer systemintern kompilierten gespeicherten Prozedur durch eine oder mehrere der folgenden Maßnahmen verbessern:  
  
-   Aggregation:  
  
-   Joins geschachtelter Schleifen.  
  
-   Auswahl-, Einfüge-, Update- und Löschvorgänge mit mehreren Anweisungen.  
  
-   Komplexe Ausdrücke.  
  
-   Prozedurale Logik, wie Bedingungsanweisungen und Schleifen.  
  
 Wenn Sie nur eine einzelne Zeile verarbeiten müssen, bietet eine systemintern kompilierte gespeicherte Prozedur u. U. keinen Leistungsvorteil.  
  
 So vermeiden Sie, dass der Server Parameternamen zuordnen und Typen konvertieren muss:  
  
-   Gleichen Sie die Typen der an die Prozedur übergebenen Parameter mit den Typen in der Prozedurdefinition ab.  
  
-   Verwenden Sie Ordnungszahlparameter (namenlos), wenn Sie systemintern kompilierte gespeicherte Prozeduren aufrufen. Verwenden Sie für die effizienteste Ausführung keine benannten Parameter.  
  
 Die Verwendung von (ineffizienten) benannten Parametern mit systemintern kompilierten gespeicherten Prozeduren kann über das XEvent `hekaton_slow_parameter_passing`, mit `reason=named_parameters`, erkannt werden.  
  
 Auf ähnliche Weise können Sie die Verwendung von nicht übereinstimmenden Typen über dasselbe XEvent `hekaton_slow_parameter_passing`, mit `reason=parameter_conversion`, erkennen.  
  
 Da Sie bei der Verwendung speicheroptimierter Tabellen (in vielen Fällen) Wiederholungslogik implementieren und bestimmte Funktionseinschränkungen umgehen müssen, können Sie eine von einem Wrapper interpretierte gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozedur erstellen. Ein Beispiel finden Sie unter [Richtlinien für Wiederholungs Logik für Transaktionen in Speicher optimierten Tabellen](memory-optimized-tables.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Nativ kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)  
  
  
