---
title: Verhaltensänderungen von Datenbank-Engine-Funktionen in SQLServer 2014 | Microsoft-Dokumentation
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
ms.openlocfilehash: be2957778e30af73abfafa210dee4746ffd869c9
ms.sourcegitcommit: 9d3ece500fa0e4a9f4fefc88df4af1db9431c619
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2019
ms.locfileid: "67463451"
---
# <a name="behavior-changes-to-database-engine-features-in-sql-server-2014"></a>Verhaltensänderungen von Datenbank-Engine-Funktionen in SQL Server 2014
  In diesem Thema werden Verhaltensänderungen in [!INCLUDE[ssDE](../includes/ssde-md.md)] beschrieben. Ein verändertes Programmverhalten wirkt sich darauf aus, wie Funktionen in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] im Vergleich zu früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]funktionieren oder zusammenwirken.  
  
## <a name="SQL14"></a> Verändertes Programmverhalten in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 In früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] geben Abfragen, die für XML-Dokumente mit Zeichenfolgen ausgeführt werden, die eine bestimmte Länge überschreiten (mehr als 4020 Zeichen), möglicherweise falsche Ergebnisse zurück. In [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] geben solche Abfragen die korrekten Ergebnisse zurück.  
  
## <a name="Denali"></a> Verändertes Programmverhalten in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="metadata-discovery"></a>Metadatenermittlung  
 Verbesserungen bei der [!INCLUDE[ssDE](../includes/ssde-md.md)] ab [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] ermöglichen SQLDescribeCol abrufen genauere Beschreibungen der erwarteten Ergebnisse als die von SQLDescribeCol zurückgegeben werden, in früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Metadatenermittlung](../relational-databases/native-client/features/metadata-discovery.md).  
  
 Die [SET FMTONLY](/sql/t-sql/statements/set-fmtonly-transact-sql) -Option zum Bestimmen des Formats einer Antwort, ohne die Abfrage tatsächlich auszuführen, durch ersetzt [Sp_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql), [Sp_describe_undeclared_parameters &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql), [Sys. dm_exec_describe_first_result_set &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-transact-sql), und [Sys. dm_ Exec_describe_first_result_set_for_object &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-describe-first-result-set-for-object-transact-sql).  
  
### <a name="changes-to-behavior-in-scripting-a-sql-server-agent-task"></a>Änderungen am Verhalten bei der Skripterstellung eines SQL Server-Agent-Tasks  
 Wenn Sie in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] einen neuen Auftrag erstellen, indem Sie das Skript aus einem bereits vorhandenen Auftrag kopieren, wird der vorhandene Auftrag möglicherweise versehentlich vom neuen Auftrag beeinflusst. Um einen neuen Auftrag mit dem Skript aus einem vorhandenen Auftrag zu erstellen, löschen Sie manuell den Parameter *@schedule_uid* ist in der Regel der letzte Parameter des Abschnitts der den Auftragszeitplan im vorhandenen Auftrag erstellt. Dadurch wird ein neuer und unabhängiger Zeitplan für den neuen Auftrag ohne Auswirkungen auf die vorhandenen Aufträge erstellt.  
  
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
  
 Um zu bestimmen, ob ein räumliches Objekt leer ist, rufen die [STIsEmpty &#40;Geometry-Datentyp&#41; ](/sql/t-sql/spatial-geometry/stisempty-geometry-data-type) Methode.  
  
### <a name="log-function-has-new-optional-parameter"></a>LOG-Funktion verfügt über neue optionale Parameter  
 Die `LOG` Funktion verfügt jetzt über einen optionalen *Basis* Parameter. Weitere Informationen finden Sie unter [LOG &#40;Transact-SQL&#41;](/sql/t-sql/functions/log-transact-sql).  
  
### <a name="statistics-computation-during-partitioned-index-operations-has-changed"></a>Das Berechnen von Statistiken hat sich während der Vorgänge für partitionierte Indizes geändert  
 In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] werden Statistiken nicht durch das Scannen aller Zeilen in der Tabelle erstellt, wenn ein partitionierter Index erstellt oder neu erstellt wird. Der Abfrageoptimierer generiert stattdessen Statistiken mithilfe des Standardalgorithmus zur Stichprobenentnahme. Nachdem eine Datenbank mit partitionierten Indizes aktualisiert wurde, bemerken Sie möglicherweise einen Unterschied in den Histogrammdaten für diese Indizes. Diese Änderung des Verhaltens beeinträchtigt die Abfrageleistung möglicherweise nicht. Um Statistiken zu partitionierten Indizes durch das Scannen aller Zeilen in der Tabelle abzurufen, verwenden Sie CREATE STATISTICS oder UPDATE STATISTICS mit der FULLSCAN-Klausel.  
  
### <a name="data-type-conversion-by-the-xml-value-method-has-changed"></a>Die Datentypkonvertierung durch die XML-Wert Methode hat sich geändert  
 Das interne Verhalten der `value`-Methode des `xml`-Datentyps hat sich geändert. Diese Methode führt für das XML-Element eine XQuery aus und gibt einen Skalarwert des angegebenen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datentyps zurück. Der xs-Typ muss in den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datentyp umgewandelt werden. Früher hat die `value`-Methode den Quellwert intern in eine xs:-Zeichenfolge konvertiert und dann die xs:-Zeichenfolge in den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datentyp konvertiert. In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] wird die Konvertierung in die xs:-Zeichenfolge in den folgenden Fällen übersprungen:  
  
