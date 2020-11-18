---
title: Herstellen einer Verbindung mit SQL Server (mysqlto SQL) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Verbindung mit einer Ziel Instanz von SQL Server, um MySQL-Datenbanken zu migrieren SSMA Ruft Metadaten zu Datenbanken in SQL Server ab.
ms.prod: sql
ms.custom: ''
ms.date: 11/16/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- connecting to SQL Server 2008, SQL Server permission
- connecting to SQL Server 2008, synchronization
ms.assetid: 08233267-693e-46e6-9ca3-3a3dfd3d2be7
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: c004f4ced6bad2b6db45f4be56e442a10965a514
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94870235"
---
# <a name="connecting-to-sql-server-mysqltosql"></a>Herstellen einer Verbindung mit SQL Server (MySqlToSql)

Um MySQL-Datenbanken zu zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , müssen Sie eine Verbindung mit der-Ziel Instanz von herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Wenn Sie eine Verbindung herstellen, erhält SSMA Metadaten zu allen Datenbanken in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und zeigt Daten Bank Metadaten im **SQL Server Metadaten-Explorer** an. SSMA speichert Informationen der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mit der Sie verbunden sind, speichert aber keine Kenn Wörter.

Die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung mit herstellen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte in Laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Daten migrieren.

Metadaten über die Instanz von werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht automatisch synchronisiert. Stattdessen müssen Sie die Metadaten manuell aktualisieren, um die Metadaten in **SQL Server Metadaten-Explorer** zu aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen finden Sie im Abschnitt "Synchronisieren von SQL Server Metadaten" weiter unten in diesem Thema.

## <a name="required-sql-server-permissions"></a>Erforderliche SQL Server Berechtigungen

Das Konto, das verwendet wird, um eine Verbindung mit herzustellen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erfordert abhängig von den Aktionen, die das Konto ausführt, unterschiedliche Berechtigungen:

