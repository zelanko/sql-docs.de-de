---
title: Entwickeln und Bereitstellen von SQL Server-Datenbanken für Linux | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: 1e924704-e07c-4a8b-b243-8c1dd8cff0d3
ms.custom: sql-linux
ms.openlocfilehash: 1c6de6fd77de2594f4d2942fa5e5c4c82c614cc6
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "46714032"
---
# <a name="use-visual-studio-to-create-databases-for-sql-server-on-linux"></a>Verwenden Sie Visual Studio zum Erstellen von Datenbanken für SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server Data Tools (SSDT) wird Visual Studio in eine leistungsstarke Entwicklungs- und Datenbank-Lebenszyklus (DLM) verwaltungsumgebung für SQL Server unter Linux. Sie können zu entwickeln, erstellen, testen und veröffentlichen Sie Ihre Datenbank aus einem quellcodeverwalteten Projekt aus, wie Sie den Anwendungscode entwickeln.

## <a name="install-visual-studio-and-sql-server-data-tools"></a>Visual Studio und SQL Server Datatools installieren

1. Wenn Sie nicht bereits Visual Studio auf Ihrem Windows-Computer installiert haben [Herunterladen Sie und installieren Sie Visual Studio]. Wenn Sie nicht über ein Visual Studio-Lizenz verfügen, wird Visual Studio Community Edition ist eine kostenlose, voll ausgestattete IDE für Studenten, Open Source- und einzelne Entwickler.

2. Wählen Sie während der Installation von Visual Studio **benutzerdefinierte** für die **wählen Sie die Installationsart** Option. Klicken Sie auf **Weiter**.

3. Wählen Sie **Microsoft SQL Server Data Tools**, **Git für Windows**, und **GitHub-Erweiterung für Visual Studio** aus der Auswahlliste der Funktion.

    <img src="./media/sql-server-linux-develop-use-ssdt/ssdt-setup.png" alt="ssdt setup" style="width: 400px;"/>

4. Weiter, und schließen Sie die Installation von Visual Studio. Es kann einige Minuten dauern.

## <a name="upgrade-sql-server-data-tools-to-ssdt-170-rc-release"></a>Aktualisieren von SQL Server Data Tools auf SSDT 17.0 RC-Version

SQL Server unter Linux wird von SSDT-Version 17.0 RC oder höher unterstützt.

