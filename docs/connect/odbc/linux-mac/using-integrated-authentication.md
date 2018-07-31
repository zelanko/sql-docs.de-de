---
title: Mithilfe der integrierten Authentifizierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- integrated authentication
ms.assetid: 9499ffdf-e0ee-4d3c-8bca-605371eb52d9
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a6e45f2253abd85387ce43b4888e934e6f2dbfde
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38984402"
---
# <a name="using-integrated-authentication"></a>Nutzung der Integrierten Authentifizierung
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Der [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] unter Linux und macOS unterstützt Verbindungen, die eine integrierte Kerberos-Authentifizierung verwenden. Er unterstützt das MIT Kerberos Key Distribution Center (KDC) und kann mit der Generic Security Services Anwendungsprogramm-Schnittstelle (GSSAPI) und mit Kerberos v5-Bibliotheken ausgeführt werden.
  
## <a name="using-integrated-authentication-to-connect-to-includessnoversionincludesssnoversionmdmd-from-an-odbc-application"></a>Herstellen einer Verbindung zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] über eine ODBC-Anwendung mithilfe der integrierten Authentifizierung  

Sie können eine integrierte Kerberos-Authentifizierung aktivieren, indem Sie **Trusted_Connection=yes** in der Verbindungszeichenfolge von **SQLDriverConnect** oder **SQLConnect**angeben. Zum Beispiel:  

```
Driver='ODBC Driver 13 for SQL Server';Server=your_server;Trusted_Connection=yes  
```
  
Beim Herstellen der Verbindung mit einem DSN, Sie können auch hinzufügen **Trusted_Connection = Yes** mit dem DSN-Eintrag im `odbc.ini`.
  
Die `-E` Option `sqlcmd` und `-T` Option `bcp` kann auch zur Angabe der integrierten Authentifizierung verwendet werden, finden Sie unter [Herstellen einer Verbindung mit **Sqlcmd** ](../../../connect/odbc/linux-mac/connecting-with-sqlcmd.md) und [ Herstellen einer Verbindung mit **Bcp** ](../../../connect/odbc/linux-mac/connecting-with-bcp.md) für Weitere Informationen.

Stellen Sie sicher, dass der Clientprinzipal, der mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] verbunden werden soll, bereits mit Kerberos KDC authentifiziert ist.
  
**ServerSPN** und **FailoverPartnerSPN** werden nicht unterstützt.  
  
## <a name="deploying-a-linux-or-macos-odbc-driver-application-designed-to-run-as-a-service"></a>Bereitstellen einer Linux- oder MacOS-ODBC-Treiber-Anwendung entwickelt für die Ausführung als Dienst

Ein Systemadministrator kann eine Anwendung bereitstellen, die als Dienst laufen soll, der eine Kerberos-Authentifizierung verwendet, um sich mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]zu verbinden.  
  
Sie müssen zuerst Kerberos auf dem Client konfigurieren und anschließend sicherstellen, dass die Anwendung die Kerberos-Anmeldeinformationen des Prinzipals Standard verwenden kann.

Stellen Sie sicher, dass Sie `kinit` oder PAM (Pluggable Authentication Module) verwenden, um das TGT für den Prinzipal, der die Verbindung verwendet, abzurufen und zwischenzuspeichern:  
  
-   Führen Sie `kinit` aus und geben Sie Prinzipalnamen und -kennwort an.  
  
-   Führen Sie `kinit` aus und geben Sie einen Prinzipalnamen und einen Speicherort einer Schlüsseltabellendatei an, die den von `ktutil` erstellten Prinzipalschlüssel enthält.  
  
-   Stellen Sie sicher, dass die Anmeldung beim System mithilfe des Kerberos-PAM (Pluggable Authentication Module) vorgenommen wurde.

