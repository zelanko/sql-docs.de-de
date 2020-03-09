---
title: SQL Server Express-Sicherheit
description: Beschreibt Sicherheitsüberlegungen für SQL Server Express.
ms.date: 09/26/2019
ms.assetid: cf9cf6d9-4b05-43e9-ac7b-6cefbfcd6d4e
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: f704511abd15c6bc4eb96afc633b4cfb46f45e1f
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896299"
---
# <a name="sql-server-express-security"></a>SQL Server Express-Sicherheit

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Microsoft SQL Server Express Edition (SQL Server Express) basiert auf Microsoft SQL Server und unterstützt den Großteil der Funktionen der Datenbank-Engine. Die Lösung ist so konzipiert, dass nicht erforderliche Features und Netzwerkkonnektivität standardmäßig deaktiviert sind. Dadurch wird die Angriffsfläche für böswillige Benutzer verkleinert.  
  
SQL Server Express wird im Allgemeinen als benannte Instanz installiert. Der Standardname der Instanz lautet `SQLExpress`. Eine benannte Instanz wird anhand des Netzwerknamens des Computers und des Instanznamens, den Sie bei der Installation angeben, identifiziert.  
  
## <a name="network-access"></a>Netzwerkzugriff  
Aus Sicherheitsgründen sind Netzwerkprotokolle in SQL Server Express standardmäßig deaktiviert. Dies verhindert Angriffe externer Benutzer, die den Computer, der die Instanz von SQL Server Express hostet, gefährden könnten. Sie müssen die Netzwerkkonnektivität explizit aktivieren und den SQL Server-Browser-Dienst starten, um von einem anderen Computer aus eine Verbindung mit einer SQL Server Express-Instanz herzustellen.  
  
Sobald die Netzwerkkonnektivität aktiviert ist, hat eine SQL Server Express-Instanz die gleichen Sicherheitsanforderungen wie die anderen Editionen von SQL Server.  
  
## <a name="user-instances"></a>Benutzerinstanzen  
Eine Benutzerinstanz ist eine separate Instanz der SQL Server Express-Datenbank-Engine, die von einer übergeordneten Instanz von SQL Server Express generiert wird. Das Hauptziel einer Benutzerinstanz ist, Benutzern, die Windows unter einem Benutzerkonto mit den geringsten Rechten ausführen, Systemadministratorrechte (`sysadmin`) für die SQL Server Express-Instanz auf ihrem lokalen Computer zu erteilen. Benutzerinstanzen sind nicht für Benutzer gedacht, die auf ihren eigenen Computern Systemadministratoren sind.  
  
Eine Benutzerinstanz wird von einer primären Instanz von SQL Server oder SQL Server Express im Auftrag eines Benutzers generiert. Sie wird als Benutzerprozess unter dem Windows-Sicherheitskontext des Benutzers und nicht als Dienst ausgeführt. SQL Server-Anmeldungen sind nicht zulässig. Nur Windows-Anmeldungen werden unterstützt. Dadurch wird verhindert, dass Software, die in einer Benutzerinstanz ausgeführt wird, systemweite Änderungen vornimmt, für die der Benutzer keine Berechtigungen hat. Eine Benutzerinstanz ist auch als untergeordnete oder Clientinstanz bekannt und wird mitunter mit dem Akronym RANU (Run As Normal User, Als normaler Benutzer ausführen) abgekürzt.  
  
Jede Benutzerinstanz ist von ihrer übergeordneten Instanz sowie von anderen Benutzerinstanzen isoliert, die auf demselben Computer ausgeführt werden. In Benutzerinstanzen installierte Datenbanken werden nur im Einzelbenutzermodus geöffnet. Mehrere Benutzer können sich nicht mit ihnen verbinden. Replikation, verteilte Abfragen und Remoteverbindungen sind für Benutzerinstanzen ebenfalls deaktiviert. Bei Verbindung mit einer Benutzerinstanz haben die Benutzer keine besonderen Berechtigungen für die übergeordnete SQL Server Express-Instanz.  
  
## <a name="external-resources"></a>Externe Ressourcen  
Weitere Informationen zu SQL Server Express finden Sie in den folgenden Ressourcen.  
  
|||  
|-|-|  
|[Microsoft SQL Server 2005 Express Edition-Onlinedokumentation](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms165706(v=sql.90))|Vollständige Dokumentation für SQL Server 2005 Express Edition.|  
|[Benutzerinstanzen für Nichtadministratoren](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms143684(v=sql.100)) in der SQL Server-Onlinedokumentation|Beschreibt die Erstellung und Bereitstellung von Benutzerinstanzen.|  
|[SQL Server Express-Benutzerinstanzen](sql-server-express-user-instances.md)|Beschreibt Benutzerinstanzfunktionen in einer ADO.NET-Anwendung. Bietet Informationen über das Aktivieren einer Benutzerinstanz, das Herstellen einer Verbindung mit einer Benutzerinstanz mithilfe von <xref:Microsoft.Data.SqlClient.SqlConnection>, die Lebensdauer der Benutzerinstanz und Szenarien mit Benutzerinstanzen.|  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Sicherheit](sql-server-security.md)
- [SQL Server Express-Benutzerinstanzen](sql-server-express-user-instances.md)
