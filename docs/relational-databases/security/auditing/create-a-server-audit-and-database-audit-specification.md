---
title: Erstellen einer Server- und Datenbanküberwachungsspezifikation
description: In diesem Artikel erfahren Sie, wie Sie eine Server- und Datenbanküberwachungsspezifikation für SQL Server erstellen. Dazu verwenden Sie SQL Server Management Studio oder Transact-SQL (T-SQL).
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql13.swb.sqlaudit.dbaudit.general.f1
helpviewer_keywords:
- audits [SQL Server], creating database specification
- database audit [SQL Server]
ms.assetid: 26ee85de-6e97-4318-b526-900924d96e62
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 55b848cd43e157a9a75670a24aea645c3279f7ea
ms.sourcegitcommit: bfb5e79586fd08d8e48e9df0e9c76d1f6c2004e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "82262065"
---
# <a name="create-a-server-audit-and-database-audit-specification"></a>Erstellen einer Server- und Datenbanküberwachungsspezifikation
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Artikel erfahren Sie, wie Sie eine Server- und eine Datenbanküberwachungsspezifikation in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../../includes/tsql-md.md)] erstellen.  
  
 Die Überwachung einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz oder einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank umfasst die Nachverfolgung und Protokollierung der Ereignisse des Systems. Das *SQL Server Audit*-Objekt erfasst eine einzelne Instanz von Aktionen oder Aktionsgruppen auf Server- oder Datenbankebene auf, die überwacht werden soll. Die Überwachung wird auf [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanzebene ausgeführt. Es können mehrere Überwachungen pro [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz vorliegen. Das Objekt für die *Überwachungsspezifikation auf Datenbankebene* gehört ebenfalls zu einer Überwachung. Sie können eine Datenbank-Überwachungsspezifikation pro SQL Server-Datenbank und pro Überwachung erstellen. Weitere Informationen finden Sie unter [SQL Server Audit &#40;Datenbank-Engine&#41;](../../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Voraussetzungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Datenbank-Überwachungsspezifikationen sind nicht sicherungsfähige Objekte, die sich in einer gegebenen Datenbank befinden. Wenn eine Datenbanküberwachungsspezifikation erstellt wird, ist diese zunächst deaktiviert.  
  
 Wenn Sie in einer Benutzerdatenbank eine Datenbank-Überwachungsspezifikation erstellen oder ändern, sollten Sie keine Überwachungsaktionen für Serverbereichsobjekte wie Systemsichten einschließen. Wenn Sie Objekte mit Serverbereich einfügen, wird die Überwachung zwar erstellt. Die Objekte mit Serverbereich sind jedoch nicht enthalten, und es wird kein Fehler zurückgegeben. Verwenden Sie eine Datenbanküberwachungsspezifikation in der Masterdatenbank, um Objekte mit Serverbereich zu überwachen.  
  
 Die Datenbanküberwachungsspezifikationen befinden sich in der Datenbank, in der sie erstellt werden, mit Ausnahme der Systemdatenbank **TempDB**.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
  
-   Benutzer mit der ALTER ANY DATABASE AUDIT-Berechtigung können Datenbanküberwachungsspezifikationen erstellen und an eine beliebige Überwachung binden.  
  
-   Nachdem eine Datenbanküberwachungsspezifikation erstellt wurde, können Prinzipale mit CONTROL SERVER- oder ALTER ANY DATABASE AUDIT-Berechtigungen diese anzeigen. Das sysadmin-Konto kann sie ebenfalls anzeigen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-create-a-server-audit"></a>So erstellen Sie eine Serverüberwachung  
  
1.  Erweitern Sie im Objekt-Explorer den Ordner **Sicherheit** .  
  
2.  Klicken Sie mit der rechten Maustaste auf den Ordner **Überwachungen**, und wählen Sie dann **Neue Überwachung** aus. Weitere Informationen finden Sie unter [Erstellen einer Serverüberwachung und einer Serverüberwachungsspezifikation](../../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md).  
  
3.  Klicken Sie auf **OK**, wenn Sie die Auswahl der Optionen abgeschlossen haben.  

#### <a name="to-create-a-database-level-audit-specification"></a>So erstellen Sie eine Überwachungsspezifikation auf Datenbankebene  
  
1.  Erweitern Sie im Objekt-Explorer die Datenbank, in der Sie eine Überwachungsspezifikation erstellen möchten.  
  
2.  Erweitern Sie den Ordner **Sicherheit** .  
  
3.  Klicken Sie mit der rechten Maustaste auf den Ordner **Datenbank-Überwachungsspezifikationen** und dann auf **Neue Datenbank-Überwachungsspezifikation...** .  
  
     Die folgenden Optionen sind im Dialogfeld **Datenbank-Überwachungsspezifikation erstellen** verfügbar:  
  
     **Name**  
     Der Name der Datenbank-Überwachungsspezifikation. Es wird automatisch ein Name generiert, wenn Sie eine Serverüberwachungsspezifikation erstellen. Der Name kann geändert werden.  
  
     **Überwachung**  
     Der Name eines vorhandenen Serverüberwachungsobjekts. Geben Sie den Namen der Überwachung ein, oder wählen Sie ihn aus der Liste aus.  
  
     **Überwachungsaktionstyp**  
     Gibt die aufzuzeichnenden Überwachungsaktionsgruppen auf Datenbankebene und Überwachungsaktionen an. Eine Liste der Überwachungsaktionsgruppen auf Datenbankebene und Überwachungsaktionen sowie eine Beschreibung der darin enthaltenen Ereignisse finden Sie unter [SQL Server Audit-Aktionsgruppen und -Aktionen](../../../relational-databases/security/auditing/sql-server-audit-action-groups-and-actions.md).  
  
     **Objektschema**  
     Zeigt das Schema für den angegebenen **Objektnamen**an.  
  
     **Objektnamen**  
     Der Name des zu überwachenden Objekts. Diese Option ist nur für Überwachungsaktionen verfügbar. Sie gilt nicht für Überwachungsgruppen.  
  
     **Auslassungspunkte (…)**  
     Öffnen Sie das Dialogfeld **Objekte auswählen**, damit Sie anhand des festgelegten **Überwachungsaktionstyps** nach einem verfügbaren Objekt suchen und dieses auswählen können.  
  
     **Prinzipalname**  
     Das Konto, anhand dessen die Überwachung für das zu überwachende Objekt gefiltert wird.  
  
     **Auslassungspunkte (…)**  
     Öffnen Sie das Dialogfeld **Objekte auswählen**, damit Sie anhand des festgelegten **Objektnamens** nach einem verfügbaren Objekt suchen und dieses auswählen können.  
  
4.  Klicken Sie auf **OK**, wenn Sie die Auswahl der Optionen abgeschlossen haben.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-create-a-server-audit"></a>So erstellen Sie eine Serverüberwachung  
  
1.  Stellen Sie mithilfe des Objekt-Explorers eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Fügen Sie das folgende Beispiel in das Abfragefenster ein, und klicken Sie dann auf **Ausführen**.  
  
    ```  
    USE master ;  
    GO  
    -- Create the server audit.   
    CREATE SERVER AUDIT Payrole_Security_Audit  
        TO FILE ( FILEPATH =   
    'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA' ) ;   
    GO  
    -- Enable the server audit.   
    ALTER SERVER AUDIT Payrole_Security_Audit   
    WITH (STATE = ON) ;  
    ```  
  
#### <a name="to-create-a-database-level-audit-specification"></a>So erstellen Sie eine Überwachungsspezifikation auf Datenbankebene  
  
1.  Stellen Sie mithilfe des Objekt-Explorers eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Fügen Sie das folgende Beispiel in das Abfragefenster ein, und klicken Sie dann auf **Ausführen**. In diesem Beispiel wird eine Datenbanküberwachungsspezifikation namens `Audit_Pay_Tables` erstellt. Sie überwacht die SELECT- und INSERT-Anweisungen des Benutzers `dbo` für die Tabelle `HumanResources.EmployeePayHistory` anhand der Serverüberwachung, die im vorherigen Abschnitt definiert wurde.  
  
    ```  
    USE AdventureWorks2012 ;   
    GO  
    -- Create the database audit specification.   
    CREATE DATABASE AUDIT SPECIFICATION Audit_Pay_Tables  
    FOR SERVER AUDIT Payrole_Security_Audit  
    ADD (SELECT , INSERT  
         ON HumanResources.EmployeePayHistory BY dbo )   
    WITH (STATE = ON) ;   
    GO  
  
    ```  
  
 Weitere Informationen finden Sie unter [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](../../../t-sql/statements/create-server-audit-transact-sql.md) und [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../../t-sql/statements/create-database-audit-specification-transact-sql.md).  
  
  
