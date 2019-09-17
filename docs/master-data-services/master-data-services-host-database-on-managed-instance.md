---
title: Hosten einer Master Data Services-Datenbank in einer verwalteten Instanz | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, wie Sie eine Master Data Service-Datenbank (MDS) für eine verwaltete-Instanz konfigurieren.
ms.custom: ''
ms.date: 07/01/2019
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 19519697-c219-44a8-9339-ee1b02545445
author: v-redu
ms.author: lle
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 747711159c92c7194c0ca622a8e734cff2e6fa2b
ms.sourcegitcommit: d1bc0dd1ac626ee7034a36b81554258994d72c15
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958386"
---
# <a name="host-an-mds-database-on-a-managed-instance"></a>Hosten einer MDS-Datenbank auf einer verwalteten Instanz

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In diesem Artikel wird beschrieben, wie Sie eine MDS-Datenbank (Master Data Services) auf einer verwalteten Instanz konfigurieren.
  
## <a name="preparation"></a>Vorbereitung

Zum Vorbereiten von müssen Sie eine verwaltete Azure SQL-Datenbank-Instanz erstellen und konfigurieren und den Webanwendungs Computer konfigurieren.

### <a name="create-and-configure-the-database"></a>Erstellen und Konfigurieren der Datenbank

1. Erstellen Sie eine verwaltete Azure SQL-Datenbank-Instanz mit einem virtuellen Netzwerk. Siehe [Schnellstart: Weitere Informationen finden Sie unter Erstellen einer](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-get-started) verwalteten Azure SQL-Datenbank-Instanz.

1. Konfigurieren Sie eine Point-to-Site-Verbindung. Weitere [Informationen finden Sie unter Konfigurieren einer Point-to-Site-Verbindung mit einem vnet mithilfe der nativen Azure-Zertifikat Authentifizierung: Azure-Portal](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal) Anweisungen.

1. Konfigurieren Sie Azure Active Directory Authentifizierung mit einer verwalteten SQL-Datenbank-Instanz. Ausführliche Informationen finden Sie [unter Konfigurieren und Verwalten der Azure Active Directory Authentifizierung mit SQL](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure) .

### <a name="configure-web-application-machine"></a>Webanwendungs Computer konfigurieren

1. Installieren Sie ein Point-to-Site-Verbindungs Zertifikat und ein VPN, um sicherzustellen, dass der Computer auf die verwaltete SQL-Datenbank-Instanz zugreifen kann. Weitere Informationen [finden Sie unter Konfigurieren einer Point-to-Site-Verbindung mit einem vnet unter Verwendung der nativen Azure-Zertifikat Authentifizierung: Azure-Portal](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal) Anweisungen.

1. Installieren Sie die folgenden Rollen und Features:
   - Rollen
     - Internetinformationsdienste (IIS)
     - Webverwaltungstools
     - IIS-Verwaltungskonsole
     - WWW (World Wide Web)-Dienste
     - Anwendungsentwicklung
     - .NET-Erweiterbarkeit 3.5
     - .NET-Erweiterbarkeit 4.5
     - ASP.NET 3.5
     - ASP.NET 4.5
     - ISAPI-Erweiterungen
     - ISAPI-Filter
     - Allgemeine HTTP-Funktionen
     - Standarddokument
     - Verzeichnissuche
     - HTTP-Fehler
     - Statischer Inhalt
     - Integrität und Diagnose
     - HTTP-Protokollierung
     - Anforderungsüberwachung
     - Leistung
     - Komprimierung statischer Inhalte
     - Sicherheit
     - Anforderungsfilterung
     - Windows-Authentifizierung
       > [!NOTE]
       > WebDAV-Veröffentlichung nicht installieren

   - Aspekte
     - .NET Framework 3.5 (einschließlich .NET 2.0 und 3.0)
     - .NET Framework 4.5 Advanced Services
     - ASP.NET 4.5
     - WCF Services
     - HTTP-Aktivierung (erforderlich)
     - TCP-Portfreigabe
     - Aktivierungsdienst für Windows-Prozesse
     - Prozessmodell
     - .NET-Umgebung
     - Konfiguration-APIs
     - Komprimierung dynamischer Inhalte

