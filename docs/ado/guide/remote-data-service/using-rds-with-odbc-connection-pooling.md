---
title: Verwenden von RDS mit ODBC-Verbindungs-Pooling | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connection pooling in RDS [ADO]
ms.assetid: e8b912c1-da5b-4e85-a000-1e6648a94237
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 40efbdd80f5c6ba814936d952cba03cc7ac5b8ae
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812198"
---
# <a name="using-rds-with-odbc-connection-pooling"></a>Verwenden von RDS mit ODBC-Verbindungspooling
Wenn Sie eine ODBC-Datenquelle verwenden, können Sie der Verbindungspooling-Option in Internet Information Services (IIS), um Behandlung Clientauslastung hohe Leistung zu erzielen. Verbindungspooling ist die Ressourcen-Manager für Verbindungen, verwalten den Zustand "geöffnet" häufig verwendete Verbindung.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Um Verbindungspooling zu aktivieren, finden Sie in der Internet Information Services-Dokumentation.  
  
 Beachten Sie, dass Verbindungspooling aktivieren den Webserver, andere Einschränkungen, für die Themenbereichsdatenbank kann wie in der Dokumentation von Microsoft Internet Information Services an.  
  
 Um sicherzustellen, dass Verbindungspooling stabil ist und zusätzliche Leistungsgewinne stellt, müssen Sie Microsoft SQL Server zur Verwendung der TCP/IP-Sockets-Netzwerkbibliothek konfigurieren.  
  
 Zu diesem Zweck müssen Sie:  
  
-   Konfigurieren Sie SQL Server-Computers zur Verwendung von TCP/IP-Sockets.  
  
-   Konfigurieren Sie den Webserver für die TCP/IP-Sockets verwendet werden.  
  
## <a name="configuring-the-sql-server-computer-to-use-tcpip-sockets"></a>Konfigurieren die SQL Server-Computers zur Verwendung von TCP/IP-Sockets  
 Führen Sie auf dem SQL Server-Computer das SQL Server-Setup-Programm, damit die Interaktionen mit der Datenquelle die TCP/IP-Sockets-Netzwerkbibliothek verwenden.  
  
### <a name="to-specify-the-tcpip-socket-network-library-on-the-sql-server-computer"></a>Die TCP/IP-Sockets-Netzwerkbibliothek für SQL Server-Computers angeben  
  
### <a name="in-microsoft-sql-server-65"></a>Microsoft SQL Server 6.5 gilt Folgendes:  
  
1.  Zeigen Sie über das Startmenü auf Programme, zeigen Sie auf der Microsoft SQL Server 6.5, und klicken Sie dann auf SQL-Setup.  
  
2.  Klicken Sie zweimal auf "Weiter".  
  
3.  In der Microsoft SQL Server – Dialogfeld "Optionen", wählen Sie die Netzwerkunterstützung ändern, und klicken Sie dann auf Weiter.  
  
4.  Stellen Sie sicher, dass das TCP/IP-Sockets-Kontrollkästchen ausgewählt ist, und klicken Sie auf OK.  
  
5.  Klicken Sie auf Weiter, um den Vorgang abzuschließen, und beenden Sie Setup aus.  
  
### <a name="in-microsoft-sql-server-70"></a>In Microsoft SQL Server 7.0:  
  
1.  Zeigen Sie über das Startmenü auf Programme, zeigen Sie auf der Microsoft SQL Server 7.0, und klicken Sie dann auf SQL Server-Netzwerkkonfiguration.  
  
2.  Klicken Sie auf der Registerkarte Allgemein des Dialogfelds auf Hinzufügen.  
  
3.  Klicken Sie auf "TCP/IP", klicken Sie im Dialogfeld Netzwerkbibliothekskonfiguration hinzufügen.  
  
4.  Geben Sie die Anschlussnummer und Proxy die Adresse von Ihrem Netzwerkadministrator bereitgestellt, in den Feldern für Proxy-Adresse und Portnummer.  
  
5.  Klicken Sie auf OK, um den Vorgang abzuschließen, und beenden Sie Setup aus.  
  
