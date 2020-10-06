---
description: Verwenden von RDS mit ODBC-Verbindungspooling
title: Verwenden von RDS mit ODBC-Verbindungs Pooling | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connection pooling in RDS [ADO]
ms.assetid: e8b912c1-da5b-4e85-a000-1e6648a94237
author: rothja
ms.author: jroth
ms.openlocfilehash: b455687f6869f073a4f8cc78f5a568b4d2eb4e7e
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91722802"
---
# <a name="using-rds-with-odbc-connection-pooling"></a>Verwenden von RDS mit ODBC-Verbindungspooling
Wenn Sie eine ODBC-Datenquelle verwenden, können Sie die Option Verbindungspooling in Internetinformationsdienste (IIS) verwenden, um eine leistungsstarke Verarbeitung der Client Auslastung zu erreichen. Das Verbindungspooling ist ein Ressourcen-Manager für Verbindungen, der den offenen Status für häufig verwendete Verbindungen aufrecht erhält.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
 Informationen zum Aktivieren von Verbindungspooling finden Sie in der Internetinformationsdienste-Dokumentation.  
  
 Beachten Sie, dass das Aktivieren des Verbindungspooling dem Webserver möglicherweise andere Einschränkungen unterliegt, wie in der Microsoft Internetinformationsdienste-Dokumentation erwähnt.  
  
 Um sicherzustellen, dass das Verbindungspooling stabil ist und zusätzliche Leistungssteigerungen bietet, müssen Sie Microsoft SQL Server für die Verwendung der TCP/IP-Socket-Netzwerk Bibliothek konfigurieren.  
  
 Gehen Sie hierzu wie folgt vor:  
  
-   Konfigurieren Sie den SQL Server Computer für die Verwendung von TCP/IP-Sockets.  
  
-   Konfigurieren Sie den Webserver für die Verwendung von TCP/IP-Sockets.  
  
## <a name="configuring-the-sql-server-computer-to-use-tcpip-sockets"></a>Konfigurieren des SQL Server Computers für die Verwendung von TCP/IP-Sockets  
 Führen Sie auf dem SQL Server Computer das SQL Server Setup Programm aus, damit Interaktionen mit der Datenquelle die TCP/IP-Socket-Netzwerk Bibliothek verwenden.  
  
### <a name="to-specify-the-tcpip-socket-network-library-on-the-sql-server-computer"></a>So geben Sie die TCP/IP-Socket-Netzwerk Bibliothek auf dem SQL Server Computer an  
  
### <a name="in-microsoft-sql-server-65"></a>In Microsoft SQL Server 6,5:  
  
1.  Zeigen Sie im Startmenü auf Programme, zeigen Sie auf Microsoft SQL Server 6,5, und klicken Sie dann auf SQL-Setup.  
  
2.  Klicken Sie zweimal auf Weiter.  
  
3.  Wählen Sie im Dialogfeld Microsoft SQL Server-Optionen die Option Netzwerkunterstützung ändern aus, und klicken Sie dann auf Weiter.  
  
4.  Stellen Sie sicher, dass das Kontrollkästchen TCP/IP-Sockets aktiviert ist, und klicken Sie auf OK.  
  
5.  Klicken Sie auf Weiter, um den Vorgang abzuschließen und Setup zu beenden.  
  
### <a name="in-microsoft-sql-server-70"></a>In Microsoft SQL Server 7,0:  
  
1.  Zeigen Sie im Startmenü auf Programme, zeigen Sie auf Microsoft SQL Server 7,0, und klicken Sie dann auf Server-Netzwerk Hilfsprogramm.  
  
2.  Klicken Sie im Dialogfeld auf der Registerkarte Allgemein auf hinzufügen.  
  
3.  Klicken Sie im Dialogfeld Konfiguration der Netzwerk Bibliothek hinzufügen auf TCP/IP.  
  
4.  Geben Sie in den Feldern Portnummer und Proxy Adresse die Portnummer und die Proxy Adresse ein, die von Ihrem Netzwerkadministrator bereitgestellt werden.  
  
5.  Klicken Sie zum Beenden auf OK, und beenden Sie Setup.  
  
