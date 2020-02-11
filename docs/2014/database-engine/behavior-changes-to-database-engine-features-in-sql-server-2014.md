---
title: Verhaltensänderungen an Datenbank-Engine Features in SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- behavior changes [SQL Server]
- Database Engine [SQL Server], what's new
- Transact-SQL behavior changes
ms.assetid: 65eaafa1-9e06-4264-b547-cbee8013c995
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bfaaea1b07c17fbf5c47bbcccf20a3ca55862123
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "72278201"
---
# <a name="behavior-changes-to-database-engine-features-in-sql-server-2014"></a>Verhaltensänderungen von Datenbank-Engine-Funktionen in SQL Server 2014
  In diesem Thema werden Verhaltensänderungen in [!INCLUDE[ssDE](../includes/ssde-md.md)] beschrieben. Ein verändertes Programmverhalten wirkt sich darauf aus, wie Funktionen in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] im Vergleich zu früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]funktionieren oder zusammenwirken.  
  
## <a name="SQL14"></a>Verhaltensänderungen in[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 In früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] geben Abfragen, die für XML-Dokumente mit Zeichenfolgen ausgeführt werden, die eine bestimmte Länge überschreiten (mehr als 4020 Zeichen), möglicherweise falsche Ergebnisse zurück. In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] geben solche Abfragen die korrekten Ergebnisse zurück.  
  
## <a name="Denali"></a>Verhaltensänderungen in[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="metadata-discovery"></a>Metadatenermittlung  
 Verbesserungen [!INCLUDE[ssDE](../includes/ssde-md.md)] am Anfang [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] von ermöglichen SQLDescribeCol, präzisere Beschreibungen der erwarteten Ergebnisse zu erhalten, als von SQLDescribeCol in früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]zurückgegeben wurden. Weitere Informationen finden Sie unter [metadatenermittlung](../relational-databases/native-client/features/metadata-discovery.md).  
  
 Die Set-Option " [lmtonly](/sql/t-sql/statements/set-fmtonly-transact-sql) " zum Ermitteln des Formats einer Antwort, ohne die Abfrage tatsächlich ausführen, wird durch [sp_describe_first_result_set &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql), [sp_describe_undeclared_parameters &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql), [sys. dm_exec_describe_first_result_set &#40;&#41;Transact-SQL ](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql)dm_exec_describe_first_result_set_for_object und [sys. &#40;&#41;Transact-SQL- ](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql)ersetzt.  
  
### <a name="changes-to-behavior-in-scripting-a-sql-server-agent-task"></a>Änderungen am Verhalten bei der Skripterstellung eines SQL Server-Agent-Tasks  
 Wenn Sie in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] einen neuen Auftrag erstellen, indem Sie das Skript aus einem bereits vorhandenen Auftrag kopieren, wird der vorhandene Auftrag möglicherweise versehentlich vom neuen Auftrag beeinflusst. Wenn Sie einen neuen Auftrag mithilfe des Skripts aus einem vorhandenen Auftrag erstellen möchten, löschen * \@* Sie den Parameter manuell schedule_uid der in der Regel der letzte Parameter des Abschnitts ist, der den Auftrags Zeitplan im vorhandenen Auftrag erstellt. Dadurch wird ein neuer und unabhängiger Zeitplan für den neuen Auftrag ohne Auswirkungen auf die vorhandenen Aufträge erstellt.  
  
### <a name="constant-folding-for-clr-user-defined-functions-and-methods"></a>Reduktion konstanter Ausdrücke für benutzerdefinierte CLR-Funktionen und -Methoden  
 In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] sind die benutzerdefinierten CLR-Objekte jetzt reduzierbar.  
  
-   Benutzerdefinierte CLR-Funktionen mit deterministischen Skalarwerten.  
  
