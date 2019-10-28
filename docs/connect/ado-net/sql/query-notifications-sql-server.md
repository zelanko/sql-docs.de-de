---
title: Abfragebenachrichtigungen in SQL Server
description: Beschreibt, wie .NET-Anwendungen Benachrichtigungen von SQL Server anfordern können, wenn sich Daten geändert haben.
ms.date: 08/15/2019
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: d47241e3656e3ca7b4f5ea0eebe9f2cc8b571bf6
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452069"
---
# <a name="query-notifications-in-sql-server"></a>Abfragebenachrichtigungen in SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Mit Abfragebenachrichtigungen, die auf der Service Broker-Infrastruktur aufsetzen, können Anwendungen benachrichtigt werden, wenn sich Daten geändert haben. Diese Funktion ist besonders nützlich für Anwendungen, die einen Informationscache aus einer Datenbank zur Verfügung stellen, z. B. eine Webanwendung, und die benachrichtigt werden müssen, wenn die Quelldaten geändert wurden.  
  
Es gibt drei Möglichkeiten, Abfrage Benachrichtigungen mithilfe von ADO.net zu implementieren:  
  
- Die Implementierung auf niedriger Ebene wird von der `SqlNotificationRequest`-Klasse bereitgestellt, die serverseitige Funktionalität verfügbar macht, sodass Sie einen Befehl mit einer Benachrichtigungs Anforderung ausführen können.  
  
- Die Implementierung auf hoher Ebene wird von der `SqlDependency`-Klasse bereitgestellt. Hierbei handelt es sich um eine Klasse, die eine allgemeine Abstraktion von Benachrichtigungsfunktionen zwischen der Quell Anwendung und SQL Server bereitstellt. so können Sie mithilfe einer Abhängigkeit eine Abhängigkeit zum Erkennen von Änderungen auf dem Server verwenden. In den meisten Fällen ist dies die einfachste und effektivste Art, die SQL Server-Benachrichtigungsfunktionen verwalteter Clientanwendungen mithilfe des Microsoft-SqlClient-Datenanbieters für SQL Server wirkungsvoll zu nutzen.  
  
- Außerdem können Webanwendungen, die mithilfe von ASP.NET 2.0 oder höher erstellt wurden, die `SqlCacheDependency`-Hilfsklassen verwenden.  
  
Abfrage Benachrichtigungen werden für Anwendungen verwendet, die als Reaktion auf Änderungen in den zugrunde liegenden Daten anzeigen oder Caches aktualisieren müssen. Microsoft SQL Server ermöglicht es .NET-Anwendungen, einen Befehl an SQL Server zu senden und eine Benachrichtigung anzufordern, sobald bei der Ausführung desselben Befehls Resultsets produziert werden, die sich von den ursprünglich abgerufenen unterscheiden. Auf dem Server generierte Benachrichtigungen werden durch Warteschlangen gesendet, um später verarbeitet zu werden.  
  
Sie können Benachrichtigungen für SELECT-und EXECUTE-Anweisungen einrichten. Wenn eine EXECUTE-Anweisung verwendet wird, registriert SQL Server eine Benachrichtigung für den ausgeführten Befehl anstelle der EXECUTE-Anweisung selbst. Der Befehl muss den Anforderungen und Einschränkungen für eine SELECT-Anweisung genügen. Wenn ein Befehl, der eine Benachrichtigung registriert, mehrere Anweisungen enthält, erstellt die Datenbank-Engine eine Benachrichtigung für jede Anweisung im Batch.  
  
Wenn Sie eine Anwendung entwickeln, in der Sie bei Datenänderungen zuverlässige Benachrichtigungen unter einer Sekunde benötigen, lesen Sie die Abschnitte **Planen einer effizienten Abfragebenachrichtigungs-Strategie** und **Alternativen zu Abfragebenachrichtigungen** im Thema [Planen von Benachrichtigungen](https://go.microsoft.com/fwlink/?LinkId=211984) in der SQL Server-Onlinedokumentation. Weitere Informationen zu Abfrage Benachrichtigungen und SQL Server Service Broker finden Sie unter den folgenden Links zu Themen in SQL Server-Onlinedokumentation.  
  
**SQL Server-Dokumentation**  
  
- [Verwenden von Abfragebenachrichtigungen](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))  
  
- [Erstellen einer Abfrage für die Benachrichtigung](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Entwicklung (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))  
  
- [Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Entwicklerhandbuch (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Aktivieren von Abfragebenachrichtigungen](enable-query-notifications.md)  
Erläutert die Verwendung von Abfrage Benachrichtigungen, einschließlich der Anforderungen für die Aktivierung und Verwendung von.  
  
[SqlDependency in einer ASP.NET-Anwendung](sqldependency-aspnet-app.md)  
Veranschaulicht die Verwendung von Abfrage Benachrichtigungen aus einer ASP.NET-Anwendung.  
  
[Ermitteln von Änderungen mit SqlDependency](detect-changes-sqldependency.md)  
Veranschaulicht, wie Sie erkennen können, wann sich die Abfrageergebnisse von den ursprünglich empfangenen unterscheiden.  
  
[SqlCommand-Ausführung mit SqlNotificationRequest](sqlcommand-execution-sqlnotificationrequest.md)  
Veranschaulicht das Konfigurieren eines <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekts für die Arbeit mit einer Abfrage Benachrichtigung.  
  
## <a name="reference"></a>Verweis  
<xref:Microsoft.Data.Sql.SqlNotificationRequest>  
Beschreibt die <xref:Microsoft.Data.Sql.SqlNotificationRequest> Klasse und alle Member.  
  
<xref:Microsoft.Data.SqlClient.SqlDependency>  
Beschreibt die <xref:Microsoft.Data.SqlClient.SqlDependency> Klasse und alle Member.  
  
<xref:System.Web.Caching.SqlCacheDependency>  
Beschreibt die <xref:System.Web.Caching.SqlCacheDependency> Klasse und alle Member.  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server und ADO.NET](index.md)
