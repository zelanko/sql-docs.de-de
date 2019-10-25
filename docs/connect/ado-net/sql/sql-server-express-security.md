---
title: SQL Server Express-Sicherheit
description: Beschreibt Sicherheitsüberlegungen für SQL Server Express.
ms.date: 09/26/2019
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 9d6b711109f7d94e3bca8d9cf2bda6d2c124c798
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452026"
---
# <a name="sql-server-express-security"></a>SQL Server Express-Sicherheit

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Microsoft SQL Server Express Edition (SQL Server Express) basiert auf Microsoft SQL Server und unterstützt den Großteil der Funktionen der Datenbank-Engine. Es ist so konzipiert, dass nicht erforderliche Features und Netzwerk Konnektivität standardmäßig deaktiviert sind. Dadurch wird die Angriffsfläche für Angriffe durch böswillige Benutzer reduziert.  
  
SQL Server Express wird normalerweise als benannte Instanz installiert. Der Standardname der Instanz lautet `SQLExpress`. Eine benannte Instanz wird durch den Netzwerknamen des Computers sowie den Instanznamen identifiziert, den Sie während der Installation angeben.  
  
## <a name="network-access"></a>Netzwerkzugriff  
Aus Sicherheitsgründen sind Netzwerkprotokolle in SQL Server Express standardmäßig deaktiviert. Dies verhindert Angriffe von außen Benutzern, die den Computer beeinträchtigen können, der die Instanz von SQL Server Express hostet. Sie müssen die Netzwerk Konnektivität explizit aktivieren und den SQL Server-Browser Dienst starten, um von einem anderen Computer aus eine Verbindung mit einer SQL Server Express Instanz herzustellen.  
  
Sobald die Netzwerk Konnektivität aktiviert ist, gelten für eine SQL Server Express Instanz dieselben Sicherheitsanforderungen wie für die anderen Editionen von SQL Server.  
  
## <a name="user-instances"></a>Benutzerinstanzen  
Eine Benutzer Instanz ist eine separate Instanz der SQL Server Express Datenbank-Engine, die von einer übergeordneten Instanz von SQL Server Express generiert wird. Das Hauptziel einer Benutzer Instanz besteht darin, Benutzern, die unter einem Benutzerkonto mit geringsten Rechten ausgeführt werden, Systemadministrator Berechtigungen (`sysadmin`) für die SQL Server Express-Instanz auf Ihrem lokalen Computer zu gewähren. Benutzer Instanzen sind nicht für Benutzer gedacht, die Systemadministratoren auf Ihren eigenen Computern sind.  
  
Eine Benutzer Instanz wird aus einer primären Instanz von SQL Server generiert oder im Auftrag eines Benutzers SQL Server Express. Er wird als Benutzer Prozess im Windows-Sicherheitskontext des Benutzers und nicht als Dienst ausgeführt. SQL Server Anmeldungen sind nicht zulässig. nur Windows-Anmeldungen werden unterstützt. Dadurch wird verhindert, dass Software, die auf einer Benutzer Instanz ausgeführt wird, systemweite Änderungen vornehmen, für die der Benutzer keine Berechtigungen hat. Eine Benutzer Instanz wird auch als untergeordnete Instanz oder Client Instanz bezeichnet und wird manchmal mit dem RANU-Akronym ("Run as Normal User") bezeichnet.  
  
Jede Benutzer Instanz ist von der übergeordneten Instanz und von anderen Benutzer Instanzen isoliert, die auf demselben Computer ausgeführt werden. Auf Benutzer Instanzen installierte Datenbanken werden nur im Einzelbenutzermodus geöffnet. mehrere Benutzer können keine Verbindung mit Ihnen herstellen. Die Replikation, verteilte Abfragen und Remote Verbindungen sind für Benutzer Instanzen deaktiviert. Beim Herstellen einer Verbindung mit einer Benutzer Instanz verfügen Benutzer nicht über spezielle Berechtigungen für die übergeordnete SQL Server Express Instanz.  
  
## <a name="external-resources"></a>Externe Ressourcen  
Weitere Informationen zu SQL Server Express finden Sie in den folgenden Ressourcen.  
  
|||  
|-|-|  
|[Microsoft SQL Server 2005 Express Edition-Onlinedokumentation](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms165706(v=sql.90))|Vervollständigen Sie die Dokumentation für SQL Server 2005 Express Edition.|  
|[Benutzerinstanzen für Nichtadministratoren](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms143684(v=sql.100)) in der SQL Server-Onlinedokumentation|Hier wird beschrieben, wie Benutzer Instanzen erstellt und bereitgestellt werden.|  
|[SQL Server Express-Benutzerinstanzen](sql-server-express-user-instances.md)|Beschreibt Benutzerinstanzfunktionen in einer ADO.NET-Anwendung. Bietet Informationen zum Aktivieren einer Benutzer Instanz, zum Herstellen einer Verbindung mit einer Benutzer Instanz mithilfe einer <xref:Microsoft.Data.SqlClient.SqlConnection>, der Lebensdauer von Benutzer Instanzen und Benutzerinstanzszenarien.|  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Sicherheit](sql-server-security.md)
- [SQL Server Express-Benutzerinstanzen](sql-server-express-user-instances.md)