## <a name="configuring-the-web-server-to-use-tcpip-sockets"></a>Konfigurieren des Webservers für die Verwendung von TCP/IP-Sockets  
 Es gibt zwei Optionen zum Konfigurieren des Webservers für die Verwendung von TCP/IP-Sockets. Was Sie tun, hängt davon ab, ob vom Webserver auf alle SQL Server-Server zugegriffen wird, oder ob auf einen bestimmten SQL Server vom Webserver aus zugegriffen wird.  
  
 Wenn vom Webserver auf alle SQL Server-Server zugegriffen wird, müssen Sie das SQL Server Client-Konfigurations Hilfsprogramm auf dem Webserver Computer ausführen. Mit den folgenden Schritten wird die Standard Netzwerk Bibliothek für alle SQL Server Verbindungen geändert, die von diesem IIS-Webserver zur Verwendung der TCP/IP-Sockets-Netzwerk Bibliothek hergestellt werden.  
  
### <a name="to-configure-the-web-server-all-sql-servers"></a>So konfigurieren Sie den Webserver (alle SQL Server-Server)  
  
### <a name="for-microsoft-sql-server-65"></a>Für Microsoft SQL Server 6,5:  
  
1.  Zeigen Sie im Startmenü auf Programme, zeigen Sie auf Microsoft SQL Server 6,5, und klicken Sie dann auf SQL-Client Konfigurations Hilfsprogramm.  
  
2.  Klicken Sie auf die Registerkarte NET-Bibliothek.  
  
3.  Wählen Sie im Feld Standard Netzwerk die Option TCP/IP-Sockets aus.  
  
4.  Klicken Sie auf Done, um die Änderungen zu speichern, und beenden Sie das  
  
### <a name="for-microsoft-sql-server-70"></a>Für Microsoft SQL Server 7,0:  
  
1.  Zeigen Sie im Startmenü auf Programme, zeigen Sie auf Microsoft SQL Server 7,0, und klicken Sie dann auf Client Netzwerk-Hilfsprogramm.  
  
2.  Klicken Sie auf die Registerkarte „Allgemein“.  
  
3.  Klicken Sie im Feld Standard Netzwerk Bibliothek auf TCP/IP.  
  
4.  Klicken Sie zum Speichern der Änderungen auf OK, und beenden Sie das Hilfsprogramm  
  
 Wenn von einem Webserver auf eine bestimmte SQL Server zugegriffen wird, müssen Sie das Hilfsprogramm für die SQL Server-Client Konfiguration auf dem Webserver Computer ausführen. Um die Netzwerk Bibliothek für eine bestimmte SQL Server Verbindung zu ändern, konfigurieren Sie die SQL Server-Client Software wie folgt auf dem Webserver Computer.  
  
### <a name="to-configure-the-web-server-a-specific-sql-server"></a>So konfigurieren Sie den Webserver (eine bestimmte SQL Server)  
  
### <a name="for-microsoft-sql-server-65"></a>Für Microsoft SQL Server 6,5:  
  
1.  Zeigen Sie im Startmenü auf Programme, zeigen Sie auf Microsoft SQL Server 6,5, und klicken Sie dann auf SQL-Client Konfigurations Hilfsprogramm.  
  
2.  Klicken Sie auf die Registerkarte „Erweitert“.  
  
3.  Geben Sie im Feld Server den Namen des Servers ein, mit dem Sie mithilfe von TCP/IP-Sockets eine Verbindung herstellen möchten.  
  
4.  Wählen Sie im Feld DLL-Name die Option TCP/IP-Sockets aus.  
  
5.  Klicken Sie auf hinzufügen/ändern. Alle Datenquellen, die auf diesen Server verweisen, verwenden jetzt TCP/IP-Sockets.  
  
6.  Klicken Sie auf Done.  
  
### <a name="for-microsoft-sql-server-70"></a>Für Microsoft SQL Server 7,0:  
  
1.  Zeigen Sie im Startmenü auf Programme, zeigen Sie auf Microsoft SQL Server 7,0, und klicken Sie dann auf Client Konfigurations Hilfsprogramm.  
  
2.  Klicken Sie auf die Registerkarte „Allgemein“.  
  
3.  Klicken Sie auf Hinzufügen.  
  
4.  Geben Sie im Feld Serveralias den Alias des Servers ein. Klicken Sie im Feld Netzwerk Bibliotheken auf TCP/IP. Geben Sie im Feldcomputer Name den Computernamen des Computers ein, der auf TCP/IP-Sockets-Clients lauscht. Geben Sie im Feld Portnummer den Port ein, auf dem der SQL Server lauscht.  
  
5.  Klicken Sie auf OK und dann erneut auf OK, um das Hilfsprogramm zu beenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu RDS](./rds-fundamentals.md)