|Quell-XS-Datentyp|Ziel-SQL Server-Datentyp|  
|-------------------------|--------------------------------------|  
|byte<br /><br /> short<br /><br /> ssNoversion<br /><br /> integer<br /><br /> long<br /><br /> unsignedByte<br /><br /> unsignedShort<br /><br /> unsignedInt<br /><br /> unsignedLong<br /><br /> positiveInteger<br /><br /> nonPositiveInteger<br /><br /> negativeInteger<br /><br /> nonNegativeInteger|TINYINT<br /><br /> SMALLINT<br /><br /> ssNoversion<br /><br /> BIGINT<br /><br /> Decimal<br /><br /> NUMERIC|  
|Decimal|Decimal<br /><br /> NUMERIC|  
|FLOAT|REAL|  
|double|FLOAT|  
  
 Das neue Verhalten verbessert die Leistung, wenn die Zwischenkonvertierung übersprungen werden kann. Wenn bei Datentypkonvertierungen jedoch Fehler auftreten, werden andere Fehlermeldungen angezeigt, als dies beim Konvertieren vom dazwischenliegenden xs:-Zeichenfolgen-Wert der Fall wäre. Wenn die Wertmethode beispielsweise den `int`-Wert "100000" nicht in einen `smallint` konvertiert hat, lautete die vorherige Fehlermeldung:  
  
 `The conversion of the nvarchar value '100000' overflowed an INT2 column. Use a larger integer column.`  
  
 In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] lautet die Fehlermeldung (ohne die Zwischenkonvertierung in die xs:-Zeichenfolge):  
  
 `Arithmetic overflow error converting expression to data type smallint.`  
  
### <a name="sqlcmdexe-behavior-change-in-xml-mode"></a>sqlcmd.exe-Verhaltensänderung im XML-Modus  
 Verändertes Programmverhalten vorhanden sind, bei der Verwendung von sqlcmd.exe mit XML-Modus (: XML ON-Befehl) beim Ausführen einer SELECT * from T FOR XML...  
  
### <a name="dbcc-checkident-revised-message"></a>Meldung "DBCC CHECKIDENT Revised" (DBCC CHECKIDENT überarbeitet)  
 In [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], vom DBCC CHECKIDENT-Befehl zurückgegebene Meldung geändert wurde, nur mit RESEED Verwendung *New_reseed_value* aktuellen Identitätswert zu ändern. Die neue Meldung lautet "Überprüfen der Identitätsinformationen: aktueller Identitätswert '\<aktueller Identitätswert >'. Die DBCC-Ausführung wurde abgeschlossen. Falls DBCC Fehlermeldungen ausgegeben hat, wenden Sie sich an den Systemadministrator."  
  
 In früheren Versionen wird die Nachricht ist "Überprüfen der Identitätsinformationen: aktueller Identitätswert '\<aktueller Identitätswert >', aktueller Spaltenwert '\<aktueller Spaltenwert >'. Die DBCC-Ausführung wurde abgeschlossen. Falls DBCC Fehlermeldungen ausgegeben hat, wenden Sie sich an den Systemadministrator." Die Meldung wird nicht verändert, wenn DBCC CHECKIDENT mit NORESEED ohne zweiten Parameter oder ohne einen reseed-Wert angegeben wird. Weitere Informationen finden Sie unter [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql).  
  
### <a name="behavior-of-exist-function-on-xml-datatype-has-changed"></a>Verhalten der exist()-Funktion auf dem XML-Datentyp hat sich geändert  
 Das Verhalten der **exist()** Funktion wurde geändert, für den Vergleich einen XML-Datentyp mit einer null-Wert auf 0 (null). Betrachten Sie das folgende Beispiel:  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Fehlerhafte Änderungen an Funktionen der Datenbank-Engine in SQLServer 2014](breaking-changes-to-database-engine-features-in-sql-server-2016.md)   
 [Veraltete Datenbankmodulfeatures in SQLServer 2014](deprecated-database-engine-features-in-sql-server-2016.md)   
 [Nicht mehr unterstützte Datenbank-Engine-Funktionalität in SQLServer 2014](discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [ALTER DATABASE-Kompatibilitätsgrad &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
  
  
