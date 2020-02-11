---
title: Arbeiten mit Abfrage Benachrichtigungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], query notifications
- rowsets [SQL Server], notifications
- SQL Server Native Client, query notifications
- notifications [SQL Server Native Client]
- query notifications [SQL Server], SQL Server Native Client
- canceling rowset changes
- IRowsetNotify interface
- SQLNCLI, query notifications
- SQL Server Native Client OLE DB provider, query notifications
- consumer notification for rowset changes [SQL Server Native Client]
ms.assetid: 2f906fff-5ed9-4527-9fd3-9c0d27c3dff7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a149e8940896210a408b36c7cb06814646fd322
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68206601"
---
# <a name="working-with-query-notifications"></a>Arbeiten mit Abfragebenachrichtigungen
  Abfragebenachrichtigungen wurden in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client eingeführt. Mit Abfragebenachrichtigungen, die auf der in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführten Service Broker-Infrastruktur aufsetzen, können Anwendungen benachrichtigt werden, wenn sich Daten geändert haben. Diese Funktion ist besonders nützlich für Anwendungen, die einen Informationscache aus einer Datenbank zur Verfügung stellen, z. B. eine Webanwendung, und die benachrichtigt werden müssen, wenn die Quelldaten geändert wurden.  
  
 Mit Abfragebenachrichtigungen können Sie eine Benachrichtigung innerhalb eines festgelegten Timeoutzeitraums anfordern, wenn sich die einer Abfrage zugrunde liegenden Daten ändern. Die Anforderung für die Benachrichtigung gibt die Benachrichtigungsoptionen an. Dazu gehören der Dienstname, der Meldungstext und der Timeoutwert für den Server. Benachrichtigungen werden durch eine Service Broker-Warteschlange übermittelt, von der Anwendungen verfügbare Benachrichtigungen abrufen können.  
  
 Die Syntax der Zeichenfolge für die Abfragebenachrichtigungsoptionen lautet:  
  
 `service=<service-name>[;(local database=<database> | broker instance=<broker instance>)]`  
  
 Beispiel:  
  
 `service=mySSBService;local database=mydb`  
  
 Benachrichtigungsabonnements überdauern den Prozess, mit dem sie initiiert wurden, da eine Anwendung ein Benachrichtigungsabonnement erstellen und anschließend beendet werden kann. Das Abonnement bleibt gültig, und die Benachrichtigung wird gesendet, wenn die Daten innerhalb des während der Erstellung des Abonnements angegebenen Timeoutzeitraums geändert werden. Eine Benachrichtigung wird durch die ausgeführte Abfrage, die Benachrichtigungsoptionen und den Meldungstext identifiziert und wird möglicherweise abgebrochen, wenn der Timeoutwert auf NULL festgelegt wird.  
  
 Benachrichtigungen werden nur einmal gesendet. Für die kontinuierliche Benachrichtigung bei Datenänderungen müssen Sie ein neues Abonnement erstellen, indem Sie die Abfrage nach der Verarbeitung jeder Benachrichtigung erneut ausführen.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client Anwendungen erhalten in der Regel Benachrichtigungen, [!INCLUDE[tsql](../../../includes/tsql-md.md)] indem Sie den [Receive](/sql/t-sql/statements/receive-transact-sql) -Befehl verwenden, um Benachrichtigungen aus der Warteschlange zu lesen, die dem in den Benachrichtigungs Optionen angegebenen Dienst zugeordnet  
  
> [!NOTE]  
>  Tabellennamen müssen in Abfragen qualifiziert werden, für die Benachrichtigungen erforderlich sind, z. B. `dbo.myTable`. Tabellennamen müssen mit zwei Teilnamen qualifiziert werden. Das Abonnement ist ungültig, wenn drei oder vier Teilnamen verwendet werden.  
  
 Die Benachrichtigungsinfrastruktur setzt auf einer in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführten Queuing-Funktion auf. Im Allgemeinen werden auf dem Server generierte Benachrichtigungen durch diese Warteschlangen gesendet, um später verarbeitet zu werden.  
  
 Für die Verwendung von Abfragebenachrichtigungen ist eine Warteschlange und ein Dienst auf dem Server erforderlich. Diese können mit [!INCLUDE[tsql](../../../includes/tsql-md.md)] erstellt werden, wie in folgendem Beispiel veranschaulicht:  
  
```  
CREATE QUEUE myQueue  
CREATE SERVICE myService ON QUEUE myQueue   
  
([https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification])  
```  
  
