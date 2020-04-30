---
title: CREATE WORKLOAD GROUP (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/20/2020
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- WORKLOAD GROUP
- WORKLOAD_GROUP_TSQL
- CREATE WORKLOAD GROUP
- CREATE_WORKLOAD_GROUP_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE WORKLOAD GROUP statement
author: julieMSFT
ms.author: jrasnick
manager: craigg
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azure-sqldw-latest||=azuresqldb-mi-current'
ms.openlocfilehash: c61185c660e650a2052a2e5a6df1ad9ac3ad0af4
ms.sourcegitcommit: c37777216fb8b464e33cd6e2ffbedb6860971b0d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2020
ms.locfileid: "82087464"
---
# <a name="create-workload-group-transact-sql"></a>CREATE WORKLOAD GROUP (Transact-SQL)

## <a name="click-a-product"></a>Wählen Sie ein Produkt.

Klicken Sie in der folgenden Zeile auf den Namen des Produkts, das Sie am meisten interessiert. Mit nur einem Klick erhalten Sie auf dieser Webseite unterschiedliche Inhalte, die zu dem Produkt passen, das Sie ausgewählt haben.

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current||=sqlallproducts-allversions"

> |||||
> |---|---|---|---|
> |**_\* SQL Server \*_** &nbsp;|[SQL-Datenbank<br />verwaltete Instanz](create-workload-group-transact-sql.md?view=azuresqldb-mi-current)|[Azure Synapse<br />Analytics](create-workload-group-transact-sql.md?view=azure-sqldw-latest)|

&nbsp;

## <a name="sql-server-and-sql-database-managed-instance"></a>Verwaltete SQL Server- und SQL-Datenbank-Instanz

Erstellt eine Arbeitsauslastungsgruppe unter Ressourcenkontrolle und verknüpft die Arbeitsauslastungsgruppe mit einem Ressourcenpool der Ressourcenkontrolle. Resource Governor ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbar. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).

