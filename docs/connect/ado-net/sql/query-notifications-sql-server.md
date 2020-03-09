---
title: Abfragebenachrichtigungen in SQL Server
description: Beschreibt, wie .NET-Anwendungen Benachrichtigungen von SQL Server anfordern können, wenn sich Daten geändert haben.
ms.date: 08/15/2019
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 57222c852ac2ba8c1aedf42075b69587a4b3843d
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896573"
---
# <a name="query-notifications-in-sql-server"></a>Abfragebenachrichtigungen in SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Mit Abfragebenachrichtigungen, die auf der Service Broker-Infrastruktur aufsetzen, können Anwendungen benachrichtigt werden, wenn sich Daten geändert haben. Diese Funktion ist besonders nützlich für Anwendungen, die einen Informationscache aus einer Datenbank zur Verfügung stellen, z. B. eine Webanwendung, und die benachrichtigt werden müssen, wenn die Quelldaten geändert wurden.  
  
Es gibt drei Möglichkeiten, Abfragebenachrichtigungen mithilfe von ADO.NET zu implementieren:  
  
- Eine einfache Implementierung wird durch die `SqlNotificationRequest`- zur Verfügung gestellt, die serverseitige Funktionalität verfügbar macht und Ihnen ermöglicht, einen Befehl mit einer Benachrichtigungsanforderung auszuführen.  
  
- Eine komplexere Implementierung wird von der `SqlDependency`-Klasse bereitgestellt, die eine komplexere Abstraktion der Benachrichtigungsfunktionalität zwischen der Quellanwendung und SQL Server bietet und Ihnen ermöglicht, eine Abhängigkeit zur Erkennung von Änderungen im Server zu nutzen. In den meisten Fällen ist dies die einfachste und effektivste Art, die SQL Server-Benachrichtigungsfunktionen verwalteter Clientanwendungen mithilfe des Microsoft-SqlClient-Datenanbieters für SQL Server wirkungsvoll zu nutzen.  
  
- Außerdem können Webanwendungen, die mithilfe von ASP.NET 2.0 oder höher erstellt wurden, die `SqlCacheDependency`-Hilfsklassen verwenden.  
  
Abfragebenachrichtigungen sind für Anwendungen sinnvoll, die Anzeigen oder Caches als Reaktion auf Änderungen in den zugrunde liegenden Daten aktualisieren müssen. Microsoft SQL Server ermöglicht es .NET-Anwendungen, einen Befehl an SQL Server zu senden und eine Benachrichtigung anzufordern, sobald bei der Ausführung desselben Befehls Resultsets produziert werden, die sich von den ursprünglich abgerufenen unterscheiden. Auf dem Server generierte Benachrichtigungen werden durch Warteschlangen gesendet, um später verarbeitet zu werden.  
  
Sie können Benachrichtigungen für SELECT- und EXECUTE-Anweisungen einrichten. Wenn eine EXECUTE-Anweisung verwendet wird, registriert SQL Server eine Benachrichtigung für den ausgeführten Befehl anstelle der EXECUTE-Anweisung selbst. Der Befehl muss den Anforderungen und Einschränkungen für eine SELECT-Anweisung genügen. Wenn ein Befehl, der eine Benachrichtigung registriert, mehrere Anweisungen enthält, erstellt die Datenbank-Engine eine Benachrichtigung für jede Anweisung im Batch.  
  
Wenn Sie eine Anwendung entwickeln, in der Sie bei Datenänderungen zuverlässige Benachrichtigungen unter einer Sekunde benötigen, lesen Sie die Abschnitte **Planen einer effizienten Abfragebenachrichtigungs-Strategie** und **Alternativen zu Abfragebenachrichtigungen** im Thema [Planen von Benachrichtigungen](https://go.microsoft.com/fwlink/?LinkId=211984) in der SQL Server-Onlinedokumentation. Weitere Informationen zu Abfragebenachrichtigungen und SQL Server Service Broker finden Sie unter den folgenden Links zu Themen in der SQL Server-Onlinedokumentation.  
  
**SQL Server-Dokumentation**  
  
- [Verwenden von Abfragebenachrichtigungen](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))  
  
- [Erstellen einer Abfrage für die Benachrichtigung](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Entwicklung (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))  
  
- [Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Entwicklerhandbuch (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Aktivieren von Abfragebenachrichtigungen](enable-query-notifications.md)  
Erläutert die Verwendung von Abfragebenachrichtigungen, einschließlich der Anforderungen zu deren Aktivierung und Nutzung.  
  
[SqlDependency in einer ASP.NET-Anwendung](sqldependency-aspnet-app.md)  
Zeigt, wie Sie Abfragebenachrichtigungen in einer ASP.NET-Anwendung verwenden können.  
  
[Ermitteln von Änderungen mit SqlDependency](detect-changes-sqldependency.md)  
Zeigt, wie Sie ermitteln, ob Abfrageergebnisse von den ursprünglich empfangenen Ergebnissen abweichen.  
  
[SqlCommand-Ausführung mit SqlNotificationRequest](sqlcommand-execution-sqlnotificationrequest.md)  
Veranschaulicht das Konfigurieren eines <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekts für dar Arbeiten mit einer Abfragebenachrichtigung.  
  
## <a name="reference"></a>Verweis  
<xref:Microsoft.Data.Sql.SqlNotificationRequest>  
Beschreibt die <xref:Microsoft.Data.Sql.SqlNotificationRequest>-Klasse und alle ihre Member.  
  
<xref:Microsoft.Data.SqlClient.SqlDependency>  
Beschreibt die <xref:Microsoft.Data.SqlClient.SqlDependency>-Klasse und alle ihre Member.  
  
<xref:System.Web.Caching.SqlCacheDependency>  
Beschreibt die <xref:System.Web.Caching.SqlCacheDependency>-Klasse und alle ihre Member.  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server und ADO.NET](index.md)
