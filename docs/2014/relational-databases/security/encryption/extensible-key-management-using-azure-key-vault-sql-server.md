---
title: Erweiterbare Schlüsselverwaltung mit Azure Key Vault (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- EKM, with key vault
- TDE, EKM and key vault
- Extensible Key Management with key vault
- Key Management with key vault
- Transparent Data Encryption, using EKM and key vault
ms.assetid: 3efdc48a-8064-4ea6-a828-3fbf758ef97c
author: jaszymas
ms.author: jaszymas
manager: craigg
ms.openlocfilehash: 9591b483380d8bfcaea8404cccfa0279d3bcc035
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74957196"
---
# <a name="extensible-key-management-using-azure-key-vault-sql-server"></a>Erweiterbare Schlüsselverwaltung mit Azure Key Vault (SQL Server)
  Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Connector für [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure Key Vault ermöglicht [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Verschlüsselung, um den Azure Key Vault-Dienst als [erweiterbare Schlüsselverwaltung &#40;EKM-&#41;](extensible-key-management-ekm.md) Anbieter zum Schutz seiner Verschlüsselungsschlüssel zu nutzen.  
  
 In diesem Thema:  
  
-   [Verwendungsmöglichkeiten für erweiterbare Schlüsselverwaltung](#Uses)  
  
-   [Schritt 1: Einrichten des Schlüsseltresors für die Verwendung durch SQL Server](#Step1)  
  
-   [Schritt 2: Installieren des SQL Server-Connectors](#Step2)  
  
-   [Schritt 3: Konfigurieren von SQL Server zur Verwendung eines Anbieters für erweiterbare Schlüsselverwaltung für den Schlüsseltresor](#Step3)  
  
-   [Beispiel A: Transparente Datenverschlüsselung mit einem asymmetrischen Schlüssel aus dem Schlüsseltresor](#ExampleA)  
  
-   [Beispiel B: Verschlüsseln von Sicherungen mit einem asymmetrischen Schlüssel aus dem Schlüsseltresor](#ExampleB)  
  
-   [Beispiel C: Verschlüsselung auf Spaltenebene mit einem asymmetrischen Schlüssel aus dem Schlüsseltresor](#ExampleC)  
  
##  <a name="Uses"></a>Verwendung von EKM  
 Organisationen können die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verschlüsselung zum Schutz sensibler Daten verwenden. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]die Verschlüsselung umfasst [transparent Data Encryption &#40;TDE&#41;](transparent-data-encryption.md), [Verschlüsselung auf Spaltenebene](/sql/t-sql/functions/cryptographic-functions-transact-sql) (CLE) und [Sicherungs Verschlüsselung](../../backup-restore/backup-encryption.md). In all diesen Fällen werden die Daten mit einem symmetrischen Datenverschlüsselungsschlüssel verschlüsselt. Der symmetrische Datenverschlüsselungsschlüssel wird außerdem geschützt durch Verschlüsselung mit einer Hierarchie von Schlüsseln, die in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]gespeichert sind. Alternativ bietet die Architektur des Anbieters für erweiterbare Schlüsselverwaltung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Möglichkeit, die Datenverschlüsselungsschlüssel mit einem asymmetrischen Schlüssel zu schützen, der außerhalb von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in einem externen Kryptografieanbieter gespeichert ist. Die Verwendung der Architektur des Anbieters für erweiterbare Schlüsselverwaltung stellt eine zusätzliche Sicherheitsebene dar und ermöglicht Unternehmen die getrennte Verwaltung von Schlüsseln und Daten.  
  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Connector für die Azure Key Vault-Vorschau ermöglicht [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] die Nutzung des skalierbaren, leistungsfähigen und hochverfügbaren Schlüsseltresordiensts als EKM-Anbieter für den Schutz des Verschlüsselungsschlüssels. Der Schlüsseltresordienst kann mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Installationen auf virtuellen [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Azure-Computern und für lokale Server verwendet werden. Der Schlüsseltresordienst bietet auch die Option, genau gesteuerte und stark überwachte Hardwaresicherheitsmodule (HSMs) für ein höheres Maß an Schutz für asymmetrische Schlüssel zu verwenden. Weitere Informationen zum Schlüsseltresor finden Sie unter [Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521401).  
  
 Die folgende Grafik enthält eine Zusammenfassung des Prozessablaufs der erweiterbaren Schlüsselverwaltung mit Schlüsseltresor. Die Nummern der Prozessschritte in der Grafik stimmen nicht mit den Nummern der Einrichtungsschritte, die auf die Grafik folgen, überein.  
  
 ![Erweiterbare Schlüsselverwaltung in SQL Server mithilfe von Azure Key Vault](../../../database-engine/media/ekm-using-azure-key-vault.png "Erweiterbare Schlüsselverwaltung in SQL Server mithilfe von Azure Key Vault")  
  
##  <a name="Step1"></a>Schritt 1: Einrichten der Key Vault für die Verwendung durch SQL Server  
 Führen Sie die folgenden Schritte aus, um einen Schlüsseltresor für die Verwendung mit der [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] für den Schutz des Verschlüsselungsschlüssels einzurichten. Für die Organisation wird möglicherweise bereits ein Tresor verwendet. Wenn kein Tresor vorhanden ist, kann der Azure-Administrator in Ihrem Unternehmen, der die Verschlüsselungsschlüssel verwaltet, einen Tresor erstellen, einen asymmetrischen Schlüssel im Tresor generieren und dann [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] autorisieren, den Schlüssel zu verwenden. Machen Sie sich unter [Erste Schritte mit Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402)und der Referenz zu PowerShell- [Azure Key Vault-Cmdlets](https://docs.microsoft.com/powershell/module/azurerm.keyvault) mit dem Schlüsseltresordienst vertraut.  
  
> [!IMPORTANT]  
>  Wenn Sie über mehrere Azure-Abonnements verfügen, müssen Sie das Abonnement nehmen, das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]enthält.  
  
1.  **Erstellen Sie einen Tresor:** Erstellen Sie einen Tresor mithilfe der Anweisungen im Abschnitt **Erstellen eines Schlüssel** Tresors in " [Get Started with Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402)". Notieren Sie den Namen des Tresors. In diesem Thema wird **ContosoKeyVault** als Schlüsseltresorname verwendet.  
  
2.  **Generieren Sie einen asymmetrischen Schlüssel im Tresor:** Der asymmetrische Schlüssel im Schlüssel Tresor dient zum Schutz [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der Verschlüsselungsschlüssel. Nur der öffentliche Teil des asymmetrischen Schlüssels verlässt jemals den Tresor, der private Teil wird nie vom Tresor exportiert. Alle kryptografischen Vorgänge mit dem asymmetrischen Schlüssel werden an den Azure-Schlüsseltresor delegiert und durch die Schlüsseltresorsicherheit geschützt.  
  
     Es gibt mehrere Möglichkeiten, wie Sie einen asymmetrischen Schlüssel generieren und im Tresor speichern können. Sie können einen Schlüssel extern generieren und den Schlüssel als PFX-Datei in den Tresor importieren. Oder Sie erstellen den Schlüssel mit den Schlüsseltresor-APIs direkt im Tresor.  
  
     Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Connector erfordert asymmetrische Schlüssel nach 2048-Bit-RSA, und der Name des Schlüssels darf nur die Zeichen „a–z“, „A–Z“, „0–9“ und „-“ enthalten. In diesem Dokument wird als Name des asymmetrischen Schlüssels **ContosoMasterKey**verwendet. Ersetzen Sie dies durch den eindeutigen Namen, den Sie für den Schlüssel verwenden.  
  
    > [!IMPORTANT]  
    >  Das Importieren des asymmetrischen Schlüssels wird für Produktionsszenarien dringend empfohlen, da der Administrator dann den Schlüssel in einem Schlüsselhinterlegungssystem hinterlegen kann. Wenn der asymmetrische Schlüssel im Tresor erstellt wird, kann er nicht hinterlegt werden, da der private Schlüssel nie den Tresor verlassen kann. Schlüssel zum Schützen wichtiger Daten sollten hinterlegt werden. Der Verlust eines asymmetrischen Schlüssels führt dazu, dass Daten dauerhaft nicht wiederhergestellt werden können.  
  
    > [!IMPORTANT]  
    >  Der Schlüsseltresor unterstützt mehrere Versionen desselben benannten Schlüssels. Schlüssel zur Verwendung durch den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Connector sollten nicht mit Versionsangabe versehen oder mehrfach wieder verwendet werden. Wenn der Administrator den Schlüssel für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verschlüsselung wieder verwenden möchte, sollte ein neuer Schlüssel mit einem anderen Namen im Tresor erstellt und zum Verschlüsseln des Datenverschlüsselungsschlüssels verwendet werden.  
  
     Weitere Informationen zum Importieren eines Schlüssels in den Tresor oder zum Erstellen eines Schlüssels im Schlüsseltresor (nicht empfohlen für Produktionsumgebungen) finden Sie im Abschnitt **Hinzufügen eines Schlüssels oder eines geheimen Schlüssels zum Schlüsseltresor** in [Erste Schritte mit Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).  
  
3.  **Holen Sie sich Azure Active Directory Dienst Prinzipale, die für SQL Server verwendet werden sollen:** Wenn sich die Organisation für einen Microsoft-clouddienst registriert, erhält Sie einen Azure Active Directory. Erstellen Sie in Azure Active Directory **Dienstprinzipale** , die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (zur Authentifizierung gegenüber Azure Active Directory) beim Zugriff auf den Schlüsseltresor verwendet.  
  
    -   Ein **Dienstprinzipal** wird von einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Administrator benötigt, um beim Konfigurieren von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] für die Verschlüsselung auf den Tresor zuzugreifen.  
  
    -   Ein anderer **Dienstprinzipal** wird von der [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] benötigt, um beim Entpacken von zur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verschlüsselung verwendeten Schlüsseln auf den Tresor zuzugreifen.  
  
     Weitere Informationen zum Registrieren einer Anwendung und Generieren eines Dienstprinzipals finden Sie im Abschnitt **Registrieren einer Anwendung in Azure Active Directory** in [Erste Schritte mit Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402). Der Registrierungsprozess gibt eine **Anwendungs-ID** (auch bekannt als **CLIENT-ID**) und einen **Authentifizierungsschlüssel** (auch bekannt als **geheimer Schlüssel**) für jeden Azure Active Directory- **Dienstprinzipal**zurück. Wenn Sie in der `CREATE CREDENTIAL` -Anweisung verwendet wird, muss der Bindestrich aus der **Client-ID**entfernt werden. Notieren Sie diese für die Verwendung in den unten stehenden Skripts:  
  
    -   **Dienst Prinzipal** für eine **sysadmin** -Anmeldung: **CLIENTID_sysadmin_login** und **SECRET_sysadmin_login**  
  
    -   **Dienst Prinzipal** für [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]die: **CLIENTID_DBEngine** und **SECRET_DBEngine**.  
  
4.  **Erteilen Sie dem Dienst Prinzipal die Berechtigung, auf die Key Vault zuzugreifen:** Sowohl der **CLIENTID_sysadmin_login** als auch **CLIENTID_DBEngineService Prinzipale** benötigen die Berechtigungen **Get**, **List**, **wrapkey**und **unwrapkey** im Schlüssel Tresor. Wenn Sie beabsichtigen, Schlüssel über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zu erstellen, müssen Sie auch die Berechtigung **create** im Schlüsseltresor erteilen.  
  
    > [!IMPORTANT]  
    >  Benutzer müssen mindestens über die Vorgänge **wrapkey** und **unwrapkey** für den Schlüssel Tresor verfügen.  
  
     Weitere Informationen zum Erteilen von Berechtigungen für den Tresor finden Sie im Abschnitt **Autorisieren der Anwendung zum Verwenden des Schlüssels oder des geheimen Schlüssels** in [Erste Schritte mit Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402).  
  
     Links zur Dokumentation für Azure Key Vault  
  
    -   [Was ist der Azure-Schlüsseltresor?](https://go.microsoft.com/fwlink/?LinkId=521401)  
  
    -   [Erste Schritte mit Azure Key Vault](https://go.microsoft.com/fwlink/?LinkId=521402)  
  
    -   Referenz der PowerShell- [Azure Key Vault-Cmdlets](https://docs.microsoft.com/powershell/module/azurerm.keyvault)  
  
##  <a name="Step2"></a>Schritt 2: Installieren des SQL Server-Connector  
 Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Connector wird vom Administrator des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Computers heruntergeladen und installiert. Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Connector steht im [Microsoft-Downloadcenter](https://go.microsoft.com/fwlink/p/?LinkId=521700)als Download zur Verfügung.  Suchen Sie nach **SQL Server-Connector für Microsoft Azure Key Vault**. Überprüfen Sie die Details, Systemanforderungen und Installationsanweisungen, wählen Sie den Download des Connectors, und starten Sie die Installation mit **Ausführen**. Lesen Sie die Lizenzbedingungen, stimmen Sie ihnen zu, und setzen Sie den Vorgang fort.  
  
 In der Standardeinstellung der Connector installiert ist, auf **C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault**. Dieser Speicherort kann während des Setups geändert werden. (Wenn Sie ihn ändern, passen Sie die unten angegebenen Skripts entsprechend an.)  
  
 Nach Abschluss der Installation ist Folgendes auf dem Computer installiert:  
  
-   **Microsoft. azurekeyvaultservice. EKM. dll**: Dies ist die kryptografiekm-Anbieter-DLL, die bei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mit der Create kryptografischen Provider-Anweisung registriert werden muss.  
  
-   **Azure Key Vault SQL Server-Connector**: Hierbei handelt es sich um einen Windows-Dienst, der dem kryptografiekm-Anbieter die Kommunikation mit dem Schlüssel Tresor ermöglicht.  
  
 Bei der Installation des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Connectors können Sie optional auch Beispielskripts für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verschlüsselung herunterladen.  
  
##  <a name="Step3"></a>Schritt 3: Konfigurieren von SQL Server für die Verwendung eines EKM-Anbieters für das Key Vault  
  
###  <a name="Permissions"></a> Berechtigungen  
 Das gesamte Verfahren erfordert die CONTROL SERVER-Berechtigung oder die Mitgliedschaft in der festen Serverrolle **sysadmin** . Bestimmte Aktionen erfordern die folgenden Berechtigungen:  
  
-   Zum Erstellen eines Kryptografieanbieters ist die CONTROL SERVER-Berechtigung oder die Mitgliedschaft in der festen Serverrolle **sysadmin** erforderlich.  
  
-   Zum Ändern einer Konfigurationsoption und Ausführen der RECONFIGURE-Anweisung muss Ihnen die ALTER SETTINGS-Berechtigung auf Serverebene erteilt worden sein. Die ALTER SETTINGS-Berechtigung ist in den festen Serverrollen **sysadmin** und **serveradmin** eingeschlossen.  
  
-   Zum Erstellen von Anmeldeinformationen ist die ALTER ANY CREDENTIAL-Berechtigung erforderlich.  
  
-   Zum Hinzufügen von Anmeldeinformationen zu einem Anmeldenamen ist die ALTER ANY LOGIN-Berechtigung erforderlich.  
  
-   Zum Erstellen eines asymmetrischen Schlüssels ist die CREATE ASYMMETRIC KEY-Berechtigung erforderlich.  
  
###  <a name="TsqlProcedure"></a>So konfigurieren Sie SQL Server für die Verwendung eines Kryptografieanbieters  
  
1.  Konfigurieren Sie die [!INCLUDE[ssDE](../../../includes/ssde-md.md)] für die Verwendung der erweiterbaren Schlüsselverwaltung, und registrieren (erstellen) Sie den Kryptografieanbieter in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
    ```sql
    -- Enable advanced options.  
    USE master;  
    GO  
  
    sp_configure 'show advanced options', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
    -- Enable EKM provider  
    sp_configure 'EKM provider enabled', 1 ;  
    GO  
    RECONFIGURE ;  
    GO  
  
    -- Create a cryptographic provider, using the SQL Server Connector  
    -- which is an EKM provider for the Azure Key Vault. This example uses   
    -- the name AzureKeyVault_EKM_Prov.  
  
    CREATE CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov   
    FROM FILE = 'C:\Program Files\SQL Server Connector for Microsoft Azure Key Vault\Microsoft.AzureKeyVaultService.EKM.dll';  
    GO
    ```  
  
2.  Richten Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldeinformationen für eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Administratoranmeldung ein, die den Schlüsseltresor verwendet, um [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verschlüsselungsszenarien einzurichten und zu verwalten.  
  
    > [!IMPORTANT]  
    >  Das **Identity** -Argument `CREATE CREDENTIAL` von erfordert den Schlüssel Tresor Namen. Das **Secret** -Argument `CREATE CREDENTIAL` von erfordert, dass die * \<Client-ID>* (ohne Bindestriche) und * \<der geheime>* gemeinsam ohne Leerzeichen zwischen Ihnen übermittelt werden.  
  
     Im folgenden Beispiel wird die **Client-ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) aus den Bindestrichen entfernt und als Zeichen `EF5C8E094D2A4A769998D93440D8115D` Folge eingegeben, und der **geheime** Schlüssel wird durch die Zeichenfolge *SECRET_sysadmin_login*dargestellt.  
  
    ```sql
    USE master;  
    CREATE CREDENTIAL sysadmin_ekm_cred   
        WITH IDENTITY = 'ContosoKeyVault',   
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_sysadmin_login'   
    FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;  
  
    -- Add the credential to the SQL Server administrators domain login   
    ALTER LOGIN [<domain>/<login>]  
    ADD CREDENTIAL sysadmin_ekm_cred;  
    ```  
  
     Ein Beispiel für die Verwendung von Variablen für `CREATE CREDENTIAL` die Argumente und die programmgesteuerte Entfernung der Bindestriche aus der Client-ID finden Sie unter [Create Credential &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql).  
  
3.  Wenn Sie einen asymmetrischen Schlüssel importiert haben, wie zuvor in Schritt 1, Abschnitt 3, beschrieben, öffnen Sie den Schlüssel, indem Sie im folgenden Beispiel Ihren Schlüsselnamen angeben.  
  
    ```sql
    CREATE ASYMMETRIC KEY CONTOSO_KEY   
    FROM PROVIDER [AzureKeyVault_EKM_Prov]  
    WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',  
    CREATION_DISPOSITION = OPEN_EXISTING;  
    ```  
  
     Obwohl dies für die Produktionsumgebung nicht empfohlen wird (da der Schlüssel nicht exportiert werden kann), ist es möglich, von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]aus einen asymmetrischen Schlüssel direkt im Tresor zu erstellen. Wenn Sie zuvor keinen Schlüssel importiert haben, erstellen Sie mit dem folgenden Skript zu Testzwecken einen asymmetrischen Schlüssel im Schlüsseltresor. Führen Sie das Skript mithilfe einer mit den Anmeldeinformationen **sysadmin_ekm_cred** bereitgestellten Anmeldung aus.  
  
    ```sql
    CREATE ASYMMETRIC KEY CONTOSO_KEY   
    FROM PROVIDER [AzureKeyVault_EKM_Prov]  
    WITH ALGORITHM = RSA_2048,  
    PROVIDER_KEY_NAME = 'ContosoMasterKey';  
    ```  
  
> [!TIP]  
>  Benutzer, die den Fehler **kann nicht öffentlichen Schlüssel vom Anbieter exportiert. Anbieterfehlercode: 2053.** erhalten, sollten ihre **get**, **list**, **wrapKey**und **unwrapKey** .  
  
 Weitere Informationen finden Sie unter  
  
-   [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
-   [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)  
  
-   [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)  
  
-   [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)  
  
-   [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql)  
  
## <a name="examples"></a>Beispiele  
  
###  <a name="ExampleA"></a>Beispiel A: Transparent Data Encryption mithilfe eines asymmetrischen Schlüssels aus der Key Vault  
 Erstellen Sie nach Abschluss der obigen Schritte Anmeldeinformationen und eine Anmeldung, und erstellen Sie einen Datenbank-Verschlüsselungsschlüssel, der durch den asymmetrischen Schlüssel im Schlüsseltresor geschützt wird. Verwenden Sie den Datenbank-Verschlüsselungsschlüssel zum Verschlüsseln einer Datenbank mit transparenter Datenverschlüsselung.  
  
 Zum Verschlüsseln einer Datenbank ist die CONTROL-Berechtigung für die Datenbank erforderlich.  
  
##### <a name="to-enable-tde-using-ekm-and-the-key-vault"></a>So aktivieren Sie die transparente Datenverschlüsselung mit erweiterbarer Schlüsselverwaltung und dem Schlüsseltresor  
  
1.  Erstellen Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldeinformationen für die [!INCLUDE[ssDE](../../../includes/ssde-md.md)] , die beim Laden der Datenbank für den Zugriff auf die erweiterbare Schlüsselverwaltung mit Schlüsseltresor verwendet werden.  
  
    > [!IMPORTANT]  
    >  Das **Identity** -Argument `CREATE CREDENTIAL` von erfordert den Schlüssel Tresor Namen. Das **Secret** -Argument `CREATE CREDENTIAL` von erfordert, dass die * \<Client-ID>* (ohne Bindestriche) und * \<der geheime>* gemeinsam ohne Leerzeichen zwischen Ihnen übermittelt werden.  
  
     Im folgenden Beispiel wird die **Client-ID** (`EF5C8E09-4D2A-4A76-9998-D93440D8115D`) aus den Bindestrichen entfernt und als Zeichen `EF5C8E094D2A4A769998D93440D8115D` Folge eingegeben, und der **geheime** Schlüssel wird durch die Zeichenfolge *SECRET_DBEngine*dargestellt.  
  
    ```sql
    USE master;  
    CREATE CREDENTIAL Azure_EKM_TDE_cred   
        WITH IDENTITY = 'ContosoKeyVault',   
        SECRET = 'EF5C8E094D2A4A769998D93440D8115DSECRET_DBEngine'   
        FOR CRYPTOGRAPHIC PROVIDER AzureKeyVault_EKM_Prov ;  
    ```  
  
2.  Erstellen Sie eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anmeldung, die von der [!INCLUDE[ssDE](../../../includes/ssde-md.md)] für die transparente Datenverschlüsselung verwendet wird, und fügen Sie die Anmeldeinformationen hinzu. In diesem Beispiel wird der asymmetrische Schlüssel CONTOSO_KEY aus dem Schlüsseltresor verwendet, der importiert oder zuvor für die Masterdatenbank erstellt wurde, wie oben in [Schritt 3, Abschnitt 3](#Step3) beschrieben.  
  
    ```sql
    USE master;  
    -- Create a SQL Server login associated with the asymmetric key   
    -- for the Database engine to use when it loads a database   
    -- encrypted by TDE.  
    CREATE LOGIN TDE_Login   
    FROM ASYMMETRIC KEY CONTOSO_KEY;  
    GO   
  
    -- Alter the TDE Login to add the credential for use by the   
    -- Database Engine to access the key vault  
    ALTER LOGIN TDE_Login   
    ADD CREDENTIAL Azure_EKM_TDE_cred ;  
    GO  
    ```  
  
3.  Erstellen Sie den Datenbank-Verschlüsselungsschlüssel (Database Encryption Key, DEK), der für die transparente Datenverschlüsselung verwendet wird. Der DEK kann mit jedem von SQL Server unterstützten Algorithmus und jeder unterstützten Schlüssellänge erstellt werden. Der DEK wird durch den asymmetrischen Schlüssel im Schlüsseltresor geschützt.  
  
     In diesem Beispiel wird der asymmetrische Schlüssel CONTOSO_KEY aus dem Schlüsseltresor verwendet, der importiert oder zuvor erstellt wurde, wie oben in [Schritt 3, Abschnitt 3](#Step3) beschrieben.  
  
    ```sql
    USE ContosoDatabase;  
    GO  
  
    CREATE DATABASE ENCRYPTION KEY   
    WITH ALGORITHM = AES_128   
    ENCRYPTION BY SERVER ASYMMETRIC KEY CONTOSO_KEY;  
    GO  
  
    -- Alter the database to enable transparent data encryption.  
    ALTER DATABASE ContosoDatabase   
    SET ENCRYPTION ON ;  
    GO  
    ```  
  
     Weitere Informationen finden Sie unter  
  
    -   [CREATE DATABASE ENCRYPTION KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-database-encryption-key-transact-sql)  
  
    -   [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
###  <a name="ExampleB"></a>Beispiel B: Verschlüsseln von Sicherungen mit einem asymmetrischen Schlüssel aus der Key Vault  
 Verschlüsselte Sicherungen werden ab [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]unterstützt. Im folgenden Beispiel wird eine Sicherung erstellt und wiederhergestellt, die mit einem Verschlüsselungsschlüssel verschlüsselt wurde, der durch den asymmetrischen Schlüssel im Schlüsseltresor geschützt wird.  
  
```sql
USE master;  
BACKUP DATABASE [DATABASE_TO_BACKUP]  
TO DISK = N'[PATH TO BACKUP FILE]'   
WITH FORMAT, INIT, SKIP, NOREWIND, NOUNLOAD,   
ENCRYPTION(ALGORITHM = AES_256, SERVER ASYMMETRIC KEY = [CONTOSO_KEY]);  
GO  
```  
  
 Beispiel für Wiederherstellungscode.  
  
```sql
RESTORE DATABASE [DATABASE_TO_BACKUP]  
FROM DISK = N'[PATH TO BACKUP FILE]' WITH FILE = 1, NOUNLOAD, REPLACE;  
GO  
```  
  
 Weitere Informationen zu Sicherungs Optionen finden Sie unter [Backup &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql).  
  
###  <a name="ExampleC"></a>Beispiel C: Verschlüsselung auf Spaltenebene mithilfe eines asymmetrischen Schlüssels aus der Key Vault  
 Das folgende Beispiel erstellt einen symmetrischen Schlüssel, der durch den asymmetrischen Schlüssel im Schlüsseltresor geschützt wird. Anschließend wird der symmetrische Schlüssel zum Verschlüsseln von Daten in der Datenbank verwendet.  
  
 In diesem Beispiel wird der asymmetrische Schlüssel CONTOSO_KEY aus dem Schlüsseltresor verwendet, der importiert oder zuvor erstellt wurde, wie oben in [Schritt 3, Abschnitt 3](#Step3) beschrieben. Um diesen asymmetrischen Schlüssel in der `ContosoDatabase` -Datenbank zu verwenden, müssen Sie die CREATE ASYMMETRIC KEY-Anweisung erneut ausführen, um der `ContosoDatabase` -Datenbank einen Verweis auf den Schlüssel zur Verfügung zu stellen.  
  
```sql
USE [ContosoDatabase];  
GO  
  
-- Create a reference to the key in the key vault  
CREATE ASYMMETRIC KEY CONTOSO_KEY   
FROM PROVIDER [AzureKeyVault_EKM_Prov]  
WITH PROVIDER_KEY_NAME = 'ContosoMasterKey',  
CREATION_DISPOSITION = OPEN_EXISTING;  
  
-- Create the data encryption key.  
-- The data encryption key can be created using any SQL Server   
-- supported algorithm or key length.  
-- The DEK will be protected by the asymmetric key in the key vault  
  
CREATE SYMMETRIC KEY DATA_ENCRYPTION_KEY  
    WITH ALGORITHM=AES_256  
    ENCRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;  
  
DECLARE @DATA VARBINARY(MAX);  
  
--Open the symmetric key for use in this session  
OPEN SYMMETRIC KEY DATA_ENCRYPTION_KEY   
DECRYPTION BY ASYMMETRIC KEY CONTOSO_KEY;  
  
--Encrypt syntax  
SELECT @DATA = ENCRYPTBYKEY(KEY_GUID('DATA_ENCRYPTION_KEY'), CONVERT(VARBINARY,'Plain text data to encrypt'));  
  
-- Decrypt syntax  
SELECT CONVERT(VARCHAR, DECRYPTBYKEY(@DATA));  
  
--Close the symmetric key  
CLOSE SYMMETRIC KEY DATA_ENCRYPTION_KEY;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-cryptographic-provider-transact-sql)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)   
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-symmetric-key-transact-sql)   
 [Erweiterbare Schlüsselverwaltung &#40;EKM-&#41;](extensible-key-management-ekm.md)   
 [Aktivieren von TDE mithilfe von EKM](enable-tde-on-sql-server-using-ekm.md)   
 [Sicherungs Verschlüsselung](../../backup-restore/backup-encryption.md)   
 [Erstellen einer verschlüsselten Sicherung](../../backup-restore/create-an-encrypted-backup.md)  
