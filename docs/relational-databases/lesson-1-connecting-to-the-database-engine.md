---
description: 'Lektion 1: Herstellen einer Verbindung mit der Datenbank-Engine'
title: 'Lektion 1: Herstellen einer Verbindung mit der Datenbank-Engine | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 02/05/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: quickstart
ms.assetid: e8db82f0-50ed-4531-9209-940006ed34cb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b1685a4d93d14b3cd49a4c9a4a031943a5b9f7e
ms.sourcegitcommit: 80701484b8f404316d934ad2a85fd773e26ca30c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93243829"
---
# <a name="lesson-1-connecting-to-the-database-engine"></a>Lektion 1: Herstellen einer Verbindung mit der Datenbank-Engine
[!INCLUDE[sqlserver](../includes/applies-to-version/sqlserver.md)]

Welche Tools beim Installieren von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]installiert werden, hängt von der Edition und den von Ihnen ausgewählten Installationsoptionen ab. In dieser Lektion werden die Haupttools vorgestellt, und Sie erfahren, wie Sie Verbindungen herstellen und eine einfache Funktion (Autorisieren zusätzlicher Benutzer) ausführen.  

Diese Lektion enthält die folgenden Aufgaben:  
- [Tools für die ersten Schritte](#tools)  
- [Herstellen einer Verbindung mit Management Studio](#connect)  
- [Autorisieren zusätzlicher Verbindungen](#additional) 

## <a name=""></a><a name="tools">Tools für die ersten Schritte</a> 
- Im Lieferumfang von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] sind eine Vielzahl von Tools enthalten. In diesem Thema wird beschrieben, welche Tools Sie zuerst benötigen und wie das richtige Tool für den Auftrag ausgewählt wird. Auf alle Tools kann über das Menü **Start** zugegriffen werden. Einige Tools wie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]werden nicht standardmäßig installiert. Die Tools müssen als Teil der Clientkomponenten während der Ausführung des Setupprogramms installiert werden. Eine vollständige Beschreibung der unten aufgeführten Tools finden Sie, indem Sie in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Onlinedokumentation danach suchen. [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] enthält nur eine Teilmenge der Tools.  

### <a name="basic-tools"></a>Haupttools
- [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (SSMS) ist das Haupttool zum Verwalten von [!INCLUDE[ssDE](../includes/ssde-md.md)] und Schreiben von [!INCLUDE[tsql](../includes/tsql-md.md)] -Code. Es wird in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Shell gehostet. SSMS steht im [Microsoft Download Center](../ssms/download-sql-server-management-studio-ssms.md)zum Herunterladen zur Verfügung. Die neueste Version kann mit älteren Versionen des [!INCLUDE[ssDE_md](../includes/ssde-md.md)]verwendet werden.  

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager wird sowohl mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] als auch mit den Clienttools installiert. Sie können damit Serverprotokolle aktivieren, Protokolloptionen wie z. B. TCP-Ports konfigurieren, Serverdienste so konfigurieren, dass sie automatisch gestartet werden, und Clientcomputer so konfigurieren, dass sie mit dem von Ihnen bevorzugten Verfahren gestartet werden. Mit diesem Tool können erweiterte Konnektivitätselemente konfiguriert, aber keine Funktionen aktiviert werden.  

### <a name="sample-database"></a>Beispieldatenbank
Die Beispieldatenbanken und Beispiele werden nicht standardmäßig mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]geliefert. Die meisten Beispiele, die in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Onlinedokumentation beschrieben werden, basieren auf der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] -Beispieldatenbank.  

##### <a name="to-start-sql-server-management-studio"></a>So starten Sie SQL Server Management Studio
- Geben Sie in den aktuellen Versionen von Windows auf der **Startseite** SSMS ein, und klicken Sie anschließend auf **Microsoft SQL Server Management Studio**.  
- Wenn Sie eine ältere Version von Windows verwenden, zeigen Sie im Menü **Start** auf **Alle Programme** , zeigen Sie auf [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], und klicken Sie anschließend auf **SQL Server Management Studio**.  

##### <a name="to-start-sql-server-configuration-manager"></a>So starten Sie den SQL Server-Konfigurations-Manager  
- Tippen Sie in aktuellen Versionen von Windows auf der **Startseite** **Configuration Manager** ein, und klicken Sie anschließend auf **SQL Server *Version* Configuration Manager**.   
- Wenn Sie eine ältere Version von Windows verwenden, zeigen Sie im **Startmenü** auf **Alle Programme** , zeigen Sie auf [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools** , und klicken Sie anschließend auf **SQL Server-Konfigurations-Manager**.  

## <a name="connecting-with-management-studio"></a><a name="connect"></a>Herstellen einer Verbindung mit Management Studio  
- Es ist sehr einfach, mithilfe von Tools, die auf demselben Computer ausgeführt werden, eine Verbindung mit [!INCLUDE[ssDE](../includes/ssde-md.md)] herzustellen, wenn Sie den Namen der Instanz kennen und wenn Sie die Verbindung als Mitglied der lokalen Administratorengruppe auf dem Computer herstellen. Die folgenden Vorgänge müssen auf dem Computer ausgeführt werden, der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]hostet.  

