---
title: Gleichzeitiges Ausführen von Anweisungen für mehrere Server
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- executing queries against multiple servers
- queries [SQL Server], multiserver
ms.assetid: 197760f3-0a06-43de-8162-69c27d3fbe56
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e39ef8e9153cc8c85e72d7f53ac873befaf9af4d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058417"
---
# <a name="execute-statements-against-multiple-servers-simultaneously-sql-server-management-studio"></a>Gleichzeitiges Ausführen von Anweisungen für mehrere Server (SQL Server Management Studio)
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]Abfragen gleichzeitig für mehrere Server durchführen, indem Sie eine lokale Servergruppe oder einen zentralen Verwaltungsserver und eine oder mehrere Servergruppen sowie einen oder mehrere registrierte Server innerhalb der Gruppen erstellen und anschließend eine Abfrage für die ganze Gruppe durchführen. Die von der Abfrage zurückgegebenen Ergebnisse können in einem einzigen Ergebnisbereich zusammengefasst oder in gesonderten Ergebnisbereichen ausgegeben werden. Das Resultset kann zusätzliche Spalten für den Servernamen und den Anmeldenamen umfassen, der für die Abfrage auf jedem einzelnen Server verwendet wird. Zentrale Verwaltungsserver und untergeordnete registrierte Server können nur mithilfe der Windows-Authentifizierung registriert werden. Server in lokalen Servergruppen können mithilfe der Windows-Authentifizierung oder der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung registriert werden.  
  
> [!NOTE]  
>  Bevor Sie die folgenden Schritte ausführen, erstellen Sie einen zentralen Verwaltungsserver und Servergruppen. Weitere Informationen finden Sie unter [Erstellen eines zentralen Verwaltungsservers und einer Servergruppe &#40;SQL Server Management Studio&#41;](create-a-central-management-server-and-server-group.md).  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **Ausführen von Anweisungen für mehrere Server mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Da die durch einen zentralen Verwaltungsserver verwalteten Verbindungen im Kontext des Benutzers unter Verwendung der Windows-Authentifizierung ausgeführt werden, können die gültigen Berechtigungen auf den registrierten Servern variieren. Der Benutzer kann beispielsweise für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz A ein Mitglied der festen Serverrolle sysadmin sein, für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz B jedoch über eingeschränkte Berechtigungen verfügen.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-execute-statements-against-multiple-configuration-targets-simultaneously"></a>So führen Sie Anweisungen gleichzeitig für mehrere Konfigurationsziele aus  
  
1.  Klicken Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]im Menü **Ansicht** auf **Registrierte Server**.  
  
2.  Erweitern Sie einen zentralen Verwaltungsserver, klicken Sie mit der rechten Maustaste auf eine Servergruppe, zeigen Sie auf **Verbinden**, und klicken Sie anschließend auf **Neue Abfrage**.  
  
3.  Geben Sie im Abfrage-Editor eine [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung ein, und führen Sie sie aus, z. B.:  
  
    ```  
    USE master  
    GO  
    SELECT * FROM sysdatabases;  
    GO  
    ```  
  
     Standardmäßig werden im Ergebnisbereich die Abfrageergebnisse aller Servern in der Servergruppe angezeigt.  
  
#### <a name="to-change-the-multiserver-results-options"></a>So ändern Sie die Optionen für Multiserverergebnisse  
  
1.  Klicken Sie in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]im Menü **Extras** auf **Optionen**.  
  
2.  Erweitern Sie **Abfrageergebnisse**, erweitern Sie **SQL Server**, und klicken Sie dann auf **Multiserverergebnisse**.  
  
3.  Geben Sie auf der Seite **Multiserverergebnisse** die gewünschten Optionseinstellungen an, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten mehrerer Server mithilfe von zentralen Verwaltungsservern](../../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