* [Herunterladen und installieren Sie SSDT 17.0 RC2](https://go.microsoft.com/fwlink/?linkid=837939).

## <a name="create-a-new-database-project-in-source-control"></a>Erstellen eines neuen Datenbankprojekts in der quellcodeverwaltung

1. Starten Sie Visual Studio.

2. Wählen Sie **Team Explorer** auf die **Ansicht** Menü. 

3. Klicken Sie auf **neu** in **lokales Git-Repository** im Abschnitt der **Connect** Seite.

    <img src="./media/sql-server-linux-develop-use-ssdt/git-repository.png" alt="local repository" style="width: 300px;"/>

3. Klicken Sie auf **Erstellen**. Nach lokalen Git-Repositorys erstellt wird, doppelklicken klicken Sie auf **SSDTRepo**.

4. Klicken Sie auf **neu** in die **Lösungen** Abschnitt. Wählen Sie **SQL Server** unter **andere Sprachen** Knoten in der **neues Projekt** Dialogfeld.

    <img src="./media/sql-server-linux-develop-use-ssdt/new-project.png" alt="local repository" style="width: 480px;"/>

5. Geben Sie in **"tutorialdb"** ein, und klicken Sie auf **OK** um ein neues Datenbankprojekt zu erstellen.

## <a name="create-a-new-table-in-the-database-project"></a>Erstellen Sie eine neue Tabelle im Datenbankprojekt

1. Wählen Sie **Projektmappen-Explorer** auf die **Ansicht** Menü.

2. Öffnen Sie die Datenbank-Menü "Projekt", indem Sie mit der rechten Maustaste auf **"tutorialdb"** im Projektmappen-Explorer.

3. Wählen Sie **Tabelle** unter **hinzufügen**.

    <img src="./media/sql-server-linux-develop-use-ssdt/create-table.png" alt="create table" style="width: 480px;"/>

4. Fügen Sie mithilfe der Tabellen-Designer zwei Spalten Name hinzu `nvarchar(50)` und den Speicherort `nvarchar(50)`, wie in der Abbildung dargestellt. SSDT generiert die `CREATE TABLE` Skript, wenn Sie die Spalten im Designer hinzufügen.

    <img src="./media/sql-server-linux-develop-use-ssdt/add-columns.png" alt="add columns" style="width: 480px;"/>

5. Speichern Sie die **Table1.sql** Datei.

## <a name="build-and-validate-the-database"></a>Erstellen Sie und überprüfen Sie die Datenbank

1. Öffnen Sie auf die Datenbank-Menü "Projekt" **"tutorialdb"** , und wählen Sie **erstellen**. SSDT kompiliert SQL-Quellcodedateien im Projekt und erstellt eine Datenebenen-Paketdatei (DACPAC-Datei). Dies kann zum Veröffentlichen einer Datenbank in Ihrer SQL Server-Instanz unter Linux verwendet werden. 

    <img src="./media/sql-server-linux-develop-use-ssdt/build.png" alt="add columns" style="width: 400px;"/>

2. Überprüfen Sie die Build-Erfolgsmeldung im **Ausgabe** Fenster in Visual Studio. 

## <a name="publish-the-database-to-sql-server-instance-on-linux"></a>Veröffentlichen Sie die Datenbank in SQL Server-Instanz unter Linux

1. Öffnen Sie auf die Datenbank-Menü "Projekt" **"tutorialdb"** , und wählen Sie **veröffentlichen**.

2. Klicken Sie auf **bearbeiten** , wählen Sie Ihre SQL Server-Instanz unter Linux.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-dialog.png" alt="publish dialog" style="width: 480px;"/>

3. Geben Sie im Dialogfeld "Verbindung" in der IP-Adresse oder den Hostnamen der Name Ihrer SQL Server-Instanz unter Linux, Benutzername und Kennwort.

    <img src="./media/sql-server-linux-develop-use-ssdt/connection-dialog.png" alt="connection dialog" style="width: 400px;"/>

4. Klicken Sie auf die **veröffentlichen** auf das Dialogfeld "Veröffentlichen" auf die Schaltfläche.

5. Überprüfen Sie den Veröffentlichungsstatus der **Datentoolvorgänge** Fenster.

6. Klicken Sie auf **Ansicht Reulst** oder **Skript anzeigen** der Datenbank auf dem SQL Server unter Linux ergebnisveröffentlichung angezeigt.

    <img src="./media/sql-server-linux-develop-use-ssdt/publish-result.png" alt="publish result" style="width: 480px;"/>

Sie haben erfolgreich eine neue Datenbank auf SQL Server-Instanz unter Linux erstellt und wurden die Grundlagen der Entwicklung einer Datenbank mit einem Datenbankprojekt mit quellcodeverwaltung.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie mit T-SQL vertraut sind, finden Sie unter [Lernprogramm: Schreiben von Transact-SQL-Anweisungen] und [Transact-SQL-Referenz (Datenbank-Engine)].

Weitere Informationen zum Entwickeln von einer Datenbank mit SQL Data Tools finden Sie unter [SSDT MSDN-Dokumente]

[Herunterladen Sie und installieren Sie Visual Studio]:https://www.visualstudio.com/downloads/
[Download and Install SSDT 17.0 RC2]:https://aka.ms/ssdt-download
[SSDT MSDN-Dokumente]: https://msdn.microsoft.com/library/hh272686(v=vs.103).aspx
[Lernprogramm: Schreiben von Transact-SQL-Anweisungen]:https://msdn.microsoft.com/library/ms365303.aspx
[Transact-SQL-Referenz (Datenbank-Engine)]:https://msdn.microsoft.com/library/bb510741.aspx
