---
title: 'Lektion 1: Herstellen einer Verbindung mit der Datenbank-Engine | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8db82f0-50ed-4531-9209-940006ed34cb
caps.latest.revision: 22
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 02942c1f5e223cdf996cb691a4e7d42cc95c1b81
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148865"
---
# <a name="lesson-1-connecting-to-the-database-engine"></a>Lektion 1: Herstellen einer Verbindung mit der Datenbank-Engine
  Welche Tools beim Installieren von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]installiert werden, hängt von der Edition und den von Ihnen ausgewählten Installationsoptionen ab. In dieser Lektion werden die Haupttools vorgestellt, und Sie erfahren, wie Sie Verbindungen herstellen und eine einfache Funktion (Autorisieren zusätzlicher Benutzer) ausführen.  
  
  
  
##  <a name="tools"></a> Tools für die ersten Schritte  
 Im Lieferumfang von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] sind eine Vielzahl von Tools enthalten. In diesem Thema wird beschrieben, welche Tools Sie zuerst benötigen und wie das richtige Tool für den Auftrag ausgewählt wird. Auf alle Tools kann über das Menü **Start** zugegriffen werden. Einige Tools wie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]werden nicht standardmäßig installiert. Die Tools müssen als Teil der Clientkomponenten während der Ausführung des Setupprogramms installiert werden. Eine vollständige Beschreibung der unten aufgeführten Tools finden Sie, indem Sie in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Onlinedokumentation danach suchen. [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] enthält nur eine Teilmenge der Tools.  
  
### <a name="basic-tools"></a>Haupttools  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ist das Haupttool zum Verwalten von [!INCLUDE[ssDE](../includes/ssde-md.md)] und Schreiben von [!INCLUDE[tsql](../includes/tsql-md.md)]-Code. Es wird in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Shell gehostet. Es ist nicht in enthalten [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] steht jedoch als separates Download vom [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=144346).  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Konfigurations-Manager wird sowohl mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] als auch mit den Clienttools installiert. Sie können damit Serverprotokolle aktivieren, Protokolloptionen wie z. B. TCP-Ports konfigurieren, Serverdienste so konfigurieren, dass sie automatisch gestartet werden, und Clientcomputer so konfigurieren, dass sie mit dem von Ihnen bevorzugten Verfahren gestartet werden. Mit diesem Tool können erweiterte Konnektivitätselemente konfiguriert, aber keine Funktionen aktiviert werden.  
  
### <a name="sample-database"></a>Beispieldatenbank  
 Die Beispieldatenbanken und Beispiele werden nicht standardmäßig mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]geliefert. Die meisten Beispiele, die in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Onlinedokumentation beschrieben werden, basieren auf der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] -Beispieldatenbank.  
  
##### <a name="to-start-sql-server-management-studio"></a>So starten Sie SQL Server Management Studio  
  
-   Auf der **starten** Sie im Menü **Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], und klicken Sie dann auf **SQL Server Management Studio**.  
  
##### <a name="to-start-sql-server-configuration-manager"></a>So starten Sie den SQL Server-Konfigurations-Manager  
  
-   Zeigen Sie im Menü **Start** auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
##  <a name="connect"></a> Herstellen einer Verbindung mit Management Studio  
 Es ist sehr einfach, mithilfe von Tools, die auf demselben Computer ausgeführt werden, eine Verbindung mit [!INCLUDE[ssDE](../includes/ssde-md.md)] herzustellen, wenn Sie den Namen der Instanz kennen und wenn Sie die Verbindung als Mitglied der Administratorengruppe auf dem Computer herstellen. Die folgenden Vorgänge müssen auf dem Computer ausgeführt werden, der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]hostet.  
  
##### <a name="to-determine-the-name-of-the-instance-of-the-database-engine"></a>So bestimmen Sie den Namen der Instanz der Datenbank-Engine  
  
1.  Melden Sie sich bei Windows als Mitglied der Administratorgruppe an, und öffnen Sie [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
    > [!IMPORTANT]  
    >  Wenn Sie Herstellen einer Verbindung mit [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] auf [!INCLUDE[wiprlhlong](../includes/wiprlhlong-md.md)] oder [!INCLUDE[nextref_longhorn](../includes/nextref-longhorn-md.md)] (oder neuere), müssen Sie möglicherweise mit der rechten Maustaste [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] , und klicken Sie dann auf **als Administrator ausführen** um eine Verbindung herzustellen, verwenden den Administrator Anmeldeinformationen. Als Neuerung in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] werden beim Setup ausgewählte Anmeldungen zu [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] hinzugefügt, sodass die Administratoranmeldeinformationen nicht erforderlich sind.  
  
2.  Klicken Sie im Dialogfeld **Verbindung mit Server herstellen** auf **Abbrechen**.  
  
3.  Wenn Registrierte Server nicht angezeigt wird, klicken Sie im Menü **Ansicht** auf **Registrierte Server**.  
  
4.  Wählen Sie in der Symbolleiste „Registrierte Server“ die Option **Datenbank-Engine** aus, erweitern Sie **Datenbank-Engine**, klicken Sie mit der rechten Maustaste auf **Lokale Servergruppen**, zeigen Sie auf **Tasks**, und klicken Sie anschließend auf **Lokale Server registrieren**. Es werden alle auf dem Computer installierten Instanzen von [!INCLUDE[ssDE](../includes/ssde-md.md)] angezeigt. Die Standardinstanz hat keinen Namen und wird mit dem Computernamen angezeigt. Eine benannte Instanz wird als der Computername, gefolgt von einem umgekehrten Schrägstrich (\\) und dem Namen der Instanz, angezeigt. Für [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] hat die Instanz den Namen *<Computername>* \sqlexpress, es sei denn, der Name wurde während des Setups geändert.  
  
