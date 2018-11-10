---
title: Verwenden von WQL mit dem WMI-Anbieter für Serverereignisse | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: dde7806e0485bc46ca9b9869e8856836006b9032
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51216288"
---
# <a name="using-wql-with-the-wmi-provider-for-server-events"></a>Verwenden von WQL mit dem WMI-Anbieter für Serverereignisse
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Verwaltungsanwendungen greifen über den WMI-Anbieter für Serverereignisse auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu, indem sie WQL-Anweisungen (WMI Query Language) ausgeben. WQL ist eine vereinfachte Teilmenge von Structured Query Language (SQL) mit einigen WMI-spezifischen Erweiterungen. Unter Verwendung von WQL ruft eine Anwendung einen Ereignistyp aus einer spezifischen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], einer Datenbank oder einem Datenbankobjekt ab. Das einzige zurzeit unterstützte Objekt ist queue. WMI-Anbieter für Serverereignisse übersetzt die Abfrage in eine ereignisbenachrichtigung, die in der Zieldatenbank für ereignisbenachrichtigungen im Serverbereich oder im Bereich einer Objekt oder in erstellt haben, wird die **master** Datenbank für das Ereignis mit Serverbereich Benachrichtigungen.  
  
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
  
 Das Argument in der `FROM`-Klausel der WQL-Abfrage (`DDL_DATABASE_LEVEL_EVENTS`) kann ein beliebiges gültiges Ereignis sein, für das eine Ereignisbenachrichtigung erstellt werden kann. Für die Argumente in den Klauseln `SELECT` und `WHERE` können beliebige Ereigniseigenschaften angegeben werden, die mit einem Ereignis oder dessen übergeordnetem Ereignis verbunden sind. Eine Liste der gültigen Ereignisse und Ereigniseigenschaften finden Sie unter [Ereignisbenachrichtigungen (Datenbankmodul)](http://technet.microsoft.com/library/ms182602.aspx).  
  
 Die folgende WQL-Syntax wird explizit vom WMI-Anbieter für Serverereignisse unterstützt. Zusätzliche WQL-Syntaxelemente können angegeben werden; sie sind jedoch nicht anbieterspezifisch für diesen Anbieter, sondern werden stattdessen vom WMI-Hostdienst analysiert. Weitere Informationen zur WMI Query Language finden Sie in der WQL-Dokumentation im Microsoft Developer Network (MSDN).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT { event_property [ ,...n ] | * }  
FROM event_type   
WHERE where_condition   
```  
  
## <a name="arguments"></a>Argumente  
 *event_property*  
 Eine Ereigniseigenschaft. Beispiele hierfür sind **PostTime**, **SPID**, und **LoginName**. Jedes Ereignis in aufgeführten Nachschlagen [WMI-Anbieter für Server Ereignisklassen und Eigenschaften](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md) bestimmen, welche Eigenschaften enthält. Das DDL_DATABASE_LEVEL_EVENTS-Ereignis enthält z. B. die **DatabaseName** und **Benutzername** Eigenschaften. Es erbt außerdem die **SQLInstance**, **LoginName**, **PostTime**, **SPID**, und **ComputerName** Eigenschaften von den jeweils übergeordneten Ereignissen.  
  
 **,** *.. ...n*  
 Gibt an, dass *Event_property* können mehrmals abgefragt werden, durch Kommas getrennt.  
  
 \*  
 Gibt an, dass alle einem Ereignis zugeordneten Eigenschaften abgefragt werden.  
  
 *event_type*  
 Jedes Ereignis, für das eine Ereignisbenachrichtigung erstellt werden kann. Eine Liste der verfügbaren Ereignisse, finden Sie unter [WMI-Anbieter für Server Ereignisklassen und Eigenschaften](http://technet.microsoft.com/library/ms186449.aspx). Beachten Sie, dass *Ereignistyp* Namen entsprechen, auf die gleiche *Event_type* | *Event_group* angegeben werden kann. Wenn Sie manuell eine ereignisbenachrichtigung erstellen. Mithilfe der CREATE EVENT NOTIFICATION. Beispiele für *Ereignistyp* sind CREATE_TABLE, LOCK_DEADLOCK, DDL_USER_EVENTS und TRC_DATABASE.  
  
> [!NOTE]  
>  Bestimmte gespeicherte Systemprozeduren, die DDL-ähnliche Vorgänge ausführen, können auch Ereignisbenachrichtigungen auslösen. Testen Sie die Ereignisbenachrichtigungen, um ihre Reaktion auf gespeicherte Systemprozeduren, die ausgeführt werden, zu bestimmen. Beispielsweise die CREATE TYPE-Anweisung und **Sp_addtype** gespeicherte Prozedur wird sowohl ausgelöst, eine ereignisbenachrichtigung, die für ein CREATE_TYPE-Ereignis erstellt wird. Allerdings die **Sp_rename** gespeicherte Prozedur wird nicht ausgelöst, keine ereignisbenachrichtigungen. Weitere Informationen finden Sie unter[DDL-Ereignisse](../../relational-databases/triggers/ddl-events.md).  
  
 *where_condition*  
 Ist eine WHERE-Klausel-Prädikat zusammen *Event_property* Namen und logischen Operatoren und Vergleichsoperatoren. Die *Where_condition* bestimmt den Bereich, in dem die entsprechende ereignisbenachrichtigung in der Zieldatenbank registriert ist. Es kann auch als Filter, um ein bestimmtes Schema oder Objekt aus der Abfrage als Ziel fungieren *Event_type.* Weitere Informationen finden Sie im Abschnitt mit den Hinweisen weiter unten in diesem Thema.  
  
 Nur die `=` Operand kann verwendet werden, zusammen mit **DatabaseName**, **SchemaName**, und **ObjectName**. Andere Ausdrücke können nicht mit diesen Ereigniseigenschaften verwendet werden.  
  
## <a name="remarks"></a>Hinweise  
 Die *Where_condition* des WMI-Anbieters für Serverereignisse bestimmt die Syntax Folgendes:  
  
-   Der Bereich, der mit dem versucht der Anbieter die angegebenen abzurufenden *Event_type*: die Serverebene, Datenbankebene oder Objektebene (das einzige zurzeit unterstützte Objekt ist Warteschlange). Letztlich bestimmt dieser Bereich den Typ der in der Zieldatenbank erstellten Ereignisbenachrichtigung. Dieser Prozess wird Ereignisbenachrichtigungsregistrierung genannt.  
  
-   Die Datenbank, das Schema und das Objekt, auf der/dem registriert werden soll.  
  
 Der WMI-Anbieter für Serverereignisse verwendet einen Algorithmus, der von unten nach oben arbeitet und die erstbestmögliche Lösung benutzt, um den engstmöglichen Gültigkeitsbereich für das zugrunde liegende EVENT NOTIFICATION-Argument anzuwenden. Der Algorithmus versucht, die interne Aktivität auf dem Server und bezüglich des Netzwerkverkehrs zwischen der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und dem WMI-Hostprozess zu reduzieren. Der Anbieter untersucht den *Event_type* in der FROM-Klausel und die Bedingungen der WHERE-Klausel angegeben, und versucht, die zugrunde liegende EVENT NOTIFICATION mit dem engsten Gültigkeitsbereich zu registrieren. Wenn der Anbieter sich nicht im engsten Gültigkeitsbereich registrieren kann, versucht er eine Registrierung in höheren Gültigkeitsbereichen, bis schließlich eine Registrierung erfolgreich ist. Wenn der höchste Bereich auf Serverebene erreicht ist und keine Registrierung zustande kam, wird dem Consumer ein Fehler zurückgegeben.  
  
 Z. B. wenn DatabaseName =**"** AdventureWorks **"** angegeben ist, in der WHERE-Klausel, versucht der Anbieter registrieren Sie eine ereignisbenachrichtigung in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] Datenbank. Wenn die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank vorhanden ist und der aufrufende Client über die erforderlichen Berechtigungen zum Erstellen einer Ereignisbenachrichtigung in [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]verfügt, ist die Registrierung erfolgreich. Andernfalls wird versucht, die Ereignisbenachrichtigung auf Serverebene zu registrieren. Die Registrierung ist erfolgreich, wenn der WMI-Client die erforderlichen Berechtigungen hat. In diesem Szenario werden Ereignisse jedoch so lange nicht an den Client zurückgegeben, bis die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank erstellt wurde.  
  
 Die *Where_condition* kann auch als Filter, um die Abfrage, um eine bestimmte Datenbank, Schema oder Objekt darüber zu beschränken. Betrachten Sie beispielsweise folgende WQL-Abfrage:  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
 Abhängig vom Ergebnis des Registrierungsprozesses kann diese WQL-Abfrage entweder auf Datenbank- oder auf Serverebene registriert werden. Auch wenn sie auf Serverebene registriert ist, filtert der Anbieter schließlich alle `ALTER_TABLE`-Ereignisse, die nicht auf die `AdventureWorks.Sales.SalesOrderDetail`-Tabelle zutreffen. Mit anderen Worten gibt der Anbieter nur die Eigenschaften der `ALTER_TABLE`-Ereignisse zurück, die in dieser Tabelle vorkommen.  
  
 Wird ein zusammengesetzter Ausdruck wie beispielsweise `DatabaseName='AW1'`OR`DatabaseName='AW2'` angegeben, wird versucht, statt zwei Ereignisbenachrichtigungen nur eine einzige Ereignisbenachrichtigung im Servergültigkeitsbereich zu registrieren. Die Registrierung ist erfolgreich, wenn der aufrufende Client die erforderlichen Berechtigungen hat.  
  
 Wenn `SchemaName='X' AND ObjectType='Y' AND ObjectName='Z'` angegeben werden die `WHERE` -Klausel, es wird versucht, die ereignisbenachrichtigung direkt für Objekt registrieren `Z` im Schema `X`. Die Registrierung ist erfolgreich, wenn der Client die erforderlichen Berechtigungen hat. Beachten Sie, dass derzeit auf Objektebene Ereignisse nur in Warteschlangen und nur für den QUEUE_ACTIVATION unterstützt werden *Event_type*.  
  
 Beachten Sie, dass nicht bei allen Ereignissen ein bestimmter Gültigkeitsbereich abgefragt werden kann. Beispielsweise können die WQL-Abfrage für ein Ablaufverfolgungsereignis wie Lock_Deadlock oder eine Ablaufverfolgungsereignisgruppe wie TRC_LOCKS nur auf Serverebene registriert werden. Auch das CREATE_ENDPOINT-Ereignis und das DDL_ENDPOINT_EVENTS-Ereignis können nur auf Serverebene registriert werden. Weitere Informationen zu den entsprechenden Aufgabenbereich für das Registrieren von Ereignissen, finden Sie unter [Entwerfen von Ereignisbenachrichtigungen](http://technet.microsoft.com/library/ms175854\(v=sql.105\).aspx). Versuch, eine WQL registrieren Abfragen, deren *Event_type* können nur registriert werden auf dem Server wird immer auf Ebene des Servers hergestellt. Die Registrierung ist erfolgreich, wenn der WMI-Client die erforderlichen Berechtigungen hat. Andernfalls wird an den Client ein Fehler zurückgegeben. In bestimmten Fällen können Sie, abhängig von den Eigenschaften des Ereignisses, die WHERE-Klausel jedoch trotzdem als Filter für serverbasierte Ereignisse verwenden. Beispielsweise weisen zahlreiche Ablaufverfolgungsereignisse eine **DatabaseName** -Eigenschaft, die in der WHERE-Klausel als Filter verwendet werden kann.  
  
 Serverbezogene ereignisbenachrichtigungen werden erstellt, der **master** Datenbank und kann für Metadaten abgefragt werden, mithilfe der [server_event_notifications](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md) -Katalogsicht angezeigt.  
  
 Bereich der Datenbank oder Objekt ereignisbenachrichtigungen werden in der angegebenen Datenbank erstellt und können nach Metadaten abgefragt werden, mithilfe der [Sys. event_notifications](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md) -Katalogsicht angezeigt. (Sie müssen der Katalogsicht den entsprechenden Datenbanknamen als Präfix hinzufügen.)  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [WMI-Anbieter für Ereignisse Serverkonzepte](http://technet.microsoft.com/library/ms180560.aspx)   
 [Ereignisbenachrichtigungen (Datenbank-Engine)](http://technet.microsoft.com/library/ms182602.aspx)  
  
  