## <a name="install-and-configure-an-mds-web-application"></a>Installieren und Konfigurieren einer MDS-Webanwendung

Als nächstes installieren und konfigurieren [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]Sie.

### <a name="install-sql-server-2019"></a>Installieren von SQL Server 2019

Verwenden Sie den Installations-Assistenten für SQL Server Setup oder eine Eingabe [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]Aufforderung, um zu installieren.

1. Öffnen `Setup.exe`Sie, und führen Sie die Schritte im Installations-Assistenten aus.

2. Wählen Sie auf der Seite [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] **Funktionsauswahl** unter **Freigegebene Funktionen** aus.
Mit dieser Aktion wird Folgendes installiert:
   - [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]
   - Assemblys
   - Ein Windows PowerShell-Snap-in
   - Ordner und Dateien für Webanwendungen und-Dienste.

   ![MDS-SQLServer2019-config-Mi-sqlfeatureselection](../master-data-services/media/mds-sqlserver2019-config-mi-sqlfeatureselection.png "MDS-SQLServer2019-config-MI_SQLFeatureSelection")  

### <a name="set-up-the-database-and-website"></a>Einrichten der Datenbank und der Website

1. Verbinden Sie den Azure-Virtual Network, um sicherzustellen, dass Sie eine Verbindung mit der verwalteten Instanz herstellen können.

   ![MDS-SQLServer2019-config-Mi-P2SVPNConnect](../master-data-services/media/mds-sqlserver2019-config-mi-p2svpnconnect.png "MDS-SQLServer2019-config-MI_P2SVPNConnect")

1. Öffnen Sie [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] das, und wählen Sie dann im linken Bereich **Daten Bank Konfiguration** aus.

1. Wählen Sie **Datenbank erstellen** , um den **Assistenten zum Erstellen einer Datenbank**zu öffnen. Wählen Sie **Weiter**aus.

1. Füllen Sie auf der Seite **Daten Bank Server** das Feld **SQL Server Instanz** aus, und wählen Sie dann den **Authentifizierungstyp**aus. Wählen Sie **Verbindung testen** aus, um zu bestätigen, dass Sie Ihre Anmelde Informationen zum Herstellen einer Verbindung mit der Datenbank über den ausgewählten Authentifizierungstyp verwenden Wählen Sie **Weiter**aus.

   > [!NOTE]
   > - Eine SQL Server-Instanz sieht `xxxxxxx.xxxxxxx.database.windows.net`wie folgt aus:.
   > - Wählen Sie für eine verwaltete Instanz aus den Authentifizierungs Typen **"SQL Server Konto"** und **"aktueller Benutzer – Active Directory integriert** " aus.
   > - Wenn Sie **Aktueller Benutzer – Active Directory** als Authentifizierungstyp integriert auswählen, ist das Feld **Benutzername** schreibgeschützt und zeigt das aktuell angemeldete Windows-Benutzerkonto an. Wenn Sie SQL Server 2019 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] auf einem virtuellen Azure-Computer (VM) ausführen, zeigt das Feld **Benutzername** den VM-Namen und den Benutzernamen für das lokale Administrator Konto auf dem virtuellen Computer an.

   Ihre Authentifizierung muss die Regel **"sysadmin"** für verwaltete Instanzen enthalten.

   ![MDS-SQLServer2019-config-Mi-anatedbconnect](../master-data-services/media/mds-sqlserver2019-config-mi-createdbconnect.png "MDS-SQLServer2019-config-MI_CreateDBConnect")  

1. Geben Sie im Feld **Datenbankname** einen Namen ein. Um eine Windows-Sortierung auszuwählen, deaktivieren Sie optional das Kontrollkästchen **SQL Server Standardsortierung** , und wählen Sie mindestens eine der verfügbaren Optionen aus. Beispielsweise wird die **Groß-/Kleinschreibung**beachtet. Wählen Sie **Weiter**aus.

   ![MDS-SQLServer2019-config-Mi-kreateddbname](../master-data-services/media/mds-sqlserver2019-config-mi-createddbname.png "MDS-SQLServer2019-config-MI_CreatedDBName")

