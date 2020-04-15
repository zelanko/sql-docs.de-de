---
title: Ausführen gespeicherter Prozeduren | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- stored procedures [ODBC], running
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], executing
ms.assetid: 866b6dd3-2acd-4dfb-aeca-a0352b2d4c6a
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0b69a9177f98c8ee1096c18f368af12b11d6b325
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304551"
---
# <a name="running-stored-procedures"></a>Ausführen gespeicherter Prozeduren
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

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
  
     Ein Beispiel für das Aufrufen einer gespeicherten Prozedur finden Sie unter [Prozessrückgabecodes und Ausgabeparameter &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Aufrufen von gespeicherten Prozeduren](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)  
  
-   [Batchverarbeitung von gespeicherten Prozeduraufrufen](../../relational-databases/native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)  
  
-   [Verarbeiten von Ergebnissen gespeicherter Prozeduren](../../relational-databases/native-client-odbc-stored-procedures/processing-stored-procedure-results.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [Ausführen gespeicherter Prozeduren How-to-Topics &#40;ODBC-&#41;](https://msdn.microsoft.com/library/c2220182-a23d-4475-b353-77a77ab613d6)  
  
  