![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## <a name="syntax"></a>Syntax

```syntaxsql
CREATE WORKLOAD GROUP group_name
[ WITH
    ( [ IMPORTANCE = { LOW | MEDIUM | HIGH } ]
      [ [ , ] REQUEST_MAX_MEMORY_GRANT_PERCENT = value ]
      [ [ , ] REQUEST_MAX_CPU_TIME_SEC = value ]
      [ [ , ] REQUEST_MEMORY_GRANT_TIMEOUT_SEC = value ]
      [ [ , ] MAX_DOP = value ]
      [ [ , ] GROUP_MAX_REQUESTS = value ] )
 ]
[ USING {
    [ pool_name | "default" ]
    [ [ , ] EXTERNAL external_pool_name | "default" ] ]
    } ]
[ ; ]
```

## <a name="arguments"></a>Argumente

*group_name*</br>
Der benutzerdefinierte Name für die Arbeitsauslastungsgruppe. *group_name* ist alphanumerisch, kann bis zu 128 Zeichen enthalten, muss innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eindeutig sein und muss den Regeln für [Bezeichner](../../relational-databases/databases/database-identifiers.md) entsprechen.

IMPORTANCE = { LOW | **MEDIUM** | HIGH }</br>
Gibt die relative Wichtigkeit einer Anforderung in der Arbeitsauslastungsgruppe an. Für die Wichtigkeit sind folgende Einstellungen möglich, wobei MEDIUM die Standardeinstellung ist:

- LOW
- MEDIUM (Standard)
- HIGH

> [!NOTE]
> Intern wird jede Wichtigkeitseinstellung als Zahl gespeichert, die für Berechnungen verwendet wird.

IMPORTANCE hat einen lokalen Bezug zum Ressourcenpool; Arbeitsauslastungsgruppen mit verschiedener Wichtigkeit innerhalb desselben Ressourcenpools beeinflussen sich gegenseitig, haben jedoch keine Auswirkungen auf Arbeitsauslastungsgruppen in anderen Ressourcenpools.

REQUEST_MAX_MEMORY_GRANT_PERCENT = *value*</br>
Gibt die Höchstmenge an Arbeitsspeicher an, die eine einzelne Anforderung vom Pool in Anspruch nehmen kann. *value* entspricht einem Prozentwert, der relativ zur Ressourcenpoolgröße ist, die mit MAX_MEMORY_PERCENT festgelegt wird.

*value* entspricht bis [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] einem Integer und ab [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] sowie in verwalteten [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]-Instanzen einer Gleitkommazahl. Der Standardwert ist 25. Der zulässige Bereich für *value* liegt zwischen 1 und 100.

> [!IMPORTANT]  
> Die angegebene Menge bezieht sich nur auf den für die Abfrageausführung gewährten Arbeitsspeicher.
>
> Das Festlegen von *value* auf 0 (null) verhindert, dass Abfragen mit SORT- und HASH JOIN-Vorgängen in benutzerdefinierten Arbeitsauslastungsgruppen ausgeführt werden.
>
> Es wird davon abgeraten, *value* auf einen höheren Wert als 70 festzulegen, da der Server möglicherweise nicht genug freien Arbeitsspeicher reservieren kann, wenn andere Abfragen gleichzeitig ausgeführt werden. Dadurch tritt möglicherweise der Timeoutfehler 8645 auf.
>
> Wenn die Arbeitsspeicheranforderungen der Abfrage den Grenzwert überschreiten, der von diesem Parameter angegeben wird, führt der Server folgende Vorgänge aus:
>
> - Bei benutzerdefinierten Arbeitsauslastungsgruppen versucht der Server, den Grad der Parallelität für diese Abfrage zu reduzieren, bis die Arbeitsspeicheranforderung den Grenzwert unterschreitet oder bis der Grad der Parallelität dem Wert 1 entspricht. Wenn die Arbeitsspeicheranforderung der Abfrage den Grenzwert immer noch überschreitet, tritt Fehler 8657 auf.
>
> - Bei internen und Standard-Arbeitsauslastungsgruppen lässt der Server zu, dass der Abfrage der erforderliche Arbeitsspeicher zugewiesen wird.
>
> Beachten Sie, dass in beiden Fällen der Timeoutfehler 8645 auftreten kann, wenn der Server nicht über ausreichend physischen Arbeitsspeicher verfügt.

REQUEST_MAX_CPU_TIME_SEC = *value*</br>
Gibt die maximale CPU-Zeit in Sekunden an, die eine Anforderung beanspruchen kann. *value* muss 0 (null) oder ein positiver Integer sein. Die Standardeinstellung für *value* ist 0 (null), also unbegrenzt.

> [!NOTE]
> Resource Governor verhindert nicht, dass eine Anforderung bei Erreichung des maximalen Zeitlimits fortgesetzt wird. Es wird jedoch ein Ereignis generiert. Weitere Informationen finden Sie unter [CPU Threshold Exceeded (Ereignisklasse)](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md).
> [!IMPORTANT]
> Ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 und [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3 bricht Resource Governor mit [Ablaufverfolgungsflag 2422](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) eine Anforderung ab, wenn die maximale Zeit überschritten wird.

REQUEST_MEMORY_GRANT_TIMEOUT_SEC = *value*</br>
Gibt die maximale Zeit in Sekunden an, die eine Abfrage auf das Freiwerden einer Speicherzuweisung (Arbeitsspeicherpuffer) wartet. *value* muss 0 (null) oder ein positiver Integer sein. Die Standardeinstellung für *value* ist 0 (null). Hierbei wird eine interne Berechnung basierend auf den Abfragekosten verwendet, um die maximale Zeit zu ermitteln.

> [!NOTE]
> Eine Abfrage schlägt nicht grundsätzlich fehl, wenn das Timeout der Arbeitsspeicherzuweisung erreicht wird. Eine Abfrage schlägt nur fehl, wenn zu viele Abfragen gleichzeitig ausgeführt werden. Andernfalls könnte die Abfrage nur die minimale Arbeitsspeicherzuweisung nutzen, was zu reduzierter Abfrageleistung führen kann.

MAX_DOP = *value*</br>
Gibt den **maximalen Grad an Parallelität (MAXDOP)** für die parallele Ausführung von Abfragen an. *value* muss 0 (null) oder ein positiver Integer sein. Der zulässige Bereich für *value* liegt zwischen 0 und 64. Die *value*-Standardeinstellung 0 verwendet die globale Einstellung. MAX_DOP wird wie folgt behandelt:

> [!NOTE]
> MAX_DOP für die Arbeitsauslastungsgruppe überschreibt die [Serverkonfiguration des maximalen Grads an Parallelität](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) und den **MAXDOP**-Wert der auf die [Datenbank beschränkten Konfiguration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md).

> [!TIP]
> Verwenden Sie den [Abfragehinweis](../../t-sql/queries/hints-transact-sql-query.md) **MAXDOP**, um dies auf Abfrageebene zu erreichen. Die Festlegung des maximalen Grads an Parallelität als Abfragehinweis gilt, solange der MAX_DOP-Wert der Arbeitsauslastungsgruppe nicht überschritten wird. Wenn der MAXDOP-Wert des Abfragehinweises den von Resource Governor konfigurierten Wert überschreitet, verwendet [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] den `MAX_DOP`-Wert von Resource Governor. Der [Abfragehinweis](../../t-sql/queries/hints-transact-sql-query.md) für MAXDOP überschreibt stets die [Serverkonfiguration des maximalen Grads an Parallelität](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).
>
> Verwenden Sie den **MAXDOP**-Wert der auf die [Datenbank beschränkten Konfiguration](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md), um dies auf Datenbankebene zu erreichen.
>
> Verwenden Sie den **MAXDOP**-Wert (maximaler Parallelitätsgrad) der [Serverkonfigurationsoption](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md), um dies auf Serverebene zu erreichen.

GROUP_MAX_REQUESTS = *value*</br>
Gibt die maximale Anzahl gleichzeitiger Anforderungen an, die in der Arbeitsauslastungsgruppe ausgeführt werden können. *value* muss 0 (null) oder ein positiver Integer sein. Der Standardwert von *value* ist 0 (null) und lässt eine unbegrenzte Anzahl von Anforderungen zu. Wenn die maximale Anzahl gleichzeitiger Anforderungen erreicht wird, kann sich ein Benutzer dieser Gruppe zwar anmelden, wird jedoch in den Wartezustand versetzt, bis die Anzahl gleichzeitiger Anforderungen unter den angegebenen Wert gefallen ist.

USING { *pool_name* |  **"default"** }</br>
Ordnet die Arbeitsauslastungsgruppe dem benutzerdefinierten Ressourcenpool zu, der durch *pool_name* identifiziert wird. Hierdurch wird die Arbeitsauslastungsgruppe im Endeffekt im Ressourcenpool platziert. Wenn *pool_name* nicht bereitgestellt wird oder wenn das USING-Argument nicht verwendet wird, wird die Arbeitsauslastungsgruppe in den vordefinierten Standardpool von Resource Governor eingefügt.

"default" ist ein reserviertes Wort und muss bei der Verwendung mit USING in Anführungszeichen ("") oder Klammern ([]) eingeschlossen werden.

> [!NOTE]
> Für vordefinierte Arbeitsauslastungsgruppen und Ressourcenpools werden ausschließlich kleingeschriebene Namen verwendet, z. B. "default". Dies sollte bei Servern beachtet werden, die bei der Sortierung zwischen Groß-/Kleinschreibung unterscheiden. Server, die bei der Sortierung keine Groß- und Kleinschreibung unterscheiden, z. B. SQL_Latin1_General_CP1_CI_AS, behandeln "default" und "Default" gleich.

EXTERNAL external_pool_name | "default"</br>
**Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]).

