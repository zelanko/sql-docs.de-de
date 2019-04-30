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
ms.openlocfilehash: 1fffca14e9c30c5fd01cff88b7bb90608eb9d30d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63185083"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank
  Diese Seite enthält Links, mit deren Hilfe Sie die erforderlichen Informationen zur Sicherheit und zum Schutz in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]und [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)]finden.  
  
> [!NOTE]  
>  Die Möglichkeiten von [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] werden fortlaufend verbessert. In der aktuellsten Version dieses Themas finden Sie die neuesten Informationen zu [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|Authentifizierung: Wer bist du?|Autorisierung: Was können Sie tun?|Verschlüsselung: Speichern von geheimen Daten|Verbindungssicherheit: Einschränken und sichern|Überwachung: Aufzeichnen des Zugriffs|  
|----------------------------------|-------------------------------------|-------------------------------------|---------------------------------------------------|--------------------------------|  
|**Wer authentifiziert?**<br /><br /> [![Sicherheitscenter zuordnen Windows-Authentifizierung](../../database-engine/media/security-center-map-windows-authenticaion.png "Sicherheitscenter Map-Windows-Authentifizierung")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> <br /><br /> [![Sicherheitscenter zuordnen SQL Server-Authentifizierung](../../database-engine/media/security-center-map-sql-authenticaion.png "Security-Center-Zuordnung SQL Server-Authentifizierung")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> **Wo authentifiziert?**<br /><br /> [![Sicherheitscenter Zuordnen von Anmeldenamen und Benutzer](../../database-engine/media/security-center-map-logins-users.png "Sicherheitscenter Zuordnen von Anmeldenamen und Benutzer")](https://msdn.microsoft.com/library/aa337562.aspx)<br /><br /> <br /><br /> [![Sicherheitscenter Zuordnen von eigenständige Datenbankbenutzer](../../database-engine/media/security-center-map-contained-users.png "Sicherheitscenter Zuordnen von Benutzer eigenständiger Datenbanken")](https://msdn.microsoft.com/library/ff929188.aspx)<br /><br /> **Verwenden anderer Identitäten**<br /><br /> [![Sicherheitscenter Zuordnen von Anmeldeinformationen](../../database-engine/media/security-center-map-credentials.png "Sicherheitscenter Zuordnen von Anmeldeinformationen")](https://msdn.microsoft.com/library/ms161950.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von Execute As Login](../../database-engine/media/security-center-map-exec-as-login.png "Sicherheitscenter Zuordnen von Execute As Login")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von Execute As User](../../database-engine/media/security-center-map-exec-as-user.png "Sicherheitscenter Zuordnen von Execute As User")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")|**Gewährung, Widerrufen und Verweigern von Berechtigungen**<br /><br /> [![Sicherheitscenter Zuordnen von sicherungsfähigen Klassen](../../database-engine/media/security-center-map-securable-classes.png "Sicherheitscenter Zuordnen von sicherungsfähigen Klassen")](https://msdn.microsoft.com/library/ms190401.aspx)<br /><br /> [![Sicherheitscenter – Serverberechtigungen zuordnen](../../database-engine/media/security-center-map-srv-perms.png "Sicherheitscenter – Serverberechtigungen zuordnen")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von Datenbankberechtigungen](../../database-engine/media/security-center-map-db-perms.png "Sicherheitscenter Zuordnen von Datenbankberechtigungen")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> **Sicherheit durch Rollen**<br /><br /> [![Sicherheitscenter – Serverrollen zuordnen](../../database-engine/media/security-center-map-srv-roles.png "Sicherheitscenter – Serverrollen zuordnen")](https://msdn.microsoft.com/library/ms188659.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von Datenbankrollen](../../database-engine/media/security-center-map-db-roles.png "Sicherheitscenter Zuordnen von Datenbankrollen")](https://msdn.microsoft.com/library/ms189121.aspx)<br /><br /> `Restricting Data Access to Selected Data Elements`<br /><br /> [![Sicherheitscenter zuordnen Sichten und Prozeduren](../../database-engine/media/security-center-map-view-procs.png "Sicherheitscenter Ansichten und Prozeduren zuordnen")](https://msdn.microsoft.com/library/ms175503.aspx)<br /><br /> [![Security Center Sicherheit auf Zeilenebene zuordnen](../../database-engine/media/security-center-map-row-level-sec.png "Sicherheitscenter Sicherheit auf Zeilenebene zuordnen")](https://msdn.microsoft.com/library/dn765131.aspx)<br /><br /> [![Sicherheitscenter zuordnen, die dynamische Datenmaskierung](../../database-engine/media/security-center-map-data-masking.png "dynamische Datenmaskierung für Security Center-Zuordnung")](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [![Sicherheitscenter Zuordnen von signierte Objekte](../../database-engine/media/security-center-map-signed-objects.png "Sicherheitscenter Zuordnen von signierte Objekte")](https://msdn.microsoft.com/library/ms181700.aspx)<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")|**Verschlüsseln von Dateien**<br /><br /> [![Sicherheitscenter Zuordnen von BitLocker](../../database-engine/media/security-center-map-bitlocker.png "Sicherheitscenter Zuordnen von BitLocker")](https://support.microsoft.com/en-us/kb/2855131)<br /><br /> [![Sicherheitscenter zuordnen NTFS-Verschlüsselung](../../database-engine/media/security-center-map-ntfs-encryp.png "NTFS-Verschlüsselung von Security Center-Zuordnung")](https://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [![Sicherheitscenter – TDE zuordnen](../../database-engine/media/security-center-map-tde.png "Sicherheitscenter – TDE zuordnen")](https://msdn.microsoft.com/library/bb934049.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von Sicherungsverschlüsselung](../../database-engine/media/security-center-map-backup-encryp.png "Sicherheitscenter Zuordnen von Sicherungsverschlüsselung")](https://msdn.microsoft.com/library/dn449489.aspx)<br /><br /> **Verschlüsseln von Quellen**<br /><br /> [![Sicherheitscenter Zuordnen von EKM](../../database-engine/media/security-center-map-ekm.png "Sicherheitscenter Zuordnen von EKM")](https://msdn.microsoft.com/library/bb895340.aspx)<br /><br /> [![Sicherheitscenter Zuordnen des Azure-Schlüsseltresor](../../database-engine/media/security-center-map-key-vault.png "Sicherheitscenter Zuordnen des Azure-Schlüsseltresor")](http://azure.microsoft.com/documentation/articles/key-vault-get-started/)<br /><br /> **Spalte, Daten und Schlüsselverschlüsselung**<br /><br /> [![Sicherheitscenter Zuordnen von verschlüsseln durch Zertifikat](../../database-engine/media/security-center-map-cert.png "Sicherheitscenter Zuordnen von verschlüsseln durch Zertifikat")](https://msdn.microsoft.com/library/ms188061.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von Verschlüsseln mit symmetrischem Schlüssel](../../database-engine/media/security-center-map-sym-key.png "Sicherheitscenter Zuordnen von Verschlüsseln mit symmetrischem Schlüssel")](https://msdn.microsoft.com/library/ms174361.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von Verschlüsseln mit asymmetrischem Schlüssel](../../database-engine/media/security-center-map-asym-key.png "Sicherheitscenter Zuordnen von Verschlüsseln mit asymmetrischem Schlüssel")](https://msdn.microsoft.com/library/ms186950.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von verschlüsseln durch Passphrase](../../database-engine/media/security-center-map-passphrase.png "Sicherheitscenter Zuordnen von verschlüsseln durch Passphrase")](https://msdn.microsoft.com/library/ms190357.aspx)|**Firewallschutz**<br /><br /> [![Sicherheitscenter zuordnen Windows Firewall](../../database-engine/media/security-center-map-windows-firewall.png "Sicherheitscenter Map-Windows-Firewall")](https://msdn.microsoft.com/library/ms175043.aspx)<br /><br /> [![Sicherheit – Dienstfirewall zuordnen](../../database-engine/media/security-center-map-service-firewall.png "Sicherheit – Dienstfirewall zuordnen")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> [![Sicherheitscenter Zuordnen der Datenbankfirewall](../../database-engine/media/security-center-map-db-firewall.png "Sicherheitscenter Zuordnen der Datenbankfirewall")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> **Verschlüsseln von Daten in Transit**<br /><br /> [![Sicherheitscenter Zuordnen von erzwungenem SSL](../../database-engine/media/security-center-map-forced-ssl.png "Sicherheitscenter Zuordnen von erzwungenem SSL")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> [![Sicherheitscenter Zuordnen des optionale SSL](../../database-engine/media/security-center-map-opt-ssl.png "Sicherheitscenter Zuordnen des optionale SSL")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")|**Automatisierte Überwachung**<br /><br /> [![SQL Server Audit für Security Center zuordnen](../../database-engine/media/security-center-map-sql-audit.png "Sicherheitscenter SQL Server Audit zuordnen")](https://msdn.microsoft.com/library/cc280386.aspx)<br /><br /> [![Sicherheitscenter SQL-Datenbank-Audit zuordnen](../../database-engine/media/security-center-map-sqldb-audit.png "Sicherheitscenter SQL-Datenbank-Audit zuordnen")](http://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> **Benutzerdefinierte Überwachung**<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> [![Sicherheitscenter – Trigger zuordnen](../../database-engine/media/security-center-map-triggers.png "Sicherheitscenter – Trigger zuordnen")](https://msdn.microsoft.com/library/ms175941.aspx)<br /><br /> **Kompatibilität**<br /><br /> [![SecCtrCompliance](../../database-engine/media/secctrcompliance.png "SecCtrCompliance")](http://azure.microsoft.com/support/trust-center/services/)<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Security Center Legend](../../database-engine/media/security-center-map-legend.png "Security Center Legend")|  
  
## <a name="links-to-specific-related-topics"></a>Links zu bestimmten verwandten Themen  
 ![Kleines Dateiordnersymbol](../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **Authentifizierung: Wer bist du?**  
 **Wer authentifiziert? (Windows oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])**  
  
-   [Auswählen eines Authentifizierungsmodus](choose-an-authentication-mode.md)  
  
 **Authentifizierung bei der Masterdatenbank** (Anmeldenamen und Datenbankbenutzer)  
  
-   [Erstellen eines SQL Server-Anmeldenamens](authentication-access/create-a-login.md)  
  
-   [Verwalten von Datenbanken und Anmeldenamen in Azure SQL-Datenbank](https://msdn.microsoft.com/library/ee336235.aspx)  
  
-   [Erstellen eines Datenbankbenutzers](authentication-access/create-a-database-user.md)  
  
 **Authentifizierung bei einer Benutzerdatenbank**  
  
-   [Eigenständige Datenbankbenutzer - machen Sie Ihre Datenbank portabel](contained-database-users-making-your-database-portable.md)  
  
 **Verwenden anderer Identitäten**  
  
-   [Anmeldeinformationen &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](authentication-access/credentials-database-engine.md)  
  
-   [Ausführen unter anderem Anmeldenamen](/sql/t-sql/statements/execute-as-transact-sql)  
  
-   [Ausführen als anderer Datenbankbenutzer](/sql/t-sql/statements/execute-as-transact-sql)  
  
 ![Kleines Dateiordnersymbol](../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **Verschlüsselung: Speichern von geheimen Daten**  
 **Verschlüsseln von Dateien**  
  
-   [BitLocker (Laufwerksebene)](https://support.microsoft.com/kb/2855131)  
  
-   [NTFS-Verschlüsselung (Ordnerebene)](https://msdn.microsoft.com/library/dd163562.aspx)  
  
-   [Transparente Datenverschlüsselung (Dateiebene)](encryption/transparent-data-encryption.md)  
  
-   [Sicherungsverschlüsselung (Dateiebene)](../backup-restore/backup-encryption.md)  
  
 **Verschlüsseln von Quellen**  
  
-   [Erweiterbares Schlüsselverwaltungsmodul](encryption/extensible-key-management-ekm.md)  
  
-   [Im Azure Schlüsseltresor gespeicherte Schlüssel](encryption/extensible-key-management-using-azure-key-vault-sql-server.md)  
  
 **Spalte, Daten und Schlüsselverschlüsselung**  
  
-   [Verschlüsseln durch Zertifikat](/sql/t-sql/functions/encryptbycert-transact-sql)  
  
-   [Verschlüsseln mit asymmetrischem Schlüssel](/sql/t-sql/functions/encryptbyasymkey-transact-sql)  
  
-   [Verschlüsseln mit symmetrischem Schlüssel](/sql/t-sql/functions/encryptbykey-transact-sql)  
  
-   [Verschlüsseln durch Passphrase](/sql/t-sql/functions/encryptbypassphrase-transact-sql)  
  
 ![Kleines Dateiordnersymbol](../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **Autorisierung: Was können Sie tun?**  
 **Gewährung, Widerrufen und Verweigern von Berechtigungen**  
  
-   [Berechtigungshierarchie &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](permissions-hierarchy-database-engine.md)  
  
-   [Berechtigungen](permissions-database-engine.md)  
  
-   [Sicherungsfähige Elemente](securables.md)  
  
 **Sicherheit durch Rollen**  
  
-   [Rollen auf Serverebene](authentication-access/server-level-roles.md)  
  
-   [Rollen auf Datenbankebene](authentication-access/database-level-roles.md)  
  
 `Restricting Data Access to Selected Data Elements`  
  
-   Einschränken des Datenzugriffs mit [Ansichten](../views/views.md) und [Verfahren](../stored-procedures/stored-procedures-database-engine.md)  
  
-   [Sicherheit auf Zeilenebene](https://msdn.microsoft.com/library/azure/dn765131.aspx)  
  
-   [Dynamische Datenmaskierung](http://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
-   [Signierte Objekte](/sql/t-sql/statements/add-signature-transact-sql)  
  
 ![Kleines Dateiordnersymbol](../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **Verbindungssicherheit: Einschränken und sichern**  
 **Firewallschutz**  
  
-   [Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
-   [Azure SQL-Datenbank-Firewalleinstellungen](/sql/relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database)  
  
-   [Azure Service-Firewalleinstellungen](/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database)  
  
 **Verschlüsseln von Daten in Transit**  
  
-   [Secure Sockets Layer für die Datenbank-Engine](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
-   [Secure Sockets Layer für SQL-Datenbank](https://msdn.microsoft.com/library/azure/ff394108.aspx)  
  
 ![Kleines Dateiordnersymbol](../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **Überwachung: Aufzeichnen des Zugriffs**  
 **Automatisierte Überwachung**  
  
-   [SQL Server Audit &amp;#40;Datenbank-Engine&amp;#41;](auditing/sql-server-audit-database-engine.md)  
  
-   [SQL-Datenbanküberwachung](http://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)  
  
 **Benutzerdefinierte Überwachungsimplementierung**  
  
-   Erstellen von [DDL Triggers](../triggers/ddl-triggers.md) und [DML Triggers](../triggers/dml-triggers.md)  
  
 ![Kleines Dateiordnersymbol](../../integration-services/media/filefolder-small.gif "Small File Folder Icon") **Compliance**  
 **SQL Server**  
  
-   [Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319)  
  
 **SQL-Datenbank**  
  
-   [Microsoft Azure Trust Center: Compliance nach Features](http://azure.microsoft.com/support/trust-center/services/)  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von SQL Server](securing-sql-server.md)   
 [Prinzipale &amp;#40;Datenbank-Engine&amp;#41;](authentication-access/principals-database-engine.md)   
 [SQL Server-Zertifikate und asymmetrische Schlüssel](sql-server-certificates-and-asymmetric-keys.md)   
 [SQL Server-Verschlüsselung](encryption/sql-server-encryption.md)   
 [Oberflächenkonfiguration](surface-area-configuration.md)   
 [Sichere Kennwörter](strong-passwords.md)   
 [TRUSTWORTHY-Datenbankeigenschaft](trustworthy-database-property.md)   
 [Datenbank-Engine-Funktionen und Tasks](../../database-engine/database-engine-features-and-tasks.md)  
  
  