-   Deterministische Methoden benutzerdefinierter CLR-Typen.  
  
 Diese Neuerung zielt auf die Verbesserung der Leistung ab, wenn diese Funktionen oder Methoden mehr als einmal mit den gleichen Argumenten aufgerufen werden. Diese Änderung verursacht jedoch möglicherweise unerwartete Ergebnisse, wenn nichtdeterministische Funktionen oder Methoden fehlerhaft als deterministisch markiert wurden. Der Determinismus einer CLR-Funktion oder Methode wird vom Wert der `IsDeterministic`-Eigenschaft vom `SqlFunctionAttribute` oder `SqlMethodAttribute` angegeben.  
  
### <a name="behavior-of-stenvelope-method-has-changed-with-empty-spatial-types"></a>Verhalten der STEnvelope()-Methode wurde mit leeren räumlichen Typen geändert  
 Das Verhalten der `STEnvelope`-Methode mit leeren Objekten ist jetzt mit dem Verhalten anderer räumlicher [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Methoden konsistent.  
  
 In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] hat die `STEnvelope`-Methode die folgenden Ergebnisse zurückgegeben, wenn sie mit leeren Objekten aufgerufen wurde:  
  
```  
select geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns POINT EMPTY  
select geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns LINESTRING EMPTY  
select geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns POLYGON EMPTY  
```  
  
 In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] gibt die `STEnvelope`-Methode nun die folgenden Ergebnisse zurück, wenn sie mit leeren Objekten aufgerufen wird:  
  
```  
select geometry::Parse('POINT EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
select geometry::Parse('LINESTRING EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
select geometry::Parse('POLYGON EMPTY').STEnvelope().ToString()  
-- returns GEOMETRYCOLLECTION EMPTY  
```  
  
 Um zu ermitteln, ob ein räumliches Objekt leer ist, müssen Sie den [Datentyp STIsEmpty &#40;geometry-Datentyp&#41;](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type) Methode abrufen.  
  
### <a name="log-function-has-new-optional-parameter"></a>LOG-Funktion verfügt über neue optionale Parameter  
 Die `LOG` Funktion verfügt jetzt über einen optionalen *Basis* Parameter. Weitere Informationen finden Sie unter [Log &#40;Transact-SQL&#41;](/sql/t-sql/functions/log-transact-sql).  
  
### <a name="statistics-computation-during-partitioned-index-operations-has-changed"></a>Das Berechnen von Statistiken hat sich während der Vorgänge für partitionierte Indizes geändert  
 In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] werden Statistiken nicht durch das Scannen aller Zeilen in der Tabelle erstellt, wenn ein partitionierter Index erstellt oder neu erstellt wird. Der Abfrageoptimierer generiert stattdessen Statistiken mithilfe des Standardalgorithmus zur Stichprobenentnahme. Nachdem eine Datenbank mit partitionierten Indizes aktualisiert wurde, bemerken Sie möglicherweise einen Unterschied in den Histogrammdaten für diese Indizes. Diese Änderung des Verhaltens beeinträchtigt die Abfrageleistung möglicherweise nicht. Um Statistiken zu partitionierten Indizes durch das Scannen aller Zeilen in der Tabelle abzurufen, verwenden Sie CREATE STATISTICS oder UPDATE STATISTICS mit der FULLSCAN-Klausel.  
  
### <a name="data-type-conversion-by-the-xml-value-method-has-changed"></a>Die Datentypkonvertierung durch die XML-Wert Methode hat sich geändert  
 Das interne Verhalten der `value`-Methode des `xml`-Datentyps hat sich geändert. Diese Methode führt für das XML-Element eine XQuery aus und gibt einen Skalarwert des angegebenen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datentyps zurück. Der xs-Typ muss in den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datentyp umgewandelt werden. Früher hat die `value`-Methode den Quellwert intern in eine xs:-Zeichenfolge konvertiert und dann die xs:-Zeichenfolge in den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datentyp konvertiert. In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] wird die Konvertierung in die xs:-Zeichenfolge in den folgenden Fällen übersprungen:  
  
