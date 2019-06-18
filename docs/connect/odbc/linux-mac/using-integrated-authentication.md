---
title: Verwenden der integrierten Authentifizierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- integrated authentication
ms.assetid: 9499ffdf-e0ee-4d3c-8bca-605371eb52d9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 27bfc5a5654042be3dde68a2a03c1dd4e6a6d4a3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66801759"
---
# <a name="using-integrated-authentication"></a>Nutzung der Integrierten Authentifizierung
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Der [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux und macOS unterstützt Verbindungen, die eine integrierte Kerberos-Authentifizierung verwenden. Er unterstützt das MIT Kerberos Key Distribution Center (KDC) und kann mit der Generic Security Services Anwendungsprogramm-Schnittstelle (GSSAPI) und mit Kerberos v5-Bibliotheken ausgeführt werden.
  
## <a name="using-integrated-authentication-to-connect-to-includessnoversionincludesssnoversion-mdmd-from-an-odbc-application"></a>Herstellen einer Verbindung zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] über eine ODBC-Anwendung mithilfe der integrierten Authentifizierung  

Sie können eine integrierte Kerberos-Authentifizierung aktivieren, indem Sie **Trusted_Connection=yes** in der Verbindungszeichenfolge von **SQLDriverConnect** oder **SQLConnect**angeben. Beispiel:  

```
Driver='ODBC Driver 13 for SQL Server';Server=your_server;Trusted_Connection=yes  
```
  
Beim Herstellen einer Verbindung mit einem DSN können Sie auch **Trusted_Connection=yes** zum DSN-Eintrag in `odbc.ini` hinzufügen.
  
Die `-E`-Option von `sqlcmd` und die `-T`-Option von `bcp` können ebenfalls zum Festlegen der integrierten Authentifizierung verwendet werden. Weitere Informationen dazu finden Sie unter [Connecting with **sqlcmd** (Herstellen einer Verbindung mit sqlcmd)](../../../connect/odbc/linux-mac/connecting-with-sqlcmd.md) und [Connecting with **bcp** (Herstellen einer Verbindung mit bcp)](../../../connect/odbc/linux-mac/connecting-with-bcp.md).

Stellen Sie sicher, dass der Clientprinzipal, der mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verbunden werden soll, bereits mit Kerberos KDC authentifiziert ist.
  
**ServerSPN** und **FailoverPartnerSPN** werden nicht unterstützt.  
  
## <a name="deploying-a-linux-or-macos-odbc-driver-application-designed-to-run-as-a-service"></a>Bereitstellen einer ODBC-Treiberanwendung zur Ausführung als Dienst unter Linux oder macOS

Ein Systemadministrator kann eine Anwendung bereitstellen, die als Dienst laufen soll, der eine Kerberos-Authentifizierung verwendet, um sich mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]zu verbinden.  
  
Sie müssen zuerst Kerberos auf dem Client konfigurieren und anschließend sicherstellen, dass die Anwendung die Kerberos-Anmeldeinformationen des Prinzipals Standard verwenden kann.

Stellen Sie sicher, dass Sie `kinit` oder PAM (Pluggable Authentication Module) verwenden, um das TGT für den Prinzipal, der die Verbindung verwendet, abzurufen und zwischenzuspeichern:  
  
-   Führen Sie `kinit` aus und geben Sie Prinzipalnamen und -kennwort an.  
  
-   Führen Sie `kinit` aus und geben Sie einen Prinzipalnamen und einen Speicherort einer Schlüsseltabellendatei an, die den von `ktutil` erstellten Prinzipalschlüssel enthält.  
  
-   Stellen Sie sicher, dass die Anmeldung beim System mithilfe des Kerberos-PAM (Pluggable Authentication Module) vorgenommen wurde.

