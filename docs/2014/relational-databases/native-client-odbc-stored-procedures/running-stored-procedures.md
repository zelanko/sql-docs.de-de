---
title: Ausführen gespeicherter Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- stored procedures [ODBC], running
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], executing
ms.assetid: 866b6dd3-2acd-4dfb-aeca-a0352b2d4c6a
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: fb03809fb465c4b23131d2133931028d7bec118d
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82709458"
---
# <a name="running-stored-procedures"></a>Ausführen gespeicherter Prozeduren
  Bei einer gespeicherten Prozedur handelt es sich um ein ausführbares Objekt, das in einer Datenbank gespeichert ist. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt:  
  
-   Gespeicherte Prozeduren:  
  
     Eine oder mehrere SQL-Anweisungen, die in eine einzelne ausführbare Prozedur vorkompiliert wurden  
  
-   Erweiterte gespeicherte Prozeduren:  
  
     In die SQL Server Open Data Services-API für erweiterte gespeicherte Prozeduren geschriebene Dynamic Link Libraries (DLL) in C oder C++. Die Open Data Services-API erweitert die Fähigkeiten gespeicherter Prozeduren, C- oder C++-Code zu enthalten.  
  
 Wenn beim Ausführen von Anweisungen eine gespeicherte Prozedur in der Datenquelle aufgerufen wird (anstatt eine Anweisung direkt in der Clientanwendung auszuführen oder vorzubereiten), bietet das folgende Vorteile:  
  
-   Höhere Leistung  
  
     SQL-Anweisungen werden analysiert und kompiliert, wenn Prozeduren erstellt werden. Dieser Aufwand ist dann bei der Ausführung der Prozeduren nicht mehr nötig.  
  
-   Geringere Netzwerkbelastung  
  
     Durch das Ausführen einer Prozedur statt Senden komplexer Abfragen über das Netzwerk wird der Netzwerkdatenverkehr reduziert. Wenn eine ODBC-Anwendung die ODBC-Syntax { CALL } zum Ausführen einer Prozedur verwendet, nimmt der ODBC-Treiber zusätzliche Optimierungen vor, die das Konvertieren von Parameterdaten überflüssig machen.  
  
-   Größere Konsistenz  
  
     Wenn die Regeln einer Organisation in einer zentralen Ressource implementiert sind, wie beispielsweise einer gespeicherten Prozedur, können Sie auf einmal codiert und getestet und Fehler behoben werden. Programmierer können dann die getesteten gespeicherten Prozeduren verwenden, statt eigene Implementierungen entwickeln zu müssen.  
  
-   Höhere Genauigkeit  
  
     Da gespeicherte Prozeduren in der Regel von erfahrenen Programmierern entwickelt werden, sind sie meist effizienter und weisen weniger Fehler auf als Code, der mehrmals von Programmierern unterschiedlicher Qualifikation entwickelt wird.  
  
-   Zusätzliche Funktionalität  
  
     Erweiterte gespeicherte Prozeduren können C- und C++-Funktionen verwenden, die in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen nicht verfügbar sind.  
  
     Ein Beispiel zum Abrufen einer gespeicherten Prozedur finden Sie unter Verarbeiten von [Rückgabe Codes und Ausgabeparametern &#40;ODBC-&#41;](../native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Aufrufen von gespeicherten Prozeduren](calling-a-stored-procedure.md)  
  
-   [Batchverarbeitung von gespeicherten Prozeduraufrufen](batching-stored-procedure-calls.md)  
  
-   [Verarbeiten von Ergebnissen gespeicherter Prozeduren](processing-stored-procedure-results.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC-&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [Gewusst-wie-Themen zur Ausführung gespeicherter Prozeduren &#40;ODBC&#41;](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
  
  