Die Arbeitsauslastungsgruppe kann einen externen Ressourcenpool angeben. Sie können eine Arbeitsauslastungsgruppe definieren und zwei Pools zuordnen:

- Ein Ressourcenpool für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Arbeitsauslastungen und Abfragen
- Ein externer Ressourcenpool für externe Prozesse. Weitere Informationen finden Sie unter [sp_execute_external_script &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

## <a name="remarks"></a>Bemerkungen

Wenn `REQUEST_MEMORY_GRANT_PERCENT` verwendet wird, kann die Indexerstellung verwendet werden, um mehr Arbeitsbereichsspeicher als ursprünglich zugewiesen zu verwenden, damit eine bessere Leistung erzielt wird. Diese besondere Behandlung wird von der Ressourcenkontrolle in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] unterstützt. Die Zuweisung anfänglichen und zusätzlichen Arbeitsspeichers wird jedoch durch den Ressourcenpool und die Einstellungen der Arbeitsauslastungsgruppe begrenzt.

Der Grenzwert `MAX_DOP` wird [taskbezogen](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md) festgelegt. Es handelt sich nicht um einen [anforderungs](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)- oder abfragebezogenen Grenzwert. Das bedeutet, dass während einer parallelen Abfrageausführung eine einzelne Abfrage mehrere Tasks erzeugen kann, die einem [Planer](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md) zugeordnet sind. Weitere Informationen finden Sie im [Handbuch zur Thread- und Taskarchitektur](../../relational-databases/thread-and-task-architecture-guide.md).

