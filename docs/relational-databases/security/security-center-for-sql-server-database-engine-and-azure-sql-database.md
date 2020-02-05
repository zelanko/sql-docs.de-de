---
title: Sicherheitsdokumentation für SQL Server und Azure SQL-Datenbank
description: Eine Referenz zu sicherheits- und schutzbezogenen Inhalten für SQL Server und Azure SQL-Datenbank.
ms.custom: seo-lt-2019
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9bf5e128b054bbea218c6b791666f5698c24c37d
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "75557705"
---
# <a name="security-center-for-sql-server-database-engine-and-azure-sql-database"></a>Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Diese Seite enthält Links, mit deren Hilfe Sie die erforderlichen Informationen zur Sicherheit und zum Schutz in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] und [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]finden.  
  
 **Legende**  
  
 ![security-center-legend](../performance/media/security-center-legend.PNG "security-center-legend")  
  
##  <a name="Who"></a> Authentifizierung: Wer sind Sie?  
  
|||  
|-|-|  
|**Wer authentifiziert?**<br /><br /> ![security-center-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Windows-Authentifizierung<br /><br /> ![security-center-both](../performance/media/security-center-both.png "Sicherheitscenter – beide") [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Azure Active Directory|Wer authentifiziert? (Windows oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])<br /><br /> [Auswählen eines Authentifizierungsmodus](../../relational-databases/security/choose-an-authentication-mode.md)<br /><br /> [Herstellen einer Verbindung mit SQL-Datenbank unter Verwendung der Azure Active Directory-Authentifizierung](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)|  
|**Wo authentifiziert?**<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") In der Masterdatenbank: Anmeldenamen und Datenbankbenutzer<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") In der Benutzerdatenbank: Eigenständige Datenbankbenutzer|Authentifizierung bei der Masterdatenbank (Anmeldenamen und Datenbankbenutzer)<br /><br /> [Erstellen eines SQL Server-Anmeldenamens](../../relational-databases/security/authentication-access/create-a-login.md)<br /><br /> [Verwalten von Datenbanken und Anmeldungen in Azure SQL-Datenbank](https://msdn.microsoft.com/library/ee336235.aspx)<br /><br /> [Erstellen eines Datenbankbenutzers](../../relational-databases/security/authentication-access/create-a-database-user.md)<br /><br /> <br /><br /> Authentifizierung bei einer Benutzerdatenbank<br /><br /> [Eigenständige Datenbankbenutzer – Generieren einer portablen Datenbank](../../relational-databases/security/contained-database-users-making-your-database-portable.md)|  
|**Verwenden anderer Identitäten**<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Anmeldeinformationen<br /><br /> ![Sicherheitscenter-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Ausführen unter anderem Anmeldenamen<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Ausführen als anderer Datenbankbenutzer|[Anmeldeinformationen &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)<br /><br /> [Ausführen unter anderem Anmeldenamen](../../t-sql/statements/execute-as-transact-sql.md)<br /><br /> [Ausführen als anderer Datenbankbenutzer](../../t-sql/statements/execute-as-transact-sql.md)|  
  
##  <a name="What"></a> Autorisierung: Was können Sie tun?  
  
|||  
|-|-|  
|**Gewährung, Widerrufen und Verweigern von Berechtigungen**<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Sicherungsfähige Klassen<br /><br /> ![Sicherheitscenter-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Granulare Serverberechtigungen<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Granulare Datenbankberechtigungen|[Berechtigungshierarchie &#40;Datenbank-Engine&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)<br /><br /> [Berechtigungen](../../relational-databases/security/permissions-database-engine.md)<br /><br /> [Sicherungsfähige Elemente](../../relational-databases/security/securables.md)<br /><br /> [Erste Schritte mit Berechtigungen für die Datenbank-Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)|  
|**Sicherheit durch Rollen**<br /><br /> ![Sicherheitscenter-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Rollen auf Serverebene<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Rollen auf Datenbankebene|[Rollen auf Serverebene](../../relational-databases/security/authentication-access/server-level-roles.md)<br /><br /> [Rollen auf Datenbankebene](../../relational-databases/security/authentication-access/database-level-roles.md)|  
|**Einschränken des Datenzugriffs auf ausgewählte Datenelemente**<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Einschränken des Datenzugriffs mit Ansichten/Verfahren<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Sicherheit auf Zeilenebene<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Dynamische Datenmaskierung<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Signierte Objekte|Einschränken des Datenzugriffs mit [Ansichten](../../relational-databases/views/views.md) und [Verfahren](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)<br /><br /> [Sicherheit auf Zeilenebene (SQL Server)](../../relational-databases/security/row-level-security.md)<br /><br /> [Sicherheit auf Zeilenebene (Azure SQL-Datenbank)](https://msdn.microsoft.com/library/azure/dn765131.aspx)<br /><br /> [Dynamische Datenmaskierung (SQL Server)](../../relational-databases/security/dynamic-data-masking.md)<br /><br /> [Dynamische Datenmaskierung (Azure SQL-Datenbank)](https://azure.microsoft.com/documentation/articles/sql-database-dynamic-data-masking-get-started/)<br /><br /> [Signierte Objekte](../../t-sql/statements/add-signature-transact-sql.md)|  
  
##  <a name="Encrypt"></a> Verschlüsselung: Speichern geheimer Schlüssel  
  
|||  
|-|-|  
|**Verschlüsseln von Dateien**<br /><br /> ![Sicherheitscenter-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") BitLocker-Verschlüsselung (Laufwerksebene)<br /><br /> ![Sicherheitscenter-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") NTFS-Verschlüsselung (Ordnerebene)<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Transparente Datenverschlüsselung (Dateiebene)<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Sicherungsverschlüsselung (Dateiebene)|[BitLocker (Laufwerksebene)](https://support.microsoft.com/kb/2855131)<br /><br /> [NTFS-Verschlüsselung (Ordnerebene)](https://msdn.microsoft.com/library/dd163562.aspx)<br /><br /> [Transparente Datenverschlüsselung (Dateiebene)](../../relational-databases/security/encryption/transparent-data-encryption.md)<br /><br /> [Sicherungsverschlüsselung (Dateiebene)](../../relational-databases/backup-restore/backup-encryption.md)|  
|**Verschlüsseln von Quellen**<br /><br /> ![Sicherheitscenter-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Erweiterbares Schlüsselverwaltungsmodul<br /><br /> ![Sicherheitscenter-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Im Azure Schlüsseltresor gespeicherte Schlüssel<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Always Encrypted|[Erweiterbares Schlüsselverwaltungsmodul](../../relational-databases/security/encryption/extensible-key-management-ekm.md)<br /><br /> [Im Azure Schlüsseltresor gespeicherte Schlüssel](../../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md)<br /><br /> [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)|  
|**Spalte, Daten und Schlüsselverschlüsselung**<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Verschlüsseln durch Zertifikat<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Verschlüsseln mit symmetrischem Schlüssel<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Verschlüsseln mit asymmetrischem Schlüssel<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Verschlüsseln durch Passphrase|[Verschlüsseln durch Zertifikat](../../t-sql/functions/encryptbycert-transact-sql.md)<br /><br /> [Verschlüsseln mit asymmetrischem Schlüssel](../../t-sql/functions/encryptbyasymkey-transact-sql.md)<br /><br /> [Verschlüsseln mit symmetrischem Schlüssel](../../t-sql/functions/encryptbykey-transact-sql.md)<br /><br /> [Verschlüsseln durch Passphrase](../../t-sql/functions/encryptbypassphrase-transact-sql.md)<br /><br /> [Verschlüsseln einer Datenspalte](../../relational-databases/security/encryption/encrypt-a-column-of-data.md)|  
  
##  <a name="Connect"></a> Verbindungssicherheit: Einschränken und Schützen  
  
|||  
|-|-|  
|**Firewallschutz**<br /><br /> ![Sicherheitscenter-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Windows-Firewalleinstellungen<br /><br /> ![Sicherheitscenter-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Azure Service-Firewalleinstellungen<br /><br /> ![Sicherheitscenter-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Datenbank-Firewalleinstellungen|[Konfigurieren einer Windows-Firewall für Datenbank-Engine-Zugriff](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)<br /><br /> [Azure SQL-Datenbank-Firewalleinstellungen](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md)<br /><br /> [Azure Service-Firewalleinstellungen](../../relational-databases/system-stored-procedures/sp-set-firewall-rule-azure-sql-database.md)|  
|**Verschlüsseln von Daten in Transit**<br /><br /> ![Sicherheitscenter-beide](../performance/media/security-center-both.png "Sicherheitscenter – beide") Erzwungene SSL-Verbindungen<br /><br /> ![Sicherheitscenter-sqlserver](../performance/media/security-center-sqlserver.png "security-center-sqlserver") Optionale SSL-Verbindungen|[Secure Sockets Layer für die Datenbank-Engine](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)<br /><br /> [Secure Sockets Layer für SQL-Datenbank](https://msdn.microsoft.com/library/azure/ff394108.aspx)<br /><br /> [TLS 1.2-Unterstützung für Microsoft SQL Server](https://support.microsoft.com/kb/3135244)|  
  
##  <a name="Audit"></a> Überwachung: Aufzeichnen des Zugriffs  
  
|||  
|-|-|  
|**Automatisierte Überwachung**<br /><br /> ![security-center-sqlserver](../../relational-databases/performance/media/security-center-sqlserver.png "security-center-sqlserver") [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Überwachung (Server- und Datenbankebene)<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Überwachung (Datenbankebene)<br /><br /> ![security-center-sqldb](../../relational-databases/security/media/security-center-sqldb.png "security-center-sqldb") Erkennen von Bedrohungen| <br /><br /> [SQL Server Audit &#40;Datenbank-Engine&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)<br /><br /> [SQL-Datenbanküberwachung](https://azure.microsoft.com/documentation/articles/sql-database-auditing-get-started/)<br /><br /> [Erste Schritte mit Advanced Threat Protection für Azure SQL-Datenbank](https://azure.microsoft.com/documentation/articles/sql-database-threat-detection-get-started/) <br /><br /> [Sicherheitsrisikobewertung mit der SQL-Datenbank](https://docs.microsoft.com/azure/sql-database/sql-vulnerability-assessment) |  
|**Benutzerdefinierte Überwachung**<br /><br /> ![Sicherheitscenter-beide](../../relational-databases/performance/media/security-center-both.png "Sicherheitscenter – beide") Trigger|Benutzerdefinierte Überwachungsimplementierung: Erstellen von [DDL-Triggern](../../relational-databases/triggers/ddl-triggers.md) und [DML-Triggern](../../relational-databases/triggers/dml-triggers.md)|  
|**Compliance**<br /><br /> ![Sicherheitscenter-beide](../../relational-databases/performance/media/security-center-both.png "Sicherheitscenter – beide") Kompatibilität|SQL Server:<br />                        [Common Criteria](https://go.microsoft.com/fwlink/?LinkId=616319)<br /><br /> SQL-Datenbank:<br />                        [Microsoft Azure Trust Center: Compliance nach Features](https://azure.microsoft.com/support/trust-center/services/)|  
  
##  <a name="SQLInjection"></a> SQL Injection  
 Bei der Einschleusung von SQL-Befehlen wird ein bösartiger Code in Zeichenfolgen eingefügt, die später zur Analyse und Ausführung an [!INCLUDE[ssDE](../../includes/ssde-md.md)] übergeben werden. Sie sollten jede Prozedur, die SQL-Anweisungen erstellt, nach Injection-Anfälligkeiten überprüfen, denn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] führt alle empfangenen gültigen Abfragen aus. Alle Datenbanksysteme unterliegen einem gewissen Risiko für die Einschleusung von SQL-Befehlen, und viele der Sicherheitslücken entstehen in der Anwendung, die [!INCLUDE[ssDE](../../includes/ssde-md.md)]abfragt. Sie können Angriffe, die das Ziel haben, SQL-Befehle einzuschleusen, abwehren, indem Sie gespeicherte Prozeduren und parametrisierte Befehle verwenden, dynamisches SQL vermeiden und die Berechtigungen aller Benutzer einschränken.  Weitere Informationen finden Sie unter [Einschleusung von SQL-Befehlen](../../relational-databases/security/sql-injection.md).  
  
 Zusätzliche Links für Anwendungsprogrammierer:  
  
-   [Anwendungssicherheitsszenarios in SQL Server](/dotnet/framework/data/adonet/sql/application-security-scenarios-in-sql-server)  
  
-   [Schreiben von sicherem dynamischem SQL in SQL Server](/dotnet/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server)  
  
-   [Gewusst wie: Schutz vor Einschleusung von SQL-Befehlen in ASP.NET](https://msdn.microsoft.com/library/ff648339.aspx)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erste Schritte mit Berechtigungen für die Datenbank-Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [Sichern von SQL Server](../../relational-databases/security/securing-sql-server.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [SQL Server-Zertifikate und asymmetrische Schlüssel](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)   
 [SQL Server-Verschlüsselung](../../relational-databases/security/encryption/sql-server-encryption.md)   
 [Oberflächenkonfiguration](../../relational-databases/security/surface-area-configuration.md)   
 [Sichere Kennwörter](../../relational-databases/security/strong-passwords.md)   
 [TRUSTWORTHY-Datenbankeigenschaft](../../relational-databases/security/trustworthy-database-property.md)   
 [Datenbank-Engine-Funktionen und Tasks](https://msdn.microsoft.com/library/d9efe145-3306-4d61-bd77-e2af43e19c34)  
 [Schutz Ihres geistigen SQL Server-Eigentums](../../relational-databases/security/protecting-your-sql-server-intellectual-property.md)   
  
[!INCLUDE[get-help-security](../../includes/get-help-security.md)]
