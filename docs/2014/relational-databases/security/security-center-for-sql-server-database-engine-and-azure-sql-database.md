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
ms.openlocfilehash: 3eeea022cff74d2ca8ddb636d9f83e4d369529bc
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85004107"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank
  Diese Seite enthält Links, mit deren Hilfe Sie die erforderlichen Informationen zur Sicherheit und zum Schutz in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]und [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)]finden.  
  
> [!NOTE]  
>  Die Möglichkeiten von [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] werden fortlaufend verbessert. In der aktuellsten Version dieses Themas finden Sie die neuesten Informationen zu [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
|Authentifizierung: Wer sind Sie?|Autorisierung: Was können Sie tun?|Verschlüsselung: Speichern geheimer Schlüssel|Verbindungssicherheit: Einschränken und Schützen|Überwachung: Aufzeichnen des Zugriffs|  
|----------------------------------|-------------------------------------|-------------------------------------|---------------------------------------------------|--------------------------------|  
|**Wer authentifiziert?**<br /><br /> [![Sicherheitscenter – Windows-Authentifizierung zuordnen](../../database-engine/media/security-center-map-windows-authenticaion.png "Sicherheitscenter – Windows-Authentifizierung zuordnen")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> <br /><br /> [![Sicherheitscenter Zuordnen von SQL Server-Authentifizierung](../../database-engine/media/security-center-map-sql-authenticaion.png "Sicherheitscenter Zuordnen von SQL Server-Authentifizierung")](https://msdn.microsoft.com/library/ms144284.aspx)<br /><br /> **Wo authentifiziert?**<br /><br /> [![Sicherheitscenter Zuordnen von Anmeldenamen und Benutzern](../../database-engine/media/security-center-map-logins-users.png "Sicherheitscenter Zuordnen von Anmeldenamen und Benutzern")](https://msdn.microsoft.com/library/aa337562.aspx)<br /><br /> <br /><br /> [![Sicherheitscenter Zuordnen von Benutzern eigenständiger Datenbanken](../../database-engine/media/security-center-map-contained-users.png "Sicherheitscenter Zuordnen von Benutzern eigenständiger Datenbanken")](https://msdn.microsoft.com/library/ff929188.aspx)<br /><br /> **Verwenden anderer Identitäten**<br /><br /> [![Sicherheitscenter Zuordnen von Anmeldeinformationen](../../database-engine/media/security-center-map-credentials.png "Sicherheitscenter Zuordnen von Anmeldeinformationen")](https://msdn.microsoft.com/library/ms161950.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von EXECUTE AS LOGIN](../../database-engine/media/security-center-map-exec-as-login.png "Sicherheitscenter Zuordnen von EXECUTE AS LOGIN")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von EXECUTE AS USER](../../database-engine/media/security-center-map-exec-as-user.png "Sicherheitscenter Zuordnen von EXECUTE AS USER")](https://msdn.microsoft.com/library/ms181362.aspx)<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")|**Gewährung, Widerrufen und Verweigern von Berechtigungen**<br /><br /> [![Sicherheitscenter – Sicherungsfähige Klassen zuordnen](../../database-engine/media/security-center-map-securable-classes.png "Sicherheitscenter – Sicherungsfähige Klassen zuordnen")](https://msdn.microsoft.com/library/ms190401.aspx)<br /><br /> [![Sicherheitscenter – Serverberechtigungen zuordnen](../../database-engine/media/security-center-map-srv-perms.png "Sicherheitscenter – Serverberechtigungen zuordnen")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von Datenbankberechtigungen](../../database-engine/media/security-center-map-db-perms.png "Sicherheitscenter Zuordnen von Datenbankberechtigungen")](https://msdn.microsoft.com/library/ms191291.aspx)<br /><br /> **Sicherheit durch Rollen**<br /><br /> [![Sicherheitscenter – Serverrollen zuordnen](../../database-engine/media/security-center-map-srv-roles.png "Sicherheitscenter – Serverrollen zuordnen")](https://msdn.microsoft.com/library/ms188659.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von Datenbankrollen](../../database-engine/media/security-center-map-db-roles.png "Sicherheitscenter Zuordnen von Datenbankrollen")](https://msdn.microsoft.com/library/ms189121.aspx)<br /><br /> `Restricting Data Access to Selected Data Elements`<br /><br /> [![Sicherheitscenter – Ansichten und Prozeduren zuordnen](../../database-engine/media/security-center-map-view-procs.png "Sicherheitscenter – Ansichten und Prozeduren zuordnen")](https://msdn.microsoft.com/library/ms175503.aspx)<br /><br /> [![Sicherheitscenter – Sicherheit auf Zeilenebene zuordnen](../../database-engine/media/security-center-map-row-level-sec.png "Sicherheitscenter – Sicherheit auf Zeilenebene zuordnen")](https://msdn.microsoft.com/library/dn765131.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von dynamischer Datenmaskierung](../../database-engine/media/security-center-map-data-masking.png "Sicherheitscenter Zuordnen von dynamischer Datenmaskierung")](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [![Sicherheitscenter – Signierte Objekte zuordnen](../../database-engine/media/security-center-map-signed-objects.png "Sicherheitscenter – Signierte Objekte zuordnen")](https://msdn.microsoft.com/library/ms181700.aspx)<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")|**Verschlüsseln von Dateien**<br /><br /> [![Sicherheitscenter Zuordnen von BitLocker](../../database-engine/media/security-center-map-bitlocker.png "Sicherheitscenter Zuordnen von BitLocker")](https://support.microsoft.com/kb/2855131)<br /><br /> [![Sicherheitscenter Zuordnen der NTFS-Verschlüsselung](../../database-engine/media/security-center-map-ntfs-encryp.png "Sicherheitscenter Zuordnen der NTFS-Verschlüsselung")](https://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [![Sicherheitscenter – TDE zuordnen](../../database-engine/media/security-center-map-tde.png "Sicherheitscenter – TDE zuordnen")](https://msdn.microsoft.com/library/bb934049.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von Sicherungsverschlüsselung](../../database-engine/media/security-center-map-backup-encryp.png "Sicherheitscenter Zuordnen von Sicherungsverschlüsselung")](https://msdn.microsoft.com/library/dn449489.aspx)<br /><br /> **Verschlüsseln von Quellen**<br /><br /> [![Sicherheitscenter Zuordnen von EKM](../../database-engine/media/security-center-map-ekm.png "Sicherheitscenter Zuordnen von EKM")](https://msdn.microsoft.com/library/bb895340.aspx)<br /><br /> [![Sicherheitscenter Zuordnen des Azure-Schlüsseltresors](../../database-engine/media/security-center-map-key-vault.png "Sicherheitscenter Zuordnen des Azure-Schlüsseltresors")](https://azure.microsoft.com/documentation/articles/key-vault-get-started/)<br /><br /> **Spalte, Verschlüsselung von Daten & Schlüsseln**<br /><br /> [![Security Center Zuordnung verschlüsseln nach Zertifikat](../../database-engine/media/security-center-map-cert.png "Security Center Zuordnung verschlüsseln nach Zertifikat")](https://msdn.microsoft.com/library/ms188061.aspx)<br /><br /> [![Sicherheitscenter – Verschlüsselung mit symmetrischem Schlüssel zuordnen](../../database-engine/media/security-center-map-sym-key.png "Sicherheitscenter – Verschlüsselung mit symmetrischem Schlüssel zuordnen")](https://msdn.microsoft.com/library/ms174361.aspx)<br /><br /> [![Sicherheitscenter Zuordnen von Verschlüsseln mit asymmetrischem Schlüssel](../../database-engine/media/security-center-map-asym-key.png "Sicherheitscenter Zuordnen von Verschlüsseln mit asymmetrischem Schlüssel")](https://msdn.microsoft.com/library/ms186950.aspx)<br /><br /> [![Sicherheitscenter – Verschlüsselung durch Passphrase zuordnen](../../database-engine/media/security-center-map-passphrase.png "Sicherheitscenter – Verschlüsselung durch Passphrase zuordnen")](https://msdn.microsoft.com/library/ms190357.aspx)|**Firewallschutz**<br /><br /> [![Sicherheitscenter – Windows Firewall zuordnen](../../database-engine/media/security-center-map-windows-firewall.png "Sicherheitscenter – Windows Firewall zuordnen")](https://msdn.microsoft.com/library/ms175043.aspx)<br /><br /> [![Sicherheitscenter – Dienstfirewall zuordnen](../../database-engine/media/security-center-map-service-firewall.png "Sicherheitscenter – Dienstfirewall zuordnen")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> [![Sicherheitscenter Zuordnen der Datenbankfirewall](../../database-engine/media/security-center-map-db-firewall.png "Sicherheitscenter Zuordnen der Datenbankfirewall")](https://msdn.microsoft.com/library/azure/ee621782.aspx)<br /><br /> **Verschlüsseln von Daten in Transit**<br /><br /> [![Sicherheitscenter Zuordnen von erzwungenem SSL](../../database-engine/media/security-center-map-forced-ssl.png "Sicherheitscenter Zuordnen von erzwungenem SSL")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> [![Sicherheitscenter – optionale SSL-Verschlüsselung zuordnen](../../database-engine/media/security-center-map-opt-ssl.png "Sicherheitscenter – optionale SSL-Verschlüsselung zuordnen")](https://msdn.microsoft.com/library/ms191192.aspx)<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")|**Automatisierte Überwachung**<br /><br /> [![Sicherheitscenter – SQL Server Audit zuordnen](../../database-engine/media/security-center-map-sql-audit.png "Sicherheitscenter – SQL Server Audit zuordnen")](https://msdn.microsoft.com/library/cc280386.aspx)<br /><br /> [![Sicherheitscenter – SQL-Datenbank-Audit zuordnen](../../database-engine/media/security-center-map-sqldb-audit.png "Sicherheitscenter – SQL-Datenbank-Audit zuordnen")](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> **Benutzerdefinierte Überwachung**<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> [![Sicherheitscenter – Trigger zuordnen](../../database-engine/media/security-center-map-triggers.png "Sicherheitscenter – Trigger zuordnen")](https://msdn.microsoft.com/library/ms175941.aspx)<br /><br /> **Compliance**<br /><br /> [!["Scctrcompliance"](../../database-engine/media/secctrcompliance.png ""Scctrcompliance"")](https://azure.microsoft.com/support/trust-center/services/)<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Platzhalter](../../database-engine/media/security-center-map-blankplaceholder.png "Platzhalter")<br /><br /> ![Sicherheitscenter Legende](../../database-engine/media/security-center-map-legend.png "Sicherheitscenter Legende")|  
  
## <a name="links-to-specific-related-topics"></a>Links zu bestimmten verwandten Themen  
 ![Kleine Datei Ordnersymbol](../../integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") - **Authentifizierung: Wer sind Sie?**  
 **Wer authentifiziert? (Windows oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] )**  
  
-   [Auswählen eines Authentifizierungsmodus](choose-an-authentication-mode.md)  
  
 **Authentifizieren bei der Master-Datenbank** (Anmeldungen und Datenbankbenutzer)  
  
-   [Erstellen eines SQL Server-Anmeldenamens](authentication-access/create-a-login.md)  
  
-   [Verwalten von Datenbanken und Anmeldungen in Azure SQL-Datenbank](https://msdn.microsoft.com/library/ee336235.aspx)  
  
-   [Erstellen eines Datenbankbenutzers](authentication-access/create-a-database-user.md)  
  
 **Authentifizierung bei einer Benutzerdatenbank**  
  
-   [Eigenständige Datenbankbenutzer – Generieren einer portablen Datenbank](contained-database-users-making-your-database-portable.md)  
  
 **Verwenden anderer Identitäten**  
  
-   [Anmeldeinformationen &#40;Datenbank-Engine&#41;](authentication-access/credentials-database-engine.md)  
  
-   [Ausführen unter anderem Anmeldenamen](/sql/t-sql/statements/execute-as-transact-sql)  
  
-   [Ausführen als anderer Datenbankbenutzer](/sql/t-sql/statements/execute-as-transact-sql)  
  
 ![Kleines Datei Ordnersymbol](../../integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") **Verschlüsselung: Speichern geheimer Daten**  
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
  
 ![Kleine Datei Ordnersymbol](../../integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") - **Autorisierung: Was können Sie tun?**  
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
  
-   [dynamische Datenmaskierung](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)  
  
-   [Signierte Objekte](/sql/t-sql/statements/add-signature-transact-sql)  
  
 ![Kleines Datei Ordnersymbol](../../integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") **Verbindungssicherheit: einschränken und sichern**  
 **Firewallschutz**  
  
-   [Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)  
  
-   [Azure SQL-Datenbank-Firewalleinstellungen](/sql/relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database)  
  
-   [Azure Service-Firewalleinstellungen](/sql/relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database)  
  
 **Verschlüsseln von Daten in Transit**  
  
-   [Secure Sockets Layer für die Datenbank-Engine](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
-   [Secure Sockets Layer für SQL-Datenbank](https://msdn.microsoft.com/library/azure/ff394108.aspx)  
  
 ![Kleines Datei Ordnersymbol](../../integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") Überwachung **: Aufzeichnen des Zugriffs**  
 **Automatisierte Überwachung**  
  
-   [SQL Server Audit &#40;Datenbank-Engine&#41;](auditing/sql-server-audit-database-engine.md)  
  
-   [SQL-Datenbanküberwachung](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)  
  
 **Benutzerdefinierte Überwachungs Implementierung**  
  
-   Erstellen von [DDL Triggers](../triggers/ddl-triggers.md) und [DML Triggers](../triggers/dml-triggers.md)  
  
 ![Kleines Datei Ordnersymbol](../../integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") **Konformität**  
 **SQL Server**  
  
-   [Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319)  
  
 **SQL-Datenbank**  
  
-   [Microsoft Azure Trust Center: Compliance nach Funktion](https://azure.microsoft.com/support/trust-center/services/)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern von SQL Server](securing-sql-server.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](authentication-access/principals-database-engine.md)   
 [SQL Server-Zertifikate und asymmetrische Schlüssel](sql-server-certificates-and-asymmetric-keys.md)   
 [SQL Server-Verschlüsselung](encryption/sql-server-encryption.md)   
 [Oberflächenkonfiguration](surface-area-configuration.md)   
 [Sichere Kennwörter](strong-passwords.md)   
 [TRUSTWORTHY-Datenbankeigenschaft](trustworthy-database-property.md)   
 [Datenbank-Engine-Funktionen und Tasks](../../database-engine/database-engine-features-and-tasks.md)  
  
  