- [!INCLUDE[tsql](../../includes/tsql-md.md)]Das Konto muss über die Berechtigung verfügen, sich bei der Instanz von anzumelden, um MySQL-Objekte in die-Syntax zu konvertieren, um Metadaten aus zu aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder um konvertierte Syntax in Skripts zu speichern [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Das Konto muss ein Mitglied der **db_ddladmin** Daten Bank Rolle sein, um Datenbankobjekte in laden zu können.

- Zum Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss das Konto wie folgt lauten:
  - Ein Mitglied der Daten Bank Rolle **db_owner** , wenn die Client seitige Daten Migrations-Engine verwendet wird.
  - Ein Mitglied der **sysadmin** -Server Rolle, wenn die serverseitige Daten Migrations-Engine verwendet wird. Dies ist erforderlich, um `CmdExec` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] während der Datenmigration den Auftrags Schritt des-Agents zu erstellen, um das SSMA-Massen Kopier Tool auszuführen.
    > [!NOTE]
    > [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Proxy Konten werden von der serverseitigen Datenmigration nicht unterstützt.

## <a name="establishing-a-sql-server-connection"></a>Einrichten einer SQL Server Verbindung

Bevor Sie MySQL-Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax konvertieren, müssen Sie eine Verbindung mit der Instanz von herstellen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der Sie die MySQL-Datenbank oder die Datenbanken migrieren möchten.

Wenn Sie die Verbindungs Eigenschaften definieren, geben Sie auch die Datenbank an, in die Objekte und Daten migriert werden. Sie können diese Zuordnung auf der MySQL-Schema Ebene anpassen, nachdem Sie eine Verbindung mit hergestellt haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen finden Sie unter [Mapping MySQL-Datenbanken zu SQL Server Schemas &#40;mysqldesql&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md).

> [!IMPORTANT]
> Bevor Sie versuchen, eine Verbindung mit herzustellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , stellen Sie sicher, dass die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird und Verbindungen akzeptieren kann.

So stellen Sie eine Verbindung mit SQL Server her

1. Wählen Sie im Menü **Datei** die Option **Verbinden mit SQL Server** aus (diese Option wird nach der Erstellung eines Projekts aktiviert).
   Wenn Sie zuvor eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt haben, wird der Befehls Name **erneut mit SQL Server** verbunden.

2. Geben Sie im Dialogfeld Verbindung den Namen der Instanz von ein, oder wählen Sie ihn aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
   - Wenn Sie eine Verbindung mit der Standard Instanz auf dem lokalen Computer herstellen, können Sie `localhost` oder einen Punkt ( `.` ) eingeben.
   - Wenn Sie eine Verbindung mit der Standard Instanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers ein.
   - Wenn Sie eine Verbindung mit einer benannten Instanz auf einem anderen Computer herstellen, geben Sie den Computernamen gefolgt von einem umgekehrten Schrägstrich und dem Instanznamen ein, z `MyServer\MyInstance` . b..

3. Wenn die Instanz von für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Annahme von Verbindungen an einem nicht standardmäßigen Port konfiguriert ist, geben Sie die Portnummer ein, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Feld **Serverport** für Verbindungen verwendet wird. Die Standard Portnummer für die Standard Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist 1433. Bei benannten Instanzen wird von SSMA versucht, die Portnummer vom- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Dienst abzurufen.

4. Wählen Sie im Feld **Authentifizierung** den Authentifizierungstyp aus, der für die Verbindung verwendet werden soll. Um das aktuelle Windows-Konto zu verwenden, wählen Sie **Windows-Authentifizierung** aus. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Wählen Sie **SQL Server Authentifizierung** aus, und geben Sie dann den Anmelde Namen und das Kennwort ein, um eine Anmeldung zu verwenden.

5. Für eine sichere Verbindung werden zwei-Steuerelemente hinzugefügt: die Kontrollkästchen **Verbindung verschlüsseln** und **TrustServerCertificate** . Nur wenn **Verbindung verschlüsseln** aktiviert ist, ist das Kontrollkästchen **TrustServerCertificate** sichtbar. Wenn **Verbindung verschlüsseln** (true) und **TrustServerCertificate** deaktiviert (false) ist, wird das SSL-Zertifikat überprüft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Das Überprüfen des Serverzertifikats ist Teil des SSL-Handshakes und stellt sicher, dass es sich bei dem Server tatsächlich um den Server handelt, mit dem eine Verbindung hergestellt werden soll. Um dies zu gewährleisten, muss ein Zertifikat sowohl auf Clientseite als auch auf Serverseite installiert werden.

6. Klicken Sie auf **Verbinden**.

> [!IMPORTANT]
> Obwohl Sie möglicherweise eine Verbindung mit einer höheren Version von herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wird die Konvertierung der-Datenbankobjekte von der Zielversion des Projekts und nicht von der Version von, mit der Sie verbunden sind, festgelegt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

## <a name="synchronizing-sql-server-metadata"></a>Synchronisieren von SQL Server-Metadaten

Metadaten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken werden nicht automatisch aktualisiert. Bei den Metadaten in **SQL Server Metadaten-Explorer** handelt es sich um eine Momentaufnahme der Metadaten, wenn Sie zum ersten Mal eine Verbindung mit hergestellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] haben oder wenn Sie die Metadaten zuletzt manuell aktualisiert haben. Sie können Metadaten für alle Datenbanken oder für eine einzelne Datenbank oder ein Datenbankobjekt manuell aktualisieren. So synchronisieren Sie Metadaten:

1. Stellen Sie sicher, dass Sie mit verbunden sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

2. Aktivieren Sie in **SQL Server metadatenexplorer** das Kontrollkästchen neben dem zu aktualisierenden Datenbankschema oder Datenbankschema.
   Wenn Sie z. b. die Metadaten für alle Datenbanken aktualisieren möchten, aktivieren Sie das Kontrollkästchen neben **Datenbanken**.

3. Klicken Sie mit der rechten Maustaste auf **Datenbanken** oder die einzelne Datenbank oder das Datenbankschema, und wählen Sie dann **mit Datenbank synchronisieren** aus.

## <a name="next-step"></a>Nächster Schritt

Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:

- Informationen zum Anpassen der Zuordnung zwischen MySQL-Schemas und SQL Server-Datenbanken und-Schemas finden Sie unter [Mapping MySQL-Datenbanken zu SQL Server Schemas &#40;mysqlto SQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md).
- Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Festlegen von Projektoptionen &#40;mysqlto SQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md).
- Informationen zum Anpassen der Zuordnung von Quell-und Ziel Datentypen finden Sie unter [Mapping MySQL and SQL Server Data Types &#40;mysqltosql&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md).
- Wenn Sie diese Aufgaben nicht ausführen müssen, können Sie die MySQL-Datenbankobjekt Definitionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekt Definitionen konvertieren. Weitere Informationen finden Sie unter [umstellen von MySQL-Datenbanken &#40;mysqldesql&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md).

## <a name="see-also"></a>Weitere Informationen

[Migrieren von MySQL-Datenbanken zu SQL Server Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)
