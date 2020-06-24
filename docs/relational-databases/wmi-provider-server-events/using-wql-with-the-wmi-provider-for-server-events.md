---
title: Verwenden von WQL mit dem WMI-Anbieter für Serverereignisse
description: Erfahren Sie, wie Verwaltungs Anwendungen auf SQL Server Ereignisse mithilfe des WMI-Anbieters für Server Ereignisse zugreifen, indem Sie WMI-Abfragesprache-Anweisungen ausgeben.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Server Events, WQL
ms.assetid: 58b67426-1e66-4445-8e2c-03182e94c4be
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e6fae362d3a8d1fe387dd7561b1476bb37f0c255
ms.sourcegitcommit: bf5e9cb3a2caa25d0a37f401b3806b7baa5adea8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85295383"
---
# <a name="using-wql-with-the-wmi-provider-for-server-events"></a>Verwenden von WQL mit dem WMI-Anbieter für Serverereignisse
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Verwaltungsanwendungen greifen über den WMI-Anbieter für Serverereignisse auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu, indem sie WQL-Anweisungen (WMI Query Language) ausgeben. WQL ist eine vereinfachte Teilmenge von Structured Query Language (SQL) mit einigen WMI-spezifischen Erweiterungen. Unter Verwendung von WQL ruft eine Anwendung einen Ereignistyp aus einer spezifischen Instanz von , einer Datenbank oder einem Datenbankobjekt ab. Das einzige zurzeit unterstützte Objekt ist queue. Der WMI-Anbieter für Server Ereignisse übersetzt die Abfrage in eine Ereignis Benachrichtigung, die in der Zieldatenbank für Ereignis Benachrichtigungen mit Daten Bankbereich oder Objektbereich oder in der **Master** Datenbank für Ereignis Benachrichtigungen auf Server Ebene erstellt wird.  
  
 Betrachten Sie beispielsweise folgende WQL-Abfrage:  
  
```  
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS WHERE DatabaseName = 'AdventureWorks'  
```  
  
 Ausgehend von dieser Abfrage versucht der WMI-Anbieter, ein Äquivalent dieser Ereignisbenachrichtigung auf dem Zielserver zu produzieren:  
  
