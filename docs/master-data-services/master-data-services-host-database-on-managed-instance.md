---
title: Hosten der Datenbank auf einer verwalteten Instanz | Microsoft-Dokumentation
description: Beschreibt, wie eine MDS-Datenbank für eine verwaltete Instanz konfiguriert wird.
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
ms.openlocfilehash: b4ca791a1a0ce46929f4d409d234f8dbc7efdec3
ms.sourcegitcommit: bcc3b2c7474297aba17b7a63b17c103febdd0af9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68794844"
---
# <a name="host-database-on-managed-instance"></a>Hosten der Datenbank auf einer verwalteten Instanz

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In diesem Artikel wird beschrieben, wie Sie eine MDS-Datenbank auf einer verwalteten Instanz von konfigurieren.
  
## <a name="preparation"></a>Vorbereitung

Wir müssen die folgenden Schritte in der Vorbereitung abschließen.
- Fertigstellen der Erstellung und Konfiguration verwalteter Instanzen Schließen Sie das virtuelle Netzwerk und das Punkt-zu-Standort-VPN ein.
- Konfiguration des Webanwendungs Computers abschließen.
  - Schließen Sie das Punkt-zu-Standort-VPN ein.
  - Installieren von Rollen und Features.

**Datenbankseite:**

1. Erstellen Sie eine verwaltete Azure SQL-Datenbank-Instanz, die virtuelles Netzwerk enthält. [Schnellstart: Erstellen einer verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-get-started)
2. Konfigurieren Sie eine Point-to-Site-Verbindung. [Konfigurieren einer Point-to-Site-Verbindung mit einem vnet unter Verwendung der nativen Azure-Zertifikat Authentifizierung: Azure-Portal](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal)
3. Konfigurieren Sie Azure Active Directory Authentifizierung mit einer verwalteten SQL-Datenbank-Instanz. [Konfigurieren und Verwalten der Azure Active Directory Authentifizierung mit SQL](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure)

**Webanwendungs Computerseite:**

1. Installieren Sie das Punkt-zu-Standort-Verbindungs Zertifikat und VPN, um sicherzustellen, dass der Computer auf die verwaltete SQL-Datenbank-Instanz [Konfigurieren einer Point-to-Site-Verbindung mit einem vnet unter Verwendung der nativen Azure-Zertifikat Authentifizierung: Azure-Portal](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-howto-point-to-site-resource-manager-portal)
2. Installieren von Rollen und Features. Folgende Funktion ist erforderlich.

- Rollen

      Internet Information Services
      Web Management Tools
      IIS Management Console
      World Wide Web Services
      Application Development
      .NET Extensibility 3.5
      .NET Extensibility 4.5
      ASP.NET 3.5
      ASP.NET 4.5
      ISAPI Extensions
      ISAPI Filters
      Common HTTP Features
      Default Document
      Directory Browsing
      HTTP Errors
      Static Content
      [Note: Do not install WebDAV Publishing]
      Health and Diagnostics
      HTTP Logging
      Request Monitor
      Performance
      Static Content Compression
      Security
      Request Filtering
      Windows Authentication

- Aspekte

      .NET Framework 3.5 (includes .NET 2.0 and 3.0)
      .NET Framework 4.5 Advanced Services
      ASP.NET 4.5
      WCF Services
      HTTP Activation [Note: This is required.]
      TCP Port Sharing
      Windows Process Activation Service
      Process Model
      .NET Environment
      Configuration APIs
      Dynamic Content Compression

## <a name="install-and-configure-includessmdsshort_mdincludesssmdsshort-mdmd-web-application"></a>Installieren und konfigurieren [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] der Webanwendung

Wir müssen die folgenden Schritte ausführen, um zu [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]installieren und zu konfigurieren.

1. Installieren Sie SQL Server 2019 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] include-Feature.
2. Erstellen Sie [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] eine Datenbank auf der Verwaltungs Instanz.
3. Erstellen und konfigurieren Sie die Webanwendung für [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)].
  
**Installieren von SQL Server 2019**

Zum Installieren [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]von verwenden Sie den Installations-Assistenten für SQL Server Setup oder eine Eingabeaufforderung.

