---
title: Aktualisieren von Master Data Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9c3543f3-3eb9-455d-a9bf-f17e9506ad21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: da78f21c6346281dc23332f40e8e6f46ff07aa06
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62774654"
---
# <a name="upgrade-master-data-services"></a>Aktualisieren von Master Data Services
  Es gibt vier Szenarien zum Aktualisieren auf Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2. Wählen Sie das Szenario aus, das der Situation entspricht.  
  
-   [Upgrade ohne Datenbank-Engine-Upgrade](#noengine)  
  
-   [Upgrade mit Datenbank-Engine-Upgrade](#engine)  
  
-   [Upgrade in einem Szenario mit zwei Computern](#twocomputer)  
  
-   [Upgrade mit Wiederherstellung einer Datenbank aus einer Sicherung](#restore)  
  
> [!IMPORTANT]
>  -   Upgrades von der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP1-Version auf die CTP2-Version werden nicht unterstützt.  
> -   Sichern Sie die Datenbank vor dem Ausführen eines beliebigen Upgrades.  
> -   Durch den Upgradevorgang werden gespeicherte Prozeduren neu erstellt und von [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]verwendete Tabellen aktualisiert. Anpassungen, die Sie an einer dieser Komponenten vorgenommen haben, können verloren gehen.  
> -   Modellbereitstellungspakete können nur in der Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden, in der sie erstellt wurden. Sie können [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] keine in erstellten Modell Bereitstellungs Pakete [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]für bereitstellen.  
> -   Sie können weiterhin die Version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1 des Master Data Services-Add-Ins für Excel verwenden, nachdem Sie für Master Data Services und Data Quality Services ein Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 ausgeführt haben. Frühere Versionen des Master Data Services-Add-Ins für Excel sind nach einem Upgrade auf SQL Server 2014 CTP2 jedoch nicht funktionsfähig. Sie können die [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP1-Version des Master Data Services-Add-Ins für Excel [hier](https://go.microsoft.com/fwlink/?LinkId=328664)herunterladen.  
  
##  <a name="upgrade-without-database-engine-upgrade"></a><a name="noengine"></a>Upgrade ohne Datenbank-Engine Upgrade  
 Dieses Szenario kann als parallele Installation betrachtet werden [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] / [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , da sowohl als auch [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] parallel auf demselben Computer oder auf separaten Computern installiert sind.  
  
 In diesem Szenario hosten Sie weiterhin die MDS-Datenbank mithilfe von [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. Sie müssen jedoch das Schema der MDS-Datenbank aktualisieren und dann eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Webanwendung erstellen, um auf die MDS-Datenbank zuzugreifen. Die MDS-Datenbank kann nicht mehr von der [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]- oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Webanwendung aus aufgerufen werden.  
  
 Wenn Sie und eine frühere [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Version von SQL Server ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]/[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) auf demselben Computer installieren möchten, können Sie dies tun, da die Dateien an einem anderen Speicherort installiert werden.  
  
-   In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]werden die Dateien standardmäßig in *Laufwerk*:\Programme\Microsoft SQL Server\120\Master Data Services installiert.  
  
-   In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]werden die Dateien standardmäßig in *Laufwerk*:\Programme\Microsoft SQL Server\110\Master Data Services installiert.  
  
-   In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]werden die Dateien standardmäßig in *Laufwerk*:\Programme\Microsoft SQL Server\Master Data Services installiert.  
  
 Führen Sie die folgenden Schritte aus, um diese Aufgabe auszuführen.  
  
1.  Installieren Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] und beliebige andere Funktionen.  
  
    1.  Öffnen Sie den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup-Assistenten.  
  
    2.  Klicken Sie im linken Bereich auf **Installation**.  
  
    3.  Klicken Sie im rechten Bereich auf **Neue eigenständige SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.  
  
    4.  Wählen Sie auf der Seite **Funktionsauswahl** die Funktion **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** sowie alle weiteren Funktionen aus, die Sie installieren möchten.  
  
    5.  Schließen Sie den Assistenten ab.  
  
2.  Wenn die Installation abgeschlossen ist, aktualisieren Sie das MDS-Datenbankschema.  
  
    1.  Öffnen Sie die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version von [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Um das MDS-Datenbankschema zu aktualisieren, müssen Sie in dem Administratorkonto angemeldet sein, das beim Erstellen der MDS-Datenbank angegeben wurde. Dieser Benutzer weist in der MDS-Datenbank in mdm.tblUser den **ID** -Wert **1**auf. Weitere Informationen zum Ändern dieses Benutzers finden Sie unter [Ändern des System Administrator Kontos &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
    2.  Klicken Sie im linken Bereich auf **Datenbankkonfiguration**.  
  
    3.  Klicken Sie im rechten Bereich auf **Datenbank auswählen** , und geben Sie die Informationen [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] für [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ihre-oder-Daten Bank Instanz an.  
  
    4.  Klicken Sie auf **Datenbank aktualisieren** , um den **Datenbankupgrade-Assistenten**zu starten. Weitere Informationen finden Sie unter [Datenbankupgrade-Assistent &#40;Konfigurations-Manager für Master Data Services&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
3.  Wenn das Upgrade abgeschlossen ist, erstellen Sie eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Webanwendung.  
  
    1.  Öffnen Sie die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version von [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  Klicken Sie im linken Bereich auf **Webkonfiguration**.  
  
    3.  Wählen Sie im rechten Bereich aus der Liste **Website** eine der folgenden Optionen aus:  
  
        -   **Standardwebsite**, klicken Sie dann auf **Anwendung erstellen**.  
  
        -   **Neue Website erstellen**. Beim Erstellen der Website wird automatisch eine neue Webanwendung erstellt.  
  
        > [!IMPORTANT]  
        >  Die vorhandene MDS-Webanwendung aus einer früheren SQL Server-Version ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) kann in der SQL Server 2014-Version des Konfigurations-Managers für Master Data Services ausgewählt werden. Sie dürfen nicht die vorhandene Webanwendung auswählen, sondern müssen stattdessen eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Webanwendung für MDS erstellen. Andernfalls wird beim Versuch, die Webanwendung der aktualisierten MDS-Datenbank zuzuordnen, eine Fehlermeldung mit dem Hinweis ausgegeben, dass auf die angeforderte Seite nicht zugegriffen werden kann, da die zugehörigen Konfigurationsdaten für die Seite ungültig sind.  
        >   
        >  Wenn Sie für die MDS-Webanwendung denselben Namen (Alias) wie für die vorhandene Webanwendung (aus [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) verwenden möchten, müssen Sie die Webanwendung und den zugehörigen Anwendungspool zunächst aus IIS löschen und dann mit der SQL Server 2014-Version des Konfigurations-Managers für Master Data Services eine Webanwendung mit demselben Namen erstellen. Informationen zum Entfernen von Webanwendungen und Anwendungspools aus IIS finden Sie unter [Entfernen einer Anwendung (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) und [Entfernen eines Anwendungspools (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).  
  
4.  Ordnen Sie nun die neue Webanwendung der aktualisierten MDS-Datenbank zu.  
  
    1.  Klicken Sie im Abschnitt **Anwendung einer Datenbank zuordnen** auf **Auswählen**.  
  
    2.  Wählen Sie die MDS-Datenbank aus.  
  
    3.  Klicken Sie auf **Anwenden**.  
  
##  <a name="upgrade-with-database-engine-upgrade"></a><a name="engine"></a> Upgrade mit Datenbankmodulupgrade  
 In diesem Szenario aktualisieren Sie sowohl die Datenbank-Engine als auch die [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]-Anwendung von [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder SQL Server 2012 auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Führen Sie die folgenden Schritte aus, um diese Aufgabe auszuführen.  
  
1.  **Nur für [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]** : Öffnen Sie **Systemsteuerung** > **Programme und Funktionen**, und deinstallieren Sie Microsoft [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].  
  
2.  Aktualisieren Sie die Datenbank-Engine auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
    1.  Öffnen Sie den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup-Assistenten.  
  
    2.  Klicken Sie im linken Bereich auf **Installation**.  
  
    3.  Klicken Sie im rechten Bereich auf **Upgrade von SQL Server 2005, SQL Server 2008, SQL Server 2008 R2 oder SQL Server 2012**.  
  
    4.  Schließen Sie den Assistenten ab.  
  
3.  **Nur [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] für**: Wenn das Upgrade fertiggestellt ist, fügen **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** Sie das Feature hinzu.  
  
    1.  Öffnen Sie den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup-Assistenten.  
  
    2.  Klicken Sie im linken Bereich auf **Installation**.  
  
    3.  Klicken Sie im rechten Bereich auf **Neue eigenständige SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.  
  
    4.  Wählen Sie im Assistenten auf der Seite **Installationstyp** die Option **Funktionen zu einer vorhandenen Instanz hinzufügen** aus, und wählen Sie die Instanz aus, auf der die MDS-Datenbank installiert ist.  
  
    5.  Wählen Sie **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** auf der Seite **Funktionsauswahl** unter frei **gegebene Funktionen**die Option aus.  
  
    6.  Schließen Sie den Assistenten ab.  
  
4.  Aktualisieren Sie das MDS-Datenbankschema.  
  
    1.  Öffnen Sie die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version von [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Um das MDS-Datenbankschema zu aktualisieren, müssen Sie in dem Administratorkonto angemeldet sein, das beim Erstellen der MDS-Datenbank angegeben wurde. Dieser Benutzer weist in der MDS-Datenbank in mdm.tblUser den **ID** -Wert **1**auf. Weitere Informationen zum Ändern dieses Benutzers finden Sie unter [Ändern des System Administrator Kontos &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
    2.  Klicken Sie im linken Bereich auf **Datenbankkonfiguration**.  
  
    3.  Klicken Sie im rechten Bereich auf **Datenbank auswählen** , und geben Sie die Informationen für die Daten Bank Instanz an.  
  
    4.  Klicken Sie auf **Datenbank aktualisieren** , um den **Datenbankupgrade-Assistenten**zu starten. Weitere Informationen finden Sie unter [Datenbankupgrade-Assistent &#40;Konfigurations-Manager für Master Data Services&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
    5.  Klicken Sie auf **Anwenden**.  
  
5.  Wenn das Upgrade abgeschlossen ist, erstellen Sie eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Webanwendung.  
  
    1.  Öffnen Sie die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version von [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  Klicken Sie im linken Bereich auf **Webkonfiguration**.  
  
    3.  Wählen Sie im rechten Bereich aus der Liste **Website** eine der folgenden Optionen aus:  
  
        -   **Standardwebsite**, klicken Sie dann auf **Anwendung erstellen**.  
  
        -   **Neue Website erstellen**. Beim Erstellen der Website wird automatisch eine neue Webanwendung erstellt.  
  
        > [!IMPORTANT]  
        >  Die vorhandene MDS-Webanwendung aus einer früheren SQL Server-Version ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) kann in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Version des Konfigurations-Managers für Master Data Services ausgewählt werden. Sie dürfen nicht die vorhandene Webanwendung auswählen, sondern müssen stattdessen eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Webanwendung für MDS erstellen. Andernfalls wird beim Versuch, die Webanwendung der aktualisierten MDS-Datenbank zuzuordnen, eine Fehlermeldung mit dem Hinweis ausgegeben, dass auf die angeforderte Seite nicht zugegriffen werden kann, da die zugehörigen Konfigurationsdaten für die Seite ungültig sind.  
        >   
        >  Wenn Sie für die MDS-Webanwendung denselben Namen (Alias) wie für die vorhandene Webanwendung (aus [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) verwenden möchten, müssen Sie die Webanwendung und den zugehörigen Anwendungspool zunächst aus IIS löschen und dann mit der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Version des Konfigurations-Managers für Master Data Services eine Webanwendung mit demselben Namen erstellen. Informationen zum Entfernen von Webanwendungen und Anwendungspools aus IIS finden Sie unter [Entfernen einer Anwendung (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) und [Entfernen eines Anwendungspools (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).  
  
6.  Ordnen Sie nun die neue Webanwendung der aktualisierten MDS-Datenbank zu.  
  
    1.  Klicken Sie im Abschnitt **Anwendung einer Datenbank zuordnen** auf **Auswählen**.  
  
    2.  Wählen Sie die MDS-Datenbank aus.  
  
    3.  Klicken Sie auf **Anwenden**.  
  
##  <a name="upgrade-in-two-computer-scenario"></a><a name="twocomputer"></a> Upgrade in einem Szenario mit zwei Computern  
 In diesem Szenario wird ein System aktualisiert, in dem SQL Server auf zwei Computern installiert ist: einer mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] und der andere mit SQL Server 2008 R2 oder SQL Server 2012.  
  
 Wenn [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] installiert ist, verwenden Sie weiterhin [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] bzw. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] zum Hosten der MDS-Datenbank auf einem Computer. Sie müssen jedoch das Schema der MDS-Datenbank aktualisieren und dann die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Webanwendung verwenden, um auf die MDS-Datenbank zuzugreifen. Die MDS-Datenbank kann nicht mehr von der [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]- oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Webanwendung aus aufgerufen werden.  
  
-   In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]werden die Dateien standardmäßig in *Laufwerk*:\Programme\Microsoft SQL Server\120\Master Data Services installiert.  
  
-   In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]werden die Dateien standardmäßig in *Laufwerk*:\Programme\Microsoft SQL Server\110\Master Data Services installiert.  
  
-   In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]werden die Dateien standardmäßig in *Laufwerk*:\Programme\Microsoft SQL Server\Master Data Services installiert.  
  
 Führen Sie die folgenden Schritte aus, um diese Aufgabe auszuführen.  
  
1.  Installieren Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] und beliebige andere Funktionen.  
  
    1.  Öffnen Sie den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup-Assistenten.  
  
    2.  Klicken Sie im linken Bereich auf **Installation**.  
  
    3.  Klicken Sie im rechten Bereich auf **Neue eigenständige SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.  
  
    4.  Wählen Sie auf der Seite **Funktionsauswahl** die Funktion **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** sowie alle weiteren Funktionen aus, die Sie installieren möchten.  
  
    5.  Schließen Sie den Assistenten ab.  
  
2.  Wenn die Installation abgeschlossen ist, aktualisieren Sie das MDS-Datenbankschema.  
  
    1.  Öffnen Sie die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version von [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Um das MDS-Datenbankschema zu aktualisieren, müssen Sie in dem Administratorkonto angemeldet sein, das beim Erstellen der MDS-Datenbank angegeben wurde. Dieser Benutzer weist in der MDS-Datenbank in mdm.tblUser den **ID** -Wert **1**auf. Weitere Informationen zum Ändern dieses Benutzers finden Sie unter [Ändern des System Administrator Kontos &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
    2.  Klicken Sie im linken Bereich auf **Datenbankkonfiguration**.  
  
    3.  Klicken Sie im rechten Bereich auf **Datenbank auswählen** , und geben Sie die Informationen [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] für [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ihre-oder-Daten Bank Instanz auf [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] dem [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] anderen Computer an, wenn oder auf dem anderen Computer installiert ist.  
  
    4.  Klicken Sie auf **Datenbank aktualisieren** , um den **Datenbankupgrade-Assistenten**zu starten. Weitere Informationen finden Sie unter [Datenbankupgrade-Assistent &#40;Konfigurations-Manager für Master Data Services&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
3.  Wenn das Upgrade abgeschlossen ist, erstellen Sie eine SQL Server 2014-Webanwendung.  
  
    1.  Öffnen Sie die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version von [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  Klicken Sie im linken Bereich auf **Webkonfiguration**.  
  
    3.  Wählen Sie im rechten Bereich aus der Liste **Website** eine der folgenden Optionen aus:  
  
        -   **Standardwebsite**, klicken Sie dann auf **Anwendung erstellen**.  
  
        -   **Neue Website erstellen**. Beim Erstellen der Website wird automatisch eine neue Webanwendung erstellt.  
  
        > [!IMPORTANT]  
        >  Die vorhandene MDS-Webanwendung aus einer früheren SQL Server-Version ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) kann in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Version des Konfigurations-Managers für Master Data Services ausgewählt werden. Sie dürfen nicht die vorhandene Webanwendung auswählen, sondern müssen stattdessen eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Webanwendung für MDS erstellen. Andernfalls wird beim Versuch, die Webanwendung der aktualisierten MDS-Datenbank zuzuordnen, eine Fehlermeldung mit dem Hinweis ausgegeben, dass auf die angeforderte Seite nicht zugegriffen werden kann, da die zugehörigen Konfigurationsdaten für die Seite ungültig sind.  
        >   
        >  Wenn Sie für die MDS-Webanwendung denselben Namen (Alias) wie für die vorhandene Webanwendung (aus [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) verwenden möchten, müssen Sie die Webanwendung und den zugehörigen Anwendungspool zunächst aus IIS löschen und dann mit der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Version des Konfigurations-Managers für Master Data Services eine Webanwendung mit demselben Namen erstellen. Informationen zum Entfernen von Webanwendungen und Anwendungspools aus IIS finden Sie unter [Entfernen einer Anwendung (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) und [Entfernen eines Anwendungspools (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).  
  
4.  Ordnen Sie nun die Webanwendung der aktualisierten MDS-Datenbank zu.  
  
    1.  Klicken Sie im Abschnitt **Anwendung einer Datenbank zuordnen** auf **Auswählen**.  
  
    2.  Wählen Sie die MDS-Datenbank aus.  
  
    3.  Klicken Sie auf **Anwenden**.  
  
##  <a name="upgrade-with-restoring-a-database-from-backup"></a><a name="restore"></a> Upgrade mithilfe einer Wiederherstellung einer Datenbank aus einer Sicherung  
 In diesem Szenario wird [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zusammen mit SQL Server 2008 R2 oder SQL Server 2012 auf demselben Computer oder auf zwei unterschiedlichen Computern installiert. Vor dem Upgrade wurde außerdem eine Datenbank in einer Version vor [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] CTP2 gesichert und muss wiederhergestellt werden.  
  
-   In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]werden die Dateien standardmäßig in *Laufwerk*:\Programme\Microsoft SQL Server\120\Master Data Services installiert.  
  
-   In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]werden die Dateien standardmäßig in *Laufwerk*:\Programme\Microsoft SQL Server\110\Master Data Services installiert.  
  
-   In [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]werden die Dateien standardmäßig in *Laufwerk*:\Programme\Microsoft SQL Server\Master Data Services installiert.  
  
 Führen Sie die folgenden Schritte aus, um diese Aufgabe auszuführen.  
  
1.  Installieren Sie [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] und beliebige andere Funktionen.  
  
    1.  Öffnen Sie den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Setup-Assistenten.  
  
    2.  Klicken Sie im linken Bereich auf **Installation**.  
  
    3.  Klicken Sie im rechten Bereich auf **Neue eigenständige SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.  
  
    4.  Wählen Sie auf der Seite **Funktionsauswahl** die Funktion **[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]** sowie alle weiteren Funktionen aus, die Sie installieren möchten.  
  
    5.  Schließen Sie den Assistenten ab.  
  
2.  Stellen Sie die Datenbank wieder her, die gesichert wurde.  
  
3.  Wenn die Installation abgeschlossen ist, aktualisieren Sie das MDS-Datenbankschema.  
  
    1.  Öffnen Sie die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version von [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
        > [!IMPORTANT]  
        >  Um das MDS-Datenbankschema zu aktualisieren, müssen Sie in dem Administratorkonto angemeldet sein, das beim Erstellen der MDS-Datenbank angegeben wurde. Dieser Benutzer weist in der MDS-Datenbank in mdm.tblUser den **ID** -Wert **1**auf. Weitere Informationen zum Ändern dieses Benutzers finden Sie unter [Ändern des System Administrator Kontos &#40;Master Data Services&#41;](../../master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
    2.  Klicken Sie im linken Bereich auf **Datenbankkonfiguration**.  
  
    3.  Klicken Sie im rechten Bereich auf **Datenbank auswählen** , und geben Sie die Informationen [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] für [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ihre-oder-Daten Bank Instanz an.  
  
    4.  Klicken Sie auf **Datenbank aktualisieren** , um den **Datenbankupgrade-Assistenten**zu starten. Weitere Informationen finden Sie unter [Datenbankupgrade-Assistent &#40;Konfigurations-Manager für Master Data Services&#41;](../../master-data-services/upgrade-database-wizard-master-data-services-configuration-manager.md).  
  
4.  Wenn das Upgrade abgeschlossen ist, erstellen Sie eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Webanwendung.  
  
    1.  Öffnen Sie die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Version von [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)].  
  
    2.  Klicken Sie im linken Bereich auf **Webkonfiguration**.  
  
    3.  Wählen Sie im rechten Bereich aus der Liste **Website** eine der folgenden Optionen aus:  
  
        -   **Standardwebsite**, klicken Sie dann auf **Anwendung erstellen**.  
  
        -   **Neue Website erstellen**. Beim Erstellen der Website wird automatisch eine neue Webanwendung erstellt.  
  
        > [!IMPORTANT]  
        >  Die vorhandene MDS-Webanwendung aus einer früheren SQL Server-Version ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) kann in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Version des Konfigurations-Managers für Master Data Services ausgewählt werden. Sie dürfen nicht die vorhandene Webanwendung auswählen, sondern müssen stattdessen eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Webanwendung für MDS erstellen. Andernfalls wird beim Versuch, die Webanwendung der aktualisierten MDS-Datenbank zuzuordnen, eine Fehlermeldung mit dem Hinweis ausgegeben, dass auf die angeforderte Seite nicht zugegriffen werden kann, da die zugehörigen Konfigurationsdaten für die Seite ungültig sind.  
        >   
        >  Wenn Sie für die MDS-Webanwendung denselben Namen (Alias) wie für die vorhandene Webanwendung (aus [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]) verwenden möchten, müssen Sie die Webanwendung und den zugehörigen Anwendungspool zunächst aus IIS löschen und dann mit der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Version des Konfigurations-Managers für Master Data Services eine Webanwendung mit demselben Namen erstellen. Informationen zum Entfernen von Webanwendungen und Anwendungspools aus IIS finden Sie unter [Entfernen einer Anwendung (IIS)](https://go.microsoft.com/fwlink/?LinkId=323537) und [Entfernen eines Anwendungspools (IIS)](https://go.microsoft.com/fwlink/?LinkId=323538).  
  
5.  Ordnen Sie nun die neue Webanwendung der aktualisierten MDS-Datenbank zu.  
  
    1.  Klicken Sie im Abschnitt **Anwendung einer Datenbank zuordnen** auf **Auswählen**.  
  
    2.  Wählen Sie die MDS-Datenbank aus.  
  
    3.  Klicken Sie auf **Anwenden**.  
  
## <a name="troubleshooting"></a>Problembehandlung  
 **Problem:** Wenn Sie die [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] -oder [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] -Webanwendung öffnen, wird die Fehlermeldung "die Client Version ist nicht mit der Datenbankversion kompatibel" angezeigt.  
  
 **Lösung:** Dieses Problem tritt auf, [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Wenn [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] eine-oder Master Data Manager-Webanwendung versucht, auf eine Datenbank [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zuzugreifen, die auf Master Data Services aktualisiert wurde. Sie müssen stattdessen eine [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Webanwendung verwenden.  
  
 Dieses Problem tritt möglicherweise auch auf, wenn Sie beim Upgrade des MDS-Datenbankschemas den **MDS-Anwendungspool** in IIS nicht angehalten und neu gestartet haben. Starten Sie den **MDS-Anwendungspool** neu, um das Problem zu beheben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installieren von Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)  
  
  