```  
USE AdventureWorks ;  
GO  
  
CREATE EVENT NOTIFICATION SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9  
    ON DATABASE  
    WITH FAN_IN  
    FOR DDL_DATABASE_LEVEL_EVENTS  
    TO SERVICE   
        'SQL/Notifications/ProcessWMIEventProviderNotification/v1.0',  
        'A7E5521A-1CA6-4741-865D-826F804E5135';  
GO  
```  
  
 Das Argument in der `FROM`-Klausel der WQL-Abfrage (`DDL_DATABASE_LEVEL_EVENTS`) kann ein beliebiges gültiges Ereignis sein, für das eine Ereignisbenachrichtigung erstellt werden kann. Für die Argumente in den Klauseln `SELECT` und `WHERE` können beliebige Ereigniseigenschaften angegeben werden, die mit einem Ereignis oder dessen übergeordnetem Ereignis verbunden sind. Eine Liste der gültigen Ereignisse und Ereignis Eigenschaften finden Sie unter [Ereignis Benachrichtigungen (Datenbank-Engine)](https://technet.microsoft.com/library/ms182602.aspx).  
  
 Die folgende WQL-Syntax wird explizit vom WMI-Anbieter für Serverereignisse unterstützt. Zusätzliche WQL-Syntaxelemente können angegeben werden; sie sind jedoch nicht anbieterspezifisch für diesen Anbieter, sondern werden stattdessen vom WMI-Hostdienst analysiert. Weitere Informationen zur WMI Query Language finden Sie in der WQL-Dokumentation im Microsoft Developer Network (MSDN).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT { event_property [ ,...n ] | * }  
FROM event_type   
WHERE where_condition   
```  
  
## <a name="arguments"></a>Argumente  
 *event_property*  
 Eine Ereigniseigenschaft. Beispiele hierfür sind **PostTime**, **SPID**und **LoginName**. Suchen Sie jedes in den [Klassen und Eigenschaften des WMI-Anbieters für Server Ereignisse](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md) aufgeführte Ereignis, um zu bestimmen, welche Eigenschaften es enthält. Das DDL_DATABASE_LEVEL_EVENTS-Ereignis enthält z. b. die Eigenschaften **DatabaseName** und **username** . Außerdem erbt Sie die Eigenschaften **SQLInstance**, **LoginName**, **PostTime**, **SPID**und **Computername** von den übergeordneten Ereignissen.  
  
 **,** *... n*  
 Gibt an, dass *event_property* mehrmals abgefragt werden können, getrennt durch Kommas.  
  
 \*  
 Gibt an, dass alle einem Ereignis zugeordneten Eigenschaften abgefragt werden.  
  
 *event_type*  
 Jedes Ereignis, für das eine Ereignisbenachrichtigung erstellt werden kann. Eine Liste der verfügbaren Ereignisse finden Sie unter [Klassen und Eigenschaften für den WMI-Anbieter für Server Ereignisse](https://technet.microsoft.com/library/ms186449.aspx). Beachten Sie, dass *Ereignistyp* Namen denselben *event_type*  |  *event_group* entsprechen, die angegeben werden können, wenn Sie eine Ereignis Benachrichtigung mithilfe von CREATE Event Notification manuell erstellen. Beispiele für *Ereignistyp* sind CREATE_TABLE, LOCK_DEADLOCK, DDL_USER_EVENTS und TRC_DATABASE.  
  
> [!NOTE]  
>  Bestimmte gespeicherte Systemprozeduren, die DDL-ähnliche Vorgänge ausführen, können auch Ereignisbenachrichtigungen auslösen. Testen Sie die Ereignisbenachrichtigungen, um ihre Reaktion auf gespeicherte Systemprozeduren, die ausgeführt werden, zu bestimmen. Beispielsweise lösen die CREATE TYPE-Anweisung und die gespeicherte Prozedur **sp_addtype** eine Ereignis Benachrichtigung aus, die für ein CREATE_TYPE-Ereignis erstellt wird. Allerdings werden von der gespeicherten Prozedur **sp_rename** keine Ereignis Benachrichtigungen ausgelöst. Weitere Informationen finden Sie unter[DDL-Ereignisse](../../relational-databases/triggers/ddl-events.md).  
  
 *where_condition*  
 Ein WHERE-Klausel-Abfrage Prädikat, das aus *event_property* Namen und logischen Operatoren und Vergleichs Operatoren besteht. Der- *where_condition* bestimmt den Bereich, in dem die entsprechende Ereignis Benachrichtigung in der Zieldatenbank registriert wird. Sie kann auch als Filter fungieren, um auf ein bestimmtes Schema oder Objekt zu abzielen, von dem event_type abgefragt werden soll *.* Weitere Informationen finden Sie im Abschnitt mit den Hinweisen weiter unten in diesem Thema.  
  
 Nur der `=` Operand kann mit **DatabaseName**, Schema Name und **SchemaName** **objectName**verwendet werden. Andere Ausdrücke können nicht mit diesen Ereigniseigenschaften verwendet werden.  
  
## <a name="remarks"></a>Hinweise  
 Die *where_condition* der Syntax des WMI-Anbieters für Server Ereignisse bestimmt Folgendes:  
  
-   Der Bereich, in dem der Anbieter versucht, die angegebene *event_type*abzurufen: Serverebene, Datenbankebene oder Objektebene (das einzige derzeit unterstützte Objekt ist Queue). Letztlich bestimmt dieser Bereich den Typ der in der Zieldatenbank erstellten Ereignisbenachrichtigung. Dieser Prozess wird Ereignisbenachrichtigungsregistrierung genannt.  
  
-   Die Datenbank, das Schema und das Objekt, auf der/dem registriert werden soll.  
  
 Der WMI-Anbieter für Serverereignisse verwendet einen Algorithmus, der von unten nach oben arbeitet und die erstbestmögliche Lösung benutzt, um den engstmöglichen Gültigkeitsbereich für das zugrunde liegende EVENT NOTIFICATION-Argument anzuwenden. Der Algorithmus versucht, die interne Aktivität auf dem Server und bezüglich des Netzwerkverkehrs zwischen der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und dem WMI-Hostprozess zu reduzieren. Der Anbieter überprüft das in der from-Klausel angegebene *event_type* und die Bedingungen in der WHERE-Klausel und versucht, die zugrunde liegende Ereignis Benachrichtigung mit dem engsten Gültigkeitsbereich zu registrieren. Wenn der Anbieter sich nicht im engsten Gültigkeitsbereich registrieren kann, versucht er eine Registrierung in höheren Gültigkeitsbereichen, bis schließlich eine Registrierung erfolgreich ist. Wenn der höchste Bereich auf Serverebene erreicht ist und keine Registrierung zustande kam, wird dem Consumer ein Fehler zurückgegeben.  
  
 Wenn beispielsweise DatabaseName =**'** AdventureWorks **'** in der WHERE-Klausel angegeben ist, versucht der Anbieter, eine Ereignis Benachrichtigung in der Datenbank zu registrieren [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . Wenn die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank vorhanden ist und der aufrufende Client über die erforderlichen Berechtigungen zum Erstellen einer Ereignisbenachrichtigung in [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]verfügt, ist die Registrierung erfolgreich. Andernfalls wird versucht, die Ereignisbenachrichtigung auf Serverebene zu registrieren. Die Registrierung ist erfolgreich, wenn der WMI-Client die erforderlichen Berechtigungen hat. In diesem Szenario werden Ereignisse jedoch so lange nicht an den Client zurückgegeben, bis die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank erstellt wurde.  
  
 Der *where_condition* kann auch als Filter fungieren, um die Abfrage zusätzlich auf eine bestimmte Datenbank, ein bestimmtes Schema oder ein bestimmtes Objekt zu beschränken. Betrachten Sie beispielsweise folgende WQL-Abfrage:  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
 Abhängig vom Ergebnis des Registrierungsprozesses kann diese WQL-Abfrage entweder auf Datenbank- oder auf Serverebene registriert werden. Auch wenn sie auf Serverebene registriert ist, filtert der Anbieter schließlich alle `ALTER_TABLE`-Ereignisse, die nicht auf die `AdventureWorks.Sales.SalesOrderDetail`-Tabelle zutreffen. Mit anderen Worten gibt der Anbieter nur die Eigenschaften der `ALTER_TABLE`-Ereignisse zurück, die in dieser Tabelle vorkommen.  
  
 Wird ein zusammengesetzter Ausdruck wie beispielsweise `DatabaseName='AW1'`OR`DatabaseName='AW2'` angegeben, wird versucht, statt zwei Ereignisbenachrichtigungen nur eine einzige Ereignisbenachrichtigung im Servergültigkeitsbereich zu registrieren. Die Registrierung ist erfolgreich, wenn der aufrufende Client die erforderlichen Berechtigungen hat.  
  
 Wenn `SchemaName='X' AND ObjectType='Y' AND ObjectName='Z'` alle in der-Klausel angegeben sind `WHERE` , wird versucht, die Ereignis Benachrichtigung direkt für ein Objekt `Z` im Schema zu registrieren `X` . Die Registrierung ist erfolgreich, wenn der Client die erforderlichen Berechtigungen hat. Beachten Sie, dass Ereignisse auf Objektebene derzeit nur für Warteschlangen und nur für die QUEUE_ACTIVATION *event_type*unterstützt werden.  
  
 Beachten Sie, dass nicht bei allen Ereignissen ein bestimmter Gültigkeitsbereich abgefragt werden kann. Beispielsweise können die WQL-Abfrage für ein Ablaufverfolgungsereignis wie Lock_Deadlock oder eine Ablaufverfolgungsereignisgruppe wie TRC_LOCKS nur auf Serverebene registriert werden. Auch das CREATE_ENDPOINT-Ereignis und das DDL_ENDPOINT_EVENTS-Ereignis können nur auf Serverebene registriert werden. Weitere Informationen zum entsprechenden Bereich für das Registrieren von Ereignissen finden Sie unter [Entwerfen von Ereignis Benachrichtigungen](https://technet.microsoft.com/library/ms175854\(v=sql.105\).aspx). Der Versuch, eine WQL-Abfrage zu registrieren, deren *event_type* nur auf Serverebene registriert werden kann, erfolgt immer auf Serverebene. Die Registrierung ist erfolgreich, wenn der WMI-Client die erforderlichen Berechtigungen hat. Andernfalls wird an den Client ein Fehler zurückgegeben. In bestimmten Fällen können Sie, abhängig von den Eigenschaften des Ereignisses, die WHERE-Klausel jedoch trotzdem als Filter für serverbasierte Ereignisse verwenden. Viele Ablauf Verfolgungs Ereignisse verfügen z. b. über eine **DatabaseName** -Eigenschaft, die in der WHERE-Klausel als Filter verwendet werden kann.  
  
 Ereignis Benachrichtigungen im Server Bereich werden in der **Master** -Datenbank erstellt und können mithilfe der [sys. server_event_notifications](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md) -Katalog Sicht für Metadaten abgefragt werden.  
  
 Ereignis Benachrichtigungen mit Daten Bankbereich oder Objektbereich werden in der angegebenen Datenbank erstellt und können mithilfe der [sys. event_notifications](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md) -Katalog Sicht für Metadaten abgefragt werden. (Sie müssen der Katalogsicht den entsprechenden Datenbanknamen als Präfix hinzufügen.)  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-querying-for-events-at-the-server-scope"></a>A. Abfragen von Ereignissen im Serverbereich  
 Die folgende WQL-Abfrage ruft alle Ereigniseigenschaften für alle `SERVER_MEMORY_CHANGE`-Ablaufverfolgungsereignisse ab, die in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auftreten.  
  
```  
SELECT * FROM SERVER_MEMORY_CHANGE  
```  
  
### <a name="b-querying-for-events-at-the-database-scope"></a>B. Abfragen von Ereignissen im Datenbankbereich  
 Die folgende WQL-Abfrage ruft bestimmte Ereigniseigenschaften für alle Ereignisse ab, die in der `AdventureWorks`-Datenbank auftreten und in der `DDL_DATABASE_LEVEL_EVENTS`-Ereignisgruppe existieren.  
  
```  
SELECT SPID, SQLInstance, DatabaseName FROM DDL_DATABASE_LEVEL_EVENTS   
WHERE DatabaseName = 'AdventureWorks'   
```  
  
### <a name="c-querying-for-events-at-the-database-scope-filtering-by-schema-and-object"></a>C. Abfragen von Ereignissen im Datenbankbereich mit Filtern nach Schema und Objekt  
 Die folgende Abfrage ruft alle Ereigniseigenschaften für alle `ALTER_TABLE`-Ereignisse ab, die in der Tabelle `AdventureWorks.Sales.SalesOrderDetail` auftreten.  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konzepte des WMI-Anbieters für Server Ereignisse](https://technet.microsoft.com/library/ms180560.aspx)   
 [Ereignisbenachrichtigung (Datenbank-Engine)](https://technet.microsoft.com/library/ms182602.aspx)  
  
  
