---
title: Transparente Datenverschlüsselung in Azure SQL-Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- TDE, SQL Database
- Transparent Data Encryption, SQL Database
- encryption (SQL Database) TDE
ms.assetid: 0bf7e8ff-1416-4923-9c4c-49341e208c62
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 541d6d27dc5dbc31dad98840e7ed6654f48a8dfc
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175391"
---
# <a name="transparent-data-encryption-with-azure-sql-database"></a>Transparente Datenverschlüsselung in Azure SQL-Datenbank
  Die transparente Datenverschlüsselung in [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] (Vorschau) unterstützt Maßnahmen zum Schutz vor bösartigen Aktivitäten, indem sie die Verschlüsselung und Entschlüsselung der Datenbank in Echtzeit sowie der ihr zugeordneten Sicherheitskopien und der Transaktionsprotokolle in Ruhephasen vornimmt, ohne Änderungen an der Anwendung zu erfordern.

 TDE verschlüsselt die Speicherung einer gesamten Datenbank, indem ein symmetrischer Schlüssel verwendet wird, der als Datenbankverschlüsselungsschlüssel bezeichnet wird. In [!INCLUDE[ssSDS](../includes/sssds-md.md)] ist der Datenbank-Verschlüsselungsschlüssel durch ein integriertes Serverzertifikat geschützt. Das integrierte Serverzertifikat ist für jeden [!INCLUDE[ssSDS](../includes/sssds-md.md)] -Server eindeutig. Wenn eine Datenbank Teil einer GeoDR-Beziehung ist, wird sie auf jedem Server durch einen anderen Schlüssel geschützt. Wenn zwei Datenbanken mit dem gleichen Server verbunden sind, verwenden sie das gleiche integrierte Zertifikat. 
  [!INCLUDE[msCoName](../includes/msconame-md.md)] tauscht diese Zertifikate mindestens alle 90 Tage automatisch untereinander. Eine allgemeine Beschreibung von TDE finden Sie unter [Transparente Datenverschlüsselung &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md).

 
  [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] unterstützt die Integration des Azure-Schlüsseltresors mit TDE nicht. 
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] kann bei der Ausführung auf einem virtuellen Azure-Computer einen asymmetrischen Schlüssel aus dem Schlüsseltresor verwenden. Weitere Informationen finden Sie unter [Example A: Transparent Data Encryption by Using an Asymmetric Key from the Key Vault](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA).