> [!NOTE]  
>  Der Dienst muss den vordefinierten Vertrag `https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification` verwenden wie oben dargestellt.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB-Anbieter  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter unterstützt Consumer-Benachrichtigungen bei der Änderung von Rowsets. Der Consumer erhält in jeder Phase der Rowsetänderung und bei jeder versuchten Änderung eine Benachrichtigung.  
  
> [!NOTE]  
>  Das übergeben einer Benachrichtigungs Abfrage an den Server mit **ICommand:: Execute** ist die einzige gültige Methode zum Abonnieren von Abfrage Benachrichtigungen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit dem Native Client OLE DB-Anbieter.  
  
### <a name="the-dbpropset_sqlserverrowset-property-set"></a>Die DBPROPSET_SQLSERVERROWSET-Eigenschaftsgruppe  
 Um Abfrage Benachrichtigungen über OLE DB zu unterstützen, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fügt Native Client die folgenden neuen Eigenschaften der DBPROPSET_SQLSERVERROWSET-Eigenschaften Gruppe hinzu.  
  
|Name|type|BESCHREIBUNG|  
|----------|----------|-----------------|  
|SSPROP_QP_NOTIFICATION_TIMEOUT|VT_UI4|Die Anzahl der Sekunden, die die Abfragebenachrichtigung aktiv bleiben soll.<br /><br /> Der Standardwert ist 432000 Sekunden (5 Tage). Der Mindestwert ist 1 Sekunde und der Höchstwert 2^31-1 Sekunden.|  
|SSPROP_QP_NOTIFICATION_MSGTEXT|VT_BSTR|Der Text der Benachrichtigung. Dieser ist benutzerdefiniert und weist kein vordefiniertes Format auf.<br /><br /> Standardmäßig ist die Zeichenfolge leer. Sie können eine Meldung mit 1-2000 Zeichen angeben.|  
|SSPROP_QP_NOTIFICATION_OPTIONS|VT_BSTR|Die Abfragebenachrichtigungsoptionen. Diese werden in einer Zeichenfolge mit *Name*=-*Wert* -Syntax angegeben. Der Benutzer ist für das Erstellen des Diensts und Lesen von Benachrichtigungen von der Warteschlange verantwortlich.<br /><br /> Der Standardwert ist eine leere Zeichenfolge.|  
  
 Für das Benachrichtigungsabonnement wird immer ein Commit durchgeführt, unabhängig davon, ob die Anweisung in einer Benutzertransaktion oder im Autocommitmodus ausgeführt wurde oder ob für die Transaktion, in der die Anweisung ausgeführt wurde, ein Commit oder Rollback durchgeführt wurde. Die Serverbenachrichtigung wird bei einer der folgenden unzulässigen Benachrichtigungsbedingungen ausgelöst: bei einer Änderung der zugrunde liegenden Daten oder des zugrunde liegenden Schemas oder bei Erreichung des Timeoutzeitraums, je nachdem, welches Ereignis früher eintritt. Benachrichtigungsregistrierungen werden gelöscht, sobald sie ausgelöst wurden. Nach dem Empfang von Benachrichtigungen muss die Anwendung das Abonnement erneuern für den Fall, dass weitere Updates abgerufen werden sollen.  
  
 Eine andere Verbindung oder ein Thread kann die Zielwarteschlange auf Benachrichtigungen überprüfen. Beispiel:  
  
```  
WAITFOR (RECEIVE * FROM MyQueue);   // Where MyQueue is the queue name.   
```  
  
 Beachten Sie, dass SELECT * den Eintrag in der Warteschlange nicht löscht, RECEIVE \* FROM jedoch schon. Dadurch wird ein Serverthread blockiert, wenn die Warteschlange leer ist. Wenn zum Zeitpunkt des Aufrufs Warteschlangeneinträge vorhanden sind, werden sie unmittelbar zurückgegeben. Andernfalls wartet der Aufruf, bis ein Warteschlangeneintrag vorgenommen wird.  
  