##### <a name="to-verify-that-the-database-engine-is-running"></a>So überprüfen Sie, ob die Datenbank-Engine ausgeführt wird  
  
1.  Wenn in Registrierte Server neben dem Namen Ihrer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ein grüner Punkt mit einem weißen Pfeil angezeigt wird, bedeutet dies, dass [!INCLUDE[ssDE](../includes/ssde-md.md)] ausgeführt wird und keine weiteren Aktionen erforderlich sind.  
  
2.  Wenn neben dem Name Ihrer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ein roter Punkt mit einem weißen Quadrat angezeigt wird, wurde [!INCLUDE[ssDE](../includes/ssde-md.md)] beendet. Klicken Sie mit der rechten Maustaste auf den [!INCLUDE[ssDE](../includes/ssde-md.md)]-Namen, und klicken Sie auf **Dienstkontrolle**und anschließend auf **Starten**. Nachdem ein Bestätigungsdialogfeld angezeigt wurde, sollte das [!INCLUDE[ssDE](../includes/ssde-md.md)] gestartet werden und ein grüner Kreis mit einem weißen Pfeil angezeigt werden.  
  
##### <a name="to-connect-to-the-database-engine"></a>So stellen Sie eine Verbindung mit der Datenbank-Engine her  
  
1.  Klicken Sie in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]im Menü **Datei** auf **Objekt-Explorer verbinden**.  
  
     Das Dialogfeld **Verbindung mit Server herstellen** wird geöffnet. Im Feld **Servertyp** wird der zuletzt verwendete Typ der Komponente angezeigt.  
  
2.  Wählen Sie **Datenbank-Engine** aus.  
  
3.  Geben Sie im Feld **Servername** den Namen der Instanz von [!INCLUDE[ssDE](../includes/ssde-md.md)]ein. Bei der Standardinstanz von SQL Server ist der Servername der Name des Computers. Bei einer benannten Instanz von SQL Server ist der Servername der *<Computername>***\\***<Instanzname>*, wie z.B. **ACCTG_SRVR\SQLEXPRESS**.  
  
4.  Klicken Sie auf **Verbinden**.  
  
##  <a name="additional"></a> Autorisieren zusätzlicher Verbindungen  
 Nachdem Sie eine Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] als Administrator hergestellt haben, besteht eine Ihrer ersten Aufgaben darin, Verbindungen für andere Benutzer zu autorisieren. Dazu erstellen Sie eine Anmeldung und erteilen dieser Anmeldung die Berechtigung, als Benutzer auf eine Datenbank zuzugreifen. Eine Anmeldung kann entweder eine Anmeldung mit Windows-Authentifizierung sein, die Windows-Anmeldeinformationen verwendet, oder eine Anmeldung mit SQL Server-Authentifizierung, die die Authentifizierungsinformationen in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] speichert und von Ihren Windows-Anmeldeinformationen unabhängig ist. Verwenden Sie nach Möglichkeit immer Windows-Authentifizierung.  
  
##### <a name="create-a-windows-authentication-login"></a>So erstellen Sie eine Anmeldung mit Windows-Authentifizierung  
  
1.  In der vorhergehenden Aufgabe haben Sie eine Verbindung mit [!INCLUDE[ssDE](../includes/ssde-md.md)] mithilfe von [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]hergestellt. Erweitern Sie im Objekt-Explorer Ihre Serverinstanz, erweitern Sie **Sicherheit**, klicken Sie mit der rechten Maustaste auf **Anmeldungen**, und klicken Sie anschließend auf **Neue Anmeldung**.  
  
     Das Dialogfeld **Anmeldung – Neu** wird angezeigt.  
  
2.  Auf der **allgemeine** Seite in der **Anmeldename** Geben Sie eine Windows-Anmeldung im Format  *\<Domäne >\\< Anmeldung\>*.  
  
3.  Wählen Sie (sofern verfügbar) **im Feld** Standarddatenbank [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] aus. Wählen Sie andernfalls **master**aus.  
  
4.  Wenn die neue Anmeldung ein Administrator sein soll, klicken Sie auf der Seite **Serverrollen** auf **sysadmin**, andernfalls lassen Sie sie leer.  
  
5.  Wählen Sie auf der Seite **Benutzerzuordnung** die Option **Zuordnen** für die [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] -Datenbank aus, sofern diese verfügbar ist. Wählen Sie andernfalls **master**aus. Beachten Sie, dass das Feld **Benutzer** mit der Anmeldung aufgefüllt wird. Wenn das Dialogfeld geschlossen wird, erstellt es diesen Benutzer in der Datenbank.  
  
6.  Geben Sie im Feld **Standardschema** den Schemanamen **dbo** ein, um die Anmeldung dem Schema für Datenbankbesitzer zuzuordnen.  
  
7.  Akzeptieren Sie die Standardeinstellungen für die Felder **Sicherungsfähige Elemente** und **Status** , und klicken Sie auf **OK** , um die Anmeldung zu erstellen.  
  
> [!IMPORTANT]  
>  Diese grundlegenden Informationen sollen Ihnen den Einstieg erleichtern. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] stellt eine umfassende Sicherheitsumgebung bereit, da das Thema Sicherheit offensichtlich einen wichtigen Aspekt des Datenbankbetriebs darstellt.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Herstellen einer Verbindung von einem anderen Computer](lesson-2-connecting-from-another-computer.md)  
  
  