Wenn `MAX_DOP` verwendet wird und die Abfrage zur Kompilierzeit als seriell markiert ist, kann sie zur Laufzeit nicht wieder in parallel geändert werden, und zwar unabhängig von der Arbeitsauslastungsgruppe oder Serverkonfigurationseinstellung. Nach der Konfiguration von `MAX_DOP` kann dieser Wert nur bei Arbeitsspeicherengpässen verringert werden. Die Neukonfiguration der Arbeitsauslastungsgruppe ist während des Wartens in der Speicherzuweisungs-Warteschlange nicht sichtbar.

### <a name="index-creation-on-a-partitioned-table"></a>Indexerstellung für eine partitionierte Tabelle

Der durch die Indexerstellung für nicht ausgerichtete partitionierte Tabellen belegte Arbeitsspeicher ist proportional zur Anzahl der beteiligten Partitionen. Wenn der insgesamt erforderliche Arbeitsspeicher die Grenze (`REQUEST_MAX_MEMORY_GRANT_PERCENT`) übersteigt, die pro Abfrage von der Resource Governor-Arbeitsauslastungsgruppe festgelegt wurde, kann die Indexerstellung möglicherweise nicht erfolgreich ausgeführt werden. Da die Arbeitsauslastungsgruppe *„default“* Abfragen zulässt, die die pro Abfrage festgelegte Grenze für mindestens erforderlichen Arbeitsspeicher übersteigen, können Benutzer dieselbe Indexerstellung in Arbeitsauslastungsgruppen des Typs *„default“* ausführen. Voraussetzung ist, dass der Ressourcenpool *„default“* über ausreichend Gesamtarbeitsspeicher verfügt, um eine solche Abfrage ausführen zu können.

## <a name="permissions"></a>Berechtigungen

Erfordert die `CONTROL SERVER`-Berechtigung.

## <a name="example"></a>Beispiel

Erstellen Sie eine Arbeitsauslastungsgruppe namens `newReports`, die Resource Governor-Standardeinstellungen verwendet und sich im Resource Governor-Standardpool befindet. Im Beispiel wird der `default`-Pool angegeben, wobei dies jedoch nicht erforderlich ist.

```sql
CREATE WORKLOAD GROUP newReports
WITH
    (REQUEST_MAX_MEMORY_GRANT_PERCENT = 2.5
      , REQUEST_MAX_CPU_TIME_SEC = 100
      , MAX_DOP = 4)    
USING "default" ;
GO
```

## <a name="see-also"></a>Weitere Informationen

- [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)
- [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)
- [CREATE RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-resource-pool-transact-sql.md)
- [ALTER RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)
- [DROP RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)
- [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md)

::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

> ||||
> |---|---|---|
> |[SQL Server](create-workload-group-transact-sql.md?view=sql-server-2017)||[SQL-Datenbank<br />verwaltete Instanz](create-workload-group-transact-sql.md?view=azuresqldb-mi-current)||**_\* Azure Synapse<br />Analytics \*_** &nbsp;||||

&nbsp;

## <a name="azure-synapse-analytics-preview"></a>Azure Synapse Analytics (Vorschauversion)

