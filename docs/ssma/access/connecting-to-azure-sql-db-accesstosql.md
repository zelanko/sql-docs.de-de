---
title: Herstellen einer Verbindung mit Azure SQL-Datenbank (accesstosql) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Verbindung mit einer Ziel Instanz von Azure SQL-Datenbank herstellen, um Zugriffs Datenbanken zu migrieren SSMA Ruft Metadaten zu Datenbanken in Azure SQL-Datenbank ab.
ms.prod: sql
ms.custom: ''
ms.date: 11/16/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- instance of SQL Azure
- metadata, refreshing
- refreshing metadata
- SQL Azure
- SQL Azure, connecting
- SQL Azure, connecting to
- SQL Azure, reconnecting
- SQL Azure, synchronizing metadata
ms.assetid: 1ba0d113-dc05-4431-8689-e14a8821bafd
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: f910e9c07bf4318419714b97e4f4db742c913753
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94869458"
---
# <a name="connecting-to-azure-sql-database-accesstosql"></a>Herstellen einer Verbindung mit Azure SQL-Datenbank (accesstosql)

Wenn Sie Access-Datenbanken zu migrieren möchten [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , müssen Sie eine Verbindung mit der-Ziel Instanz herstellen [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] . Wenn Sie eine Verbindung herstellen, erhält SSMA Metadaten zu allen Datenbanken in der Instanz von [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] und zeigt Daten Bank Metadaten im **metadatenexplorer von Azure SQL-Datenbank** an. SSMA speichert Informationen zu der Instanz von [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , mit der Sie verbunden sind, speichert aber keine Kenn Wörter.

Die Verbindung mit [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung mit herstellen, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte in Laden [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] und Daten migrieren.

Metadaten über die Instanz von werden [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] nicht automatisch synchronisiert. Stattdessen müssen Sie die Metadaten manuell aktualisieren, um die Metadaten im **metadatenexplorer von Azure SQL-Datenbank** zu aktualisieren [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] . Weitere Informationen finden Sie im Abschnitt "Synchronisieren von Metadaten von Azure SQL-Datenbank" weiter unten in diesem Thema.

## <a name="required-azure-sql-database-permissions"></a>Erforderliche Azure SQL-Daten Bank Berechtigungen

Das Konto, das verwendet wird, um eine Verbindung mit herzustellen, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] erfordert abhängig von den Aktionen, die das Konto ausführt, unterschiedliche Berechtigungen:

- [!INCLUDE[tsql](../../includes/tsql-md.md)]Das Konto muss über die Berechtigung verfügen, sich bei der Instanz von anzumelden, um Zugriffs Objekte in die-Syntax zu konvertieren, um Metadaten aus zu aktualisieren [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] oder um konvertierte Syntax in Skripts zu speichern [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

- [!INCLUDE[ssAzure](../../includes/ssazure_md.md)]Das Konto muss ein Mitglied der **db_ddladmin** Daten Bank Rolle sein, um Datenbankobjekte in laden zu können.

- Zum Migrieren von Daten zu [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] muss das Konto Mitglied der **db_owner** Daten Bank Rolle sein.

## <a name="establishing-an-azure-sql-database-connection"></a>Einrichten einer Azure SQL-Datenbankverbindung

Bevor Sie Access-Datenbankobjekte in [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Syntax konvertieren, müssen Sie eine Verbindung mit der Instanz von herstellen, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] in der Sie die Access-Datenbank oder die Datenbanken migrieren möchten.

Wenn Sie die Verbindungs Eigenschaften definieren, geben Sie auch die Datenbank an, in die Objekte und Daten migriert werden. Sie können diese Zuordnung auf der Ebene des Zugriffs Schemas anpassen, nachdem Sie eine Verbindung mit hergestellt haben [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] . Weitere Informationen finden Sie unter [Zuordnung von Access-Datenbanken zu SQL Server Schemas](mapping-source-and-target-databases-accesstosql.md).
  
> [!IMPORTANT]
> Bevor Sie versuchen, eine Verbindung mit herzustellen [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , stellen Sie sicher, dass Ihre IP-Adresse über die Firewall zugelassen wird [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .
  
So stellen Sie eine Verbindung mit dem [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] her

1. Wählen Sie im Menü **Datei** die Option **Verbinden mit SQL Azure** aus (diese Option wird nach der Erstellung eines Projekts aktiviert).
   Wenn Sie zuvor eine Verbindung mit [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] hergestellt haben, wird der Befehls Name **erneut mit SQL Azure** verbunden.

2. Geben Sie im Dialogfeld Verbindung den Servernamen ein, oder wählen Sie ihn aus [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

3. Geben **Sie den Daten** Banknamen ein, oder wählen Sie ihn aus.

4. Geben Sie **username** ein, oder wählen Sie

5. Geben Sie das **Kennwort ein**.

6. SSMA empfiehlt eine verschlüsselte Verbindung mit [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

7. Klicken Sie auf **Verbinden**.
  
Wenn keine Datenbanken in vorhanden sind [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] , können Sie die erste Datenbank mithilfe der Option **Create Azure Database** erstellen, die auf der Schaltfläche **Durchsuchen** klicken angezeigt wird.

## <a name="synchronizing-azure-sql-database-metadata"></a>Synchronisieren von Metadaten von Azure SQL-Datenbank

Metadaten zu Datenbanken in werden [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] nicht automatisch aktualisiert. Bei den Metadaten im **metadatenexplorer von Azure SQL-Datenbank** handelt es sich um eine Momentaufnahme der Metadaten, wenn Sie zum ersten Mal eine Verbindung mit hergestellt [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] haben oder wenn Sie die Metadaten zuletzt manuell aktualisiert Sie können Metadaten für alle Datenbanken oder für eine einzelne Datenbank oder ein Datenbankobjekt manuell aktualisieren. So synchronisieren Sie Metadaten:

1. Stellen Sie sicher, dass Sie mit verbunden sind [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] .

2. Aktivieren Sie im **metadatenexplorer von Azure SQL-Datenbank** das Kontrollkästchen neben der Datenbank oder dem Datenbankschema, das Sie aktualisieren möchten.
   Wenn Sie z. b. die Metadaten für alle Datenbanken aktualisieren möchten, aktivieren Sie das Kontrollkästchen neben **Datenbanken**.

3. Klicken Sie mit der rechten Maustaste auf **Datenbanken** oder die einzelne Datenbank oder das Datenbankschema, und wählen Sie dann **mit Datenbank synchronisieren** aus.

## <a name="refreshing-azure-sql-database-metadata"></a>Aktualisieren von Metadaten für Azure SQL-Datenbank

Wenn [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Schemas geändert werden, nachdem Sie eine Verbindung hergestellt haben, können Sie die Metadaten vom Server aktualisieren.

So aktualisieren Sie [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Metadaten:

- Klicken Sie im **metadatenexplorer von Azure SQL-Datenbank** mit der rechten Maustaste auf **Datenbanken**, und wählen Sie dann **aus Datenbank aktualisieren aus**

## <a name="reconnecting-to-azure-sql-database"></a>Erneutes Herstellen einer Verbindung mit Azure SQL-Datenbank

Die Verbindung mit [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung mit herstellen, [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte in Laden [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] und Daten migrieren.

Die Vorgehensweise für das erneute Herstellen einer Verbindung mit entspricht dem [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] Verfahren zum Herstellen einer Verbindung.

## <a name="next-steps"></a>Nächste Schritte

Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:

- Informationen zum Anpassen der Zuordnung zwischen Zugriffs Schemas und Azure SQL-Datenbank finden Sie unter [Mapping Access Database to SQL Server Schemas](mapping-source-and-target-databases-accesstosql.md).
- Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Setting Project Options](setting-conversion-and-migration-options-accesstosql.md).
- Informationen zum Anpassen der Zuordnung von Quell-und Ziel Datentypen finden Sie unter [Zuordnung von Quell-und Ziel Datentypen](mapping-source-and-target-data-types-accesstosql.md).
- Wenn Sie diese Aufgaben nicht ausführen müssen, können Sie die Objekt Definitionen der Access-Datenbank in SQL Azure Objekt Definitionen konvertieren. Weitere Informationen finden Sie unter " [umstellen von Access-Datenbanken](converting-access-database-objects-accesstosql.md)".

## <a name="see-also"></a>Weitere Informationen

[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)
