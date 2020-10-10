---
title: Grundlegendes zum WMI-Anbieter für Serverereignisse
description: Erfahren Sie, wie der WMI-Anbieter für Server Ereignisse Windows-Verwaltungsinstrumentation zum Überwachen von Ereignissen verwendet, indem SQL Server in ein verwaltetes WMI-Objekt verwandelt wird.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- architecture [WMI]
- SQL Server Agent [WMI]
- WMI Provider for Server Events, about WMI Provider for Server Events
ms.assetid: 8fd7bd18-76d0-4b28-8fee-8ad861441ab2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6187c97f246a8c4eb445fb0afe224922b2c57f03
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891960"
---
# <a name="understanding-the-wmi-provider-for-server-events"></a>Grundlegendes zum WMI-Anbieter für Serverereignisse
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Über den WMI-Anbieter für Serverereignisse können Sie Ereignisse in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mithilfe von WMI (Windows Management Instrumentation) überwachen. Der Anbieter wandelt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in ein verwaltetes WMI-Objekt um. Jedes Ereignis, das eine Ereignisbenachrichtigung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generieren kann, kann mithilfe dieses Anbieters von WMI verwendet werden. Darüber hinaus kann der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent als eine mit WMI interagierende Verwaltungsanwendung auf diese Ereignisse reagieren. Dadurch wird der durch den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent abgedeckte Ereignisbereich im Gegensatz zu früheren Versionen erweitert.  
  
 Verwaltungsanwendungen wie der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent können über den WMI-Anbieter für Serverereignisse auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zugreifen, indem sie WQL-Anweisungen (WMI Query Language) ausgeben. WQL ist eine vereinfachte Teilmenge von Structured Query Language (SQL) mit einigen WMI-spezifischen Erweiterungen. Bei Verwendung von WQL ruft eine Anwendung einen Ereignistyp für eine bestimmte Datenbank oder ein bestimmtes Datenbankobjekt ab. Der WMI-Anbieter für Serverereignisse übersetzt die Abfrage in eine Ereignisbenachrichtigung und erstellt dadurch auf effektive Weise eine Ereignisbenachrichtigung in der Zieldatenbank. Weitere Informationen zur Funktionsweise von Ereignisbenachrichtigungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]finden Sie unter [Konzepte des WMI-Anbieters für Serverereignisse](./wmi-provider-for-server-events-concepts.md). Die Ereignisse, die abgefragt werden können, sind in [Klassen und Eigenschaften für WMI-Anbieter für Serverereignisse](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md)aufgelistet.  
  
 Wenn ein Ereignis auftritt, das die Ereignisbenachrichtigungsfunktion zum Senden einer Meldung veranlasst, wird die Benachrichtigung an einen vordefinierten Zieldienst in **msdb** mit dem Namen **SQL/Notifications/ProcessWMIEventProviderNotification/v1.0**übermittelt. Der Zieldienst fügt das Ereignis in eine vordefinierte Warteschlange in **msdb** ein. Ihr Name ist **WMIEventProviderNotificationQueue**. (Sowohl der Dienst als auch die Warteschlange werden vom Anbieter dynamisch erstellt, wenn er zum ersten Mal eine Verbindung mit herstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .) Der Anbieter liest dann die Ereignisdaten aus dieser Warteschlange und wandelt sie in das Managed Object Format (MOF) um, bevor Sie an die Anwendung zurückgegeben wird. Die folgende Abbildung veranschaulicht diesen Prozess.  
  
 ![Flussdiagramm des WMI-Anbieters für Serverereignisse](../../relational-databases/wmi-provider-server-events/media/wmi-provider-functional-spec.gif "Flussdiagramm des WMI-Anbieters für Serverereignisse")  
  
 Betrachten Sie beispielsweise folgende WQL-Abfrage:  
  
```  
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS  
WHERE DatabaseName = 'AdventureWorks'  
```  
  
 Als Reaktion auf diese Abfrage erstellt der WMI-Anbieter für Serverereignisse die entsprechende Ereignisbenachrichtigung in der Zieldatenbank:  
  
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
  
 In diesem Beispiel ist `SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9` ein [!INCLUDE[tsql](../../includes/tsql-md.md)] -Bezeichner, der aus dem Präfix `SQLWEP_` und einer GUID besteht. `SQLWEP` erstellt eine neue GUID für jeden Bezeichner. Der Wert `A7E5521A-1CA6-4741-865D-826F804E5135` in der `TO SERVICE` -Klausel ist der GUID, der die Broker-Instanz in der **msdb** -Datenbank identifiziert.  
  
 Weitere Informationen zur Arbeit mit WQL finden Sie unter [Verwenden von WQL mit dem WMI-Anbieter für Serverereignisse](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).  
  
 Verwaltungsanwendungen verweisen den WMI-Anbieter für Serverereignisse an eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , indem sie eine Verbindung zu einem vom Anbieter definierten WMI-Namespace herstellen. Der WMI-Dienst ordnet der Anbieter-DLL Sqlwep.dll diesen Namespace zu und lädt sie in den Arbeitsspeicher. Der Anbieter verwaltet für jede Instanz von einen WMI-Namespace für Server Ereignisse [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , und das Format lautet: \\ \\ . \\ *root*\microsoft\sqlserver\serverevents \\ *instance_name*, wobei *instance_name* standardmäßig auf MSSQLSERVER festgelegt ist. Weitere Informationen dazu, wie eine Verbindung mit einem WMI-Namespace für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz hergestellt wird, finden Sie unter [Verwenden von WQL mit dem WMI-Anbieter für Serverereignisse](https://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx).  
  
 Die Anbieter-DLL, Sqlwep.dll, wird nur einmal in den WMI-Hostdienst des Serverbetriebssystems geladen, dabei ist es irrelevant, wie viele Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sich auf dem Server befinden.  
  
 Ein Beispiel für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Verwaltungsanwendung, die den WMI-Anbieter für Serverereignisse verwendet, finden Sie unter [Beispiel: Erstellen einer SQL Server-Agent-Warnung mit dem WMI-Anbieter für Serverereignisse](./sample-creating-a-sql-server-agent-alert-with-the-wmi-provider.md). Ein Beispiel für eine Verwaltungsanwendung, die den WMI-Anbieter für Serverereignisse in verwaltetem Code verwendet, finden Sie unter [Beispiel: Verwenden des WMI-Ereignisanbieters in verwaltetem Code](./sample-using-the-wmi-event-provider-with-the-net-framework.md). Weitere Informationen finden Sie auch unter WMI im [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konzepte des WMI-Anbieters für Serverereignisse](./wmi-provider-for-server-events-concepts.md)  
  
