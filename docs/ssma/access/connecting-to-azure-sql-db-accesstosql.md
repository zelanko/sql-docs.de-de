---
title: Herstellen einer Verbindung mit Azure SQL-Datenbank (accesstosql) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie eine Verbindung mit einer Ziel Instanz von Azure SQL-Datenbank herstellen, um Zugriffs Datenbanken zu migrieren SSMA Ruft Metadaten zu Datenbanken in Azure SQL-Datenbank ab.
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
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
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: f07d63387a6abd55aa2a130f2809681b00a71b19
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293127"
---
# <a name="connecting-to-azure-sql-db-accesstosql"></a>Herstellen einer Verbindung mit Azure SQL-Datenbank (accesstosql)
Wenn Sie Access-Datenbanken zu SQL Azure migrieren möchten, müssen Sie eine Verbindung mit der Ziel Instanz von SQL Azure herstellen. Wenn Sie eine Verbindung herstellen, erhält SSMA Metadaten zu allen Datenbanken in der Instanz von SQL Azure und zeigt Daten Bank Metadaten im SQL Azure Metadaten-Explorer an. SSMA speichert Informationen darüber, mit welcher Instanz von SQL Azure Sie verbunden sind, speichert aber keine Kenn Wörter.  
  
Die Verbindung mit SQL Azure bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung mit SQL Azure herstellen, wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte in SQL Azure laden und Daten migrieren.  
  
Metadaten über die Instanz von SQL Azure werden nicht automatisch synchronisiert. Zum Aktualisieren der Metadaten in SQL Azure Metadaten-Explorer müssen Sie stattdessen die SQL Azure Metadaten manuell aktualisieren. Weitere Informationen finden Sie im Abschnitt "Synchronisieren von SQL Azure Metadaten" weiter unten in diesem Thema.  
  
## <a name="required-sql-azure-permissions"></a>Erforderliche SQL Azure Berechtigungen  
Das Konto, das zum Herstellen einer Verbindung mit SQL Azure verwendet wird, erfordert abhängig von den Aktionen, die das Konto ausführt, unterschiedliche Berechtigungen:  
  
