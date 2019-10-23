---
title: Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- Security [SQL Server]
helpviewer_keywords:
- SQL Server, security
- security [SQL Server]
- database security [SQL Server]
- databases [SQL Server], security
ms.assetid: dfb39d16-722a-4734-94bb-98e61e014ee7
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 131fb3639f84c1b59796d59bcfff17159da8f063
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028659"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank
  Diese Seite enthält Links, mit deren Hilfe Sie die erforderlichen Informationen zur Sicherheit und zum Schutz in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]und [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)]finden.  
  
> [!NOTE]  
>  Die Möglichkeiten von [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] werden fortlaufend verbessert. In der aktuellsten Version dieses Themas finden Sie die neuesten Informationen zu [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|Genehmigung Wer sind Sie?|Autorisierungs Was können Sie tun?|Verschlüsselungs Speichern geheimer Daten|Verbindungssicherheit: Einschränken und Sichern|Überwachung: Aufzeichnen des Zugriffs|  
|----------------------------------|-------------------------------------|-------------------------------------|---------------------------------------------------|--------------------------------|  
|**Wer authentifiziert?**<br /><br /> [![Security Center](../../database-engine/media/security-center-map-windows-authenticaion.png "Zuordnung der Windows-Authentifizierung Security Center")](https://msdn.microsoft.com/library/ms144284.aspx) Zuordnung der Windows-Authentifizierung<br /><br /> <br /><br /> [![Security Center Karte SQL Server Authentifizierung](../../database-engine/media/security-center-map-sql-authenticaion.png "Security Center Karte SQL Server Authentifizierung")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> **Wo authentifiziert?**<br /><br /> [![Security Center Zuordnung von Anmeldungen und Benutzern](../../database-engine/media/security-center-map-logins-users.png " Security Center Zuordnung von Anmeldungen und Benutzern")](https://msdn.microsoft.com/library/aa337562.aspx)<br /><br /> <br /><br /> [![Security Center Zuordnung von eigenständigen Datenbankbenutzern](../../database-engine/media/security-center-map-contained-users.png "Security Center Zuordnung von eigenständigen Datenbankbenutzern")](https://msdn.microsoft.com/library/ff929188.aspx)<br /><br /> **Verwenden anderer Identitäten**<br /><br /> [![Security Center Karten Anmelde](../../database-engine/media/security-center-map-credentials.png " Informationen Security Center Karten Anmelde")](https://msdn.microsoft.com/library/ms161950.aspx) Informationen<br /><br /> [![Security Center Zuordnung EXECUTE AS Login](../../database-engine/media/security-center-map-exec-as-login.png "Security Center Zuordnung EXECUTE AS Login")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> [![Security Center Zuordnung als Benutzer ausführen](../../database-engine/media/security-center-map-exec-as-user.png "Security Center Zuordnung als Benutzer ausführen")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")|**Gewährung, Widerrufen und Verweigern von Berechtigungen**<br /><br /> [Security Center Zuordnen von Sicherungs ![fähigen Klassen](../../database-engine/media/security-center-map-securable-classes.png " Security Center Zuordnen von Sicherungs fähigen Klassen")](https://msdn.microsoft.com/library/ms190401.aspx)<br /><br /> [![Security Center Map Server-Berechtigungen](../../database-engine/media/security-center-map-srv-perms.png "Security Center Map Server-Berechtigungen")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> [![Security Center Zuordnen von Daten Bank Berechtigungen](../../database-engine/media/security-center-map-db-perms.png "Security Center Zuordnen von Daten Bank Berechtigungen")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> **Sicherheit durch Rollen**<br /><br /> [![Security Center Map-Server Rollen](../../database-engine/media/security-center-map-srv-roles.png "Security Center Map-Server Rollen")](https://msdn.microsoft.com/library/ms188659.aspx)<br /><br /> [![Security Center Zuordnen von Daten bankrollen](../../database-engine/media/security-center-map-db-roles.png "Security Center Zuordnen von Daten bankrollen")](https://msdn.microsoft.com/library/ms189121.aspx)<br /><br /> `Restricting Data Access to Selected Data Elements`<br /><br /> [![Security Center Karten Sichten und-Prozeduren](../../database-engine/media/security-center-map-view-procs.png "Security Center Karten Sichten und-Prozeduren")](https://msdn.microsoft.com/library/ms175503.aspx)<br /><br /> [![Security Center Karte Sicherheit auf Zeilenebene](../../database-engine/media/security-center-map-row-level-sec.png "Security Center Karte Sicherheit auf Zeilenebene")](https://msdn.microsoft.com/library/dn765131.aspx)<br /><br /> [![Security Center Karte dynamische Datenmaskierung](../../database-engine/media/security-center-map-data-masking.png "Security Center Karte dynamische Datenmaskierung")](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [![Security Center Map-signierte Objekte](../../database-engine/media/security-center-map-signed-objects.png "Security Center Map-signierte Objekte")](https://msdn.microsoft.com/library/ms181700.aspx)<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")|**Verschlüsseln von Dateien**<br /><br /> [![BitLocker Security Center Map](../../database-engine/media/security-center-map-bitlocker.png "BitLocker Security Center Map")](https://support.microsoft.com/en-us/kb/2855131)<br /><br /> [![Security Center Zuordnung der NTFS-Verschlüsselung](../../database-engine/media/security-center-map-ntfs-encryp.png "Security Center Zuordnung der NTFS-Verschlüsselung")](https://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [![TDE Security Center Map](../../database-engine/media/security-center-map-tde.png "TDE Security Center Map")](https://msdn.microsoft.com/library/bb934049.aspx)<br /><br /> [![Security Center Zuordnung der Sicherungs Verschlüsselung](../../database-engine/media/security-center-map-backup-encryp.png "Security Center Zuordnung der Sicherungs Verschlüsselung")](https://msdn.microsoft.com/library/dn449489.aspx)<br /><br /> **Verschlüsseln von Quellen**<br /><br /> [![EKM Security Center Map](../../database-engine/media/security-center-map-ekm.png "EKM Security Center Map")](https://msdn.microsoft.com/library/bb895340.aspx)<br /><br /> [![Security Center Karte Azure Key Vault](../../database-engine/media/security-center-map-key-vault.png "Security Center Karte Azure Key Vault")](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)<br /><br /> **Spalte, Verschlüsselung von Daten & Schlüsseln**<br /><br /> [![Security Center Zuordnung verschlüsseln nach Zertifikat](../../database-engine/media/security-center-map-cert.png "Security Center Zuordnung verschlüsseln nach Zertifikat")](https://msdn.microsoft.com/library/ms188061.aspx)<br /><br /> [![Security Center Zuordnung verschlüsseln durch symmetrischen Schlüssel](../../database-engine/media/security-center-map-sym-key.png "Security Center Zuordnung verschlüsseln durch symmetrischen Schlüssel")](https://msdn.microsoft.com/library/ms174361.aspx)<br /><br /> [![Security Center Zuordnung verschlüsseln mit asymmetrischem Schlüssel](../../database-engine/media/security-center-map-asym-key.png "Security Center Zuordnung verschlüsseln mit asymmetrischem Schlüssel")](https://msdn.microsoft.com/library/ms186950.aspx)<br /><br /> [![Security Center Zuordnung verschlüsseln durch Passphrase](../../database-engine/media/security-center-map-passphrase.png "Security Center Zuordnung verschlüsseln durch Passphrase")](https://msdn.microsoft.com/library/ms190357.aspx)|**Firewallschutz**<br /><br /> [![Security Center Zuordnung der Windows-Firewall](../../database-engine/media/security-center-map-windows-firewall.png "Security Center Zuordnung der Windows-Firewall")](https://msdn.microsoft.com/library/ms175043.aspx)<br /><br /> [![Security Center Map-Dienst Firewall](../../database-engine/media/security-center-map-service-firewall.png "Security Center Map-Dienst Firewall")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> [![Security Center Map Database Firewall](../../database-engine/media/security-center-map-db-firewall.png "Security Center Map Database Firewall")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> **Verschlüsseln von Daten in Transit**<br /><br /> [![Security Center Zuordnung erzwungenes SSL](../../database-engine/media/security-center-map-forced-ssl.png "Security Center Zuordnung erzwungenes SSL")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> [![Optionales Security Center Map-SSL](../../database-engine/media/security-center-map-opt-ssl.png "Optionales Security Center Map-SSL")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")|**Automatisierte Überwachung**<br /><br /> [![Security Center Map SQL Server Audit](../../database-engine/media/security-center-map-sql-audit.png "Security Center Map SQL Server Audit")](https://msdn.microsoft.com/library/cc280386.aspx)<br /><br /> [![SQL-Daten Bank Überwachung Security Center Map](../../database-engine/media/security-center-map-sqldb-audit.png "SQL-Daten Bank Überwachung Security Center Map")](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> **Benutzerdefinierte Überwachung**<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> [![Security Center Map-Trigger](../../database-engine/media/security-center-map-triggers.png "Security Center Map-Trigger")](https://msdn.microsoft.com/library/ms175941.aspx)<br /><br /> **Kompatibilität**<br /><br /> [![Scctrcompliance](../../database-engine/media/secctrcompliance.png "Scctrcompliance")](https://azure.microsoft.com/support/trust-center/services/)<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Security Center Legende](../../database-engine/media/security-center-map-legend.png "Security Center Legende")|  
  
## <a name="links-to-specific-related-topics"></a>Links zu bestimmten verwandten Themen  
 ![Kleines Datei Ordnersymbol](../../integration-services/media/filefolder-small.gif "Kleines Datei Ordnersymbol") **Authentifizierung: Wer bist du?**  
 **Wer authentifiziert? (Windows oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])**  
  
-   [Auswählen eines Authentifizierungsmodus](choose-an-authentication-mode.md)  
  
 **Authentifizierung bei der Masterdatenbank** (Anmeldenamen und Datenbankbenutzer)  
  
-   [Erstellen eines SQL Server-Anmeldenamens](authentication-access/create-a-login.md)  
  
-   [Verwalten von Datenbanken und Anmeldenamen in Azure SQL-Datenbank](https://msdn.microsoft.com/library/ee336235.aspx)  
  
-   [Erstellen eines Datenbankbenutzers](authentication-access/create-a-database-user.md)  
  
 **Authentifizieren bei einer Benutzerdatenbank**  
  
-   [Eigenständige Datenbankbenutzer - machen Sie Ihre Datenbank portabel](contained-database-users-making-your-database-portable.md)  
  
 **Verwenden anderer Identitäten**  
  
-   [Anmeldeinformationen &#40;Datenbank-Engine&#41;](authentication-access/credentials-database-engine.md)  
  
-   [Ausführen unter anderem Anmeldenamen](/sql/t-sql/statements/execute-as-transact-sql)  
  
-   [Ausführen als anderer Datenbankbenutzer](/sql/t-sql/statements/execute-as-transact-sql)  
  
 ![Kleines Datei Ordnersymbol](../../integration-services/media/filefolder-small.gif "Kleines Datei Ordnersymbol") **Verschlüsselung: Speichern von geheimen Daten**  
 **Verschlüsseln von Dateien**  
  
-   [BitLocker (Laufwerksebene)](https://support.microsoft.com/kb/2855131)  
  
-   [NTFS-Verschlüsselung (Ordnerebene)](https://msdn.microsoft.com/library/dd163562.aspx)  
  
-   [Transparente Datenverschlüsselung (Dateiebene)](encryption/transparent-data-encryption.md)  
  
-   [Sicherungsverschlüsselung (Dateiebene)](../backup-restore/backup-encryption.md)  
  
 **Verschlüsseln von Quellen**  
  
-   [Erweiterbares Schlüsselverwaltungsmodul](encryption/extensible-key-management-ekm.md)  
  
-   [Im Azure Schlüsseltresor gespeicherte Schlüssel](encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 **Spalten-, Daten-und Schlüssel Verschlüsselung**  
  
-   [Verschlüsseln durch Zertifikat](/sql/t-sql/functions/encryptbycert-transact-sql)  
  
-   [Verschlüsseln mit asymmetrischem Schlüssel](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
  
-   [Verschlüsseln mit symmetrischem Schlüssel](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [Verschlüsseln durch Passphrase](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
  
 ![Kleines Datei Ordnersymbol](../../integration-services/media/filefolder-small.gif "Kleines Datei Ordnersymbol") **Autorisierung: Was können Sie tun?**  
 **Gewährung, Widerrufen und Verweigern von Berechtigungen**  
  
-   [Berechtigungshierarchie &#40;Datenbank-Engine&#41;](permissions-hierarchy-database-engine.md)  
  
-   [Berechtigungen](permissions-database-engine.md)  
  
-   [Sicherungsfähige Elemente](securables.md)  
  
 **Sicherheit durch Rollen**  
  
-   [Rollen auf Serverebene](authentication-access/server-level-roles.md)  
  
-   [Rollen auf Datenbankebene](authentication-access/database-level-roles.md)  
  
 `Restricting Data Access to Selected Data Elements`  
  
-   Einschränken des Datenzugriffs mit [Ansichten](../views/views.md) und [Verfahren](../stored-procedures/stored-procedures-database-engine.md)  
  
-   [Sicherheit auf Zeilenebene](https://msdn.microsoft.com/library/azure/dn765131.aspx)  
  
-   [Dynamische Datenmaskierung](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
-   [Signierte Objekte](/sql/t-sql/statements/add-signature-transact-sql)  
  
 ![Kleines Datei Ordnersymbol](../../integration-services/media/filefolder-small.gif "Kleines Datei Ordnersymbol") **Verbindungssicherheit: Einschränken und sichern**  
 **Firewallschutz**  
  
-   [Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
-   [Azure SQL-Datenbank-Firewalleinstellungen](/sql/relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database)  
  
-   [Azure Service-Firewalleinstellungen](/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database)  
  
 **Verschlüsseln von Daten in Transit**  
  
-   [Secure Sockets Layer für die Datenbank-Engine](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
-   [Secure Sockets Layer für SQL-Datenbank](https://msdn.microsoft.com/library/azure/ff394108.aspx)  
  
 ![Kleines Datei Ordnersymbol](../../integration-services/media/filefolder-small.gif "Kleines Datei Ordnersymbol") **Überwachung: Aufzeichnen des Zugriffs**  
 **Automatisierte Überwachung**  
  
-   [SQL Server Audit &#40;Datenbank-Engine&#41;](auditing/sql-server-audit-database-engine.md)  
  
-   [SQL-Datenbanküberwachung](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)  
  
 **Benutzerdefinierte Überwachungs Implementierung**  
  
-   Erstellen von [DDL Triggers](../triggers/ddl-triggers.md) und [DML Triggers](../triggers/dml-triggers.md)  
  
 ![Kleines Datei Ordnersymbol](../../integration-services/media/filefolder-small.gif "Kleines Datei Ordnersymbol") **Konformität**  
 **SQL Server**  
  
-   [Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319)  
  
 **SQL-Datenbank**  
  
-   [Microsoft Azure Trust Center: Compliance nach Funktion](https://azure.microsoft.com/support/trust-center/services/)  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von SQL Server](securing-sql-server.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](authentication-access/principals-database-engine.md)   
 [SQL Server-Zertifikate und asymmetrische Schlüssel](sql-server-certificates-and-asymmetric-keys.md)   
 [SQL Server-Verschlüsselung](encryption/sql-server-encryption.md)   
 [Oberflächenkonfiguration](surface-area-configuration.md)   
 [Sichere Kennwörter](strong-passwords.md)   
 [TRUSTWORTHY-Datenbankeigenschaft](trustworthy-database-property.md)   
 [Datenbank-Engine-Funktionen und Tasks](../../database-engine/database-engine-features-and-tasks.md)  
  
  