1. Doppelklicken Sie auf Setup.exe, und befolgen Sie die Schritte im Installations-Assistenten.

2. Wählen [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Sie auf der Seite Funktionsauswahl unter freigegebene Funktionen aus.
Dadurch werden [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], Assemblys, das Windows PowerShell-Snap-In sowie Ordner und Dateien für Webanwendungen und Dienste installiert.

    ![MDS-SQLServer2019-config-Mi-sqlfeatureselection](../master-data-services/media/mds-sqlserver2019-config-mi-sqlfeatureselection.png "MDS-SQLServer2019-config-MI_SQLFeatureSelection")  

**Einrichten der Datenbank und der Website**

1. Verbinden Sie den Windows Azure-Virtual Network, um sicherzustellen, dass Sie eine Verbindung mit der verwalteten Instanz herstellen können.

    ![MDS-SQLServer2019-config-Mi-P2SVPNConnect](../master-data-services/media/mds-sqlserver2019-config-mi-p2svpnconnect.png "MDS-SQLServer2019-config-MI_P2SVPNConnect")  

2. Starten Sie [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]die. Klicken Sie im linken Bereich auf **Daten Bank Konfiguration** .

3. Klicken Sie auf **Datenbank erstellen**, und klicken Sie dann im Assistenten zum **Erstellen einer Datenbank** auf Weiter.

4. Füllen Sie auf der Seite **Daten Bank Server** die **SQL Server Instanz** aus, wählen Sie den **Authentifizierungstyp** aus, und klicken Sie dann auf **Verbindung testen** , um zu bestätigen, dass Sie mithilfe der Anmelde Informationen für den Authentifizierungstyp, den Sie gewählte. Klicken Sie auf Weiter.

   > [!NOTE]
   > - SQL Server Instanz für eine verwaltete Instanz wie "xxxxxxx.xxxxxxx.Database.Windows.net"
   > - Für eine verwaltete Instanz werden der Authentifizierungstyp **"SQL Server Konto"** und **"aktueller Benutzer – Active Directory integriert"** unterstützt.
   > - Wenn Sie **Aktueller Benutzer – Active Directory** als Authentifizierungstyp integriert auswählen, ist das Feld **Benutzername** schreibgeschützt und zeigt den Namen des Windows-Benutzerkontos an, das auf dem Computer angemeldet ist. Wenn Sie SQL Server 2019 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] auf einem virtuellen Azure-Computer (VM) ausführen, zeigt das Feld **Benutzername** den VM-Namen und den Benutzernamen für das lokale Administrator Konto auf dem virtuellen Computer an.

    Stellen Sie sicher, dass Ihre Authentifizierung die Regel **"sysadmin"** für die verwaltete Instanz enthält.
![MDS-SQLServer2019-config-Mi-anatedbconnect](../master-data-services/media/mds-sqlserver2019-config-mi-createdbconnect.png "MDS-SQLServer2019-config-MI_CreateDBConnect")  

5. Geben Sie im Feld **Datenbankname** einen Namen ein. Deaktivieren Sie optional das Kontrollkästchen **SQL Server-Standardsortierung**, um eine Windows-Sortierung auszuwählen und mindestens eine verfügbare Option anzugeben, z.B. **Groß-/Kleinschreibung wird beachtet** . Klicken Sie auf **Weiter**.

    ![MDS-SQLServer2019-config-Mi-kreateddbname](../master-data-services/media/mds-sqlserver2019-config-mi-createddbname.png "MDS-SQLServer2019-config-MI_CreatedDBName")  

6. Geben Sie im Feld **Benutzername** das Windows-Konto des Benutzers an, bei dem es sich um den Standard [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]-Super Benutzer für handelt. Ein Administrator verfügt über Zugriff auf alle Funktionsbereiche und kann alle Modelle hinzufügen, löschen oder aktualisieren.

    ![MDS-SQLServer2019-config-Mi-buildsername](../master-data-services/media/mds-sqlserver2019-config-mi-createdbusername.png "MDS-SQLServer2019-config-MI_createDBUserName")