Erstellt eine Arbeitsauslastungsgruppe Arbeitsauslastungsgruppen sind Container für eine Reihe von Anforderungen und die Grundlage für die Konfiguration der Workloadverwaltung auf einem System. Mit Arbeitsauslastungsgruppen können Sie Ressourcen für die Workloadisolation reservieren und Ressourcen beibehalten, pro Anforderung definieren oder Ausführungsregeln durchsetzen. Sobald die Anweisung abgeschlossen ist, sind die Einstellungen wirksam.

 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

```syntaxsql
CREATE WORKLOAD GROUP group_name
[ WITH
 (  [ MIN_PERCENTAGE_RESOURCE = value ]
  [ [ , ] CAP_PERCENTAGE_RESOURCE = value ]
  [ [ , ] REQUEST_MIN_RESOURCE_GRANT_PERCENT = value ]
  [ [ , ] REQUEST_MAX_RESOURCE_GRANT_PERCENT = value ]
  [ [ , ] IMPORTANCE = { LOW | BELOW_NORMAL | NORMAL | ABOVE_NORMAL | HIGH } ]
  [ [ , ] QUERY_EXECUTION_TIMEOUT_SEC = value ] )
  [ ; ]
]
```

*group_name*</br>
Gibt den Namen an, mit dem die Arbeitsauslastungsgruppe identifiziert werden kann. Der Name *group_name* ist vom Datentyp „sysname“. Dieses Argument kann bis zu 128 Zeichen lang sein und muss innerhalb der Instanz einen eindeutigen Namen haben.

