---
description: Deterministische und nicht deterministische Funktionen
title: Deterministische und nicht deterministische Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- built-in functions [SQL Server]
- nondeterministic functions
- extended stored procedures [SQL Server], functions that call
- deterministic functions
- user-defined functions [SQL Server], deterministic
ms.assetid: 2f3ce5f5-c81c-4470-8141-8144d4f218dd
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: eebd2896dc1931e03dd121867ee09c1940d02d36
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97466711"
---
# <a name="deterministic-and-nondeterministic-functions"></a>Deterministische und nicht deterministische Funktionen
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Deterministische Funktionen geben bei jedem Aufrufen dasselbe Ergebnis zurück, wenn sie mit einem bestimmten Satz von Eingabewerten aufgerufen werden und die Datenbank denselben Status aufweist. Nicht deterministische Funktionen können bei jedem Aufrufen unterschiedliche Ergebnisse zurückgeben, wenn sie mit einem bestimmten Satz von Eingabewerten aufgerufen werden – selbst wenn die Datenbank, auf die zugegriffen wird, immer denselben Status aufweist. Beispielsweise gibt die AVG-Funktion immer dasselbe Ergebnis zurück, sofern die zuvor genannten Bedingungen erfüllt sind. Die GETDATE-Funktion hingegen, die den aktuellen datetime-Wert liefert, gibt immer ein anderes Ergebnis zurück.  
  
 Benutzerdefinierte Funktionen weisen eine Reihe von Eigenschaften auf, mit denen festgelegt wird, ob das [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in der Lage ist, die Ergebnisse der Funktion zu indizieren – entweder durch Indizes für berechnete Spalten, die die Funktion aufrufen, oder durch indizierte Sichten, die auf die Funktion verweisen. Der Determinismus einer Funktion ist eine solche Eigenschaft. Für eine Sicht kann z. B. kein gruppierter Index erstellt werden, falls die Sicht auf nicht deterministische Funktionen verweist. Weitere Informationen zu Eigenschaften von Funktionen, einschließlich Determinismus, finden Sie unter [Benutzerdefinierte Funktionen](../../relational-databases/user-defined-functions/user-defined-functions.md).  
  
 In diesem Thema werden der Determinismus integrierter Systemfunktionen und die Auswirkungen auf die deterministische Eigenschaft benutzerdefinierter Funktionen erläutert, wenn in dieser ein Aufruf erweiterter gespeicherter Prozeduren enthalten ist.  
  
## <a name="built-in-function-determinism"></a>Determinismus integrierter Funktionen  
 Der Determinismus integrierter Funktionen kann nicht beeinflusst werden. Jede integrierte Funktion ist abhängig von deren Implementierung durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]deterministisch oder nicht deterministisch. Wenn beispielsweise eine ORDER BY-Klausel in einer Abfrage angegeben wird, wird der Determinismus einer in der Abfrage verwendeten Funktion nicht geändert.  
  
 Alle integrierten Zeichenfolgenfunktionen sind deterministisch, mit Ausnahme von [FORMAT](../../t-sql/functions/format-transact-sql.md). Eine Liste dieser Funktionen finden Sie unter [Zeichenfolgenfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md).  
  
 Die folgenden integrierten Funktionen aus Kategorien anderer integrierter Funktionen als Zeichenfolgenfunktionen sind immer deterministisch:  
  
:::row:::
    :::column:::
        ABS (ABS)
    :::column-end:::
    :::column:::
        DATEDIFF
    :::column-end:::
    :::column:::
        POWER
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ACOS
    :::column-end:::
    :::column:::
        DAY
    :::column-end:::
    :::column:::
        RADIANS
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ASIN
    :::column-end:::
    :::column:::
        DEGREES
    :::column-end:::
    :::column:::
        ROUND
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ATAN
    :::column-end:::
    :::column:::
        EXP
    :::column-end:::
    :::column:::
        SIGN
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        ATN2
    :::column-end:::
    :::column:::
        FLOOR
    :::column-end:::
    :::column:::
        SIN
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CEILING
    :::column-end:::
    :::column:::
        ISNULL
    :::column-end:::
    :::column:::
        SQUARE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        COALESCE
    :::column-end:::
    :::column:::
        ISNUMERIC
    :::column-end:::
    :::column:::
        SQRT
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        COS
    :::column-end:::
    :::column:::
        PROTOKOLL
    :::column-end:::
    :::column:::
        TAN
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        COT
    :::column-end:::
    :::column:::
        LOG10
    :::column-end:::
    :::column:::
        YEAR
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        DATALENGTH
    :::column-end:::
    :::column:::
        MONTH
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        DATEADD
    :::column-end:::
    :::column:::
        NULLIF
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::
 
 Die folgenden Funktionen sind nicht immer deterministisch, können jedoch in indizierten Sichten oder Indizes für berechnete Spalten verwendet werden, wenn sie als deterministische Funktion angegeben werden.  
  
