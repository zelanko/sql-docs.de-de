---
title: Arbeiten mit Abfragebenachrichtigungen | Microsoft-Dokumentation
description: Arbeiten mit Abfragebenachrichtigungen im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], query notifications
- rowsets [SQL Server], notifications
- OLE DB Driver for SQL Server, query notifications
- notifications [OLE DB Driver for SQL Server]
- query notifications [SQL Server], OLE DB Driver for SQL Server
- canceling rowset changes
- IRowsetNotify interface
- MSOLEDBSQL, query notifications
- OLE DB Driver for SQL Server, query notifications
- consumer notification for rowset changes [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 29aaab523b3a754c65b1b7a0312ceb5ea122f2d3
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68419317"
---
# <a name="working-with-query-notifications"></a>Arbeiten mit Abfragebenachrichtigungen

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Abfragebenachrichtigungen wurden in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und im OLE DB-Treiber für SQL Server eingeführt. Mit Abfragebenachrichtigungen, die auf der in SQL Server 2005 (9.x) eingeführten Service Broker-Infrastruktur basieren, können Anwendungen benachrichtigt werden, wenn sich Daten ändern. Dieses Feature ist besonders nützlich für Anwendungen, die einen Informationscache aus einer Datenbank (z. B. eine Webanwendung) zur Verfügung stellen und die benachrichtigt werden müssen, wenn die Quelldaten geändert werden.

Mit Abfragebenachrichtigungen können Sie Benachrichtigungen innerhalb eines festgelegten Timeoutzeitraums anfordern, wenn sich die einer Abfrage zugrunde liegenden Daten ändern. In der Anforderung werden die Benachrichtigungsoptionen angegeben. Dazu gehören der Dienstname, der Meldungstext und der Timeoutwert für den Server. Benachrichtigungen werden über eine Service Broker-Warteschlange übermittelt, aus der Anwendungen verfügbare Benachrichtigungen abrufen können.

Die Syntax der Zeichenfolge für die Abfragebenachrichtigungsoptionen lautet:

`service=<service-name>[;(local database=<database> | broker instance=<broker instance>)]`

 Beispiel:

`service=mySSBService;local database=mydb`

Benachrichtigungsabonnements überdauern den Prozess, mit dem sie initiiert werden. Dies liegt daran, dass eine Anwendung ein Benachrichtigungsabonnement erstellen und dann beenden kann. Das Abonnement bleibt gültig, und die Benachrichtigung wird gesendet, wenn die Daten innerhalb des Timeoutzeitraums geändert werden, der bei der Erstellung des Abonnements angegeben wurde. Eine Benachrichtigung wird durch die ausgeführte Abfrage, die Benachrichtigungsoptionen und den Meldungstext identifiziert. Sie können sie abbrechen, indem Sie den Timeoutwert auf 0 (null) festlegen.

Benachrichtigungen werden nur einmal gesendet. Um kontinuierlich bei Datenänderungen benachrichtigt zu werden, erstellen Sie ein neues Abonnement, indem Sie die Abfrage nach der Verarbeitung jeder Benachrichtigung erneut ausführen.

OLE DB-Treiber für SQL Server-Anwendungen empfangen normalerweise Benachrichtigungen mit dem Befehl [!INCLUDE[tsql](../../../includes/tsql-md.md)] [RECEIVE](../../../t-sql/statements/receive-transact-sql.md). Dieser Befehl wird verwendet, um Benachrichtigungen aus der Warteschlange zu lesen, die dem in den Benachrichtigungsoptionen angegebenen Dienst zugeordnet ist.

> [!NOTE]
> Tabellennamen müssen in Abfragen angegeben werden, für die Benachrichtigungen erforderlich sind. Beispiel: `dbo.myTable`. Die Tabellennamen müssen aus zwei Teilen bestehen. Das Abonnement ist ungültig, wenn drei oder vier Teilnamen verwendet werden.

Die Benachrichtigungsinfrastruktur setzt auf einer in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführten Queuing-Funktion auf. Im Allgemeinen werden auf dem Server generierte Benachrichtigungen durch diese Warteschlangen gesendet, um später verarbeitet zu werden.

Für die Verwendung von Abfragebenachrichtigungen ist eine Warteschlange und ein Dienst auf dem Server erforderlich. Diese können mit dem [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Befehl erstellt werden, wie in folgendem Beispiel veranschaulicht:

```sql
CREATE QUEUE myQueue
CREATE SERVICE myService ON QUEUE myQueue
([https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification])
```

> [!NOTE]
> Der Dienst muss, wie oben dargestellt, den vordefinierten Vertrag verwenden.

## <a name="ole-db-driver-for-sql-server"></a>OLE DB-Treiber für SQL Server

Der OLE DB-Treiber für SQL Server unterstützt Benachrichtigungen von Consumern bei Rowsetänderungen. Der Consumer erhält in jeder Phase der Rowsetänderung und bei jeder versuchten Änderung eine Benachrichtigung.

> [!NOTE]
> Die einzige zulässige Möglichkeit, Abfragebenachrichtigungen beim OLE DB-Treiber für SQL Server zu abonnieren, besteht in der Übergabe einer Benachrichtigungsabfrage an den Server mit **ICommand::Execute**.

### <a name="dbpropset_sqlserverrowset-property-set"></a>DBPROPSET_SQLSERVERROWSET-Eigenschaftensatz

Der OLE DB-Treiber für SQL Server fügt dem `DBPROPSET_SQLSERVERROWSET`-Eigenschaftensatz die folgenden neuen Eigenschaften hinzu, um Abfragebenachrichtigungen mit OLE DB zu unterstützen.

|Name|type|Beschreibung|
|----------|----------|-----------------|
|SSPROP_QP_NOTIFICATION_TIMEOUT|VT_UI4|Die Anzahl der Sekunden, die die Abfragebenachrichtigung aktiv bleiben soll.<br /><br /> Der Standardwert ist 432.000 Sekunden (5 Tage). Der Mindestwert ist 1 Sekunde und der Höchstwert 2^31-1 Sekunden.|
|SSPROP_QP_NOTIFICATION_MSGTEXT|VT_BSTR|Der Text der Benachrichtigung. Dieser ist benutzerdefiniert und weist kein vordefiniertes Format auf.<br /><br /> Standardmäßig ist die Zeichenfolge leer. Geben Sie eine Nachricht mithilfe von 1 bis 2.000 Zeichen an.|
|SSPROP_QP_NOTIFICATION_OPTIONS|VT_BSTR|Die Abfragebenachrichtigungsoptionen. Diese werden in einer Zeichenfolge mit der Syntax *name*=*value* angegeben. Der Benutzer ist für das Erstellen des Diensts und Lesen von Benachrichtigungen von der Warteschlange verantwortlich.<br /><br /> Der Standardwert ist eine leere Zeichenfolge.|

Für das Benachrichtigungsabonnement wird immer ein Commit ausgeführt. Dies geschieht unabhängig davon, ob die Anweisung in einer Benutzertransaktion oder im Autocommitmodus ausgeführt wurde oder ob für die Transaktion, in der die Anweisung ausgeführt wurde, ein Commit oder Rollback durchgeführt wurde. Die Serverbenachrichtigung wird bei einer der folgenden unzulässigen Benachrichtigungsbedingungen ausgelöst: bei einer Änderung der zugrunde liegenden Daten oder des zugrunde liegenden Schemas oder bei Erreichung des Timeoutzeitraums, je nachdem, welches Ereignis früher eintritt. 

Benachrichtigungsregistrierungen werden gelöscht, nachdem sie ausgelöst wurden. Wenn Sie weitere Updates abrufen möchten, muss die Anwendung nach dem Empfang von Benachrichtigungen das Abonnement erneuern.

Eine andere Verbindung oder ein Thread kann die Zielwarteschlange auf Benachrichtigungen überprüfen. Beispiel:

```sql
WAITFOR (RECEIVE * FROM MyQueue); -- Where MyQueue is the queue name.
```

> [!NOTE]
> `SELECT *` löscht den Eintrag nicht aus der Warteschlange. Dies erfolgt jedoch mit `RECEIVE * FROM`. Dadurch wird ein Serverthread blockiert, wenn die Warteschlange leer ist. Wenn zum Zeitpunkt des Aufrufs Warteschlangeneinträge vorhanden sind, werden diese sofort zurückgegeben. Andernfalls wartet der Befehl, bis ein Warteschlangeneintrag erstellt wird.

```sql
RECEIVE * FROM MyQueue
```

Diese Anweisung gibt unverzüglich ein leeres Resultset zurück, wenn die Warteschlange leer ist. Andernfalls werden alle Warteschlangenbenachrichtigungen zurückgegeben.

Wenn `SSPROP_QP_NOTIFICATION_MSGTEXT` und `SSPROP_QP_NOTIFICATION_OPTIONS` ungleich NULL und nicht leer sind, wird der TDS-Header der Abfragebenachrichtigungen, der die drei oben definierten Eigenschaften enthält, an den Server gesendet. Dies erfolgt bei jeder Ausführung des Befehls. Wenn einer der beiden Werte NULL (oder leer) ist, wird der Header nicht gesendet und `DB_E_ERRORSOCCURRED` ausgelöst (oder `DB_S_ERRORSOCCURRED` wird ausgelöst, wenn beide Eigenschaften als optional gekennzeichnet sind). Der Statuswert wird dann auf `DBPROPSTATUS_BADVALUE` festgelegt. Die Überprüfung wird beim Ausführen und Vorbereiten vorgenommen. Entsprechend wird `DB_S_ERRORSOCCURED` ausgelöst, wenn die Eigenschaften der Abfragebenachrichtigung für Verbindungen mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Versionen vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] festgelegt wurden. In diesem Fall ist der Statuswert `DBPROPSTATUS_NOTSUPPORTED`.

Die Initialisierung eines Abonnements gewährleistet nicht, dass nachfolgende Meldungen erfolgreich übermittelt werden. Außerdem wird nicht überprüft, ob der angegebene Dienstname gültig ist.

> [!NOTE]
> Beim Vorbereiten von Anweisungen wird das Abonnement niemals initiiert. Nur die Anweisungsausführung führt zu einer Initiierung. Die Verwendung von OLE DB-Kerndiensten wirkt sich nicht auf Abfragebenachrichtigungen aus.

Weitere Informationen zum `DBPROPSET_SQLSERVERROWSET`-Eigenschaftensatz finden Sie unter [Eigenschaften und Verhaltensweisen von Rowsets](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md).

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)