```  
RECEIVE * FROM MyQueue  
```  
  
 Diese Anweisung gibt unverzüglich ein leeres Resultset zurück, wenn die Warteschlange leer ist. Andernfalls gibt sie alle Warteschlangenbenachrichtigungen zurück.  
  
 Wenn SSPROP_QP_NOTIFICATION_MSGTEXT und SSPROP_QP_NOTIFICATION_OPTIONS nicht NULL und nicht leer sind, wird der TDS-Abfragebenachrichtigungsheader mit den drei oben definierten Eigenschaften bei jeder Ausführung des Befehls an den Server gesendet. Wenn einer der Werte NULL (oder leer) ist, wird der Header nicht gesendet und DB_E_ERRORSOCCURRED ausgelöst (oder DB_S_ERRORSOCCURRED, wenn die Eigenschaften beide als optional gekennzeichnet sind). Der Statuswert wird auf DBPROPSTATUS_BADVALUE festgelegt. Die Überprüfung wird bei Ausführen/Vorbereiten vorgenommen. Entsprechend wird DB_S_ERRORSOCCURED ausgelöst, wenn die Abfragebenachrichtigungseigenschaften für Verbindungen mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Versionen vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] festgelegt wurden. In diesem Fall ist der Statuswert DBPROPSTATUS_NOTSUPPORTED.  
  
 Ein Abonnement zu initiieren gewährleistet nicht, dass nachfolgende Meldungen erfolgreich übermittelt werden. Außerdem wird keine Prüfung im Hinblick auf die Gültigkeit des angegebenen Dienstnamens durchgeführt.  
  
> [!NOTE]  
>  Durch Vorbereiten der Anweisungen wird nie eine Initiierung des Abonnements ausgelöst. Dies wird nur durch die Ausführung der Anweisung erreicht. Abfragebenachrichtigungen werden von der Verwendung von OLE DB-Basisdiensten nicht beeinflusst.  
  
 Weitere Informationen zum DBPROPSET_SQLSERVERROWSET-Eigenschaften Satz finden Sie unter [Eigenschaften und Verhaltensweisen von Rowsets](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>ODBC-Treiber für SQL Server Native Client  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt Abfrage Benachrichtigungen durch das Hinzufügen von drei neuen Attributen zu den Funktionen [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) und [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) :  
  
-   SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
  
-   SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS  
  
-   SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT  
  
 Wenn SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT und SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS nicht NULL sind, wird der TDS-Abfragebenachrichtigungsheader mit den drei oben definierten Attributen bei jeder Ausführung des Befehls an den Server gesendet. Wenn eine der Eigenschaften NULL ist, wird der Header nicht gesendet und SQL_SUCCESS_WITH_INFO zurückgegeben. Die Überprüfung erfolgt auf der [SQLPrepare-Funktion](https://go.microsoft.com/fwlink/?LinkId=59360), **SQLExecDirect**und **SQLExecute**, die alle fehlschlagen, wenn die Attribute nicht gültig sind. Entsprechend schlägt die Ausführung mit SQL_SUCCESS_WITH_INFO fehl, wenn diese Abfragebenachrichtigungsattribute für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Versionen vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] festgelegt werden.  
  
> [!NOTE]  
>  Durch Vorbereiten der Anweisungen wird nie eine Initiierung des Abonnements ausgelöst. Das Abonnement kann nur durch die Anweisungsausführung initiiert werden.  
  
## <a name="special-cases-and-restrictions"></a>Sonderfälle und Einschränkungen  
 Die folgenden Datentypen werden für Benachrichtigungen nicht unterstützt:  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
 Wenn eine Benachrichtigungsanforderung für eine Abfrage gesendet wird, die einen dieser Typen zurückgibt, wird die Benachrichtigung sofort mit dem Hinweis ausgelöst, dass das Benachrichtigungsabonnement nicht möglich sei.  
  
 Wenn eine Abonnementanforderung für einen Batch oder eine gespeicherte Prozedur erfolgt, wird für jede Anweisung, die innerhalb des Batches oder der gespeicherten Prozedur ausgeführt wird, eine separate Abonnementanforderung ausgegeben. EXECUTE-Anweisungen registrieren keine Benachrichtigung, sondern senden die Benachrichtigungsanforderung an den ausgeführten Befehl. Wenn es sich um einen Batch handelt, wird der Kontext auf die ausgeführten Anweisungen angewendet, und es gelten die gleichen Regeln wie oben beschrieben.  
  
 Die Übermittlung einer Abfrage für eine Benachrichtigung, die vom gleichen Benutzer unter demselben Daten Bank Kontext gesendet wurde und die dieselbe Vorlage, dieselben Parameterwerte, dieselbe Benachrichtigungs-ID und denselben Übermittlungs Speicherort eines vorhandenen aktiven Abonnements aufweist, erneuert die vorhandene Abonnement, das das neue angegebene Timeout zurücksetzt. Dies bedeutet, dass nur eine Benachrichtigung gesendet wird, wenn eine Benachrichtigung für identische Abfragen angefordert wird. Dies gilt sowohl für Abfragen, die in einem Batch dupliziert werden, als auch für Abfragen in einer gespeicherten Prozedur, die mehrmals aufgerufen wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](sql-server-native-client-features.md)  
  
  