1. Geben Sie im Feld **Benutzername** das Windows-Konto des Standard-Super Benutzers für [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]an. Ein Administrator hat Zugriff auf alle Funktionsbereiche und kann alle Modelle hinzufügen, löschen und aktualisieren.

   ![MDS-SQLServer2019-config-Mi-buildsername](../master-data-services/media/mds-sqlserver2019-config-mi-createdbusername.png "MDS-SQLServer2019-config-MI_createDBUserName")

1. Wählen Sie **weiter** aus, um eine Zusammenfassung der Einstellungen [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] für die Datenbank anzuzeigen. Klicken Sie erneut auf **weiter** , um die Datenbank zu erstellen. Die Seite Status **und fertig** Stellung wird angezeigt.

1. Nachdem die Datenbank erstellt und konfiguriert wurde, klicken Sie auf **Fertig**stellen.

   Weitere Informationen zu den Einstellungen im Assistenten zum **Erstellen einer Datenbank**finden Sie unter [Assistent &#40; [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] zum Erstellen&#41;einer Datenbank Configuration Manager](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).

1. Wählen Sie auf der Seite **Daten Bank Konfiguration** in der die [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]Option **Datenbank auswählen**aus.

1. Wählen Sie **verbinden**, wählen [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Sie die Datenbank aus, und klicken Sie dann auf **OK**

   ![MDS-SQLServer2019-config-Mi-connectdbname](../master-data-services/media/mds-sqlserver2019-config-mi-connectdbname.png "MDS-SQLServer2019-config-MI_connectDBName")

1. Wählen [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]Sie in im linken Bereich **Webkonfiguration** aus.

1. Wählen Sie im Listenfeld **Website** die Option **Standard Website**aus, und wählen Sie dann **Erstellen** aus, um eine Webanwendung zu erstellen.

   ![MDS-SQLServer2019-config-Mi-webconfiguration](../master-data-services/media/mds-sqlserver2019-config-mi-webconfiguration.png "MDS-SQLServer2019-config-MI_WebConfiguration")

   > [!NOTE]
   > Wenn Sie **Standard Website**auswählen, müssen Sie eine Webanwendung separat erstellen. Wenn Sie im Listenfeld **neue Website erstellen** auswählen, wird die Anwendung automatisch erstellt.

1. Geben Sie im Abschnitt **Anwendungs Pool** einen anderen Benutzernamen ein, geben Sie das Kennwort ein, und klicken Sie dann auf **OK**.

   ![MDS-SQLServer2019-config-Mi-conatewebapplication](../master-data-services/media/mds-sqlserver2019-config-mi-createwebapplication.png "MDS-SQLServer2019-config-MI_CreateWebApplication")

   > [!NOTE]
   > Stellen Sie sicher, dass der Benutzer mit der Active Directory integrierten Authentifizierung, die Sie kürzlich erstellt haben, auf die Datenbank zugreifen kann. Alternativ dazu können Sie die Verbindung `web.config` später ändern.

   Weitere Informationen zum Dialogfeld **Webanwendung erstellen** finden Sie unter [Dialogfeld &#40; [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] "Webanwendung&#41;erstellen" Configuration Manager](../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md).

1. Wählen Sie im Fenster Webanwendung im Fenster **Webanwendung** die Anwendung aus, die Sie erstellt haben, und wählen Sie dann im Abschnitt **Anwendung einer Datenbank zuordnen** die Option **auswählen** aus.

1. Wählen Sie **verbinden** aus, [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] und wählen Sie die Datenbank aus, die Sie der Webanwendung zuordnen möchten. Wählen Sie **OK**.

   Die Einrichtung der Website ist abgeschlossen. Auf der Seite **Webkonfiguration** werden nun die von Ihnen ausgewählte Website, die von Ihnen erstellte Webanwendung und die [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] der Anwendung zugeordnete Datenbank angezeigt.

   ![MDS-SQLServer2019-config-Mi-webconfigselectdb](../master-data-services/media/mds-sqlserver2019-config-mi-webconfigselectdb.png "MDS-SQLServer2019-config-MI_WebConfigSelectDB")

1. Wählen Sie **Anwenden**aus. Die Meldung zum **vervollständigen der Konfiguration** wird angezeigt. Wählen Sie im Meldungs Feld **OK** aus, um die-Webanwendung zu starten. Die Website Adresse lautet `http://server name/web application/`.

## <a name="configure-authentication"></a>Konfigurieren der Authentifizierung

Um die verwaltete Instanzdatenbank mit der-Webanwendung zu verbinden, müssen Sie den anderen Authentifizierungstyp ändern.

Suchen Sie `web.config` die Datei `C:\Program Files\Microsoft SQL Server\150\Master Data Services\WebApplication`unter. Ändern Sie ConnectionString, um den anderen Authentifizierungstyp zum Herstellen einer Verbindung mit der verwalteten Instanzdatenbank zu ändern.

Der Standard Authentifizierungstyp ist `Active Directory Integrated` wie in der folgenden Beispiel Verbindungs Zeichenfolge dargestellt:

   ```xml
   <add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;Authentication=&quot;Active Directory Integrated&quot;" />
   ```

MDS unterstützt auch Active Directory Kenn Wort Authentifizierung und SQL Server Authentifizierung, wie in den folgenden Beispiel Verbindungs Zeichenfolgen gezeigt:

- Active Directory Kenn Wort Authentifizierung

   ```xml
   <add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;Authentication=&quot;Active Directory Password&quot; ; UID=bob@contoso.onmicrosoft.com; PWD=MyPassWord!" />
   ```

- SQL Server Authentifizierung

   ```xml
   <add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;User ID=UserName;Password=MyPassword!;" />
   ```

## <a name="upgrade-includessmdsshort_mdincludesssmdsshort-mdmd-and-sql-database-version"></a>Upgrade [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] und SQL-Datenbankversion

### <a name="upgrade-includessmdsshort_mdincludesssmdsshort-mdmd"></a>Zuführen[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]

Installieren Sie das **kumulative Update SQL Server 2019**. [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]wird automatisch aktualisiert.

### <a name="upgrade-sql-server"></a>Aktualisieren von SQL Server

Möglicherweise wird der folgende Fehler `The client version is incompatible with the database version` angezeigt: nach der Installation des **kumulativen Updates SQL Server 2019**.
![MDS-SQLServer2019-config-Mi-upgradebug Page](../master-data-services/media/mds-sqlserver2019-config-mi-upgradedbpage.png "MDS-SQLServer2019-config-MI_UpgradeDBPage")

Um dieses Problem zu beheben, müssen Sie die Datenbankversion aktualisieren:

1. Öffnen Sie [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]das, und wählen Sie dann im linken Bereich **Daten Bank Konfiguration** aus.

1. Wählen Sie auf der Seite **Daten Bank Konfiguration** in der die [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]Option **Datenbank auswählen**aus.

1. Wählen Sie [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] die Datenbank aus, die Sie der Webanwendung zugeordnet haben. Wählen Sie **verbinden**aus, und klicken Sie dann auf **OK**.

   ![MDS-SQLServer2019-config-Mi-connectdbname](../master-data-services/media/mds-sqlserver2019-config-mi-connectdbname.png "MDS-SQLServer2019-config-MI_ConnectDBName")

1. Wählen Sie **Datenbank aktualisieren...** .

   ![MDS-SQLServer2019-config-Mi-selectupgrade DB](../master-data-services/media/mds-sqlserver2019-config-mi-selectupgradedb.png "MDS-SQLServer2019-config-MI_SelectUpgradeDB")

1. Klicken Sie im Assistenten zum Aktualisieren von Datenbanken auf der **Willkommens** Seite auf weiter und auf der Seite **Upgradeüberprüfung** auf **weiter** .

   ![MDS-SQLServer2019-config-Mi-upgradebug-Assistent](../master-data-services/media/mds-sqlserver2019-config-mi-upgradedbwizard.png "MDS-SQLServer2019-config-MI_UpgradeDBWizard")

1. Wählen Sie **Fertig** stellen aus, nachdem alle Aufgaben abgeschlossen sind.

## <a name="see-also"></a>Siehe auch

- [Master Data Services-Datenbank](../master-data-services/master-data-services-database.md)
- [Master Data Manager-Webanwendung](../master-data-services/master-data-manager-web-application.md)
- [Datenbankkonfiguration &#40;Seite im Konfigurations-Manager für Master Data Services&#41;](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)
- [Neues in Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md)
