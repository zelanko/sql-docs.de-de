---
title: OLE DB-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.oledbconnection.f1
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c455e449ff59296848c7e3f15d07aaee80d415c7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66221159"
---
# <a name="ole-db-connection-manager"></a>OLE DB-Verbindungs-Manager

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Durch einen OLE DB-Verbindungs-Manager kann ein Paket mithilfe eines OLE DB-Anbieters eine Verbindung mit einer Datenquelle herstellen. Beispielsweise kann ein OLE DB-Verbindungs-Manager, der eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellt, den [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwenden.    
    
> [!NOTE]
>  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 OLEDB-Anbieter unterstützt die neuen Schlüsselwörter für Verbindungszeichenfolgen (MultiSubnetFailover=True) für Multisubnetz-Failoverclustering nicht. Weitere Informationen finden Sie in den [Versionsanmerkungen zu SQL Server](https://go.microsoft.com/fwlink/?LinkId=247824) und im Blogbeitrag zu [Always On-Multisubnetz-Failover und SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/)unter www.mattmasson.com.    
> 
> [!NOTE]
>  Wenn es sich bei der Datenquelle um [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007 handelt, erfordert die Datenquelle einen anderen Datenanbieter als frühere Versionen von Excel oder Access. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einer Excel-Arbeitsmappe](../../integration-services/connection-manager/connect-to-an-excel-workbook.md) und [Herstellen einer Verbindung mit einer Access-Datenbank](../../integration-services/connection-manager/connect-to-an-access-database.md).    
    
 Mehrere Tasks und Datenflusskomponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwenden einen OLE DB-Verbindungs-Manager. Beispielsweise extrahieren und laden die OLE DB-Quelle und das OLE DB-Ziel mit diesem Verbindungs-Manager Daten. Und der Task SQL ausführen kann damit eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank herstellen, um Abfragen auszuführen.    
    
 Der OLE DB-Verbindungs-Manager wird auch für den Zugriff auf OLE DB-Datenquellen in benutzerdefinierten Tasks verwendet, die in nicht verwaltetem Code und einer Programmiersprache wie z. B. C++ geschrieben sind.    
    
 Wenn Sie einem Paket einen OLE DB-Verbindungs-Manager hinzufügen, erstellt [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit in eine OLE DB-Verbindung aufgelöst wird, die Eigenschaften des Verbindungs-Managers festlegt und der **Connections** -Sammlung im Paket den Verbindungs-Manager hinzufügt.    
    
 Die **ConnectionManagerType** -Eigenschaft des Verbindungs-Managers ist auf **OLEDB**festgelegt.    
    
 Der OLE DB-Verbindungs-Manager kann wie folgt konfiguriert werden:    
    
-   Stellen Sie eine Verbindungszeichenfolge bereit, die die Anforderungen des ausgewählten Anbieters erfüllt.    
    
-   Schließen Sie in Abhängigkeit vom Anbieter den Namen der Datenquelle ein, mit der eine Verbindung hergestellt werden soll.    
    
-   Stellen Sie entsprechende Sicherheitsanmeldeinformationen für den ausgewählten Anbieter bereit.    
    
-   Geben Sie an, ob die im Verbindungs-Manager erstellte Verbindung zur Laufzeit beibehalten wird.    
    
## <a name="logging"></a>Protokollierung    
 Sie können die vom OLE DB-Verbindungs-Manager an externe Datenanbieter gerichteten Aufrufe protokollieren. Mithilfe dieser Protokollierungsfunktionen können Sie Probleme bei Verbindungen behandeln, die vom OLE DB-Verbindungs-Manager mit externen Datenquellen hergestellt werden. Aktivieren Sie zum Protokollieren der vom OLE DB-Verbindungs-Manager an externe Datenanbieter gerichteten Aufrufe die Paketprotokollierung, und wählen Sie das **Diagnostic** -Ereignis auf Paketebene aus. Weitere Informationen finden Sie unter [Behandeln von Problemen mit Paketausführungstools](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).    
    
## <a name="configuration-of-the-oledb-connection-manager"></a>Konfiguration des OLEDB-Verbindungs-Managers    
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen. Weitere Informationen zu den Eigenschaften, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können, finden Sie unter [Konfigurieren des OLE DB-Verbindungs-Managers](../../integration-services/connection-manager/configure-ole-db-connection-manager.md). Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie in der Dokumentation zur **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** -Klasse im Entwicklerhandbuch.    
    
## <a name="related-content"></a>Verwandte Inhalte    
    
-   Wiki-Artikel, [SSIS with Oracle Connectors](https://go.microsoft.com/fwlink/?LinkId=220670) , auf social.technet.microsoft.com.    
    
-   Technischer Artikel, [Connection Strings for OLE DB Providers](https://go.microsoft.com/fwlink/?LinkId=220744)(Verbindungszeichenfolgen für OLE DB-Anbieter), auf carlprothman.net.    
    
## <a name="configure-ole-db-connection-manager"></a>OLE DB-Verbindungs-Manager konfigurieren
  Fügen Sie mithilfe des Dialogfelds **OLE DB-Verbindungs-Manager konfigurieren** einer Datenquelle eine Verbindung hinzu. Dabei kann es sich um eine neue Verbindung oder eine Kopie einer vorhandenen Verbindung handeln.  
  
> [!NOTE]  
>  Wenn es sich bei der Datenquelle um [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 handelt, erfordert die Datenquelle einen anderen Verbindungs-Manager als frühere Versionen von Excel. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einer Excel-Arbeitsmappe](../../integration-services/connection-manager/connect-to-an-excel-workbook.md).  
>   
>  Wenn es sich bei der Datenquelle um [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007 handelt, erfordert die Datenquelle einen anderen OLE DB-Anbieter als frühere Versionen von Access. Weitere Informationen finden Sie unter [Herstellen einer Verbindung zu einer Access-Datenbank](../../integration-services/connection-manager/connect-to-an-access-database.md).  
  
 Weitere Informationen zum OLE DB-Verbindungs-Manager finden Sie unter [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
### <a name="options"></a>enthalten  
 **Datenverbindungen**  
 Wählen Sie aus der Liste eine vorhandene OLE DB-Datenverbindung aus.  
  
 **Datenverbindungseigenschaften**  
 Zeigt die Eigenschaften und Werte der ausgewählten OLE DB-Datenverbindung an.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Verbindungs-Manager** eine OLE DB-Datenverbindung.  
  
 **Löschen**  
 Wählen Sie eine Datenverbindung aus, und löschen Sie sie mithilfe der Schaltfläche **Löschen** .  
  
### <a name="managed-identities-for-azure-resources-authentication"></a>Verwaltete Identitäten für die Authentifizierung von Azure-Ressourcen
Beim Ausführen von SSIS-Paketen in [Azure-SSIS Integration Runtime in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime) können Sie die [verwaltete Identität](https://docs.microsoft.com/azure/data-factory/connector-azure-sql-database#managed-identity), die Ihrer Data Factory zugeordnet ist, zur Authentifizierung der Azure SQL-Datenbank (oder verwalteten Instanz) verwenden. Die angegebene Factory kann mithilfe dieser Identität auf Daten zugreifen und Daten aus der oder in die Datenbank kopieren.

Damit Sie die Authentifizierung der verwalteten Identität für die Azure SQL-Datenbank verwenden können, führen Sie die folgenden Schritte zum Konfigurieren der Datenbank aus:

1. **Erstellen Sie eine Gruppe in Azure AD.** Geben Sie die verwaltete Identität als ein Mitglied der Gruppe an.
    
   1. [Suchen Sie die verwaltete Identität für Data Factory im Azure-Portal](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity). Wechseln Sie zu den **Eigenschaften** der Data Factory. Kopieren Sie die **Objekt-ID der verwalteten Identität**.
    
   1. Installieren Sie das [Azure AD PowerShell](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2)-Modul. Melden Sie sich mit dem Befehl `Connect-AzureAD` an. Führen Sie die folgenden Befehle zum Erstellen einer Gruppe und Hinzufügen der verwalteten Identität als Mitglied aus.
      ```powershell
      $Group = New-AzureADGroup -DisplayName "<your group name>" -MailEnabled $false -SecurityEnabled $true -MailNickName "NotSet"
      Add-AzureAdGroupMember -ObjectId $Group.ObjectId -RefObjectId "<your data factory managed identity object ID>"
      ```
    
1. **[Stellen Sie einen Azure Active Directory-Administrator für Ihren Azure SQL-Server im Azure-Portal bereit](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-azure-sql-database-server)** , wenn dies noch nicht geschehen ist. Der Azure AD-Administrator kann ein Azure AD-Benutzer oder eine Azure AD-Gruppe sein. Wenn Sie der Gruppe mit der verwalteten Identität eine Administratorrolle zuweisen, überspringen Sie die Schritte 3 und 4. Der Administrator hat vollen Zugriff auf die Datenbank.

1. **[Erstellen Sie eigenständige Datenbankbenutzer](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#create-contained-database-users-in-your-database-mapped-to-azure-ad-identities)** für die Azure AD-Gruppe. Stellen Sie eine Verbindung mit der Datenbank her, aus der oder in die Sie Daten kopieren möchten. Verwenden Sie dazu Tools wie SSMS und eine Azure AD-Identität, die mindestens über ALTER ANY USER-Berechtigung verfügt. Führen Sie folgenden T-SQL-Code aus: 
    
    ```sql
    CREATE USER [your AAD group name] FROM EXTERNAL PROVIDER;
    ```

1. **Gewähren Sie der Azure AD-Gruppe die notwendigen Berechtigungen**, wie Sie es normalerweise für SQL-Benutzer und andere tun. Führen Sie beispielsweise den folgenden Code aus:

    ```sql
    ALTER ROLE [role name] ADD MEMBER [your AAD group name];
    ```

Damit Sie die Authentifizierung der verwalteten Identität für die verwaltete Azure SQL-Datenbank-Instanz verwenden können, führen Sie die folgenden Schritte zum Konfigurieren der Datenbank aus:
    
1. **[Stellen Sie einen Azure Active Directory-Administrator für Ihre verwaltete Instanz im Azure-Portal bereit](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure#provision-an-azure-active-directory-administrator-for-your-managed-instance)** , wenn dies noch nicht geschehen ist. Der Azure AD-Administrator kann ein Azure AD-Benutzer oder eine Azure AD-Gruppe sein. Wenn Sie der Gruppe mit der verwalteten Identität eine Administratorrolle zuweisen, überspringen Sie die Schritte 2 bis 5. Der Administrator hat vollen Zugriff auf die Datenbank.

1. **[Suchen Sie die verwaltete Identität für Data Factory im Azure-Portal](https://docs.microsoft.com/azure/data-factory/data-factory-service-identity)** . Wechseln Sie zu den **Eigenschaften** der Data Factory. Kopieren Sie die **Anwendungs-ID der verwalteten Identität** (NICHT die **Objekt-ID der verwalteten Identität**).

1. **Konvertieren Sie die verwaltete Identität für Data Factory in den Binärtyp**. Stellen Sie eine Verbindung mit der **master**-Datenbank in Ihrer verwalteten Instanz her. Verwenden Sie dazu Tools wie SSMS und Ihr SQL/Active Directory-Administratorkonto. Führen Sie den folgenden T-SQL-Code für die **master**-Datenbank aus, um die Anwendungs-ID der verwalteten Identität im Binärformat zu erhalten:
    
    ```sql
    DECLARE @applicationId uniqueidentifier = '{your managed identity application ID}'
    select CAST(@applicationId AS varbinary)
    ```

1. **Fügen Sie die verwaltete Identität für Data Factory als einen Benutzer in der verwalteten Azure SQL-Datenbank-Instanz hinzu**. Führen Sie den folgenden T-SQL-Code für die **master**-Datenbank aus:
    
    ```sql
    CREATE LOGIN [{a name for the managed identity}] FROM EXTERNAL PROVIDER with SID = {your managed identity application ID as binary}, TYPE = E
    ```

1. **Erteilen Sie der verwalteten Identität für Data Factory die notwendigen Berechtigungen**. Führen Sie den folgenden T-SQL-Code für die Datenbank aus, aus der oder in die Daten kopiert werden sollen:

    ```sql
    CREATE USER [{the managed identity name}] FOR LOGIN [{the managed identity name}] WITH DEFAULT_SCHEMA = dbo
    ALTER ROLE db_owner ADD MEMBER [{the managed identity name}]
    ```

Dann **konfigurieren Sie den OLE DB-Anbieter** für den OLE DB-Verbindungs-Manager. Es gibt dafür zwei Möglichkeiten.
    
1. Konfigurieren zur Entwurfszeit. Doppelklicken Sie im SSIS-Designer auf den OLE DB-Verbindungs-Manager, um das Fenster **Verbindungs-Manager** zu öffnen. Wählen Sie in der Dropdownliste **Anbieter** die Option [**Microsoft OLE DB-Treiber für SQL Server**](https://go.microsoft.com/fwlink/?linkid=871294) aus.
    > [!NOTE]
    >  Andere Anbieter in der Dropdownliste bieten möglicherweise KEINE Unterstützung für die Authentifizierung der verwalteten Identität.
    
1. Konfigurieren zur Laufzeit. Beim Ausführen des Pakets über [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) oder die [Aktivität „SSIS-Paket ausführen“ von Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity) suchen Sie die Verbindungs-Manager-Eigenschaft **ConnectionString** für den OLE DB-Verbindungs-Manager, und aktualisieren Sie die Verbindungseigenschaft **Provider** auf den Wert **MSOLEDBSQL** (d.h. Microsoft OLE DB-Treiber für SQL Server).
    ```vb
    Data Source=serverName;Initial Catalog=databaseName;Provider=MSOLEDBSQL;...
    ```

Zum Schluss **konfigurieren Sie die Authentifizierung der verwalteten Identität** für den OLE DB-Verbindungs-Manager. Es gibt dafür zwei Möglichkeiten.
    
1. Konfigurieren zur Entwurfszeit. Klicken Sie im SSIS-Designer mit der rechten Maustaste auf den OLE DB-Verbindungs-Manager, und klicken Sie dann auf **Eigenschaften**, um das **Eigenschaftenfenster** zu öffnen. Aktualisieren Sie die Eigenschaft **ConnectUsingManagedIdentity** auf den Wert **True**.
    > [!NOTE]
    >  Derzeit hat die Eigenschaft **ConnectUsingManagedIdentity** des Verbindungs-Managers KEINE Auswirkung (Angabe, dass die Authentifizierung der verwalteten Identität nicht funktioniert) beim Ausführen des SSIS-Pakets im SSIS-Designer oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.

1. Konfigurieren zur Laufzeit. Beim Ausführen des Pakets über SSMS oder die Aktivität „SQL-Paket ausführen“ suchen Sie den OLE DB-Verbindungs-Manager, und aktualisieren Sie die Eigenschaft **ConnectUsingManagedIdentity** auf den Wert **True**.
    > [!NOTE]
    >  In Azure-SSIS Integration Runtime werden alle anderen Authentifizierungsmethoden (z.B. integrierte Sicherheit, Kennwort), die im OLE DB-Verbindungs-Manager vorkonfiguriert sind, **überschrieben**, wenn die Authentifizierung der verwalteten Identität zum Herstellen einer Datenbankverbindung verwendet wird.

> [!NOTE]
>  Zum Konfigurieren der Authentifizierung der verwalteten Identität bei vorhandenen Paketen stellen Sie sicher, dass Sie das SSIS-Projekt mindestens einmal mit dem [neuesten SSIS-Designer](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) neu erstellen und dieses SSIS-Projekt in Azure-SSIS Integration Runtime erneut bereitstellen, damit die neue Eigenschaft **ConnectUsingManagedIdentity** des Verbindungs-Managers automatisch allen OLE DB-Verbindungs-Managern im SSIS-Projekt hinzugefügt wird.

## <a name="see-also"></a>Weitere Informationen    
 [OLE DB-Quelle](../../integration-services/data-flow/ole-db-source.md)     
 [OLE DB-Ziel](../../integration-services/data-flow/ole-db-destination.md)     
 [SQL ausführen (Task)](../../integration-services/control-flow/execute-sql-task.md)     
 [Integration Services-Verbindungen &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)    
    
  
