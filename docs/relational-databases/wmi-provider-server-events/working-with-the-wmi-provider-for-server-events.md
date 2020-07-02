---
title: Verwenden des WMI-Anbieters für Serverereignisse
description: Beachten Sie diese Richtlinien für die Programmierung mit dem WMI-Anbieter für Server Ereignisse. Erfahren Sie mehr über das Aktivieren von Service Broker, Verbindungs Zeichenfolgen und Berechtigungen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- event notifications [WMI]
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- Service Broker [WMI]
- WMI Provider for Server Events, connection strings
- WMI Provider for Server Events, Service Broker
- notifications [WMI]
- WMI Provider for Server Events, security
ms.assetid: cd974b3b-2309-4a20-b9be-7cfc93fc4389
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d03a5a5171175b18719a218315863d04a82f893a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85633173"
---
# <a name="working-with-the-wmi-provider-for-server-events"></a>Verwenden des WMI-Anbieters für Serverereignisse
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]
  Dieses Thema enthält Richtlinien, die Sie vor dem Programmieren mit dem WMI-Anbieter für Serverereignisse lesen sollten.  
  
## <a name="enabling-service-broker"></a>Aktivieren von Service Broker  
 Der WMI-Anbieter für Serverereignisse übersetzt WQL-Abfragen für Ereignisse in Ereignisbenachrichtigungen in der Zieldatenbank. Kenntnisse darüber, wie Ereignisbenachrichtigungen funktionieren, können bei der Programmierung mit dem Anbieter hilfreich sein. Weitere Informationen finden Sie unter [Konzepte des WMI-Anbieters für Serverereignisse](https://technet.microsoft.com/library/ms180560.aspx).  
  
 Da die vom WMI-Anbieter erstellten Ereignisbenachrichtigungen Meldungen zu Serverereignissen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senden, muss dieser Dienst aktiviert sein, wenn die Ereignisse generiert werden. Wenn Ihr Programm Ereignisse in einer Serverinstanz abfragt, muss der [!INCLUDE[ssSB](../../includes/sssb-md.md)] dieser Instanz in msdb aktiviert sein, da dies der Speicherort des [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Zieldiensts (mit dem Namen SQL/Notifications/ProcessWMIEventProviderNotification/v1.0) ist, der vom Anbieter erstellt wird. Wenn Ihr Programm Ereignisse in einer Datenbank oder in einem bestimmten Datenbankobjekt abfragt, muss der [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Dienst in dieser Zieldatenbank aktiviert sein. Wenn der entsprechende [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Dienst nach dem Bereitstellen der Anwendung nicht aktiviert wird, werden die von der zugrundeliegenden Ereignisbenachrichtigung generierten Ereignisse an die Warteschlange des von der Ereignisbenachrichtigung verwendeten Diensts gesendet, aber erst nach der Aktivierung des [!INCLUDE[ssSB](../../includes/sssb-md.md)]-Diensts an die WMI-Verwaltungsanwendung zurückgegeben.  
  
 Mit der folgenden Abfrage wird bestimmt, welche Service Broker auf einer Serverinstanz aktiviert werden, und die GUID der Broker-Instanz wird festgelegt:  
  
```  
SELECT name, is_broker_enabled, service_broker_guid FROM sys.databases;  
```  
  
 Die Service Broker-GUID von msdb ist besonders interessant, da dies der Speicherort des Zieldiensts des Anbieters ist.  
  
 Um [!INCLUDE[ssSB](../../includes/sssb-md.md)] in einer Datenbank zu aktivieren, verwenden Sie die ENABLE_BROKER SET-Option der [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) -Anweisung.  
  
## <a name="specifying-a-connection-string"></a>Angeben einer Verbindungszeichenfolge  
 Anwendungen leiten den WMI-Anbieter für Serverereignisse an eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] weiter, indem sie eine Verbindung mit einem vom Anbieter definierten WMI-Namespace herstellen. Der WMI-Dienst ordnet der Anbieter-DLL Sqlwep.dll diesen Namespace zu und lädt sie in den Arbeitsspeicher. Jede Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügt über einen eigenen WMI-Namespace, der standardmäßig auf festgelegt ist \\ \\ . \\ *root*\microsoft\sqlserver\serverevents \\ *instance_name*. *instance_name* in einer Standardinstallation von standardmäßig auf MSSQLSERVER festgelegt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="permissions-and-server-authentication"></a>Berechtigungen und Serverauthentifizierung  
 Um auf den WMI-Anbieter für Serverereignisse zugreifen zu können, muss der Client, von dem eine WMI-Verwaltungsanwendung stammt, dem Windows-authentifizierten Benutzer- oder Gruppennamen in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entsprechen, die in der Verbindungszeichenfolge der Anwendung angegeben ist.  
  
## <a name="permissions-and-event-notification-scope"></a>Berechtigungen und Bereich der Ereignisbenachrichtigungen  
 Der WMI-Anbieter für Serverereignisse übersetzt WQL-Abfragen in Ereignisbenachrichtigungen in der Zieldatenbank. Daher muss die aufrufende Anwendung über die erforderlichen Mindestberechtigungen für den Zugriff auf den Anbieter sowie über die richtigen Berechtigungen in der Datenbank zum Erstellen der erforderlichen Ereignisbenachrichtigungen verfügen. Die folgenden Berechtigungen sind erforderlich:  
  
-   Zum Erstellen einer Ereignisbenachrichtigung, die sich auf die Datenbank bezieht, ist mindestens die CREATE DATABASE DDL EVENT NOTIFICATION-Berechtigung in der aktuellen Datenbank erforderlich.  
  
-   Zum Erstellen einer Ereignisbenachrichtigung für eine DDL-Anweisung, die sich auf den Server bezieht, ist mindestens die CREATE DDL EVENT NOTIFICATION-Berechtigung auf dem Server erforderlich.  
  
-   Zum Erstellen einer Ereignisbenachrichtigung für ein Ablaufverfolgungsereignis ist mindestens die CREATE TRACE EVENT NOTIFICATION-Berechtigung auf dem Server erforderlich.  
  
-   Zum Erstellen einer Ereignisbenachrichtigung, die sich auf eine Warteschlange bezieht, ist mindestens die ALTER-Berechtigung für die Warteschlange erforderlich.  
  
 Informationen dazu, wie WQL-Abfragen bezogen werden, finden [Sie unter Verwenden von WQL mit dem WMI-Anbieter für Server Ereignisse](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).  
  
 Betrachten Sie zur Darstellung des Bereichs eine WMI-Anbieteranwendung, die die folgende WQL-Abfrage enthält:  
  
```  
SELECT * FROM ALTER_TABLE  
WHERE DatabaseName = "AdventureWorks2012"   
    AND SchemaName = "Person"  
    AND ObjectName = "Person"  
    AND ObjectType = "TABLE";  
```  
  
 Der WMI-Anbieter übersetzt diese Abfrage in eine Ereignisbenachrichtigung, die in der Datenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] erstellt wird. Das bedeutet, dass der Aufrufer über die erforderlichen Berechtigungen zum Erstellen einer Ereignisbenachrichtigung dieser Art, insbesondere über die CREATE DATABASE DDL EVENT NOTIFICATION-Berechtigung, in der Datenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] verfügen muss.  
  
 Wenn eine WQL-Abfrage eine auf der Serverebene zugewiesene Ereignisbenachrichtigung beispielsweise durch die Ausgabe der Abfrage SELECT * FROM ALTER_TABLE angibt, muss die aufrufende Anwendung über die Berechtigung CREATE DDL EVENT NOTIFICATION auf Serverebene verfügen. Serverbezogene Ereignisbenachrichtigungen werden in der master-Datenbank gespeichert. Sie können die [sys. server_event_notifications](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md) -Katalog Sicht verwenden, um Ihre Metadaten anzuzeigen.  
  
> [!NOTE]  
>  Der vom WMI-Anbieter (Server, Datenbank oder Objekt) erstellte Bereich der Ereignisbenachrichtigung ist letztlich von dem vom WMI-Anbieter verwendeten Ergebnis der Überprüfung der Berechtigungen abhängig. Dies wird durch die Berechtigungen des Benutzers, der den Anbieter aufruft, sowie durch die Überprüfung der abgefragten Datenbank bestimmt.  
>   
>  Im vorherigen Beispiel erstellt der Anbieter zunächst eine Ereignisbenachrichtigung, die sich auf die Datenbank bezieht (`ON DATABASE`). Wenn der Anbieter bestätigt, dass die Datenbank vorhanden ist und dass der Aufrufer über die erforderlichen Berechtigungen zum Erstellen einer Ereignisbenachrichtigung in der Datenbank verfügt, ist die Registrierung erfolgreich. Wenn die Registrierung nicht erfolgreich ist, erstellt der Anbieter eine Ereignisbenachrichtigung auf dem Server (`ON SERVER`). Wenn diese Registrierung erfolgreich ist, werden alle auf dem Server auftretenden `ALTER_TABLE`-Ereignisse vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozess an den WMI-Dienstprozess gesendet. Der Anbieter filtert jedoch alle Ereignisse heraus, die nicht für die `AdventureWorks`-Datenbank bestimmt sind. Durch diesen Prozess wird der Netzwerkverkehr, der für den Bereich des Ereignisses erforderlich ist, möglicherweise erhöht. Mithilfe dieses Prozesses können Sie jedoch WQL-Abfragen bereits vor dem Erstellen von Datenbanken auf den Datenbanken registrieren und nach dem Erstellen der Datenbank Ereignisdaten empfangen und DDL-Aktivitäten starten.  
  
## <a name="permissions-and-message-verification"></a>Berechtigungen und Meldungsüberprüfung  
 Der WMI-Anbieter sendet keine Meldungen für Ereignisbenachrichtigungen, wenn die beiden folgenden Bedingungen zutreffen:  
  
-   Der Benutzer, der die Ereignisbenachrichtigung über den WMI-Anbieter erstellt hat, ist in der Datenbank nicht mehr vorhanden oder verfügt nicht mehr über die erforderliche Berechtigung zum Erstellen einer ähnlichen Ereignisbenachrichtigung.  
  
-   Die Ereignisbenachrichtigungen werden bei folgenden Ereignissen erstellt:  
  
    -   DROP_LOGIN  
  
    -   ALTER_LOGIN  
  
    -   DROP_USER  
  
    -   ALTER_USER  
  
    -   ADD_ROLE_MEMBER  
  
    -   DROP_ROLE_MEMBER  
  
    -   ADD_SERVER_ROLE_MEMBER  
  
    -   DROP_SERVER_ROLE_MEMBER  
  
    -   DENY oder REVOKE (Gilt nur für die Berechtigungen ALTER DATABASE, ALTER ANY DATABASE EVENT NOTIFICATION, CREATE DATABASE DDL EVENT NOTIFICATION, CONTROL SERVER, ALTER ANY EVENT NOTIFICATION, CREATE DDL EVENT NOTIFICATION oder CREATE TRACE EVENT NOTIFICATION.)  
  
## <a name="working-with-event-data-on-the-client-side"></a>Verwenden von Ereignisdaten auf der Clientseite  
 Nachdem der WMI-Anbieter für Server Ereignisse die erforderliche Ereignis Benachrichtigung in der Zieldatenbank erstellt hat, sendet die Ereignis Benachrichtigung Ereignisdaten an den Ziel Dienst in msdb mit dem Namen " **SQL/Benachrichtigungen/ProcessWMIEventProviderNotification/v 1.0**". Der Ziel Dienst fügt das Ereignis in eine Warteschlange in der **msdb** -Datenbank ein, die den Namen **WMIEventProviderNotificationQueue**hat. (Sowohl der Dienst als auch die Warteschlange werden vom Anbieter dynamisch erstellt, wenn er zum ersten Mal eine Verbindung mit herstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .) Der Anbieter liest dann die XML-Ereignisdaten aus dieser Warteschlange und wandelt sie in das Managed Object Format (MOF) um, bevor Sie an die Client Anwendung zurückgegeben wird. Die MOF-Daten bestehen aus den Eigenschaften des Ereignisses, das von der WQL-Abfrage als CIM-Classendefinition (Common Information Model) angefordert wird. Jede Eigenschaft verfügt über einen entsprechenden CIM-Typ. Beispielsweise wird die- `SPID` Eigenschaft als CIM-Typ **sint32**zurückgegeben. Die CIM-Typen für jede Eigenschaft werden unter jeder Ereignisklasse in den [Klassen und Eigenschaften des WMI-Anbieters für Server Ereignisse](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md)aufgelistet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konzepte des WMI-Anbieters für Serverereignisse](https://technet.microsoft.com/library/ms180560.aspx)  
  
  