> [!NOTE]  
> Dieses Thema beschreibt das Herstellen einer Verbindung mit einem lokalen SQL Server. Informationen zum Herstellen einer Verbindung mit der Azure SQL-Datenbank finden Sie unter [Herstellen einer Verbindung mit einer SQL-Datenbank mit SQL Server Management Studio und Ausführen einer T-SQL-Beispielabfrage](/azure/azure-sql/database/connect-query-ssms).  

##### <a name="to-determine-the-name-of-the-instance-of-the-database-engine"></a>So bestimmen Sie den Namen der Instanz der Datenbank-Engine  

1.  Melden Sie sich bei Windows als Mitglied der Administratorgruppe an, und öffnen Sie [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
2.  Klicken Sie im Dialogfeld **Verbindung mit Server herstellen** auf **Abbrechen**.  
3.  Wenn Registrierte Server nicht angezeigt wird, klicken Sie im Menü **Ansicht** auf **Registrierte Server**.
4.  Wählen Sie in der Symbolleiste „Registrierte Server“ die Option **Datenbank-Engine** aus, erweitern Sie **Datenbank-Engine** , klicken Sie mit der rechten Maustaste auf **Lokale Servergruppen** , zeigen Sie auf **Tasks** , und klicken Sie anschließend auf **Lokale Server registrieren**. Erweitern Sie **Lokale Servergruppen** , um alle Instanzen der auf dem Computer installierten [!INCLUDE[ssDE](../includes/ssde-md.md)] anzuzeigen. Die Standardinstanz hat keinen Namen und wird mit dem Computernamen angezeigt. Eine benannte Instanz wird als der Computername, gefolgt von einem umgekehrten Schrägstrich (\\) und dem Namen der Instanz, angezeigt. Für [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] hat die Instanz den Namen *<Computername>* \sqlexpress, es sei denn, der Name wurde während des Setups geändert.  

##### <a name="to-verify-that-the-database-engine-is-running"></a>So überprüfen Sie, ob die Datenbank-Engine ausgeführt wird

1.  Wenn in Registrierte Server neben dem Namen Ihrer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ein grüner Punkt mit einem weißen Pfeil angezeigt wird, bedeutet dies, dass [!INCLUDE[ssDE](../includes/ssde-md.md)] ausgeführt wird und keine weiteren Aktionen erforderlich sind.  

2.  Wenn neben dem Name Ihrer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ein roter Punkt mit einem weißen Quadrat angezeigt wird, wurde [!INCLUDE[ssDE](../includes/ssde-md.md)] beendet. Klicken Sie mit der rechten Maustaste auf den [!INCLUDE[ssDE](../includes/ssde-md.md)]-Namen, und klicken Sie auf **Dienstkontrolle** und anschließend auf **Starten**. Nachdem ein Bestätigungsdialogfeld angezeigt wurde, sollte das [!INCLUDE[ssDE](../includes/ssde-md.md)] gestartet werden und ein grüner Kreis mit einem weißen Pfeil angezeigt werden.  

##### <a name="to-connect-to-the-database-engine"></a>So stellen Sie eine Verbindung mit der Datenbank-Engine her  

Mindestens ein Administratorkonto wurde ausgewählt, als [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] installiert wurde. Führen Sie den folgenden Schritt aus, während Sie bei Windows als Administrator angemeldet sind.

1.  Klicken Sie in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]im Menü **Datei** auf **Objekt-Explorer verbinden**. 
- Das Dialogfeld **Verbindung mit Server herstellen** wird geöffnet. Im Feld **Servertyp** wird der zuletzt verwendete Typ der Komponente angezeigt.  

2.  Wählen Sie **Datenbank-Engine** aus.

![Screenshot: Objekt-Explorer mit Hervorhebung des Dropdownmenüs bei „Verbinden“ und der Option „Datenbank-Engine“](../relational-databases/media/object-explorer.png)

3.  Geben Sie im Feld **Servername** den Namen der Instanz von [!INCLUDE[ssDE](../includes/ssde-md.md)]ein. Bei der Standardinstanz von SQL Server ist der Servername der Name des Computers. Bei einer benannten Instanz von SQL Server wird der Servername nach dem Schema _\<computer_name\>_ **\\** _\<instance_name\>_ gebildet. Beispiel: **ACCTG_SRVR\SQLEXPRESS**. Der folgende Screenshot zeigt das Herstellen einer Verbindung mit der (unbenannten) Standardinstanz von [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] auf einem Computer namens „PracticeComputer“. Der Benutzer, der bei Windows angemeldet ist, ist Mary aus der Domain „Contoso“. Bei Verwendung der Windows-Authentifizierung können Sie den Benutzernamen nicht ändern. 

