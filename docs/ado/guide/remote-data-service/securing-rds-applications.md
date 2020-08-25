---
description: Schützen von RDS-Anwendungen
title: Sichern von RDS-Anwendungen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS security [ADO]
ms.assetid: 82fb1330-d6c6-4c17-ad3e-d417ff822b25
author: rothja
ms.author: jroth
ms.openlocfilehash: aff7a1a180e29adf457feab1d0c7f57f4629cfea
ms.sourcegitcommit: c4d564435c008e2c92035efd2658172f20f07b2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88759280"
---
# <a name="securing-rds-applications"></a>Schützen von RDS-Anwendungen
Dieses Thema enthält Sicherheitsinformationen für RDS.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="microsoft-internet-explorer-security-issues"></a>Sicherheitsprobleme bei Microsoft Internet Explorer  
 Mit neuen Sicherheitsverbesserungen, die zu Microsoft Internet Explorer hinzugefügt wurden, sind einige ADO-und RDS-Objekte auf die Ausführung in einer "sicheren" Umgebung beschränkt. Dies erfordert, dass Sie diese Probleme kennen, einschließlich unterschiedlicher Zonen, Sicherheitsstufen, restriktivem Verhalten, unsicherer Vorgänge und angepassten Sicherheitseinstellungen.  
  
## <a name="security-and-your-web-server"></a>Sicherheit und Webserver  
 Wenn Sie das [RDSServer. DataFactory](../../reference/rds-api/datafactory-object-rdsserver.md) -Objekt auf dem Internet-Webserver verwenden, sollten Sie daran denken, dass dadurch ein potenzielles Sicherheitsrisiko entsteht. Externe Benutzer, die gültige Datenquellen Namen (Data Source Name, DSN), Benutzer-ID und Kenn Wort Informationen erhalten, können Seiten schreiben, um eine beliebige Abfrage an diese Datenquelle zu senden. Wenn Sie einen eingeschränkteren Zugriff auf eine Datenquelle benötigen, können Sie die Registrierung und das Löschen des **RDSServer. DataFactory** -Objekts (msadcf.dll) aufheben und stattdessen benutzerdefinierte Geschäftsobjekte mit hart codierten Abfragen verwenden.  
  
 Weitere Informationen zu den Sicherheitsauswirkungen der Verwendung des RDSServer. DataFactory-Objekts finden Sie im Microsoft-Sicherheits Bulletin MS99-025 auf der Microsoft Security-Website.  
  
## <a name="client-impersonation-and-security"></a>Client Identitätswechsel und-Sicherheit  
 Wenn die Eigenschaft Kenn **Wort Authentifizierung** für Ihren IIS-Webserver auf Windows NT Challenge/Response-Authentifizierung (für Windows NT 4,0) oder auf integrierte Windows-Authentifizierung (für Windows 2000) festgelegt ist, werden Geschäftsobjekte im Sicherheitskontext des Clients aufgerufen. Dies ist ein neues Feature in RDS 1,5, das Client Identitätswechsel über HTTP ermöglicht. Bei der Arbeit in diesem Modus ist die Anmeldung beim Webserver (IIS) nicht anonym, sondern verwendet die Benutzer-ID und das Kennwort, unter denen der Client Computer ausgeführt wird. Wenn die ODBC-DSNs für die Verwendung vertrauenswürdiger Verbindungen eingerichtet sind, erfolgt der Zugriff auf Datenbanken, wie z. b. SQL Server, auch im Sicherheitskontext des Clients. Dies funktioniert jedoch nur, wenn sich die Datenbank auf demselben Computer wie die IIS befindet. die Client Anmelde Informationen können nicht auf einen anderen Computer übertragen werden.  
  
 Beispielsweise ist ein Client, John Doe, mit UserID = "JohnD" und Password = "Secret" bei einem Client Computer angemeldet. Er führt eine browserbasierte Anwendung aus, die auf das **RDSServer. DataFactory** -Objekt zugreifen muss, um ein [Recordset](../../reference/ado-api/recordset-object-ado.md) durch Ausführen einer SQL-Abfrage auf dem Computer "MyServer" zu erstellen, auf dem IIS ausgeführt wird. MyServer, ein System, auf dem Windows NT Server 4,0 ausgeführt wird, ist so eingerichtet, dass die Windows NT Challenge/Response-Authentifizierung verwendet wird, der ODBC-DSN "vertrauenswürdige Verbindung verwenden" ausgewählt ist und der Server außerdem die SQL Server Datenquelle enthält. Wenn eine Anforderung auf dem Webserver eingeht, wird der Client aufgefordert, die Benutzer-ID und das Kennwort einzugeben. Folglich wird die Anforderung auf myserver als aus "JohnD"/"Secret" und nicht mit "IUSER_MyServer" protokolliert (Dies ist die Standardeinstellung, wenn die anonyme Kenn Wort Authentifizierung aktiviert ist). Ebenso wird bei der Anmeldung bei SQL Server "JohnD"/"Secret" verwendet.  
  
 Folglich ermöglicht der IIS Windows NT Challenge/Response-Authentifizierungsmodus die Erstellung von HTML-Seiten, ohne dass der Benutzer explizit aufgefordert wird, die Benutzer-ID und das Kennwort anzugeben, die für die Anmeldung bei der Datenbank erforderlich sind. Wenn die IIS-Standard Authentifizierung verwendet wurde, wäre dies ebenfalls erforderlich.  
  
## <a name="password-authentication"></a>Kenn Wort Authentifizierung  
 RDS kann mit einem IIS-Webserver kommunizieren, der in einem der drei Kenn Wort Authentifizierungs Modi ausgeführt wird: anonyme, Basic-oder NT Challenge/Response-Authentifizierung (als integrierte Windows-Authentifizierung in Windows 2000 bezeichnet). Diese Einstellungen definieren, wie ein Webserver den Zugriff über ihn steuert, z. b., wenn ein Client Computer über explizite Zugriffsberechtigungen auf dem NT-Webserver verfügt.