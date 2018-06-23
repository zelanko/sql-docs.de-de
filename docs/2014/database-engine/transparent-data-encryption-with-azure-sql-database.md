---
title: Transparente Datenverschlüsselung in Azure SQL-Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-security
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TDE, SQL Database
- Transparent Data Encryption, SQL Database
- encryption (SQL Database) TDE
ms.assetid: 0bf7e8ff-1416-4923-9c4c-49341e208c62
caps.latest.revision: 31
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 1850458778cadbfe871880d42a7830c94078c2a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160492"
---
# <a name="transparent-data-encryption-with-azure-sql-database"></a>Transparente Datenverschlüsselung in Azure SQL-Datenbank
  [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] Transparente datenverschlüsselung (Vorschau) schützt gegen das Risiko einer böswilligen Aktivität anhand der Echtzeit Ver- und Entschlüsselung der Datenbank, zugehörige Sicherungen und Transaktionsprotokolldateien ruhende ohne Änderungen an der Anwendung.  
  
 TDE verschlüsselt den Speicher einer ganze Datenbank mithilfe dieses symmetrischen Schlüssels, der als Verschlüsselungsschlüssel für die Datenbank bezeichnet wird. In [!INCLUDE[ssSDS](../includes/sssds-md.md)] ist der Datenbank-Verschlüsselungsschlüssel durch ein integriertes Serverzertifikat geschützt. Das integrierte Serverzertifikat ist für jeden [!INCLUDE[ssSDS](../includes/sssds-md.md)] -Server eindeutig. Wenn sich eine Datenbank in einer GeoDR-Beziehung befindet, ist sie auf jedem Server durch einen anderen Schlüssel geschützt. Wenn zwei Datenbanken mit dem gleichen Server verbunden sind, verwenden sie das gleiche integrierte Zertifikat. [!INCLUDE[msCoName](../includes/msconame-md.md)] tauscht diese Zertifikate mindestens alle 90 Tage automatisch untereinander. Eine allgemeine Beschreibung von TDE finden Sie unter [Transparente Datenverschlüsselung &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md).  
  
 [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] unterstützt die Integration des Azure-Schlüsseltresors mit TDE nicht. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] kann bei der Ausführung auf einem virtuellen Azure-Computer einen asymmetrischen Schlüssel aus dem Schlüsseltresor verwenden. Weitere Informationen finden Sie unter [Beispiel A: Transparente datenverschlüsselung mit einem asymmetrischen Schlüssel aus dem Schlüsseltresor](../relational-databases/security/encryption/extensible-key-management-using-azure-key-vault-sql-server.md#ExampleA).  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[sqldbesa](../includes/sqldbesa-md.md)] ([Vorschau in einigen Regionen](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).|  
  
> [!IMPORTANT]  
>  Dies ist zurzeit eine Vorschaufunktion. Ich bestätige und stimme zu, dass diese Implementierung des [!INCLUDE[ssSDS](../includes/sssds-md.md)] -datenverschlüsselung in meinen Datenbanken den vorschaubestimmungen in meinem Lizenzvertrag (z. B. das Enterprise Agreement, Microsoft Azure Agreement oder Microsoft Online Subscription unterliegt Vereinbarung) sowie allen anwendbaren [ergänzenden Nutzungsbedingungen für Microsoft Azure Preview](http://azure.microsoft.com/support/legal/preview-supplemental-terms/).  
  
 Die Vorschau des Status von TDE gilt auch in der Teilmenge der geografischen Regionen, in denen die Versionsproduktfamilie V12 von [!INCLUDE[ssSDS](../includes/sssds-md.md)] als jetzt allgemein verfügbar angekündigt wird. TDE für [!INCLUDE[ssSDS](../includes/sssds-md.md)] dient nicht zur Verwendung in den Produktionsdatenbanken bis [!INCLUDE[msCoName](../includes/msconame-md.md)] ankündigt, dass TDE von der Vorschau zu GA heraufgestuft wird. Weitere Informationen zu [!INCLUDE[ssSDS](../includes/sssds-md.md)] V12 finden Sie unter [Neuerungen in Azure SQL-Datenbank](http://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/).  
  
##  <a name="Permissions"></a> Berechtigungen  
 Um sich für die Vorschau zu registrieren und TDE über das Azure-Portal mithilfe der REST-API oder mithilfe von PowerShell zu konfigurieren,müssen Sie als Azure-Besitzer, Azure-Mitwirkender oder SQL-Sicherheitsmanager verbunden sein.  
  
 Zum Konfigurieren von TDE mithilfe von [!INCLUDE[tsql](../includes/tsql-md.md)] müssen folgende Voraussetzungen erfüllt sein:  
  
-   Sie müssen bereits für die TDE-Vorschau registriert sein.  
  
-   Um den Datenbankverschlüsselungsschlüssel erstellen müssen Sie eine [!INCLUDE[ssSDS](../includes/sssds-md.md)] Administrator, oder Sie müssen Mitglied der der **Dbmanager** -Rolle in der Master-Datenbank und über die **Steuerelement** Berechtigung für die Datenbank.  
  
-   Zum Ausführen der Anweisung ALTER DATABASE mit der Option SET ist lediglich die Mitgliedschaft in der Rolle **dbmanager** erforderlich.  
  
##  <a name="Preview"></a> Registrieren für die Vorschau von TDE und Aktivieren von TDE für eine Datenbank  
  
1.  Besuchen Sie das Azure-Portal unter [ https://portal.azure.com ](https://portal.azure.com) und melden Sie sich mit Ihrem Azure-Administrator- oder Mitwirkendenkonto an.  
  
2.  Klicken Sie auf dem linken Banner auf **DURCHSUCHEN**, und klicken Sie dann auf **SQL-Datenbanken**.  
  
3.  Klicken Sie auf Ihre Benutzerdatenbank, während **SQL-Datenbanken** im linken Bereich ausgewählt ist.  
  
4.  Klicken Sie auf dem Datenbankblatt auf **Alle Einstellungen**.  
  
5.  Klicken Sie auf dem Blatt **Einstellungen** auf das Part **Transparente Datenverschlüsselung (Vorschau)** , um das Blatt **Transparente Datenverschlüsselung VORSCHAU** zu öffnen. Wenn Sie sich noch nicht für die TDE-Vorschau registriert haben, sind die Einstellungen für die Datenverschlüsselung deaktiviert, bis Sie die Registrierung abgeschlossen haben.  
  
6.  Klicken Sie auf **VORSCHAUBESTIMMUNGEN**.  
  
7.  Lesen Sie die Bedingungen der Preview aus, und wenn Sie den Bedingungen zustimmen, wählen Sie die **Transparent Data EncryptionPreview Begriffe** Kontrollkästchen, und klicken Sie dann auf **OK** unten auf der Seite. Zum Zurückgeben der **Daten EncryptionPREVIEW** Blatt, in dem die **datenverschlüsselung** Schaltfläche sollte jetzt aktiviert sein.  
  
8.  Schieben Sie auf dem Blatt **Datenverschlüsselung VORSCHAU** den Schalter **Datenverschlüsselung** auf **Ein**, und klicken Sie dann auf **Speichern** (oben auf der Seite), um die Einstellung zu übernehmen. Der **Verschlüsselungsstatus** ist eine ungefähre Angabe zum Fortschritt der transparenten Datenverschlüsselung.  
  
     ![SQLDB_TDE_TermsNewUI](../../2014/database-engine/media/sqldb-tde-termsnewui.png "SQLDB_TDE_TermsNewUI")  
  
     Sie können den Verlauf der Verschlüsselung aber auch überwachen, indem Sie die Verbindung mit [!INCLUDE[ssSDS](../includes/sssds-md.md)] mithilfe eines Abfragetools wie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] als Datenbankbenutzer mit der Berechtigung **DATENBANKSTATUS ANZEIGEN** herstellen. Abfrage der `encryption_state` Spalte die [dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) anzeigen.  
  
##  <a name="Encrypt"></a> Aktivieren von TDE für [!INCLUDE[ssSDS](../includes/sssds-md.md)] mithilfe von Transact-SQL  
 In den folgenden Schritten wird angenommen, dass Sie sich bereits für die Vorschau registriert haben.  
  
###  <a name="TsqlProcedure"></a>  
  
1.  Stellen Sie eine Verbindung mit der Datenbank mithilfe eines Kontos her, das ein Administratorkonto oder ein Mitglied der Rolle **dbmanager** in der Masterdatenbank ist.  
  
2.  Führen Sie die folgenden Anweisungen aus, um einen Datenbankverschlüsselungsschlüssel zu erstellen und die Datenbank zu verschlüsseln.  
  
    ```  
    -- Create the database encryption key that will be used for TDE.  
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_256   
    ENCRYPTION BY SERVER CERTIFICATE ##MS_TdeCertificate##;  
  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION ON;  
    GO  
    ```  
  
3.  Überwachen Sie den Verlauf der Verschlüsselung auf [!INCLUDE[ssSDS](../includes/sssds-md.md)], Datenbankbenutzer mit der **VIEW DATABASE STATE** Berechtigung kann Abfragen der `encryption_state` Spalte die [dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) Zeigen Sie an.  
  
## <a name="enabling-tde-on-sql-database-by-using-powershell"></a>Aktivieren von TDE für SQL-Datenbank mithilfe von PowerShell  
 Mithilfe von Azure PowerShell können Sie den folgenden Befehl ausführen, um TDE ein- oder auszuschalten. Sie müssen eine Verbindung Ihres Kontos mit dem PS-Fenster herstellen, bevor Sie den Befehl ausführen. In den folgenden Schritten wird angenommen, dass Sie sich bereits für die Vorschau registriert haben. Weitere Informationen zu PowerShell finden Sie unter [Installieren und Konfigurieren von Azure PowerShell](http://azure.microsoft.com/documentation/articles/powershell-install-configure/).  
  
1.  Um TDE zu aktivieren, geben Sie den TDE-Status zurück, und zeigen Sie die Veschlüsselungsaktivität an.  
  
    ```  
    PS C:\> Switch-AzureMode -Name AzureResourceManager  
  
    PS C:\> Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Enabled"  
  
    PS C:\> Get-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
  
    PS C:\> Get-AzureSqlDatabaseTransparentDataEncryptionActivity -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1"  
  
    ```  
  
2.  So deaktivieren Sie TDE:  
  
    ```  
    PS C:\> Set-AzureSqlDatabaseTransparentDataEncryption -ServerName "myserver" -ResourceGroupName "Default-SQL-WestUS" -DatabaseName "database1" -State "Disabled"  
  
    PS C:\> Switch-AzureMode -Name AzureServiceManagement  
    ```  
  
##  <a name="Decrypt"></a> Entschlüsseln Sie eine mithilfe von TDE geschützte Datenbank auf [!INCLUDE[ssSDS](../includes/sssds-md.md)]  
  
#### <a name="to-disable-tde-by-using-the-azure-portal"></a>So deaktivieren Sie TDE mithilfe des Azure-Portals  
  
1.  Besuchen Sie das Azure-Portal unter [ https://portal.azure.com ](https://portal.azure.com) und melden Sie sich mit Ihrem Azure-Administrator- oder Mitwirkendenkonto an.  
  
2.  Klicken Sie auf dem linken Banner auf **DURCHSUCHEN**, und klicken Sie dann auf **SQL-Datenbanken**.  
  
3.  Klicken Sie auf Ihre Benutzerdatenbank, während **SQL-Datenbanken** im linken Bereich ausgewählt ist.  
  
4.  Klicken Sie auf dem Datenbankblatt auf **Alle Einstellungen**.  
  
5.  Klicken Sie auf dem Blatt **Einstellungen** auf das Part **Transparente Datenverschlüsselung (Vorschau)** , um das Blatt **Transparente Datenverschlüsselung VORSCHAU** zu öffnen.  
  
6.  Schieben Sie auf dem Blatt **Transparente Datenverschlüsselung VORSCHAU** den Schalter **Datenverschlüsselung** auf **Aus**, und klicken Sie dann auf **Speichern** (oben auf der Seite), um die Einstellung zu übernehmen. Der **Verschlüsselungsstatus** zeigt annähernd den Status der transparenten Datenentschlüsselung an.  
  
     Sie können den Verlauf der Entschlüsselung aber auch überwachen, indem Sie die Verbindung mit [!INCLUDE[ssSDS](../includes/sssds-md.md)] mithilfe eines Abfragetools wie [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] als Datenbankbenutzer mit der Berechtigung **DATENBANKSTATUS ANZEIGEN** herstellen. Abfrage der `encryption_state` Spalte die [dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql)anzeigen.  
  
#### <a name="to-disable-tde-by-using-transact-sql"></a>So deaktivieren Sie TDE mithilfe von Transact-SQL  
  
1.  Stellen Sie eine Verbindung mit der Datenbank mithilfe eines Kontos her, das ein Administratorkonto oder ein Mitglied der Rolle **dbmanager** in der Masterdatenbank ist.  
  
2.  Führen Sie die folgenden Anweisungen aus, um die Datenbank zu entschlüsseln.  
  
    ```  
    -- Enable encryption  
    ALTER DATABASE [AdventureWorks] SET ENCRYPTION OFF;  
    GO  
    ```  
  
3.  Überwachen Sie den Verlauf der Verschlüsselung auf [!INCLUDE[ssSDS](../includes/sssds-md.md)], Datenbankbenutzer mit der **VIEW DATABASE STATE** Berechtigung kann Abfragen der `encryption_state` Spalte die [dm_database_encryption_keys](/sql/relational-databases/system-dynamic-management-views/sys-dm-database-encryption-keys-transact-sql) Zeigen Sie an.  
  
##  <a name="Working"></a> Arbeiten mit durch TDE geschützten Datenbanken in [!INCLUDE[ssSDS](../includes/sssds-md.md)]  
 Für Vorgänge in Azure brauchen Datenbanken nicht entschlüsselt zu werden. Die TDE-Einstellungen für die Quelldatenbank oder die primäre Datenbank werden transparent an das Ziel vererbt. Dazu gehören auch Vorgänge, die dieses beinhalten:  
  
-   Geowiederherstellung  
  
-   Self-Service-Point-In-Time-Wiederherstellung  
  
-   Wiederherstellung einer gelöschten Datenbank  
  
-   Aktive Georeplikation  
  
-   Erstellen einer Datenbankkopie  
  
##  <a name="Moving"></a> Verschieben einer durch TDE geschützten Datenbanken mithilfe von. Bacpac-Dateien  
 Beim Exportieren einer durch TDE geschützten Datenbank mithilfe von der Funktion "Datenbank exportieren" in der [!INCLUDE[ssSDSfull](../includes/sssdsfull-md.md)] Portal oder die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Import / Export-Assistenten die Datenbankinhalte nicht verschlüsselt. Die Inhalte werden in BACPAC-Dateien gespeichert, die nicht verschlüsselt sind.  Achten Sie darauf, die BACPAC-Dateien in geeigneter Weise zu schützen und TDE zu aktivieren, sobald der Import der neuen Datenbank abgeschlossen ist.  
  
## <a name="related-sql-server-topic"></a>Verwandte SQL Server-Themen  
 [Aktivieren von TDE mit EKM](../relational-databases/security/encryption/enable-tde-on-sql-server-using-ekm.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Transparente Datenverschlüsselung &#40;TDE&#41;](../relational-databases/security/encryption/transparent-data-encryption.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)   
 [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