||
|-|
|**Gilt für**: [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] ([Vorschau in einigen Regionen](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).|

> [!IMPORTANT]
>  Dies ist zurzeit eine Vorschaufunktion. Ich bestätige und erkläre mich damit einverstanden, dass diese Implementierung von transparenter [!INCLUDE[ssSDS](../includes/sssds-md.md)] -Datenverschlüsselung in meinen Datenbanken den Vorschaubedingungen in meinem Lizenzvertrag (z. B. das Enterprise Agreement, Microsoft Azure Agreement oder Microsoft Online-Abonnementvertrag) und gegebenenfalls den [Nutzungsbedingungen für Microsoft Azure Preview](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)unterliegt.

 Die Vorschau des Status von TDE gilt auch in der Teilmenge der geografischen Regionen, in denen die Versionsproduktfamilie V12 von [!INCLUDE[ssSDS](../includes/sssds-md.md)] als jetzt allgemein verfügbar angekündigt wird. TDE für [!INCLUDE[ssSDS](../includes/sssds-md.md)] dient nicht zur Verwendung in den Produktionsdatenbanken bis [!INCLUDE[msCoName](../includes/msconame-md.md)] ankündigt, dass TDE von der Vorschau zu GA heraufgestuft wird. Weitere Informationen zu [!INCLUDE[ssSDS](../includes/sssds-md.md)] V12 finden Sie unter [Neuerungen in Azure SQL-Datenbank](https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/).

##  <a name="Permissions"></a> Berechtigungen
 Um sich für die Vorschau zu registrieren und TDE über das Azure-Portal mithilfe der REST-API oder mithilfe von PowerShell zu konfigurieren,müssen Sie als Azure-Besitzer, Azure-Mitwirkender oder SQL-Sicherheitsmanager verbunden sein.

 Zum Konfigurieren von TDE mithilfe von [!INCLUDE[tsql](../includes/tsql-md.md)] müssen folgende Voraussetzungen erfüllt sein:

-   Sie müssen bereits für die TDE-Vorschau registriert sein.

-   Zum Erstellen des Datenbank-Verschlüsselungsschlüssels müssen Sie ein [!INCLUDE[ssSDS](../includes/sssds-md.md)] -Administrator oder ein Mitglied der Rolle **dbmanager** in der Masterdatenbank sein und über die Berechtigung **STEUERN** für die Datenbank verfügen.

-   Zum Ausführen der Anweisung ALTER DATABASE mit der Option SET ist lediglich die Mitgliedschaft in der Rolle **dbmanager** erforderlich.

##  <a name="Preview"></a>Registrieren für die Vorschau von TDE und Aktivieren von TDE für eine Datenbank

1.  Besuchen Sie das Azure- [https://portal.azure.com](https://portal.azure.com) Portal unter, und melden Sie sich mit Ihrem Azure-Administrator-oder Mitwirkenden Konto an.

2.  Klicken Sie auf dem linken Banner auf **DURCHSUCHEN**, und klicken Sie dann auf **SQL-Datenbanken**.

3.  Klicken Sie auf Ihre Benutzerdatenbank, während im linken Bereich **SQL-Datenbanken** ausgewählt ist.

4.  Klicken Sie auf dem Daten Bank Blatt auf **alle Einstellungen**.

5.  Klicken Sie auf dem Blatt **Einstellungen** auf **transparent Data Encryption (Vorschau)** , um das Blatt **transparente Datenverschlüsselung Vorschau** zu öffnen. Wenn Sie sich noch nicht für die TDE-Vorschau registriert haben, sind die Einstellungen für die Datenverschlüsselung deaktiviert, bis Sie die Registrierung abgeschlossen haben.

6.  Klicken Sie auf **VORSCHAUBESTIMMUNGEN**.

7.  Lesen Sie die Nutzungsbedingungen für die Vorschau. Wenn Sie den Bedingungen zustimmen, aktivieren Sie das Kontrollkästchen **transparente Daten Verschlüsselungs Vorschau** , und klicken Sie dann am unteren Rand der Seite auf **OK** . Zurück zum Blatt " **Daten** Verschlüsselung", auf dem die Schaltfläche " **Datenverschlüsselung** " jetzt aktiviert werden soll.

8.  Schieben Sie auf dem Blatt **Datenverschlüsselung VORSCHAU** den Schalter **Datenverschlüsselung** auf **Ein**, und klicken Sie dann auf **Speichern** (oben auf der Seite), um die Einstellung zu übernehmen. Der **Verschlüsselungs Status** geht ungefähr zum Fortschritt der transparenten Datenverschlüsselung.

     ![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")

     Sie können den Verlauf der Verschlüsselung aber auch überwachen, indem Sie die Verbindung mit [!INCLUDE[ssSDS](../includes/sssds-md.md)] mithilfe eines Abfragetools wie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] als Datenbankbenutzer mit der Berechtigung **DATENBANKSTATUS ANZEIGEN** herstellen. Fragen Sie `encryption_state` die-Spalte der [sys. dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) -Sicht ab.

##  <a name="Encrypt"></a>Aktivieren von TDE [!INCLUDE[ssSDS](../includes/sssds-md.md)] für mithilfe von Transact-SQL
 In den folgenden Schritten wird angenommen, dass Sie sich bereits für die Vorschau registriert haben.

###  <a name="TsqlProcedure"></a>

1.  Stellen Sie eine Verbindung mit der Datenbank mithilfe eines Kontos her, das ein Administratorkonto oder ein Mitglied der Rolle **dbmanager** in der Masterdatenbank ist.

2.  Führen Sie die folgenden Anweisungen aus, um einen Datenbankverschlüsselungsschlüssel zu erstellen und die Datenbank zu verschlüsseln.

    ```sql
    -- Create the database encryption key that will be used for TDE.
    CREATE DATABASE ENCRYPTION KEY 
    WITH ALGORITHM = AES_256 
    ENCRYPTION BY SERVER CERTIFICATE ##MS_TdeCertificate##;

    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;
    GO
    ```

3.  Um den Fortschritt der Verschlüsselung in [!INCLUDE[ssSDS](../includes/sssds-md.md)]zu überwachen, können Datenbankbenutzer mit der **View Database State** -Berechtigung die `encryption_state` -Spalte der [sys. dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) -Sicht Abfragen.

## <a name="enabling-tde-on-sql-database-by-using-powershell"></a>Aktivieren von TDE für SQL-Datenbank mithilfe von PowerShell
 Mithilfe von Azure PowerShell können Sie den folgenden Befehl ausführen, um TDE ein- oder auszuschalten. Sie müssen eine Verbindung Ihres Kontos mit dem PS-Fenster herstellen, bevor Sie den Befehl ausführen. In den folgenden Schritten wird angenommen, dass Sie sich bereits für die Vorschau registriert haben. Weitere Informationen zu PowerShell finden Sie unter [Installieren und Konfigurieren von Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).

1.  Um TDE zu aktivieren, geben Sie den TDE-Status zurück, und zeigen Sie die Veschlüsselungsaktivität an.

    ```powershell
    Switch-AzureMode -Name AzureResourceManager
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"

    Get-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    Get-AzureSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"
    ```

2.  So deaktivieren Sie TDE:

    ```powershell
    Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"
    Switch-AzureMode -Name AzureServiceManagement
    ```

##  <a name="Decrypt"></a>Entschlüsseln einer TDE-geschützten Datenbank auf[!INCLUDE[ssSDS](../includes/sssds-md.md)]

#### <a name="to-disable-tde-by-using-the-azure-portal"></a>So deaktivieren Sie TDE mithilfe des Azure-Portals

1.  Besuchen Sie das Azure- [https://portal.azure.com](https://portal.azure.com) Portal unter, und melden Sie sich mit Ihrem Azure-Administrator-oder Mitwirkenden Konto an.

2.  Klicken Sie auf dem linken Banner auf **DURCHSUCHEN**, und klicken Sie dann auf **SQL-Datenbanken**.

3.  Klicken Sie auf Ihre Benutzerdatenbank, während im linken Bereich **SQL-Datenbanken** ausgewählt ist.

4.  Klicken Sie auf dem Daten Bank Blatt auf **alle Einstellungen**.

5.  Klicken Sie auf dem Blatt **Einstellungen** auf **transparent Data Encryption (Vorschau)** , um das Blatt **transparente Datenverschlüsselung Vorschau** zu öffnen.

6.  Schieben Sie auf dem Blatt **Transparente Datenverschlüsselung VORSCHAU** den Schalter **Datenverschlüsselung** auf **Aus**, und klicken Sie dann auf **Speichern** (oben auf der Seite), um die Einstellung zu übernehmen. Der **Verschlüsselungsstatus** zeigt annähernd den Status der transparenten Datenentschlüsselung an.

     Sie können den Verlauf der Entschlüsselung aber auch überwachen, indem Sie die Verbindung mit [!INCLUDE[ssSDS](../includes/sssds-md.md)] mithilfe eines Abfragetools wie [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] als Datenbankbenutzer mit der Berechtigung **DATENBANKSTATUS ANZEIGEN** herstellen. Fragen Sie `encryption_state` die-Spalte der [sys. dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)-Sicht ab.

#### <a name="to-disable-tde-by-using-transact-sql"></a>So deaktivieren Sie TDE mithilfe von Transact-SQL

1.  Stellen Sie eine Verbindung mit der Datenbank mithilfe eines Kontos her, das ein Administratorkonto oder ein Mitglied der Rolle **dbmanager** in der Masterdatenbank ist.

2.  Führen Sie die folgenden Anweisungen aus, um die Datenbank zu entschlüsseln.

    ```sql
    -- Enable encryption
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;
    GO
    ```

3.  Um den Fortschritt der Verschlüsselung in [!INCLUDE[ssSDS](../includes/sssds-md.md)]zu überwachen, können Datenbankbenutzer mit der **View Database State** -Berechtigung die `encryption_state` -Spalte der [sys. dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) -Sicht Abfragen.

##  <a name="Working"></a>Arbeiten mit durch TDE geschützten Datenbanken auf[!INCLUDE[ssSDS](../includes/sssds-md.md)]
 Für Vorgänge in Azure brauchen Datenbanken nicht entschlüsselt zu werden. Die TDE-Einstellungen für die Quelldatenbank oder die primäre Datenbank werden transparent an das Ziel vererbt. Dazu gehören auch Vorgänge, die dieses beinhalten:

-   Geografische Wiederherstellung

-   Self-Service-Point-In-Time-Wiederherstellung

-   Wiederherstellung einer gelöschten Datenbank

-   Aktive Georeplikation

-   Erstellen einer Datenbankkopie

##  <a name="Moving"></a>Verschieben einer TDE-geschützten Datenbank mithilfe von. BacPac-Dateien
 Beim Exportieren einer durch TDE geschützten Datenbank mithilfe der Funktion „Datenbank exportieren“ im [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)]-Portal oder im [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Import- und -Export-Assistenten werden die Datenbankinhalte nicht verschlüsselt. Die Inhalte werden in BACPAC-Dateien gespeichert, die nicht verschlüsselt sind.  Achten Sie darauf, die BACPAC-Dateien in geeigneter Weise zu schützen und TDE zu aktivieren, sobald der Import der neuen Datenbank abgeschlossen ist.

## <a name="related-sql-server-topic"></a>Verwandte SQL Server-Themen
 [Aktivieren von TDE mithilfe von EKM](../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)

## <a name="see-also"></a>Weitere Informationen
 [Transparent Data Encryption &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md) [Create Credential &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) [Create asymmetrikey &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql) [Create Database Encryption Key &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql) [ALTER DATABASE &#40;Transact-SQL](/sql/t-sql/statements/alter-database-transact-sql)&#41;[ALTER DATABASE Set options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)