![Screenshot: Dialogfeld „Verbindung mit Server herstellen“ mit hervorgehobenem Textfeld „Servername“](../relational-databases/media/connect-to-server.png)

4.  Klicken Sie auf **Verbinden**.

> [!NOTE]
> In diesem Tutorial wird davon ausgegangen, dass Sie neu bei [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sind und keine besonderen Probleme beim Herstellen einer Verbindung haben. Dies sollte für die meisten Benutzer ausreichen, und so wird das Tutorial einfach gehalten. Detaillierte Schritte zur Fehlerbehebung finden Sie unter [Beheben von Verbindungsfehlern mit der SQL Server-Datenbank-Engine](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md). 

## <a name="authorizing-additional-connections"></a><a name="additional"></a>Autorisieren zusätzlicher Verbindungen  
Nachdem Sie eine Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] als Administrator hergestellt haben, besteht eine Ihrer ersten Aufgaben darin, Verbindungen für andere Benutzer zu autorisieren. Dazu erstellen Sie eine Anmeldung und erteilen dieser Anmeldung die Berechtigung, als Benutzer auf eine Datenbank zuzugreifen. Eine Anmeldung kann entweder eine Anmeldung mit Windows-Authentifizierung sein, die Windows-Anmeldeinformationen verwendet, oder eine Anmeldung mit SQL Server-Authentifizierung, die die Authentifizierungsinformationen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] speichert und von Ihren Windows-Anmeldeinformationen unabhängig ist. Verwenden Sie nach Möglichkeit immer Windows-Authentifizierung.

> [!TIP]
> Die meisten Organisationen verfügen über Domänenbenutzer und werden Windows-Authentifizierung verwenden. Sie können selbst herumexperimentieren, indem Sie zusätzliche lokale Benutzer auf Ihrem Computer erstellen. Lokale Benutzer werden von Ihrem Computer authentifiziert, also ist die Domäne der Computername. Wenn Ihr Computer beispielsweise `MyComputer` heißt, und Sie einen Benutzer namens `Test`erstellen, dann lautet die Windows-Beschreibung des Benutzers `Mycomputer\Test`.  

##### <a name="create-a-windows-authentication-login"></a>So erstellen Sie eine Anmeldung mit Windows-Authentifizierung 

1.  In der vorhergehenden Aufgabe haben Sie eine Verbindung mit [!INCLUDE[ssDE](../includes/ssde-md.md)] mithilfe von [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]hergestellt. Erweitern Sie im Objekt-Explorer Ihre Serverinstanz, erweitern Sie **Sicherheit** , klicken Sie mit der rechten Maustaste auf **Anmeldungen** , und klicken Sie anschließend auf **Neue Anmeldung**. Das Dialogfeld **Anmeldung – Neu** wird angezeigt.  

2.  Geben Sie auf der Seite **Allgemein** im Feld **Anmeldename** eine Windows-Anmeldung in folgendem Format ein: `<domain>\\<login>`

![Screenshot: Dialogfeld „Anmeldung - Neu“ mit hervorgehobenem Textfeld „Anmeldename“](../relational-databases/media/new-login.png)

3.  Wählen Sie (sofern verfügbar) **im Feld** Standarddatenbank [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] aus. Wählen Sie andernfalls **master** aus.  
4.  Wenn die neue Anmeldung ein Administrator sein soll, klicken Sie auf der Seite **Serverrollen** auf **sysadmin** , andernfalls lassen Sie sie leer.  
5.  Wählen Sie auf der Seite **Benutzerzuordnung** die Option **Zuordnen** für die [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] -Datenbank aus, sofern diese verfügbar ist. Wählen Sie andernfalls **master** aus. Beachten Sie, dass das Feld **Benutzer** mit der Anmeldung aufgefüllt wird. Wenn das Dialogfeld geschlossen wird, erstellt es diesen Benutzer in der Datenbank.  
6.  Geben Sie im Feld **Standardschema** den Schemanamen **dbo** ein, um die Anmeldung dem Schema für Datenbankbesitzer zuzuordnen.   
7.  Akzeptieren Sie die Standardeinstellungen für die Felder **Sicherungsfähige Elemente** und **Status** , und klicken Sie auf **OK** , um die Anmeldung zu erstellen.  

> [!IMPORTANT]  
> Diese grundlegenden Informationen sollen Ihnen den Einstieg erleichtern. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stellt eine umfassende Sicherheitsumgebung bereit, da das Thema Sicherheit offensichtlich einen wichtigen Aspekt des Datenbankbetriebs darstellt.  

## <a name="next-lesson"></a>Nächste Lektion  
[Lektion 2: Herstellen einer Verbindung von einem anderen Computer](../relational-databases/lesson-2-connecting-from-another-computer.md)    