|Quell-XS-Datentyp|Ziel-SQL Server-Datentyp|  
|-------------------------|--------------------------------------|  
|byte<br /><br /> short<br /><br /> INT<br /><br /> integer<br /><br /> long<br /><br /> unsignedByte<br /><br /> unsignedShort<br /><br /> unsignedInt<br /><br /> unsignedLong<br /><br /> positiveInteger<br /><br /> nonPositiveInteger<br /><br /> negativeInteger<br /><br /> nonNegativeInteger|TINYINT<br /><br /> SMALLINT<br /><br /> INT<br /><br /> BIGINT<br /><br /> Decimal<br /><br /> NUMERIC|  
|Decimal|Decimal<br /><br /> NUMERIC|  
|float|real|  
|double|float|  
  
 Das neue Verhalten verbessert die Leistung, wenn die Zwischenkonvertierung übersprungen werden kann. Wenn bei Datentypkonvertierungen jedoch Fehler auftreten, werden andere Fehlermeldungen angezeigt, als dies beim Konvertieren vom dazwischenliegenden xs:-Zeichenfolgen-Wert der Fall wäre. Wenn die Wertmethode beispielsweise den `int`-Wert "100000" nicht in einen `smallint` konvertiert hat, lautete die vorherige Fehlermeldung:  
  
 `The conversion of the nvarchar value '100000' overflowed an INT2 column. Use a larger integer column.`  
  
 In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] lautet die Fehlermeldung (ohne die Zwischenkonvertierung in die xs:-Zeichenfolge):  
  
 `Arithmetic overflow error converting expression to data type smallint.`  
  
### <a name="sqlcmdexe-behavior-change-in-xml-mode"></a>sqlcmd.exe-Verhaltensänderung im XML-Modus  
 Es gibt Verhaltensänderungen, wenn Sie sqlcmd. exe mit dem XML-Modus (: XML on-Befehl) verwenden, wenn Sie SELECT * from T for XML... ausführen.  
  
### <a name="dbcc-checkident-revised-message"></a>Meldung "DBCC CHECKIDENT Revised" (DBCC CHECKIDENT überarbeitet)  
 In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]wurde die vom DBCC CHECKIDENT-Befehl zurückgegebene Nachricht nur geändert, wenn Sie mit reseed *new_reseed_value* verwendet wird, um den aktuellen Identitäts Wert zu ändern. Die neue Meldung lautet: "Überprüfen der Identitätsinformationen: aktueller\<Identitäts Wert>". Die DBCC-Ausführung wurde abgeschlossen. Falls DBCC Fehlermeldungen ausgegeben hat, wenden Sie sich an den Systemadministrator."  
  
 In früheren Versionen lautete die Meldung "Überprüfen der Identitätsinformationen: aktueller Identitäts Wert\<>", aktueller Spaltenwert "\<aktueller Spaltenwert>". Die DBCC-Ausführung wurde abgeschlossen. Falls DBCC Fehlermeldungen ausgegeben hat, wenden Sie sich an den Systemadministrator." Die Meldung wird nicht verändert, wenn DBCC CHECKIDENT mit NORESEED ohne zweiten Parameter oder ohne einen reseed-Wert angegeben wird. Weitere Informationen finden Sie unter [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql).  
  
### <a name="behavior-of-exist-function-on-xml-datatype-has-changed"></a>Verhalten der exist()-Funktion auf dem XML-Datentyp hat sich geändert  
 Beim Vergleich eines XML-Datentyps mit einem NULL-Wert mit 0 (null) hat sich das Verhalten der **exist ()** -Funktion geändert. Betrachten Sie das folgenden Beispiel:  
  
```xml  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 0;  
```  
  
 In früheren Versionen wurde bei diesem Vergleich "1" (true) zurückgegeben, jetzt wird stattdessen "0" (null, false) zurückgegeben.  
  
 Die folgenden Vergleiche haben sich nicht geändert:  
  
```xml  
DECLARE @test XML;  
SET @test = null;  
SELECT COUNT(1) WHERE @test.exist('/dogs') = 1; -- 0 expected, 0 returned  
SELECT COUNT(1) WHERE @test.exist('/dogs') IS NULL; -- 1 expected, 1 returned  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wichtige Änderungen an Datenbank-Engine Features in SQL Server 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md)   
 [Veraltete Datenbank-Engine Features in SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md)   
 [Nicht mehr unterstützte Datenbank-Engine Funktionen in SQL Server 2014](discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
