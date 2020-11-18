---
description: Herstellen einer Verbindung mit Azure SQL-Datenbank (sybaseto SQL)
title: Herstellen einer Verbindung mit Azure SQL-Datenbank (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/16/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9e77e4b0-40c0-455c-8431-ca5d43849aa7
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: f88b7b5357a61708910846f78c09f80e7c783957
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94870419"
---
# <a name="connecting-to-azure-sql-database-sybasetosql"></a>Herstellen einer Verbindung mit Azure SQL-Datenbank (sybaseto SQL)

Um Sybase-Datenbanken zu zu migrieren [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , müssen Sie eine Verbindung mit der-Ziel Instanz von herstellen [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] . Wenn Sie eine Verbindung herstellen, erhält SSMA Metadaten zu allen Datenbanken in der Instanz von [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] und zeigt Daten Bank Metadaten im **metadatenexplorer von Azure SQL-Datenbank** an. SSMA speichert Informationen der Instanz von [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , mit der Sie verbunden sind, speichert aber keine Kenn Wörter.

Die Verbindung mit [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung mit herstellen, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte in Laden [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] und Daten migrieren.

Metadaten über die Instanz von werden [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] nicht automatisch synchronisiert. Stattdessen müssen Sie die Metadaten manuell aktualisieren, um die Metadaten im **metadatenexplorer von Azure SQL-Datenbank** zu aktualisieren [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] . Weitere Informationen finden Sie im Abschnitt "Synchronisieren von Metadaten von Azure SQL-Datenbank" weiter unten in diesem Thema.

## <a name="required-azure-sql-database-permissions"></a>Erforderliche Azure SQL-Daten Bank Berechtigungen

Das Konto, das verwendet wird, um eine Verbindung mit herzustellen, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] erfordert abhängig von den Aktionen, die das Konto ausführt, unterschiedliche Berechtigungen:

- [!INCLUDE[tsql](../../includes/tsql-md.md)]Das Konto muss über die Berechtigung verfügen, sich bei der Instanz von anzumelden, um ASE-Objekte in die-Syntax zu konvertieren, um Metadaten aus zu aktualisieren [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] oder um konvertierte Syntax in Skripts zu speichern [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

- [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]Das Konto muss ein Mitglied der **db_ddladmin** Daten Bank Rolle sein, um Datenbankobjekte in laden zu können.

- Zum Migrieren von Daten zu [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] muss das Konto Mitglied der **db_owner** Daten Bank Rolle sein.

- Zum Ausführen des von SSMA generierten Codes muss das Konto über `EXECUTE` Berechtigungen für alle benutzerdefinierten Funktionen im **ssma_syb** Schema der Zieldatenbank verfügen. Diese Funktionen bieten eine äquivalente Funktionalität von ASE-Systemfunktionen und werden von konvertierten Objekten verwendet.

## <a name="establishing-an-azure-sql-database-connection"></a>Einrichten einer Azure SQL-Datenbankverbindung

Vor dem Konvertieren von Sybase-Datenbankobjekten in [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Syntax müssen Sie eine Verbindung mit der Instanz von herstellen, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] in der Sie die Sybase-Datenbank oder die Datenbanken migrieren möchten.

Wenn Sie die Verbindungs Eigenschaften definieren, geben Sie auch die Datenbank an, in die Objekte und Daten migriert werden. Sie können diese Zuordnung auf der Sybase-Schema Ebene anpassen, nachdem Sie eine Verbindung mit Azure SQL-Datenbank hergestellt haben. Weitere Informationen finden Sie unter [Mapping Sybase ASE Schemas to SQL Server Schemas &#40;sybasedesql&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).

> [!IMPORTANT]
> Bevor Sie versuchen, eine Verbindung mit herzustellen [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , stellen Sie sicher, dass Ihre IP-Adresse über die Firewall zugelassen wird [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

So stellen Sie eine Verbindung mit dem [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] her

1. Wählen Sie im Menü **Datei** die Option **mit Azure SQL-Datenbank verbinden** aus. (diese Option wird nach der Projekt Erstellung aktiviert.)
   Wenn Sie zuvor eine Verbindung mit [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] hergestellt haben, wird der Befehls Name **erneut mit der Azure SQL-Datenbank** verbunden.

2. Geben Sie im Dialogfeld Verbindung den Servernamen ein, oder wählen Sie ihn aus [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

3. Geben Sie den Datenbanknamen ein, oder **Suchen** Sie ihn.

4. Geben Sie **username** ein, oder wählen Sie

5. Geben Sie das **Kennwort ein**.

6. SSMA empfiehlt eine verschlüsselte Verbindung mit [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

7. Klicken Sie auf **Verbinden**.

## <a name="synchronizing-azure-sql-database-metadata"></a>Synchronisieren von Metadaten von Azure SQL-Datenbank

Metadaten zu [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Datenbanken werden nicht automatisch aktualisiert. Bei den Metadaten im metadatenexplorer von Azure SQL-Datenbank handelt es sich um eine Momentaufnahme der Metadaten, wenn Sie zum ersten Mal eine Verbindung mit Azure SQL-Datenbank hergestellt haben oder wenn Sie die Metadaten zuletzt manuell aktualisiert Sie können Metadaten für alle Datenbanken oder für eine einzelne Datenbank oder ein Datenbankobjekt manuell aktualisieren. So synchronisieren Sie Metadaten:

1. Stellen Sie sicher, dass Sie mit verbunden sind [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

2. Aktivieren Sie im **metadatenexplorer von Azure SQL-Datenbank** das Kontrollkästchen neben der Datenbank oder dem Datenbankschema, das Sie aktualisieren möchten.
   Wenn Sie z. b. die Metadaten für alle Datenbanken aktualisieren möchten, aktivieren Sie das Kontrollkästchen neben **Datenbanken**.

3. Klicken Sie mit der rechten Maustaste auf **Datenbanken** oder die einzelne Datenbank oder das Datenbankschema, und wählen Sie dann **mit Datenbank synchronisieren** aus.

## <a name="next-step"></a>Nächster Schritt

Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:

- Informationen zum Anpassen der Zuordnung zwischen Sybase-Schemas und- [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Datenbanken und-Schemas finden Sie unter [Mapping von Sybase-ASE-Schemas zu SQL Server Schemas &#40;Sybase&#41;- ](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).
- Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Festlegen von Projektoptionen &#40;sybasedesql&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md).
- Informationen zum Anpassen der Zuordnung von Quell-und Ziel Datentypen finden Sie unter [Mapping Sybase ASE und SQL Server Data Types &#40;sybasetosql&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).
- Wenn Sie diese Aufgaben nicht ausführen müssen, können Sie die Sybase-Datenbankobjekt Definitionen in [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Objekt Definitionen konvertieren. Weitere Informationen finden Sie unter " [umstellen von Sybase ASE-Datenbankobjekten &#40;sybasedesql&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).

## <a name="see-also"></a>Weitere Informationen

[Migrieren von Sybase ASE-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)
