---
title: SQL Server-Sicherheit
description: Bietet eine Übersicht über die SQL Server-Sicherheitsfunktionen und Anwendungsszenarios zum Erstellen sicherer ADO.NET-Anwendungen, die auf SQL Server zugreifen.
ms.date: 09/26/2019
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: bb9e02743122958cb567e01f5011fc9f8b3481e6
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452003"
---
# <a name="sql-server-security"></a>SQL Server-Sicherheit

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Server besitzt viele Funktionen, die das Erstellen sicherer Datenbankanwendungen unterstützen.  
  
Allgemeine Sicherheitsfragen, wie der Schutz vor Datendiebstahl oder Vandalismus, bleiben jedoch ungeachtet der jeweils verwendeten SQL Server-Version immer aktuell. Die Datenintegrität sollte auch als Sicherheitsproblem angesehen werden. Wenn Daten nicht geschützt sind, kann es möglicherweise wertlos werden, wenn eine Ad-hoc-Datenbearbeitung zulässig ist und die Daten versehentlich oder böswillig mit falschen Werten geändert oder vollständig gelöscht werden. Außerdem müssen häufig gesetzliche Anforderungen befolgt werden, wie z. b. die korrekte Speicherung vertraulicher Informationen. Die Speicherung einiger personenbezogener Daten ist abhängig von den Gesetzen, die in einem bestimmten Zuständigkeitsbereich gelten, vollständig.  
  
Genau wie jede Windows-Version besitzt auch jede SQL Server-Version andere Sicherheitsfunktionen, wobei der Funktionsumfang in höheren Versionen dem früherer Versionen überlegen ist. Es ist wichtig zu verstehen, dass Sicherheitsfeatures allein keine sichere Datenbankanwendung garantieren können. Jede Datenbankanwendung ist in Ihren Anforderungen, der Ausführungsumgebung, dem Bereitstellungs Modell, dem physischen Speicherort und der Benutzer Population eindeutig. Einige Anwendungen, die sich im Bereich befinden, benötigen möglicherweise nur minimale Sicherheit, während andere lokale Anwendungen oder Anwendungen, die über das Internet bereitgestellt werden, möglicherweise strenge Sicherheitsmaßnahmen und eine laufende Überwachung und Auswertung erfordern.  
  
Welche Sicherheitsanforderungen eine SQL Server-Datenbankanwendung erfüllen muss, sollte bereits in der Entwurfsphase geklärt werden. Wenn Sie Bedrohungen früh im Entwicklungszyklen auswerten, haben Sie die Möglichkeit, potenzielle Schäden zu verringern, wenn ein Sicherheitsrisiko erkannt wird.  
  
Selbst wenn der anfängliche Entwurf einer Anwendung vernünftig ist, können neue Bedrohungen auftreten, wenn sich das System weiterentwickelt. Indem Sie mehrere Verteidigungslinien für die Datenbank erstellen, können Sie den Schaden minimieren, der durch eine Sicherheitsverletzung verursacht wird. Ihre erste Verteidigungslinie besteht darin, die Angriffsfläche zu verringern, indem Sie niemals mehr Berechtigungen gewährt, als Sie unbedingt benötigen.  
  
In den Themen in diesem Abschnitt werden die für Entwickler relevanten Sicherheitsfunktionen in SQL Server kurz umrissen. Außerdem finden Sie hier Links zu entsprechenden Themen in der SQL Server-Onlinedokumentation und anderen Ressourcen mit ausführlicheren Informationen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Authentifizierung in SQL Server](authentication-sql-server.md)  
Beschreibt Anmeldungen und Authentifizierung in SQL Server und enthält Links zu weiteren Ressourcen. 
  
[Anwendungssicherheitsszenarios in SQL Server](application-security-scenarios-sql-server.md)  
Enthält Themen, in denen verschiedene Anwendungssicherheitsszenarien für ADO.NET- und SQL Server-Anwendungen erläutert werden.  
  
[SQL Server Express-Sicherheit](sql-server-express-security.md)  
Beschreibt Sicherheitsüberlegungen für SQL Server Express.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
[Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank](../../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
Beschreibt Sicherheitsüberlegungen für SQL Server und Azure SQL-Datenbank.

[Überlegungen zur Sicherheit bei SQL Server-Installationen](../../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
Beschreibt Sicherheitsbedenken, die vor der Installation von SQL Server zu berücksichtigen sind.

## <a name="next-steps"></a>Nächste Schritte
- [SQL Server und ADO.NET](index.md)