Wenn eine Anwendung als Dienst ausgeführt wird, da die Kerberos-Anmeldeinformationen programmbedingt ablaufen, erneuern Sie die Anmeldeinformationen, um eine kontinuierliche Verfügbarkeit des Diensts sicherzustellen. Der ODBC-Treiber erneuert nicht Anmeldeinformationen selbst; Stellen Sie sicher, dass es ist ein `cron` Job oder ein Skript, das regelmäßig ausgeführt wird, um die Anmeldeinformationen vor deren Ablauf zu verlängern. Um zu vermeiden, müssen das Kennwort für jede Erneuerung, können Sie eine Keytab-Datei verwenden.  
  
[Kerberos-Konfiguration und Verwendung](http://commons.oreilly.com/wiki/index.php/Linux_in_a_Windows_World/Centralized_Authentication_Tools/Kerberos_Configuration_and_Use) bietet ausführliche Informationen zu Methoden zum kerberisieren von Diensten unter Linux.
  
## <a name="tracking-access-to-a-database"></a>Nachverfolgen von Zugriffen auf eine Datenbank

Ein Datenbankadministrator kann einen Audit-Trail des Zugriffs auf eine Datenbank erstellen, wenn Systemkonten genutzt werden, um mithilfe integrierter Authentifizierung auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] zuzugreifen.  
  
Beim Anmelden bei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] wird das Systemkonto verwendet und es gibt keine Funktionen für Linux, um die Identität des Sicherheitskontexts zu wechseln. Aus diesem Grund muss der Benutzer genauer bestimmt werden.
  
Zur Überwachung von Aktivitäten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] unter einer anderen Identität als dem Systemkonto muss die Anwendung [!INCLUDE[tsql](../../../includes/tsql_md.md)] **EXECUTE AS** verwenden.  
  
Zum Verbessern der Anwendungsleistung kann eine Anwendung Verbindungspooling mit integrierten Authentifizierung und Überwachung verwenden. Das Kombinieren von Verbindungspooling, integrierter Authentifizierung und Überwachung stellt jedoch ein Sicherheitsrisiko dar, da der UnixODBC-Treiber-Manager unterschiedlichen Benutzern ermöglicht, gepoolte Verbindungen wiederzuverwenden. Weitere Informationen finden Sie unter [ODBC-Verbindungspooling](http://www.unixodbc.org/doc/conn_pool.html).  

Vor der Wiederverwendung muss eine Anwendung gepoolte Verbindungen durch Ausführen von `sp_reset_connection` zurücksetzen.  

## <a name="using-active-directory-to-manage-user-identities"></a>Verwalten von Benutzeridentitäten mithilfe von Active Directory

Ein Systemadministrator, der für Anwendungen zuständig ist, muss keine separaten Sätze von Anmeldeinformationen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]verwalten. Es ist möglich, Active Directory als ein Schlüsselverteilungscenter (KDC) für die integrierte Authentifizierung zu konfigurieren. Finden Sie unter [Microsoft Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747(v=vs.85).aspx) für Weitere Informationen.

## <a name="using-linked-server-and-distributed-queries"></a>Verbindungsserver und verteilte Abfragen nutzen

Entwickler können eine Anwendung bereitstellen, die einen Verbindungsserver oder verteilte Abfragen nutzt. Dies geschieht ohne einen Datenbankadministrator, der separate Sätze von SQL-Anmeldeinformationen verwaltet. In diesem Fall muss ein Entwickler eine Anwendung so konfigurieren, dass sie integrierte Authentifizierung nutzt:  
  
-   Der Benutzer meldet sich bei einem Clientcomputer an und authentifiziert sich beim Anwendungsserver.  
  
-   Der Anwendungsserver ist mit anderem Datenbanknamen authentifiziert und stellt eine Verbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] her.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] ist als Datenbankbenutzer bei einer anderen Datenbank ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]) authentifiziert.  
  
Nachdem die integrierte Authentifizierung konfiguriert ist, werden Anmeldeinformationen für den Verbindungsserver übergeben.  
  
## <a name="integrated-authentication-and-sqlcmd"></a>Integrierte Authentifizierung und sqlcmd
Verwenden Sie für den Zugriff auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] mithilfe der integrierten Authentifizierung die `-E`-Option `sqlcmd`. Stellen Sie sicher, dass das Konto, das führt `sqlcmd` der Standard-Kerberos-Client-Prinzipal zugeordnet ist.

