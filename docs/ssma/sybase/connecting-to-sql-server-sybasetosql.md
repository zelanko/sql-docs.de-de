---
description: Herstellen einer Verbindung mit SQL Server (SybaseToSQL)
title: Herstellen einer Verbindung mit SQL Server (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/16/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Server
ms.assetid: dd368a1a-45b0-40e9-b4d3-5cdb48c26606
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 2988f57c5d0e3162c9b6dc54d8a7371efcf5da05
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94870409"
---
# <a name="connecting-to-sql-server-sybasetosql"></a>Herstellen einer Verbindung mit SQL Server (SybaseToSQL)

Um die Datenbanken von Sybase Adaptive Server Enterprise (ASE) zu zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , müssen Sie eine Verbindung mit der-Ziel Instanz von herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Wenn Sie eine Verbindung herstellen, erhält SSMA Metadaten zu allen Datenbanken in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und zeigt Daten Bank Metadaten im **SQL Server Metadaten-Explorer** an. SSMA speichert Informationen zu der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mit der Sie verbunden sind, speichert aber keine Kenn Wörter.

Die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung mit herstellen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte in Laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Daten migrieren.

Metadaten über die Instanz von werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht automatisch synchronisiert. Wenn Sie die Metadaten in **SQL Server Metadaten-Explorer** aktualisieren möchten, müssen Sie stattdessen die Metadaten manuell aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wie im Abschnitt "Synchronisieren von SQL Server Metadaten" weiter unten in diesem Thema beschrieben.

## <a name="required-sql-server-permissions"></a>Erforderliche SQL Server Berechtigungen

Das Konto, das verwendet wird, um eine Verbindung mit herzustellen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erfordert abhängig von den Aktionen, die das Konto ausführt, unterschiedliche Berechtigungen:

- [!INCLUDE[tsql](../../includes/tsql-md.md)]Das Konto muss über die Berechtigung verfügen, sich bei der Instanz von anzumelden, um ASE-Objekte in die-Syntax zu konvertieren, um Metadaten aus zu aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder um konvertierte Syntax in Skripts zu speichern [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Das Konto muss ein Mitglied der **db_ddladmin** Daten Bank Rolle sein, um Datenbankobjekte in laden zu können.

- Zum Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss das Konto wie folgt lauten:
  - Ein Mitglied der Daten Bank Rolle **db_owner** , wenn die Client seitige Daten Migrations-Engine verwendet wird.
  - Ein Mitglied der **sysadmin** -Server Rolle, wenn die serverseitige Daten Migrations-Engine verwendet wird. Dies ist erforderlich, um `CmdExec` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] während der Datenmigration den Auftrags Schritt des-Agents zu erstellen, um das SSMA-Massen Kopier Tool auszuführen.
    > [!NOTE]
    > [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Proxy Konten werden von der serverseitigen Datenmigration nicht unterstützt.

- Zum Ausführen des von SSMA generierten Codes muss das Konto über `EXECUTE` Berechtigungen für alle benutzerdefinierten Funktionen im **ssma_syb** Schema der Zieldatenbank verfügen. Diese Funktionen bieten eine äquivalente Funktionalität von ASE-Systemfunktionen und werden von konvertierten Objekten verwendet.

## <a name="establishing-a-sql-server-connection"></a>Einrichten einer SQL Server Verbindung

Vor dem Konvertieren von ASE-Datenbankobjekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax müssen Sie eine Verbindung mit der Instanz von herstellen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der Sie die ASE-Datenbank oder die Datenbanken migrieren möchten.

Wenn Sie die Verbindungs Eigenschaften definieren, geben Sie auch die Datenbank an, in die Objekte und Daten migriert werden. Sie können diese Zuordnung auf ASE-Schema Ebene anpassen, nachdem Sie eine Verbindung mit hergestellt haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen finden Sie unter [Mapping Sybase ASE Schemas to SQL Server Schemas &#40;sybasedesql&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).

> [!IMPORTANT]
> Bevor Sie versuchen, eine Verbindung mit herzustellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , stellen Sie sicher, dass die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird und Verbindungen akzeptieren kann.

So stellen Sie eine Verbindung mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her
  
1. Wählen Sie im Menü **Datei** die Option **mit SQL Server verbinden** aus.
   Wenn Sie zuvor eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt haben, wird der Befehls Name **erneut mit SQL Server** verbunden.

2. Geben Sie im Dialogfeld Verbindung den Namen der Instanz von ein, oder wählen Sie ihn aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
   - Wenn Sie eine Verbindung mit der Standard Instanz auf dem lokalen Computer herstellen, können Sie `localhost` oder einen Punkt ( `.` ) eingeben.
   - Wenn Sie eine Verbindung mit der Standard Instanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers ein.
   - Wenn Sie eine Verbindung mit einer benannten Instanz auf einem anderen Computer herstellen, geben Sie den Computernamen gefolgt von einem umgekehrten Schrägstrich und dem Instanznamen ein, z `MyServer\MyInstance` . b..

3. Wenn die Instanz von für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Annahme von Verbindungen an einem nicht standardmäßigen Port konfiguriert ist, geben Sie die Portnummer ein, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Feld **Serverport** für Verbindungen verwendet wird. Die Standard Portnummer für die Standard Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist 1433. Bei benannten Instanzen wird von SSMA versucht, die Portnummer vom- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Dienst abzurufen.

4. Geben Sie im Feld **Datenbank** den Namen der Zieldatenbank ein.
   Diese Option ist nicht verfügbar, wenn Sie eine erneute Verbindung mit herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

5. Wählen Sie im Feld **Authentifizierung** den Authentifizierungstyp aus, der für die Verbindung verwendet werden soll. Um das aktuelle Windows-Konto zu verwenden, wählen Sie **Windows-Authentifizierung** aus. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Wählen Sie **SQL Server Authentifizierung** aus, und geben Sie dann den Anmelde Namen und das Kennwort an

6. Für eine sichere Verbindung werden zwei-Steuerelemente hinzugefügt: die Kontrollkästchen **Verbindung verschlüsseln** und **TrustServerCertificate** . Nur wenn **Verbindung verschlüsseln** aktiviert ist, ist das Kontrollkästchen **TrustServerCertificate** sichtbar. Wenn **Verbindung verschlüsseln** (true) und **TrustServerCertificate** deaktiviert (false) ist, wird das SSL-Zertifikat überprüft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Das Überprüfen des Serverzertifikats ist Teil des SSL-Handshakes und stellt sicher, dass es sich bei dem Server tatsächlich um den Server handelt, mit dem eine Verbindung hergestellt werden soll. Um dies zu gewährleisten, muss ein Zertifikat sowohl auf Clientseite als auch auf Serverseite installiert werden.

7. Klicken Sie auf **Verbinden**.

> [!IMPORTANT]
> Obwohl Sie möglicherweise eine Verbindung mit einer höheren Version von herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wird die Konvertierung der-Datenbankobjekte von der Zielversion des Projekts und nicht von der Version von, mit der Sie verbunden sind, festgelegt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

## <a name="reconnecting-to-sql-server"></a>Erneutes Herstellen einer Verbindung mit SQL Server

Die Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung mit herstellen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Metadaten aktualisieren, Datenbankobjekte in Laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Daten migrieren.

Die Vorgehensweise für das erneute Herstellen einer Verbindung mit entspricht dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verfahren zum Herstellen einer Verbindung.

## <a name="synchronizing-sql-server-metadata"></a>Synchronisieren von SQL Server-Metadaten

Metadaten zu den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken werden nicht automatisch aktualisiert. Bei den Metadaten in **SQL Server Metadaten-Explorer** handelt es sich um eine Momentaufnahme der Metadaten, wenn Sie zum ersten Mal eine Verbindung mit hergestellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] haben oder wenn Sie die Metadaten zuletzt manuell aktualisiert haben. Sie können Metadaten für alle Datenbanken oder für eine einzelne Datenbank oder ein Datenbankobjekt manuell aktualisieren. So synchronisieren Sie Metadaten:

1. Stellen Sie sicher, dass Sie mit verbunden sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .

2. Aktivieren Sie in **SQL Server metadatenexplorer** das Kontrollkästchen neben dem zu aktualisierenden Datenbankschema oder Datenbankschema.
   Wenn Sie z. b. die Metadaten für alle Datenbanken aktualisieren möchten, aktivieren Sie das Kontrollkästchen neben **Datenbanken**.

3. Klicken Sie mit der rechten Maustaste auf **Datenbanken** oder die einzelnen Datenbanken oder Datenbankschemas, und wählen Sie dann **mit Datenbank synchronisieren**

## <a name="next-step"></a>Nächster Schritt

Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:

- Wenn Sie die Zuordnung zwischen den ASE-Datenbanken und-Schemas und- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken und-Schemas anpassen möchten, finden Sie weitere Informationen unterzuordnen von [Sybase-ASE-Schemas zu SQL Server Schemas &#40;Sybase&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).
- Wenn Sie die Konfigurationsoptionen für die Projekte anpassen möchten, finden Sie weitere Informationen unter [Festlegen von Projektoptionen &#40;sybaseto SQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).
- Wenn Sie eine benutzerdefinierte Zuordnung der Quell-und Ziel Datentypen durcharbeiten möchten, finden Sie weitere Informationen unter [Mapping Sybase ASE und SQL Server Datentyp &#40;sybasetosql&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).
- Wenn Sie diese Schritte nicht ausführen müssen, können Sie die Objekt Definitionen der Sybase-ASE-Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekt Definitionen konvertieren. Weitere Informationen finden Sie unter " [umstellen von Sybase ASE-Datenbankobjekten &#40;sybasedesql&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).

## <a name="see-also"></a>Weitere Informationen

[Migrieren von Sybase ASE-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)