*MIN_PERCENTAGE_RESOURCE* = value</br>
Diese Zeile gibt eine garantierte minimale Ressourcenzuordnung für diese Arbeitsauslastungsgruppe an, die nicht mit anderen Arbeitsauslastungsgruppen geteilt wird. Dabei entspricht *value* einem Integer zwischen 0 und 100. Die Summe von min_percentage_resource darf für alle Auslastungsgruppen nicht 100 überschreiten. Der Wert für min_percentage_resource darf den von cap_percentage_resource nicht übersteigen. Es gibt effektive Mindestwerte, die pro Dienstebene zulässig sind. Weitere Informationen finden Sie unter [Effektive Werte](#effective-values).

*CAP_PERCENTAGE_RESOURCE* = value</br>
Diese Zeile gibt die maximale Ressourcenverwendung für alle Anforderungen in einer Arbeitsauslastungsgruppe an. Der zulässige Integerbereich für value liegt zwischen 1 und 100. Der Wert für cap_percentage_resource muss den von min_percentage_resource übersteigen. Der effektive Wert für cap_percentage_resource kann reduziert werden, wenn min_percentage_resource in anderen Arbeitsauslastungsgruppen auf 0 oder höher festgelegt wird.

*REQUEST_MIN_RESOURCE_GRANT_PERCENT* = value</br>
Diese Zeile legt die Mindestmenge der Ressourcen fest, die pro Anforderung zugeordnet werden. Hierbei ist *value* ein erforderlicher Parameter mit einem Gleitkommawert zwischen 0.75 und 100.00. Der Wert für request_min_resource_grant_percent muss ein Vielfaches von 0,25, ein Faktor von min_percentage_resource und weniger als cap_percentage_resource sein. Es gibt effektive Mindestwerte, die pro Dienstebene zulässig sind. Weitere Informationen finden Sie unter [Effektive Werte](#effective-values).

Beispiel:

```sql
CREATE WORKLOAD GROUP wgSample 
WITH
  ( MIN_PERCENTAGE_RESOURCE = 26                -- integer value
    , REQUEST_MIN_RESOURCE_GRANT_PERCENT = 3.25 -- factor of 26 (guaranteed a minimum of 8 concurrency)
    , CAP_PERCENTAGE_RESOURCE = 100 )
```

Sehen Sie sich die Werte an, die für die Ressourcenklassen als Richtlinie für request_min_resource_grant_percent verwendet werden.  Die folgende Tabelle enthält die Ressourcenzuordnung für Gen2.

|Ressourcenklasse|Ressourcen in Prozent|
|---|---|
|Smallrc|3 %|
|Mediumrc|10 %|
|Largerc|22 %|
|Xlargerc|70 %|
|||

*REQUEST_MAX_RESOURCE_GRANT_PERCENT* = value</br>         
Diese Zeile legt die Maximalmenge der Ressourcen fest, die pro Anforderung zugeordnet werden. Dabei ist *value* ein optionaler Dezimalparameter mit einem Standardwert, der „request_min_resource_grant_percent“ entspricht. Der Wert von *value* muss größer oder gleich „request_min_resource_grant_percent“ sein. Wenn der Wert von request_max_resource_grant_percent größer als request_min_resource_grant_percent ist und Systemressourcen verfügbar sind, werden einer Anforderung zusätzliche Ressourcen zugeordnet.

*IMPORTANCE* = { LOW | BELOW_NORMAL | NORMAL | ABOVE_NORMAL | HIGH }</br>        
Diese Zeile gibt die Standardwichtigkeit einer Anforderung für die Arbeitsauslastungsgruppe an. Für die Wichtigkeit sind folgende Einstellungen möglich, wobei NORMAL die Standardeinstellung ist:

- LOW
- BELOW_NORMAL
- NORMAL (Standard)
- ABOVE_NORMAL
- HIGH

Die Wichtigkeit, die für eine Arbeitsauslastungsgruppe festgelegt wird, entspricht der Standardwichtigkeit für alle Anforderungen in der Arbeitsauslastungsgruppe. Benutzer können die Wichtigkeit auch auf Klassifizierungsebene festlegen und somit die festgelegte Wichtigkeit der Arbeitsauslastungsgruppe überschreiben. Dadurch wird eine Differenzierung der Wichtigkeit für Anforderungen innerhalb einer Arbeitsauslastungsgruppe ermöglicht, um schneller auf nicht reservierte Ressourcen zugreifen zu können. Wenn die Summe von min_percentage_resource in den Arbeitsauslastungsgruppen weniger als 100 ist, sind nicht reservierte Ressourcen vorhanden, die nach Wichtigkeit zugewiesen werden.

*QUERY_EXECUTION_TIMEOUT_SEC* = value</br>     
Diese Zeile gibt die maximale Zeit in Sekunden an, für deren Dauer eine Abfrage ausgeführt werden kann, bevor sie abgebrochen wird. *value* muss 0 (null) oder ein positiver Integer sein. Die Standardeinstellung für value ist 0 (null). Das bedeutet, dass für die Abfrage kein Timeout eintritt. QUERY_EXECUTION_TIMEOUT_SEC zählt, sobald die Abfrage als ausgeführt erkannt wird, nicht jedoch, wenn die Abfrage in die Warteschlange eingereiht wird.

## <a name="remarks"></a>Bemerkungen

Die entsprechenden Arbeitsauslastungsgruppen für Ressourcenklassen werden aufgrund der Abwärtskompatibilität automatisch generiert. Diese vom System definierten Arbeitsauslastungsgruppen können nicht gelöscht werden. Es können acht zusätzliche benutzerdefinierte Arbeitsauslastungsgruppen erstellt werden.

Wenn eine Arbeitsauslastungsgruppe mit `min_percentage_resource` größer als 0 (null) erstellt wird, wird die `CREATE WORKLOAD GROUP`-Anweisung in die Warteschlange eingereiht, bis genügend Ressourcen zum Erstellen der Arbeitsauslastungsgruppe vorhanden sind.

## <a name="effective-values"></a>Effektive Werte

Die Parameter `min_percentage_resource`, `cap_percentage_resource`, `request_min_resource_grant_percent` und `request_max_resource_grant_percent` haben effektive Werte, die basierend auf dem aktuellen Servicelevel und der Konfiguration anderer Arbeitsauslastungsgruppen angepasst werden.

Der `request_min_resource_grant_percent`-Parameter hat einen effektiven Wert, da je nach Servicelevel minimale Ressourcen pro Abfrage benötigt werden.  Beispielsweise sind auf dem niedrigsten Servicelevel (DW100c) mindestens 25 % der Ressourcen pro Anforderung erforderlich.  Wenn die Workloadgruppe mit 3 % `request_min_resource_grant_percent` und `request_max_resource_grant_percent` konfiguriert ist, passen sich die effektiven Werte für beide Parameter auf 25 % an, wenn die Instanz gestartet wird.  Wenn die Instanz zu DW1000c hochskaliert wird, sind die konfigurierten und effektiven Werte für beide Parameter 3 %, da 3 % der unterstützte Mindestwert für diesen Servicelevel ist.  Wenn die Instanz höher als DW1000c skaliert wird, bleiben die konfigurierten und effektiven Werte für beide Parameter bei 3 %.  In der folgenden Tabelle finden Sie weitere Informationen zu effektiven Werten bei verschiedenen Servicelevels.

|Dienstebene|Niedrigster effektiver Wert für REQUEST_MIN_RESOURCE_GRANT_PERCENT|Maximale Anzahl gleichzeitiger Abfragen|
|---|---|---|
|DW100c|25 %|4|
|DW200c|12,5 %|8|
|DW300c|8 %|12|
|DW400c|6,25 %|16|
|DW500c|5 %|20|
|DW1000c|3 %|32|
|DW1500c|3 %|32|
|DW2000c|2 %|48|
|DW2500c|2 %|48|
|DW3000c|1,5 %|64|
|DW5000c|1,5 %|64|
|DW6000c|0,75 %|128|
|DW7500c|0,75 %|128|
|DW10000c|0,75 %|128|
|DW15000c|0,75 %|128|
|DW30000c|0,75 %|128|
||||

Der `min_percentage_resource`-Parameter muss größer oder gleich dem effektiven `request_min_resource_grant_percent` sein. Bei einer Workloadgruppe, deren Wert für `min_percentage_resource` kleiner als der effektive Wert von `min_percentage_resource` ist, wird der Wert zur Laufzeit auf 0 (null) angepasst. In diesem Fall sind die für `min_percentage_resource` konfigurierten Ressourcen für alle Arbeitsauslastungsgruppen freigegeben. Beispielsweise hätte die Workloadgruppe `wgAdHoc` mit einem Wert für `min_percentage_resource` von 10 % unter DW1000c einen effektiven Wert für `min_percentage_resource` von 10 % (3 % ist der Mindestwert bei DW1000c). Bei DW100c hätte `wgAdhoc` einen effektiven Wert für min_percentage_resource von 0 %. Die für `wgAdhoc` konfigurierten 10 % würden für alle Arbeitsauslastungsgruppen freigegeben werden.

Der Parameter `cap_percentage_resource` hat ebenfalls einen effektiven Wert. Wenn eine Arbeitsauslastungsgruppe `wgAdhoc` mit einem Wert von 100 % für `cap_percentage_resource` konfiguriert wird und eine andere Arbeitsauslastungsgruppe `wgDashboards` mit einem Wert von 25 % für `min_percentage_resource`, wird der effektive Wert von `cap_percentage_resource` für `wgAdhoc` 75 %.

Die Laufzeitwerte für Ihre Arbeitsauslastungsgruppe lassen sich am einfachsten erklären, indem Sie die Systemsicht [sys.dm_workload_management_workload_groups_stats](../../relational-databases/system-dynamic-management-views/sys-dm-workload-management-workload-group-stats-transact-sql.md) abfragen.

## <a name="permissions"></a>Berechtigungen

Erfordert die `CONTROL DATABASE`-Berechtigung

## <a name="see-also"></a>Weitere Informationen

- [DROP WORKLOAD GROUP (Transact-SQL)](drop-workload-group-transact-sql.md)
- [sys.workload_management_workload_groups](../../relational-databases/system-catalog-views/sys-workload-management-workload-groups-transact-sql.md)
- [sys.dm_workload_management_workload_groups_stats](../../relational-databases/system-dynamic-management-views/sys-dm-workload-management-workload-group-stats-transact-sql.md)
- Schnellstart zum Erstellen und Verwenden einer [Arbeitsauslastungsgruppe](https://docs.microsoft.com/azure/sql-data-warehouse/quickstart-configure-workload-isolation-tsql)

::: moniker-end