## <a name="integrated-authentication-and-bcp"></a>Integrierte Authentifizierung und bcp
Verwenden Sie für den Zugriff auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] mithilfe der integrierten Authentifizierung die `-T`-Option `bcp`. Stellen Sie sicher, dass das Konto, das führt `bcp` der Standard-Kerberos-Client-Prinzipal zugeordnet ist. 
  
Es ist ein Fehler mit `-T` mit der `-U` oder `-P` Option.
  
## <a name="supported-syntax-for-an-spn-registered-by-includessnoversionincludesssnoversionmdmd"></a>Unterstützte Syntax für einen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] registrierten SPN

Die Syntax, die SPNs in den Attributen für Verbindungszeichenfolgen und Verbindungen verwenden, lautet wie folgt:  

|Syntax|und Beschreibung|  
|----------|---------------|  
|MSSQLSvc/*fqdn*:*port*|Der vom Anbieter erstellte Standard-SPN, wenn TCP verwendet wird. *port* ist eine TCP-Portnummer. *fqdn* ist ein vollqualifizierter Domänenname.|  
  
## <a name="authenticating-a-linux-or-macos-computer-with-active-directory"></a>Authentifizieren eines Linux- oder macOS-Computers mit Active Directory

Um Kerberos zu konfigurieren, geben Sie auf der Daten in die `krb5.conf` Datei. `krb5.conf` befindet sich im `/etc/` jedoch finden Sie in einer anderen Datei, die mit der Syntax, z. B. `export KRB5_CONFIG=/home/dbapp/etc/krb5.conf`. Im Folgenden finden Sie eine `krb5.conf`-Beispieldatei:  
  
```  
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  
  
[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  
```  
  
Wenn Ihre Linux- oder MacOS-Computer konfiguriert ist, um das Dynamic Host Configuration Protocol (DHCP) mit einem Windows-DHCP-Server, die Bereitstellung von DNS-Server zu verwenden, um verwenden, können Sie **Dns_lookup_kdc = True**. Jetzt können Sie Kerberos verwenden, mit der Domäne anmelden, mit dem Befehl `kinit alias@YYYY.CORP.CONTOSO.COM`. Parameter zu übergeben, um `kinit` Groß-/Kleinschreibung beachtet und die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Computer so konfiguriert, dass in der Domäne befinden, müssen diesen Benutzer `alias@YYYY.CORP.CONTOSO.COM` Anmeldenamen hinzugefügt. Sie können nun vertrauenswürdige Verbindungen (**Trusted_Connection=YES** in einer Verbindungszeichenfolge **bcp -T** oder **sqlcmd -E**) verwenden.  
  
Die Uhrzeit auf dem Linux oder MacOS-Computer und die Zeit auf den Kerberos Key Distribution Center (KDC) müssen möglichst übereinstimmen. Stellen Sie sicher, dass die Systemzeit richtig eingestellt ist, d.h., dass die Network Time Protocol (NTP) verwendet wird.  

Wenn die Kerberos-Authentifizierung fehlschlägt, verwendet der ODBC-Treiber unter Linux oder macOS nicht die NTLM-Authentifizierung.  

Weitere Informationen zum Authentifizieren von Linux oder MacOS-Computer mit Active Directory finden Sie unter [Linux-Clients mit Active Directory authentifizieren](http://technet.microsoft.com/magazine/2008.12.linux.aspx#id0060048) und [bewährte Methoden für die Integration von OS X in Active Directory](http://training.apple.com/pdf/Best_Practices_for_Integrating_OS_X_with_Active_Directory.pdf). Weitere Informationen zum Konfigurieren von Kerberos finden Sie unter den [MIT Kerberos-Dokumentation](https://web.mit.edu/kerberos/krb5-1.12/doc/index.html).

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md)

[Versionsanmerkungen](../../../connect/odbc/linux-mac/release-notes.md)

[Verwendung von Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md)