-   Zum Konvertieren von Zugriffs Objekten in [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax, zum Aktualisieren von Metadaten aus SQL Azure oder zum Speichern konvertierter Syntax in Skripts muss das Konto über die Berechtigung verfügen, sich bei der Instanz von SQL Azure anzumelden.  
  
-   Zum Laden von Datenbankobjekten in SQL Azure ist die Mindestanforderung für Berechtigungen die Mitgliedschaft in der Daten Bank Rolle **db_owner** in der Zieldatenbank.  
  
## <a name="establishing-a-sql-azure-connection"></a>Einrichten einer SQL Azure Verbindung  
Bevor Sie Access-Datenbankobjekte in SQL Azure-Syntax konvertieren, müssen Sie eine Verbindung mit der Instanz von herstellen, SQL Azure der Sie die Access-Datenbank oder die Datenbanken migrieren möchten.  
  
Wenn Sie die Verbindungs Eigenschaften definieren, geben Sie auch die Datenbank an, in die Objekte und Daten migriert werden. Sie können diese Zuordnung auf der Ebene des Zugriffs Schemas anpassen, nachdem Sie eine Verbindung mit SQL Azure hergestellt haben. Weitere Informationen finden Sie unter [Zuordnung von Access-Datenbanken zu SQL Server Schemas](mapping-source-and-target-databases-accesstosql.md) .  
  
> [!IMPORTANT]  
> Bevor Sie versuchen, eine Verbindung mit SQL Azure herzustellen, stellen Sie sicher, dass die Instanz von SQL Azure ausgeführt wird und Verbindungen akzeptieren kann.  
  
**Zum Herstellen einer Verbindung mit SQL Azure**  
  
1.  Wählen Sie im Menü **Datei** die Option **Verbinden mit SQL Azure** aus (diese Option wird nach der Erstellung eines Projekts aktiviert).  
  
    Wenn Sie zuvor eine Verbindung mit SQL Azure hergestellt haben, wird der Befehls Name **erneut mit SQL Azure**verbunden.  
  
2.  Geben Sie im Dialogfeld Verbindung den Servernamen SQL Azure ein, oder wählen Sie ihn aus.  
  
3.  Geben Sie den Datenbanknamen ein, oder **Suchen** Sie ihn.  
  
4.  Geben Sie **username**ein, oder wählen Sie  
  
5.  Geben Sie das **Kennwort ein**.  
  
6.  SSMA empfiehlt eine verschlüsselte Verbindung mit SQL Azure.  
  
7.  Klicken Sie auf **Verbinden**.  
  
> [!IMPORTANT]  
> SSMA für Access unterstützt keine Verbindung mit der **Master** -Datenbank in SQL Azure.  
  
Wenn das SQL Azure Konto keine Datenbanken enthält, können Sie die erste Datenbank mithilfe der Option **Create Azure Database** erstellen, die auf der Schaltfläche **Durchsuchen** klicken angezeigt wird.  
  
## <a name="synchronizing-sql-azure-metadata"></a>Synchronisieren von SQL Azure-Metadaten  
Metadaten zu SQL Azure-Datenbanken werden nicht automatisch aktualisiert. Bei den Metadaten in SQL Azure Metadaten-Explorer handelt es sich um eine Momentaufnahme der Metadaten, wenn Sie zum ersten Mal eine Verbindung mit SQL Azure hergestellt haben oder wenn Sie die Metadaten zuletzt manuell aktualisiert haben. Sie können Metadaten für alle Datenbanken oder für eine einzelne Datenbank oder ein Datenbankobjekt manuell aktualisieren.  
  
**So synchronisieren Sie Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit SQL Azure verbunden sind.  
  
2.  Aktivieren Sie in SQL Azure metadatenexplorer das Kontrollkästchen neben dem zu aktualisierenden Datenbankschema oder Datenbankschema.  
  
    Wenn Sie z. b. die Metadaten für alle Datenbanken aktualisieren möchten, aktivieren Sie das Kontrollkästchen neben Datenbanken.  
  
3.  Klicken Sie mit der rechten Maustaste auf Datenbanken oder die einzelne Datenbank oder das Datenbankschema, und wählen Sie dann **mit Datenbank synchronisieren**aus.  
  
## <a name="refreshing-sql-azure-metadata"></a>Aktualisieren von SQL Azure-Metadaten  
Wenn sich SQL Azure Schemas ändern, nachdem Sie eine Verbindung hergestellt haben, können Sie die Metadaten vom Server aktualisieren.  
  
**So aktualisieren Sie SQL Azure Metadaten**  
  
-   Klicken Sie in SQL Azure Metadaten-Explorer mit der rechten Maustaste auf **Datenbanken**, und wählen Sie dann **aus Datenbank aktualisieren aus**  
  
## <a name="reconnecting-to-sql-azure"></a>Erneutes Herstellen einer Verbindung mit SQL Azure  
Die Verbindung mit SQL Azure bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung mit SQL Azure herstellen, wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte in SQL Azure laden und Daten migrieren.  
  
Die Vorgehensweise für das erneute Herstellen einer Verbindung mit SQL Azure entspricht der Vorgehensweise zum Herstellen einer Verbindung.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:  
  
-   Informationen zum Anpassen der Zuordnung zwischen Zugriffs Schemas und SQL Azure Datenbanken und Schemas finden Sie unter [Mapping Access-Datenbanken zu SQL Server Schemas](mapping-source-and-target-databases-accesstosql.md).  
  
-   Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Setting Project Options](setting-conversion-and-migration-options-accesstosql.md).  
  
-   Informationen zum Anpassen der Zuordnung von Quell-und Ziel Datentypen finden Sie unter [Zuordnung von Quell-und Ziel Datentypen](mapping-source-and-target-data-types-accesstosql.md).  
  
-   Wenn Sie diese Aufgaben nicht ausführen müssen, können Sie die Objekt Definitionen der Access-Datenbank in SQL Azure Objekt Definitionen konvertieren. Weitere Informationen finden Sie unter [umstellen von Access-Datenbanken](converting-access-database-objects-accesstosql.md) .  
  
## <a name="see-also"></a>Weitere Informationen  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
