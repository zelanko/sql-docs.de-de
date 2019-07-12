---
title: Verwenden von SSMS zum Verwalten von SQLServer unter Linux
description: ''
author: VanMSFT
ms.author: vanto
manager: jroth
ms.date: 05/21/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: b2fcf858-21c3-462a-8d49-50c85647d092
ms.openlocfilehash: 8eba01fdd332e86327da627dd934806c1eedc9d5
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834939"
---
# <a name="use-sql-server-management-studio-on-windows-to-manage-sql-server-on-linux"></a>Verwenden von SQL Server Management Studio auf Windows zum Verwalten von SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel werden [SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md) und führt Sie durch eine Reihe von Aufgaben. SSMS ist eine Windows-Anwendung, also SSMS verwenden, wenn Sie einen Windows-Computer verfügen, der zu einer Remoteinstanz von SQL Server unter Linux eine Verbindung herstellen können.

> [!TIP]
> Wenn Sie nicht für die Ausführung von SSMS auf einen Windows-Computer verfügen, sollten Sie die neue [Studio für Azure Data](../azure-data-studio/index.md). Es enthält ein grafisches Tool zum Verwalten von SQL Server und auf Linux- und Windows ausgeführt wird.

[SQL Server Management Studio (SSMS)](../ssms/sql-server-management-studio-ssms.md) ist Teil einer Suite von SQL-Tools, die kostenlose Angebote von Microsoft kostenlos für Entwicklung und Verwaltung. SSMS ist eine integrierte Umgebung zum zugreifen, konfigurieren, verwalten, verwalten und entwickeln aller Komponenten von SQL Server. Sie können mit SQL Server auf einer beliebigen Plattform sowohl lokal, in Docker-Containern, und klicken Sie in der Cloud verbinden. Es wird auch zum Azure SQL-Datenbank und Azure SQL Data Warehouse. SSMS kombiniert eine umfassende Gruppe grafischer Tools mit einer Reihe von funktionsreichen Skript-Editoren, um Zugriff auf SQL Server für Entwickler und Administratoren mit verschiedenem Kenntnisstand bereitzustellen.

SSMS bietet ein breites Spektrum an Funktionen für Entwicklung und Verwaltung für SQL Server, Tools, einschließlich:

- Konfigurieren, überwachen und Verwalten von einzelnen oder mehrere Instanzen von SQL Server
- Bereitstellen, überwachen und Aktualisieren von Datenebenenkomponenten wie z. B. Datenbanken und Data Warehouses
- Sichern und Wiederherstellen von Datenbanken
- Erstellen und Ausführen von T-SQL-Abfragen und Skripts und Ergebnisse anzeigen
- Generieren von T-SQL-Skripts für Datenbankobjekte
- Anzeigen und Bearbeiten von Daten in Datenbanken
- Visuelles Entwerfen von T-SQL-Abfragen und Datenbankobjekte, z. B. Sichten, Tabellen und gespeicherten Prozeduren

Finden Sie unter [neuerungen von SSMS?](../ssms/sql-server-management-studio-ssms.md) für Weitere Informationen zu SSMS.

## <a name="install-the-newest-version-of-sql-server-management-studio-ssms"></a>Installieren Sie die neueste Version von SQL Server Management Studio (SSMS)

