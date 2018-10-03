---
title: Sichern von RDS-Anwendungen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS security [ADO]
ms.assetid: 82fb1330-d6c6-4c17-ad3e-d417ff822b25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60f2d64fbb682cf3fcab866d1d76c7990f6b2341
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798734"
---
# <a name="securing-rds-applications"></a>Schützen von RDS-Anwendungen
Dieses Thema enthält Informationen zur Sicherheit für RDS.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="microsoft-internet-explorer-security-issues"></a>Microsoft Internet Explorer-Sicherheit-Probleme  
 Mit neuen sicherheitsverbesserungen, die Microsoft Internet Explorer hinzugefügt werden sind einige ADO und RDS-Objekte beschränkt, nur in Umgebungen mit "sicheren" Modus ausgeführt. Dies erfordert, dass Sie diese Probleme, z. B. verschiedenen Zonen, Sicherheitsebenen, restriktiv Verhalten, unsichere Vorgänge kennen und Sicherheitseinstellungen angepasst.  
  
## <a name="security-and-your-web-server"></a>Sicherheit und den Webserver  
 Bei Verwendung der [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) Objekt auf dem Internetinformationsdienste-Webserver, denken Sie daran, dass dies daher ein potenzielles Sicherheitsrisiko erstellt. Externe Benutzer, die gültigen Datenquellennamen (DSN), Benutzer-ID und Kennwortinformationen abrufen konnte Seiten zum Senden von einer Abfrage an, die Datenquelle geschrieben werden. Wunsch eingeschränkteren Zugriff auf eine Datenquelle ist eine Option zum Aufheben der Registrierung, und löschen die **RDSServer.DataFactory** (msadcf.dll)-Objekt und verwenden Sie stattdessen benutzerdefinierte Geschäftsobjekte mit hartcodierten Abfragen.  
  
 Weitere Informationen zu Auswirkungen auf die Sicherheit unter Verwendung des Objekts RDSServer.DataFactory finden Sie unter der Microsoft Security Bulletin MS99-025 auf der Microsoft Security-Website.  
  
## <a name="client-impersonation-and-security"></a>Clientidentitätswechsel und Sicherheit  
 Wenn die **Kennwortauthentifizierung** Eigenschaft für den IIS-Webserver auf Windows NT Challenge/Response-Authentifizierung (für Windows NT 4.0) oder die integrierte Windows-Authentifizierung (für Windows 2000) festgelegt wird, dann sind Geschäftsobjekte im Sicherheitskontext des Clients aufgerufen. Dies ist ein neues Feature in RDS-1.5, die Identitätswechsel des Clients über HTTP ermöglicht. Wenn Sie in diesem Modus arbeiten zu können, die Anmeldung an den Webserver (IIS) nicht anonym, aber verwendet werden, die Benutzer-ID und Kennwort, das unter der Clientcomputer ausgeführt wird. Wenn die ODBC-DSNs so eingerichtet werden, vertrauenswürdige Verbindung verwenden, erfolgt der Zugriff auf Datenbanken wie SQL Server, auch im Sicherheitskontext des Clients. Aber dies funktioniert nur, wenn die Datenbank auf demselben Computer wie die IIS befindet; die Anmeldeinformationen des Clients können nicht auf einem dritten Computer übernommen werden.  
  
 Beispielsweise ein Client, John Doe, der mit Benutzer-ID = "HerbertD" und das Kennwort = "geheimer Schlüssel" auf einem Clientcomputer angemeldet ist. Er führt eine browserbasierte Anwendung, die Zugriff auf die **RDSServer.DataFactory** zu erstellenden Objekts eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) durch Ausführen einer SQL-Abfrage auf dem Computer "MyServer" dem IIS ausgeführt wird. "Myserver", ein System mit ausgeführtem Windows NT Server 4.0, richten Sie Windows NT Challenge/Response-Authentifizierung verwenden, die ODBC-DSN hat "Vertrauenswürdige Verbindung verwenden" ausgewählt und der Server enthält außerdem die SQL Server-Datenquelle. Wenn eine Anforderung auf dem Webserver empfangen wird, fordert den Client den Benutzer-ID und das Kennwort. Daher die Anforderung angemeldet ist "myserver" aus "HerbertD" / "Geheimnis" anstelle von IUSER_MyServer (der Standard ist, wenn anonyme Kennwort-Authentifizierung aktiviert ist). Auf ähnliche Weise beim Anmelden an SQL Server, "HerbertD" / "Geheimnis" verwendet wird.  
  
 Daher kann der IIS-Windows NT Challenge/Response-Authentifizierungsmodus HTML-Seiten, ohne dass der Benutzer aufgefordert zu werden explizit für die Benutzer-ID und Kennwort erforderlichen Informationen zum Melden Sie sich mit der Datenbank erstellt werden. Wenn die IIS-Standardauthentifizierung verwendet wurden, klicken Sie dann wäre diese auch erforderlich.  
  
## <a name="password-authentication"></a>Kennwort-Authentifizierung  
 RDS mit IIS-Webserver ausgeführt wird, in einem der drei Modi Kennwortauthentifizierung kommunizieren kann: anonym, Standard, oder die NT-Abfrage/Rückmeldung-Authentifizierung (integrierte Windows-Authentifizierung in Windows 2000 genannt). Diese Einstellungen definieren, wie ein Webserver-Steuerelemente Zugriff über, beispielsweise, dass die expliziten Zugriffsberechtigungen auf dem NT-Webserver verfügen über einen Clientcomputer.