|Funktion|Kommentare|  
|--------------|--------------|  
|alle Aggregatfunktionen|Alle Aggregatfunktionen sind deterministisch, es sei denn, sie werden mit den OVER- und ORDER BY-Klauseln angegeben. Eine Liste dieser Funktionen finden Sie unter [Aggregatfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/aggregate-functions-transact-sql.md).|  
|CAST|Deterministisch, wenn nicht mit **datetime**, **smalldatetime** oder **sql_variant** verwendet.|  
|CONVERT|Deterministisch, wenn nicht eine der folgenden Bedingungen vorliegt:<br /><br /> <br /><br /> Der Typ ist **sql_variant**.<br /><br /> Der Zieltyp ist **sql_variant** , und der Quelltyp ist nicht deterministisch.<br /><br /> Der Quell- oder Zieltyp ist **datetime** oder **smalldatetime**, der andere Quell- oder Zieltyp ist eine Zeichenfolge, und es wird ein nicht deterministisches Format angegeben. Ein deterministisches Format kann nur verwendet werden, wenn der style-Parameter konstant ist. Wenn die Werte für "style" kleiner oder gleich 100 sind, sind sie nicht deterministisch, mit Ausnahme der style-Werte 20 und 21. style-Werte über 100 sind deterministisch, mit Ausnahme der style-Werte 106, 107, 109 und 113.|  
|CHECKSUM|Deterministisch, mit Ausnahme von CHECKSUM(*).|  
|ISDATE|Nur deterministisch in Verbindung mit der CONVERT-Funktion, wenn der style-Parameter von CONVERT angegeben ist und "style" nicht den Wert 0, 100, 9 oder 109 aufweist.|  
|RAND|RAND ist nur deterministisch, wenn ein *seed* -Parameter angegeben wird.|  
  
 Alle Konfigurations-, Cursor-, Metadaten-, Sicherheits- und statistischen Systemfunktionen sind nicht deterministisch. Eine Liste dieser Funktionen finden Sie unter [Konfigurationsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md), [Cursorfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-functions-transact-sql.md), [Metadatenfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md), [Sicherheitsfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md) und [Statistische Systemfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md).  
  
 Die folgenden integrierten Funktionen aus anderen Kategorien sind immer nicht deterministisch:  
  
:::row:::
    :::column:::
        @@CONNECTIONS
    :::column-end:::
    :::column:::
        GETDATE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@CPU_BUSY
    :::column-end:::
    :::column:::
        GETUTCDATE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@DBTS
    :::column-end:::
    :::column:::
        GET_TRANSMISSION_STATUS
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@IDLE
    :::column-end:::
    :::column:::
        LAG
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@IO_BUSY
    :::column-end:::
    :::column:::
        LAST_VALUE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@MAX_CONNECTIONS
    :::column-end:::
    :::column:::
        LEAD
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@PACK_RECEIVED
    :::column-end:::
    :::column:::
        MIN_ACTIVE_ROWVERSION
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@PACK_SENT
    :::column-end:::
    :::column:::
        NEWID
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@PACKET_ERRORS
    :::column-end:::
    :::column:::
        NEWSEQUENTIALID
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@TIMETICKS
    :::column-end:::
    :::column:::
        NEXT VALUE FOR
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@TOTAL_ERRORS
    :::column-end:::
    :::column:::
        NTILE
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@TOTAL_READ
    :::column-end:::
    :::column:::
        PARSENAME
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        @@TOTAL_WRITE
    :::column-end:::
    :::column:::
        PERCENTILE_CONT
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        AT TIME ZONE
    :::column-end:::
    :::column:::
        PERCENTILE_DISC
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        CUME_DIST
    :::column-end:::
    :::column:::
        PERCENT_RANK
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        CURRENT_TIMESTAMP
    :::column-end:::
    :::column:::
        RAND
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        DENSE_RANK
    :::column-end:::
    :::column:::
        RANK
    :::column-end:::
:::row-end:::  
:::row:::
    :::column:::
        FIRST_VALUE
    :::column-end:::
    :::column:::
        ROW_NUMBER
    :::column-end:::
:::row-end:::   
:::row:::
    :::column:::
        FORMAT
    :::column-end:::
    :::column:::
        TEXTPTR
    :::column-end:::
:::row-end:::
 
## <a name="calling-extended-stored-procedures-from-functions"></a>Aufrufen erweiterter gespeicherter Prozeduren aus Funktionen  
 Funktionen, die erweiterte gespeicherte Prozeduren aufrufen, sind nicht deterministisch, da erweiterte gespeicherte Prozeduren Nebeneffekte im Hinblick auf die Datenbank verursachen können. Nebeneffekte sind Änderungen am globalen Status der Datenbank, wie z. B. ein Update einer Tabelle, oder an einer externen Ressource, wie z. B. einer Datei oder des Netzwerkes. Beispiel: Änderungen an einer Datei oder Senden einer E-Mail-Nachricht. Verlassen Sie sich nicht auf die Rückgabe eines konsistenten Resultsets, wenn Sie eine erweiterte gespeicherte Prozedur von einer benutzerdefinierten Funktion aus ausführen. Die Verwendung benutzerdefinierter Funktionen, die zu Nebeneffekten hinsichtlich der Datenbank führen, wird nicht empfohlen.  
  
 Wenn eine erweiterte gespeicherte Prozedur aus einer Funktion heraus aufgerufen wird, kann die Prozedur keine Resultsets an den Client zurückgeben. Jede Open Data Services-API, die Resultsets an den Client zurückgibt, weist den Rückgabecode FAIL auf.  
  
 Die erweiterte gespeicherte Prozedur kann erneut eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]herstellen. Die Prozedur kann jedoch keine Verbindung mit derselben Transaktion wie die ursprüngliche Funktion herstellen, durch die die erweiterte gespeicherte Prozedur aufgerufen wurde.  
  
 Wie bei Aufrufen von einem Batch oder einer gespeicherten Prozedur aus wird die erweiterte gespeicherte Prozedur im Kontext des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Sicherheitskontos ausgeführt, unter dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird. Der Besitzer der erweiterten gespeicherten Prozedur sollte diese Berechtigungen dieses Sicherheitskontexts berücksichtigen, wenn er anderen Benutzern Berechtigungen zum Ausführen der Prozedur erteilt.  
  
  