Bei der Arbeit mit SQL Server sollten Sie immer die neueste Version von SQL Server Management Studio (SSMS) verwenden. Die neueste Version von SSMS wird ständig aktualisiert und optimiert und arbeitet zurzeit mit SQL Server unter Linux. Zum Herunterladen und installieren die neueste Version, finden Sie unter [Herunterladen von SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Um auf dem neuesten Stand zu bleiben, die neueste Version von SSMS werden Sie aufgefordert, wenn eine neue Versionen zum download zur Verfügung.

> [!NOTE]
> Lesen Sie vor dem mithilfe von SSMS zum Verwalten von Linux, die [bekannte Probleme](sql-server-linux-release-notes.md) für SSMS unter Linux.

## <a name="connect-to-sql-server-on-linux"></a>Verbinden Sie mit SQLServer unter Linux

Verwenden Sie die folgenden grundlegenden Schritte, um eine Verbindung herzustellen:

1. Starten Sie SSMS, indem Sie eingeben **Microsoft SQL Server Management Studio** in der Windows-Suchfeld ein, und klicken Sie dann auf die desktop-app.

    ![SQL Server Management Studio](./media/sql-server-linux-manage-ssms/ssms.png)

1. In der **Herstellen einer Verbindung mit Server** Fenster, geben Sie die folgende Informationen (wenn SSMS bereits ausgeführt wird, klicken Sie auf **verbinden > Datenbank-Engine** zu öffnen der **Verbindung mit Server herstellen** (Fenster):

   | Einstellung | Beschreibung |
   |-----|-----|
   | **Servertyp** | Die Standardeinstellung ist die Datenbank-Engine. Ändern Sie diesen Wert nicht. |
   | **Servername** | Geben Sie den Namen der Zielcomputer für die virtuellen SQL Server oder die IP-Adresse ein. |
   | **Authentifizierung** | Verwenden Sie für SQL Server unter Linux **SQL Server-Authentifizierung**. |
   | **Anmeldename** | Geben Sie den Namen eines Benutzers mit Zugriff auf eine Datenbank auf dem Server (z. B. die Standardeinstellung **SA** Konto während des Setups erstellt wurde). |
   | **Kennwort** | Geben Sie das Kennwort für den angegebenen Benutzer (für die **SA** -Konto Sie dies während des Setups erstellt). |

    ![SQL Server Management Studio: Verbinden mit einem SQL-Datenbankserver](./media/sql-server-linux-manage-ssms/connect.png)

1. Klicken Sie auf **Verbinden**.

    > [!TIP]
    > Wenn Sie einen Verbindungsfehler erhalten, versuchen Sie zunächst das Problem aus der Fehlermeldung zu ermitteln. Überprüfen Sie anschließend die [Empfehlungen zur Verbindungsproblembehandlung](sql-server-linux-troubleshooting-guide.md#connection).
 
1. Nach der erfolgreichen Verbindung mit SQL Server, **Objekt-Explorer** geöffnet, und Sie können jetzt auf Ihre Datenbank aus, um administrative Aufgaben oder Abfragen von Daten zugreifen.

## <a name="run-transact-sql-queries"></a>Ausführen von Transact-SQL-Abfragen

Nach der verbindungsherstellung mit Ihrem Server können Sie eine Verbindung mit einer Datenbank herstellen und Ausführen von Transact-SQL-Abfragen. Transact-SQL-Abfragen können für nahezu jede Datenbankaufgabe verwendet werden.

1. In **Objekt-Explorer**, navigieren Sie in die Zieldatenbank auf dem Server. Erweitern Sie z. B. **Systemdatenbanken** zum Arbeiten mit der **master** Datenbank.

1. Mit der rechten Maustaste in der Datenbank, und wählen Sie dann **neue Abfrage**.

1. In das Abfragefenster Schreiben einer Transact-SQL-Abfrage zurück auf die Namen aller Datenbanken auf dem Server.

   ```sql
   SELECT [Name]
   FROM sys.Databases
   ```

   Wenn Sie dem Schreiben von Abfragen vertraut sind, finden Sie unter [Schreiben von Transact-SQL-Anweisungen](../t-sql/tutorial-writing-transact-sql-statements.md).

1. Klicken Sie auf die **Execute** Schaltfläche, um die Abfrage auszuführen und die Ergebnisse angezeigt.

   ![Erfolg. Verbinden Sie mit SQL-Datenbankserver: SQL Server Management Studio](./media/sql-server-linux-manage-ssms/execute-query.png)

Obwohl es möglich, fast jede Verwaltungsaufgabe mit Transact-SQL-Abfragen ist, ist SSMS ein grafisches Tool, das einfacher zu SQL Server zu verwalten. Die folgenden Abschnitte enthalten einige Beispiele für die Verwendung der grafischen Benutzeroberfläche.

## <a name="create-and-manage-databases"></a>Erstellen und Verwalten von Datenbanken

Während der Verbindung mit der *master* -Datenbank, Sie können Datenbanken auf dem Server erstellen und ändern oder vorhandene Datenbanken löschen. Die folgenden Schritte beschreiben, wie Sie mehrere allgemeine Aufgaben der datenbankverwaltung über Management Studio ausführen. Um diese Aufgaben auszuführen, stellen Sie sicher, dass Sie verbunden sind die *master* -Datenbank mit der prinzipalanmeldung auf Serverebene, die Sie erstellt, wenn Sie SQL Server unter Linux einrichten.

### <a name="create-a-new-database"></a>Erstellen einer neuen Datenbank

1. Starten Sie SSMS, und Verbinden mit dem Server in SQL Server unter Linux

2. Objekt-Explorer mit der Maustaste auf die *Datenbanken* Ordner, und klicken Sie dann auf * neue Datenbank... "

3. In der *neue Datenbank* Dialogfeld Geben Sie einen Namen für Ihre neue Datenbank, und klicken Sie dann auf *OK*

Die neue Datenbank wird auf dem Server wurde erfolgreich erstellt. Wenn Sie eine neue Datenbank mit T-SQL erstellen möchten, finden Sie unter [CREATE DATABASE (SQL Server Transact-SQL)](../t-sql/statements/create-database-sql-server-transact-sql.md).

### <a name="drop-a-database"></a>Löschen einer Datenbank

1. Starten Sie SSMS, und Verbinden mit dem Server in SQL Server unter Linux

2. Erweitern Sie im Objekt-Explorer die *Datenbanken* Ordner, um eine Liste mit allen in der Datenbank auf dem Server angezeigt.

3. Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf die Datenbank, die Sie löschen möchten, und klicken Sie dann auf *löschen*

4. In der *Objekt löschen* Dialogfeld Kontrollkästchen *bestehende Verbindungen schließen* , und klicken Sie dann auf *OK*

Die Datenbank wird vom Server wurde erfolgreich gelöscht. Wenn Sie eine Datenbank mit T-SQL löschen möchten, finden Sie unter [DROP DATABASE (SQL Server Transact-SQL)](../t-sql/statements/drop-database-transact-sql.md).

## <a name="use-activity-monitor-to-see-information-about-sql-server-activity"></a>Verwenden Sie Aktivitätsmonitor, um Informationen zu SQL Server-Aktivitäten finden Sie unter

Die [Aktivitätsmonitor](../relational-databases/performance-monitor/activity-monitor.md) Tool wird in SQL Server Management Studio (SSMS) erstellt und zeigt Informationen zu SQL Server-Prozesse und Auswirkungen diese Prozesse auf die aktuelle Instanz von SQL Server.

1. Starten Sie SSMS, und Verbinden mit dem Server in SQL Server unter Linux

1. Klicken Sie im Objekt-Explorer mit der Maustaste der *Server* Knoten, und klicken Sie dann auf *Aktivitätsmonitor*

Aktivitätsmonitor zeigt erweiterbare und reduzierbare Bereichen mit den folgenden Informationen an:

- Übersicht
- Prozesse
- Ressourcenwartevorgänge
- Datendatei-e/a-
- Aktuelle wertvolle Abfragen
- Aktive ressourcenintensive Abfragen

Wenn ein Bereich erweitert wird, fragt der Aktivitätsmonitor die Instanz nach Informationen. Wenn ein Bereich reduziert wird, werden sämtliche Abfrageaktivitäten für diesen Bereich angehalten. Sie können einen oder mehrere Bereiche gleichzeitig an verschiedene Arten von Aktivitäten in der Instanz erweitern.

## <a name="see-also"></a>Siehe auch
- [Was ist SSMS?](../ssms/sql-server-management-studio-ssms.md)
- [Exportieren Sie und importieren Sie eine Datenbank mit SSMS](sql-server-linux-migrate-ssms.md)
- [Tutorial: SQL Server Management Studio](../ssms/tutorials/tutorial-sql-server-management-studio.md)
- [Tutorial: Schreiben von Transact-SQL-Anweisungen](../t-sql/tutorial-writing-transact-sql-statements.md)
- [Überwachen der Serverleistung und -aktivität](../relational-databases/performance/server-performance-and-activity-monitoring.md)