7. Klicken Sie auf **Weiter** , um eine Zusammenfassung der Einstellungen für die [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] -Datenbank anzuzeigen. Klicken Sie anschließend erneut auf **Weiter** , um die Datenbank zu erstellen. Die Seite **Status und Fertig stellen** wird angezeigt.

8. Wenn die Datenbank erstellt und konfiguriert wurde, klicken Sie auf **Fertig stellen**.

    Weitere Informationen zu den Einstellungen im Assistenten zum **Erstellen einer Datenbank**finden Sie unter [Assistent &#40; [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] zum Erstellen&#41;einer Datenbank Configuration Manager](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).

9. Klicken Sie im [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]auf der Seite **Daten Bank Konfiguration** auf **Datenbank auswählen**.

10. Klicken Sie auf **verbinden**, [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] wählen Sie die Datenbank aus, die Sie in Schritt 8 erstellt haben, und klicken Sie auf **OK**.

    ![MDS-SQLServer2019-config-Mi-connectdbname](../master-data-services/media/mds-sqlserver2019-config-mi-connectdbname.png "MDS-SQLServer2019-config-MI_connectDBName")

11. Klicken Sie im [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]im linken Bereich auf **Webkonfiguration** .

12. Klicken Sie im Listenfeld **Website** auf **Standardwebsite**und anschließend auf **Erstellen** , um eine Webanwendung zu erstellen.
![MDS-SQLServer2019-config-Mi-webconfiguration](../master-data-services/media/mds-sqlserver2019-config-mi-webconfiguration.png "MDS-SQLServer2019-config-MI_WebConfiguration")

   > [!NOTE] 
   > Wenn Sie **Standardwebsite**auswählen, müssen Sie eine Webanwendung erstellen. Wenn Sie die Option **Neue Website erstellen** im Listenfeld auswählen, wird die Anwendung automatisch erstellt.

    

13. Geben Sie im Abschnitt **Anwendungs Pool** einen anderen Benutzernamen ein, geben Sie das Kennwort ein, und klicken Sie dann auf OK.
![MDS-SQLServer2019-config-Mi-conatewebapplication](../master-data-services/media/mds-sqlserver2019-config-mi-createwebapplication.png "MDS-SQLServer2019-config-MI_CreateWebApplication")

   > [!NOTE]
   > Sie müssen sicherstellen, dass der Benutzer mit Active Directory integrierten Authentifizierung, die Sie soeben erstellt haben, auf die Datenbank zugreifen kann. Oder Sie müssen die Verbindung später in der Datei "Web. config" ändern.

    

14. Weitere Informationen zum Dialogfeld **Webanwendung erstellen** finden Sie unter [ &#40; [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] Dialogfeld "Webanwendung&#41;erstellen" Configuration Manager](../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md).

15. Klicken Sie auf der Seite **Webkonfiguration** im Feld **Webanwendung** auf die Anwendung, die Sie erstellt haben, und klicken Sie dann im Abschnitt **Anwendung einer Datenbank zuordnen** auf **auswählen** .

16. Klicken Sie auf **Verbinden**, wählen Sie die [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] -Datenbank aus, die Sie der Web-Anwendung zuordnen möchten, und klicken Sie anschließend auf **OK**.

    Somit ist die Einrichtung der Website abgeschlossen. Auf der Seite **Webkonfiguration** werden nun die von Ihnen ausgewählte Website, die von Ihnen erstellte Webanwendung und die [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] der Anwendung zugeordnete Datenbank angezeigt.

    ![MDS-SQLServer2019-config-Mi-webconfigselectdb](../master-data-services/media/mds-sqlserver2019-config-mi-webconfigselectdb.png "MDS-SQLServer2019-config-MI_WebConfigSelectDB")

17. Klicken Sie auf **Übernehmen**. Das Meldungsfeld **Konfiguration abgeschlossen** wird angezeigt. Klicken Sie im Meldungsfeld auf **OK**, um die Webanwendung zu starten. Die Website Adresse lautet http://server "Name"/"Webanwendung/".

## <a name="other-authentication-type-to-connect-managed-instance-database-on-web-application"></a>Anderer Authentifizierungstyp zum Herstellen einer Verbindung mit einer verwalteten Instanzdatenbank in

Wir können die Datei " **Web. config** " unter "c:\Programme\Microsoft SQL server\150\master Data services\webapplication" erhalten. Wir können ConnectionString ändern, um einen anderen Authentifizierungstyp zu ändern, um eine Verbindung mit einer verwalteten Instanz herzustellen

Der Standard Authentifizierungstyp ist "**Active Directory integriert**". im folgenden finden Sie die Beispiel Verbindungs Zeichenfolge.

```xml
<add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;Authentication=&quot;Active Directory Integrated&quot;" />
```

Wir unterstützen auch Active Directory Kenn Wort Authentifizierung und die SQL Server Authentifizierung. im folgenden finden Sie die Beispiel Verbindungs Zeichenfolge.

Active Directory Kenn Wort Authentifizierung

```xml
<add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;Authentication=&quot;Active Directory Password&quot; ; UID=bob@contoso.onmicrosoft.com; PWD=MyPassWord!" />
```

SQL Server-Authentifizierung

```xml
<add name="MDS1" connectionString="Data Source=*****.*****.database.windows.net;Initial Catalog=MasterDataServices;Integrated Security=False;Connect Timeout=60;User ID=UserName;Password=MyPassword!;" />
```

## <a name="upgrade-includessmdsshort_mdincludesssmdsshort-mdmd-and-database-version"></a>Upgrade [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] und Datenbankversion

**Zuführen[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]**

Installieren Sie das **kumulative Update**SQL Server 2019 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] , wird automatisch aktualisiert.

**Aktualisieren der Datenbankversion**

Wenn nach der Installation des **kumulativen Updates SQL Server 2019 das kumulative Update**"die Client Version ist nicht mit der Datenbankversion kompatibel" angezeigt wird, müssen Sie die Datenbankversion aktualisieren.

![MDS-SQLServer2019-config-Mi-upgradebug Page](../master-data-services/media/mds-sqlserver2019-config-mi-upgradedbpage.png "MDS-SQLServer2019-config-MI_UpgradeDBPage")

1. Starten Sie [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]die. Klicken Sie im linken Bereich auf **Daten Bank Konfiguration** .

2. Klicken Sie im [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]auf der Seite **Daten Bank Konfiguration** auf **Datenbank auswählen**.

3. Klicken Sie auf **verbinden**, [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] wählen Sie die Datenbank aus, die Sie der Webanwendung zugeordnet haben, und klicken Sie auf **OK**

    ![MDS-SQLServer2019-config-Mi-connectdbname](../master-data-services/media/mds-sqlserver2019-config-mi-connectdbname.png "MDS-SQLServer2019-config-MI_ConnectDBName")

4. Klicken Sie auf **Datenbank aktualisieren...** Schaltfläche

    ![MDS-SQLServer2019-config-Mi-selectupgrade DB](../master-data-services/media/mds-sqlserver2019-config-mi-selectupgradedb.png "MDS-SQLServer2019-config-MI_SelectUpgradeDB")

5. Klicken Sie im Assistenten zum Aktualisieren von Datenbanken auf der Seite **Willkommen** auf **weiter** , und aktualisieren Sie die **Überprüfungs** Seite.

    ![MDS-SQLServer2019-config-Mi-upgradebug-Assistent](../master-data-services/media/mds-sqlserver2019-config-mi-upgradedbwizard.png "MDS-SQLServer2019-config-MI_UpgradeDBWizard")

6. Klicken Sie nach Abschluss der Aufgabe auf **Fertig** stellen

## <a name="see-also"></a>Siehe auch

 [Master Data Services Datenbank](../master-data-services/master-data-services-database.md) [Webanwendung Master Data Manager](../master-data-services/master-data-manager-web-application.md) [Seite &#40;"Daten Bank&#41; Konfiguration" Konfigurations-Manager für Master Data Services](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md) [Neues in Master Data Services &#40;MDS&#41; ](../master-data-services/what-s-new-in-master-data-services-mds.md)