Wenn eine Anwendung als Dienst ausgeführt wird, da die Kerberos-Anmeldeinformationen programmbedingt ablaufen, erneuern Sie die Anmeldeinformationen, um eine kontinuierliche Verfügbarkeit des Diensts sicherzustellen. Der ODBC-Treiber erneuert Anmeldeinformationen nicht selbst. Stellen Sie also sicher, dass regelmäßig ein `cron`-Auftrag oder -Skript ausgeführt wird, um die Anmeldeinformationen zu erneuern, bevor sie ablaufen. Sie können eine Schlüsseltabellendatei verwenden, um zu vermeiden, dass das Kennwort für jede Erneuerung angegeben werden muss.  
  
[Kerberos-Konfiguration und Verwendung](https://commons.oreilly.com/wiki/index.php/Linux_in_a_Windows_World/Centralized_Authentication_Tools/Kerberos_Configuration_and_Use) bietet ausführliche Informationen zu Methoden zum kerberisieren von Diensten unter Linux.
  
## <a name="tracking-access-to-a-database"></a>Nachverfolgen von Zugriffen auf eine Datenbank

Ein Datenbankadministrator kann einen Audit-Trail des Zugriffs auf eine Datenbank erstellen, wenn Systemkonten genutzt werden, um mithilfe integrierter Authentifizierung auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zuzugreifen.  
  
Beim Anmelden in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird das Systemkonto verwendet und es gibt keine Funktionalität für Linux, um die Identität des Sicherheitskontexts anzunehmen. Aus diesem Grund muss der Benutzer genauer bestimmt werden.
  
Zur Überwachung von Aktivitäten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter einer anderen Identität als dem Systemkonto muss die Anwendung [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE AS** verwenden.  
  
Zum Verbessern der Anwendungsleistung kann eine Anwendung Verbindungspooling mit integrierten Authentifizierung und Überwachung verwenden. Das Kombinieren von Verbindungspooling, integrierter Authentifizierung und Überwachung stellt jedoch ein Sicherheitsrisiko dar, da der UnixODBC-Treiber-Manager unterschiedlichen Benutzern ermöglicht, gepoolte Verbindungen wiederzuverwenden. Weitere Informationen finden Sie unter [ODBC-Verbindungspooling](http://www.unixodbc.org/doc/conn_pool.html).  

Vor der Wiederverwendung muss eine Anwendung gepoolte Verbindungen durch Ausführen von `sp_reset_connection` zurücksetzen.  

## <a name="using-active-directory-to-manage-user-identities"></a>Verwalten von Benutzeridentitäten mithilfe von Active Directory

Ein Systemadministrator, der für Anwendungen zuständig ist, muss keine separaten Sätze von Anmeldeinformationen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verwalten. Es ist möglich, Active Directory als ein Schlüsselverteilungscenter (KDC) für die integrierte Authentifizierung zu konfigurieren. Weitere Informationen finden Sie im Artikel zu [Microsoft Kerberos](/windows/desktop/SecAuthN/microsoft-kerberos).

## <a name="using-linked-server-and-distributed-queries"></a>Verbindungsserver und verteilte Abfragen nutzen

Entwickler können eine Anwendung bereitstellen, die einen Verbindungsserver oder verteilte Abfragen nutzt. Dies geschieht ohne einen Datenbankadministrator, der separate Sätze von SQL-Anmeldeinformationen verwaltet. In diesem Fall muss ein Entwickler eine Anwendung so konfigurieren, dass sie integrierte Authentifizierung nutzt:  
  
-   Der Benutzer meldet sich bei einem Clientcomputer an und authentifiziert sich beim Anwendungsserver.  
  
-   Der Anwendungsserver ist mit anderem Datenbanknamen authentifiziert und stellt eine Verbindung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] her.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist als Datenbankbenutzer bei einer anderen Datenbank ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) authentifiziert.  
  
Nachdem die integrierte Authentifizierung konfiguriert ist, werden Anmeldeinformationen für den Verbindungsserver übergeben.  
  
## <a name="integrated-authentication-and-sqlcmd"></a>Integrierte Authentifizierung und sqlcmd
Verwenden Sie für den Zugriff auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe der integrierten Authentifizierung die `-E`-Option `sqlcmd`. Stellen Sie sicher, dass das Konto, auf dem `sqlcmd` ausgeführt wird, dem Kerberos-Standardclientprinzipal zugeordnet ist.

## <a name="integrated-authentication-and-bcp"></a>Integrierte Authentifizierung und bcp
Verwenden Sie für den Zugriff auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mithilfe der integrierten Authentifizierung die `-T`-Option `bcp`. Stellen Sie sicher, dass das Konto, auf dem `bcp` ausgeführt wird, dem Kerberos-Standardclientprinzipal zugeordnet ist. 
  
Es ist ein Fehler, `-T` mit den Optionen `-U` oder `-P` zu verwenden.
  
## <a name="supported-syntax-for-an-spn-registered-by-includessnoversionincludesssnoversion-mdmd"></a>Unterstützte Syntax für einen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] registrierten SPN

Die Syntax, die SPNs in den Attributen für Verbindungszeichenfolgen und Verbindungen verwenden, lautet wie folgt:  

|Syntax|und Beschreibung|  
|----------|---------------|  
|MSSQLSvc/*fqdn*:*port*|Der vom Anbieter erstellte Standard-SPN, wenn TCP verwendet wird. *port* ist eine TCP-Portnummer. *fqdn* ist ein vollqualifizierter Domänenname.|  
  
## <a name="authenticating-a-linux-or-macos-computer-with-active-directory"></a>Authentifizieren eines Linux- oder macOS-Computers mit Active Directory

Geben Sie Daten in die `krb5.conf`-Datei ein, um Kerberos zu konfigurieren. `krb5.conf` befindet sich in `/etc/`, mithilfe der Syntax `export KRB5_CONFIG=/home/dbapp/etc/krb5.conf` können Sie jedoch auf eine andere Datei verweisen. Im Folgenden finden Sie eine `krb5.conf`-Beispieldatei:  
  
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
  
Wenn Ihr Linux- oder macOS-Computer zur Verwendung des Dynamic Host Configuration-Protokolls (DHCP) mit einem Windows-DHCP-Server konfiguriert ist, der die zu verwendenden DNS-Server bereitstellt, können Sie **dns_lookup_kdc=true** verwenden. Jetzt können Sie Kerberos verwenden, um sich bei Ihrer Domäne anzumelden, indem Sie den Befehl `kinit alias@YYYY.CORP.CONTOSO.COM` verwenden. Parameter, die an `kinit` übergeben werden, berücksichtigen die Groß-/Kleinschreibung, und der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Computer, der für die Domäne konfiguriert wurde, muss den Benutzer `alias@YYYY.CORP.CONTOSO.COM` für die Anmeldung aufweisen. Sie können nun vertrauenswürdige Verbindungen (**Trusted_Connection=YES** in einer Verbindungszeichenfolge **bcp -T** oder **sqlcmd -E**) verwenden.  
  
Die Uhrzeit auf dem Linux- oder macOS-Computer und die Uhrzeit im Schlüsselverteilungscenter müssen nah aneinander liegen. Stellen Sie sicher, dass die Systemzeit richtig eingestellt ist, d.h., dass die Network Time Protocol (NTP) verwendet wird.  

Wenn die Kerberos-Authentifizierung fehlschlägt, verwendet der ODBC-Treiber unter Linux oder macOS nicht die NTLM-Authentifizierung.  

Weitere Informationen zur Authentifizierung von Linux- oder macOS-Computern bei Active Directory finden Sie unter [Authentifizieren von Linux-Clients bei Active Directory](https://technet.microsoft.com/magazine/2008.12.linux.aspx#id0060048) und [Best Practices for Integrating OS X with Active Directory (Bewährte Methoden für die Integration von Mac OS X bei Active Directory)](https://training.apple.com/pdf/Best_Practices_for_Integrating_OS_X_with_Active_Directory.pdf). Weitere Informationen zur Konfiguration von Kerberos finden Sie in der [Kerberos-Dokumentation des MIT](https://web.mit.edu/kerberos/krb5-1.12/doc/index.html).

## <a name="see-also"></a>Weitere Informationen  
[Programmierrichtlinien](../../../connect/odbc/linux-mac/programming-guidelines.md)

[Versionsanmerkungen](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)

[Verwendung von Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md)