## <a name="configuring-the-web-server-to-use-tcpip-sockets"></a>Konfigurieren des Webservers zur Verwendung von TCP/IP-Sockets  
 Es gibt zwei Optionen zum Konfigurieren des Webservers TCP/IP-Sockets verwendet werden. Was Sie tun abhängig, ob alle SQL Server von den Webserver aus zugegriffen wird oder nur eine bestimmte SQL-Server wird vom Webserver zugegriffen.  
  
 Wenn alle SQL Server, die vom Webserver zugegriffen wird, müssen Sie das SQL Server-Clientkonfigurationsprogramm auf dem Webservercomputer ausführen. Die folgenden Schritte aus, Ändern der Standard-Netzwerkbibliothek für alle SQL Server-Verbindungen zwischen diesen IIS-Webserver und die Verwendung der TCP/IP-Sockets-Netzwerkbibliothek hergestellt.  
  
### <a name="to-configure-the-web-server-all-sql-servers"></a>So konfigurieren Sie die Web-Server (alle SQL Server)  
  
### <a name="for-microsoft-sql-server-65"></a>Für Microsoft SQL Server 6.5:  
  
1.  Zeigen Sie über das Startmenü auf Programme, zeigen Sie auf der Microsoft SQL Server 6.5, und klicken Sie dann auf SQL Clientkonfigurations-Hilfsprogramm.  
  
2.  Klicken Sie auf der Registerkarte "Bibliothek".  
  
3.  Wählen Sie im Feld Standardnetzwerk TCP/IP-Sockets.  
  
4.  Klicken Sie auf "erfolgt, um die Änderungen zu speichern und beenden Sie das Dienstprogramm".  
  
### <a name="for-microsoft-sql-server-70"></a>Für Microsoft SQL Server 7.0:  
  
1.  Zeigen Sie über das Startmenü auf Programme, zeigen Sie auf der Microsoft SQL Server 7.0, und klicken Sie dann auf SQL Server-Clientkonfiguration.  
  
2.  Klicken Sie auf der Registerkarte "Allgemein".  
  
3.  Klicken Sie auf "TCP/IP", in das Standard-Netzwerk-Bibliothek.  
  
4.  Klicken Sie auf OK, um Änderungen zu speichern und beenden Sie das Dienstprogramm.  
  
 Wenn einer bestimmten SQL Server von einem Webserver zugegriffen wird, müssen Sie das SQL Server-Clientkonfigurationsprogramm auf dem Webservercomputer ausführen. Um die Netzwerkbibliothek für eine bestimmte SQL Server-Verbindung zu ändern, konfigurieren Sie die SQL Server-Clientsoftware auf dem Webservercomputer folgendermaßen.  
  
### <a name="to-configure-the-web-server-a-specific-sql-server"></a>So konfigurieren Sie die Webserver (einer bestimmten SQL Server)  
  
### <a name="for-microsoft-sql-server-65"></a>Für Microsoft SQL Server 6.5:  
  
1.  Zeigen Sie über das Startmenü auf Programme, zeigen Sie auf der Microsoft SQL Server 6.5, und klicken Sie dann auf SQL Clientkonfigurations-Hilfsprogramm.  
  
2.  Klicken Sie auf der Registerkarte "Erweitert".  
  
3.  Geben Sie den Namen des Servers für die Verbindung mit der Verwendung von TCP/IP-Sockets, klicken Sie im Server.  
  
4.  Wählen Sie die DLL-Name im TCP/IP-Sockets.  
  
5.  Klicken Sie auf hinzufügen/ändern. Alle Datenquellen, die auf diesen Server verweisen, verwenden nun TCP/IP-Sockets.  
  
6.  Klicken Sie auf "Fertig".  
  
### <a name="for-microsoft-sql-server-70"></a>Für Microsoft SQL Server 7.0:  
  
1.  Zeigen Sie über das Startmenü auf Programme, zeigen Sie auf der Microsoft SQL Server 7.0, und klicken Sie dann auf Clientkonfigurations-Hilfsprogramm.  
  
2.  Klicken Sie auf der Registerkarte "Allgemein".  
  
3.  Klicken Sie auf Hinzufügen.  
  
4.  Geben Sie den Alias des Servers im aliasfeld ein. Klicken Sie auf "TCP/IP" im Feld Netzwerk-Bibliotheken. Geben Sie in das Feld Computername ein den Computernamen des Computers, der TCP/IP-Sockets-Clients lauscht. Geben Sie im Feld Portnummer des auf dem SQL Server Lauscht auf Ports ein.  
  
5.  Klicken Sie auf OK, und klicken Sie dann erneut auf um das Hilfsprogramm zu beenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)






















