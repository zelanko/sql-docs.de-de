---
title: Arbeiten mit Abfrage Benachrichtigungen | Microsoft-Dokumentation
description: Arbeiten mit Abfrage Benachrichtigungen in OLE DB Treiber für SQL Server
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
ms.openlocfilehash: 5b563099b161fa9b55a72820edd3411a4c72b4fe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67988729"
---
# <a name="working-with-query-notifications"></a>Arbeiten mit Abfragebenachrichtigungen

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Abfrage Benachrichtigungen wurden in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und OLE DB Treiber für SQL Server eingeführt. Mit Abfragebenachrichtigungen, die auf der in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführten Service Broker-Infrastruktur aufsetzen, können Anwendungen benachrichtigt werden, wenn sich Daten geändert haben. Diese Funktion ist besonders nützlich für Anwendungen, die einen Informationscache aus einer Datenbank zur Verfügung stellen, z. B. eine Webanwendung, und die benachrichtigt werden müssen, wenn die Quelldaten geändert wurden.

Mit Abfragebenachrichtigungen können Sie eine Benachrichtigung innerhalb eines festgelegten Timeoutzeitraums anfordern, wenn sich die einer Abfrage zugrunde liegenden Daten ändern. Die Anforderung für die Benachrichtigung gibt die Benachrichtigungsoptionen an. Dazu gehören der Dienstname, der Meldungstext und der Timeoutwert für den Server. Benachrichtigungen werden durch eine Service Broker-Warteschlange übermittelt, von der Anwendungen verfügbare Benachrichtigungen abrufen können.

Die Syntax der Zeichenfolge für die Abfragebenachrichtigungsoptionen lautet:

`service=<service-name>[;(local database=<database> | broker instance=<broker instance>)]`

 Beispiel:

`service=mySSBService;local database=mydb`

Benachrichtigungsabonnements überdauern den Prozess, mit dem sie initiiert wurden, da eine Anwendung ein Benachrichtigungsabonnement erstellen und anschließend beendet werden kann. Das Abonnement bleibt gültig, und die Benachrichtigung wird gesendet, wenn die Daten innerhalb des während der Erstellung des Abonnements angegebenen Timeoutzeitraums geändert werden. Eine Benachrichtigung wird durch die ausgeführte Abfrage, die Benachrichtigungsoptionen und den Meldungstext identifiziert und wird möglicherweise abgebrochen, wenn der Timeoutwert auf NULL festgelegt wird.

Benachrichtigungen werden nur einmal gesendet. Für die kontinuierliche Benachrichtigung bei Datenänderungen müssen Sie ein neues Abonnement erstellen, indem Sie die Abfrage nach der Verarbeitung jeder Benachrichtigung erneut ausführen.

