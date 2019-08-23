---
title: ADO.NET-Verbindungs-Manager | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.adonetconnection.f1
helpviewer_keywords:
- connection managers [Integration Services], ADO.NET
- ADO.NET connection manager [Integration Services]
- connections [Integration Services], ADO.NET
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b3856f1f651db485aa9e54758c2d2a92ebf2ea0a
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028784"
---
# <a name="adonet-connection-manager"></a>ADO.NET-Verbindungs-Manager

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Ein [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Verbindungs-Manager ermöglicht einem Paket den Zugriff auf Datenquellen mithilfe eines .NET-Anbieters. Dieser Verbindungs-Manager dient in der Regel für den Zugriff auf Datenquellen, z.B. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sowie Datenquellen, die durch OLE DB und XML in benutzerdefinierten Tasks verfügbar gemacht werden, die mit einer Programmiersprache wie C# in verwaltetem Code geschrieben sind.  
  
 Wenn Sie einem Paket einen [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Verbindungs-Manager hinzufügen, erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] einen Verbindungs-Manager, der zur Laufzeit als [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Verbindung aufgelöst wird, die Eigenschaften des Verbindungs-Managers festlegt und der **Connections** -Sammlung im Paket den Verbindungs-Manager hinzufügt.  
  
 Die **ConnectionManagerType** -Eigenschaft des Verbindungs-Managers ist auf **ADO.NET**festgelegt. Der Wert von **ConnectionManagerType** ist qualifiziert, um den Namen des .NET-Anbieters einzuschließen, der vom Verbindungs-Manager verwendet wird.  
  
## <a name="adonet-connection-manager-troubleshooting"></a>Problembehandlung des ADO.NET-Verbindungs-Managers  
 Sie können die vom [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Verbindungs-Manager an externe Datenanbieter gerichteten Aufrufe protokollieren. Mithilfe dieser Protokollierungsfunktionen können Sie Probleme bei Verbindungen behandeln, die vom [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Verbindungs-Manager mit externen Datenquellen hergestellt werden. Aktivieren Sie zum Protokollieren der vom [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Verbindungs-Manager an externe Datenprovider gerichteten Aufrufe die Paketprotokollierung, und wählen Sie das **Diagnostic** -Ereignis auf Paketebene aus. Weitere Informationen finden Sie unter [Behandeln von Problemen mit Paketausführungstools](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
 Daten bestimmter [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Datumsdatentypen generieren beim Lesen durch einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verbindungs-Manager die in der folgenden Tabelle dargestellten Ergebnisse.  
  
|SQL Server-Datentyp|Ergebnis|  
|--------------------------|------------|  
|**time**, **datetimeoffset**|Das Paket erzeugt einen Fehler, sofern das Paket keine parametrisierten SQL-Befehle verwendet. Um parametrisierte SQL-Befehle zu verwenden, verwenden Sie den Task SQL ausführen im Paket. Weitere Informationen finden Sie unter [SQL ausführen (Task)](../../integration-services/control-flow/execute-sql-task.md) und [Parameter und Rückgabecodes im Task „SQL ausführen“](https://msdn.microsoft.com/library/a3ca65e8-65cf-4272-9a81-765a706b8663).|  
|**datetime2**|Der [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Verbindungs-Manager schneidet den Millisekundenwert ab.|  
  
> [!NOTE]  
>  Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen sowie deren Zuordnung zu [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Datentypen finden Sie unter [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md) und [SQL Server Integration Services-Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
## <a name="adonet-connection-manager-configuration"></a>Konfiguration des ADO.NET-Verbindungs-Managers  
 Es gibt folgende Möglichkeiten, um einen [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Verbindungs-Manager zu konfigurieren:  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
-   Stellen Sie eine Verbindungszeichenfolge bereit, die die Anforderungen des ausgewählten .NET-Anbieters erfüllt.  
  
-   Schließen Sie in Abhängigkeit vom Anbieter den Namen der Datenquelle ein, mit der eine Verbindung hergestellt werden soll.  
  
-   Stellen Sie entsprechende Sicherheitsanmeldeinformationen für den ausgewählten Anbieter bereit.  
  
-   Geben Sie an, ob die im Verbindungs-Manager erstellte Verbindung zur Laufzeit beibehalten wird.  
  
 Viele der Konfigurationsoptionen des [!INCLUDE[vstecado](../../includes/vstecado-md.md)] -Verbindungs-Managers hängen vom .NET-Anbieter ab, der vom Verbindungs-Manager verwendet wird.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [ADO.NET-Verbindungs-Manager konfigurieren](../../integration-services/connection-manager/configure-ado-net-connection-manager.md)  
  
 Weitere Informationen zum programmgesteuerten Konfigurieren eines Verbindungs-Managers finden Sie unter <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> und [Programmgesteuertes Hinzufügen von Verbindungen](../../integration-services/building-packages-programmatically/adding-connections-programmatically.md)festgelegt.  
  
## <a name="configure-adonet-connection-manager"></a>ADO.NET-Verbindungs-Manager konfigurieren
  Verwenden Sie das Dialogfeld **ADO.NET-Verbindungs-Manager konfigurieren** , um einer Datenquelle, auf die mithilfe eines .NET Framework-Datenanbieters (z. B. des SqlClient-Anbieters) zugegriffen werden kann, eine Verbindung hinzuzufügen. Der Verbindungs-Manager kann eine vorhandene Verbindung verwenden, oder Sie können eine neue erstellen.  
  
 Weitere Informationen zum ADO.NET-Verbindungs-Manager finden Sie unter [ADO.NET Connection Manager](../../integration-services/connection-manager/ado-net-connection-manager.md).  
  
### <a name="options"></a>enthalten  
 **Datenverbindungen**  
 Wählen Sie in der Liste eine vorhandene ADO.NET.Datenverbindung aus.  
  
 **Datenverbindungseigenschaften**  
 Zeigt Eigenschaften und Werte für die ausgewählte ADO.NET-Datenverbindung an.  
  
 **Neu**  
 Erstellen Sie mithilfe des Dialogfelds **Verbindungs-Manager** eine ADO.NET-Datenverbindung.  
  
 **Löschen**  
 Wählen Sie eine Verbindung aus, und löschen Sie sie mithilfe der Schaltfläche **Löschen** .  
  
### <a name="managed-identities-for-azure-resources-authentication"></a>Verwaltete Identitäten für die Authentifizierung von Azure-Ressourcen
Beim Ausführen von SSIS-Paketen in [Azure-SSIS Integration Runtime in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime) können Sie die [verwaltete Identität](https://docs.microsoft.com/azure/data-factory/connector-azure-sql-database#managed-identity), die Ihrer Data Factory zugeordnet ist, zur Authentifizierung der Azure SQL-Datenbank (oder verwalteten Instanz) verwenden. Die angegebene Factory kann mithilfe dieser Identität auf Daten zugreifen und Daten aus der oder in die Datenbank kopieren.

> [!NOTE]
>  Wenn Sie Azure AD-Authentifizierung (einschließlich der Authentifizierung der verwalteten Identität) zum Herstellen einer Verbindung mit der Azure SQL-Datenbank-Instanz (oder verwalteten Instanz) verwenden, können bekannte Probleme zu Fehlern bei der Paketausführung oder unerwarteten Verhaltensänderungen führen. Weitere Informationen finden Sie unter [Funktionen und Einschränkungen von Azure AD](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication#azure-ad-features-and-limitations).

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

1. **Gewähren Sie der Azure AD-Gruppe die notwendigen Berechtigungen**, wie Sie es normalerweise für SQL-Benutzer und andere tun. Informationen zu den entsprechenden Rollen finden Sie unter [Rollen auf Datenbankebene](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles). Führen Sie beispielsweise den folgenden Code aus:

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

1. **Erteilen Sie der verwalteten Identität für Data Factory die notwendigen Berechtigungen**. Informationen zu den entsprechenden Rollen finden Sie unter [Rollen auf Datenbankebene](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles). Führen Sie den folgenden T-SQL-Code für die Datenbank aus, aus der oder in die Daten kopiert werden sollen:

    ```sql
    CREATE USER [{the managed identity name}] FOR LOGIN [{the managed identity name}] WITH DEFAULT_SCHEMA = dbo
    ALTER ROLE [role name] ADD MEMBER [{the managed identity name}]
    ```

Zum Schluss **konfigurieren Sie die Authentifizierung der verwalteten Identität** für den ADO.NET-Verbindungs-Manager. Es gibt dafür zwei Möglichkeiten.
    
1. Konfigurieren zur Entwurfszeit. Klicken Sie im SSIS-Designer mit der rechten Maustaste auf den ADO.NET-Verbindungs-Manager, und klicken Sie dann auf **Eigenschaften**, um das **Eigenschaftenfenster** zu öffnen. Aktualisieren Sie die Eigenschaft **ConnectUsingManagedIdentity** auf den Wert **True**.
    > [!NOTE]
    >  Derzeit hat die Eigenschaft **ConnectUsingManagedIdentity** des Verbindungs-Managers KEINE Auswirkung (Angabe, dass die Authentifizierung der verwalteten Identität nicht funktioniert) beim Ausführen des SSIS-Pakets im SSIS-Designer oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQL Server.
    
1. Konfigurieren zur Laufzeit. Beim Ausführen des Pakets über [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/integration-services/ssis-quickstart-run-ssms) oder die [Aktivität „SSIS-Paket ausführen“ von Azure Data Factory](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity) suchen Sie den ADO.NET-Verbindungs-Manager, und aktualisieren Sie die Eigenschaft  **ConnectUsingManagedIdentity** auf den Wert **True**.
    > [!NOTE]
    >  In Azure-SSIS Integration Runtime werden alle anderen Authentifizierungsmethoden (z.B. integrierte Authentifizierung, Kennwort), die im ADO.NET-Verbindungs-Manager vorkonfiguriert sind, **überschrieben**, wenn die Authentifizierung der verwalteten Identität zum Herstellen einer Datenbankverbindung verwendet wird.

> [!NOTE]
>  Zum Konfigurieren der Authentifizierung der verwalteten Identität bei vorhandenen Paketen sollten Sie das SSIS-Projekt mindestens einmal mit dem [neuesten SSIS-Designer](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt) neu erstellen und dieses SSIS-Projekt in der Azure-SSIS Integration Runtime erneut bereitstellen, damit die neue Eigenschaft **ConnectUsingManagedIdentity** des Verbindungs-Managers automatisch allen ADO.NET-Verbindungs-Managern im SSIS-Projekt hinzugefügt wird. Die alternative Methode besteht darin, die Eigenschaft direkt mit dem Eigenschaftenpfad **\Package.Connections[{Name Ihres Verbindungs-Managers}].Properties[ConnectUsingManagedIdentity]** zur Runtime zu verwenden.

## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Verbindungen &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)  
  
  