Anwendungen von OLE DB-Treibern für SQL Server erhalten normalerweise Benachrichtigungen mit dem [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Befehl [RECEIVE](../../../t-sql/statements/receive-transact-sql.md), um Benachrichtigungen aus der Warteschlange zu lesen, die mit dem in den Benachrichtigungsoptionen angegebenen Dienst verknüpft ist.

> [!NOTE]
> Tabellennamen müssen in Abfragen qualifiziert werden, für die Benachrichtigungen erforderlich sind, z. B. `dbo.myTable`. Tabellennamen müssen mit zwei Teilnamen qualifiziert werden. Das Abonnement ist ungültig, wenn drei oder vier Teilnamen verwendet werden.

Die Benachrichtigungsinfrastruktur setzt auf einer in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführten Queuing-Funktion auf. Im Allgemeinen werden auf dem Server generierte Benachrichtigungen durch diese Warteschlangen gesendet, um später verarbeitet zu werden.

Für die Verwendung von Abfragebenachrichtigungen ist eine Warteschlange und ein Dienst auf dem Server erforderlich. Diese können mit [!INCLUDE[tsql](../../../includes/tsql-md.md)] erstellt werden, wie in folgendem Beispiel veranschaulicht:

```sql
CREATE QUEUE myQueue
CREATE SERVICE myService ON QUEUE myQueue
([https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification])
```

> [!NOTE]
> Der Dienst muss den vordefinierten Vertrag wie zuvor dargestellt verwenden.

## <a name="ole-db-driver-for-sql-server"></a>OLE DB-Treiber für SQL Server

Der OLE DB-Treiber für SQL Server unterstützt Consumer-Benachrichtigungen bei der Änderung von Rowsets. Der Consumer erhält in jeder Phase der Rowsetänderung und bei jeder versuchten Änderung eine Benachrichtigung.

> [!NOTE]
> Die einzige zulässige Möglichkeit, Abfragebenachrichtigungen beim OLE DB-Treiber für SQL Server zu abonnieren, besteht in der Übergabe einer Benachrichtigungsabfrage an den Server mit **ICommand::Execute**.

### <a name="the-dbpropsetsqlserverrowset-property-set"></a>Die DBPROPSET_SQLSERVERROWSET-Eigenschaftsgruppe

Um Abfragebenachrichtigungen mit OLE DB zu unterstützen, fügt der OLE DB-Treiber für SQL Server dem DBPROPSET_SQLSERVERROWSET-Eigenschaftensatz die folgenden neuen Eigenschaften hinzu.

|Name|Typ|und Beschreibung|
|----------|----------|-----------------|
|SSPROP_QP_NOTIFICATION_TIMEOUT|VT_UI4|Die Anzahl der Sekunden, die die Abfragebenachrichtigung aktiv bleiben soll.<br /><br /> Der Standardwert ist 432.000 Sekunden (5 Tage). Der Mindestwert ist 1 Sekunde und der Höchstwert 2^31-1 Sekunden.|
|SSPROP_QP_NOTIFICATION_MSGTEXT|VT_BSTR|Der Text der Benachrichtigung. Dieser ist benutzerdefiniert und weist kein vordefiniertes Format auf.<br /><br /> Standardmäßig ist die Zeichenfolge leer. Sie können eine Meldung mit 1-2000 Zeichen angeben.|
|SSPROP_QP_NOTIFICATION_OPTIONS|VT_BSTR|Die Abfragebenachrichtigungsoptionen. Diese werden in einer Zeichenfolge mit der Syntax *name*=*value* angegeben. Der Benutzer ist für das Erstellen des Diensts und Lesen von Benachrichtigungen von der Warteschlange verantwortlich.<br /><br /> Der Standardwert ist eine leere Zeichenfolge.|

Für das Benachrichtigungsabonnement wird immer ein Commit durchgeführt, unabhängig davon, ob die Anweisung in einer Benutzertransaktion oder im Autocommitmodus ausgeführt wurde oder ob für die Transaktion, in der die Anweisung ausgeführt wurde, ein Commit oder Rollback durchgeführt wurde. Die Serverbenachrichtigung wird bei einer der folgenden unzulässigen Benachrichtigungsbedingungen ausgelöst: bei einer Änderung der zugrunde liegenden Daten oder des zugrunde liegenden Schemas oder bei Erreichung des Timeoutzeitraums, je nachdem, welches Ereignis früher eintritt. Benachrichtigungsregistrierungen werden gelöscht, sobald sie ausgelöst wurden. Nach dem Empfang von Benachrichtigungen muss die Anwendung das Abonnement erneuern für den Fall, dass weitere Updates abgerufen werden sollen.

Eine andere Verbindung oder ein Thread kann die Zielwarteschlange auf Benachrichtigungen überprüfen. Beispiel:

```sql
WAITFOR (RECEIVE * FROM MyQueue); -- Where MyQueue is the queue name.
```

> [!NOTE]
> Mit SELECT * wird der Eintrag in der Warteschlange nicht gelöscht, mit RECEIVE \* FROM jedoch schon. Dadurch wird ein Serverthread blockiert, wenn die Warteschlange leer ist. Wenn zum Zeitpunkt des Aufrufs Warteschlangeneinträge vorhanden sind, werden sie unmittelbar zurückgegeben. Andernfalls wartet der Aufruf, bis ein Warteschlangeneintrag vorgenommen wird.

```sql
RECEIVE * FROM MyQueue
```

Diese Anweisung gibt unverzüglich ein leeres Resultset zurück, wenn die Warteschlange leer ist. Andernfalls gibt sie alle Warteschlangenbenachrichtigungen zurück.

Wenn SSPROP_QP_NOTIFICATION_MSGTEXT und SSPROP_QP_NOTIFICATION_OPTIONS nicht NULL und nicht leer sind, wird der TDS-Abfragebenachrichtigungsheader mit den drei oben definierten Eigenschaften bei jeder Ausführung des Befehls an den Server gesendet. Wenn einer der Werte NULL (oder leer) ist, wird der Header nicht gesendet und DB_E_ERRORSOCCURRED ausgelöst (oder DB_S_ERRORSOCCURRED, wenn die Eigenschaften beide als optional gekennzeichnet sind). Der Statuswert wird auf DBPROPSTATUS_BADVALUE festgelegt. Die Überprüfung wird bei Ausführen/Vorbereiten vorgenommen. Entsprechend wird DB_S_ERRORSOCCURED ausgelöst, wenn die Abfragebenachrichtigungseigenschaften für Verbindungen mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Versionen vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] festgelegt wurden. In diesem Fall ist der Statuswert DBPROPSTATUS_NOTSUPPORTED.

Ein Abonnement zu initiieren gewährleistet nicht, dass nachfolgende Meldungen erfolgreich übermittelt werden. Außerdem wird keine Prüfung im Hinblick auf die Gültigkeit des angegebenen Dienstnamens durchgeführt.

> [!NOTE]
> Durch Vorbereiten der Anweisungen wird nie eine Initiierung des Abonnements ausgelöst. Dies wird nur durch die Ausführung der Anweisung erreicht. Abfragebenachrichtigungen werden von der Verwendung von OLE DB-Basisdiensten nicht beeinflusst.

Weitere Informationen zum DBPROPSET_SQLSERVERROWSET-Eigenschaften Satz finden Sie unter [Rowset-Eigenschaften und-Verhalten](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md).

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)
