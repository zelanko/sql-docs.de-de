---
title: Herstellen einer Verbindung mit Azure SQL-Datenbank (mysqlto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Azure, SQL Azure permissions
- Connecting to SQL Azure, synchronization
ms.assetid: d0b6f16a-1880-459d-a0c7-28b7ef15c56a
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 8e288b91c92d8d086d5b066f95868fa0fa733bb9
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935939"
---
# <a name="connecting-to-azure-sql-database-mysqltosql"></a>Herstellen einer Verbindung mit Azure SQL-Datenbank (mysqlto SQL)
Um MySQL-Datenbanken zu SQL Azure zu migrieren, müssen Sie eine Verbindung mit der Ziel Instanz von SQL Azure herstellen. Wenn Sie eine Verbindung herstellen, erhält SSMA Metadaten zu allen Datenbanken in der Instanz von SQL Azure und zeigt Daten Bank Metadaten im SQL Azure Metadaten-Explorer an. SSMA speichert Informationen über die Instanz von SQL Azure mit denen Sie verbunden sind, speichert aber keine Kenn Wörter.  
  
Die Verbindung mit SQL Azure bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung mit SQL Azure herstellen, wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte in SQL Azure laden und Daten migrieren.  
  
Metadaten über die Instanz von SQL Azure werden nicht automatisch synchronisiert. Zum Aktualisieren der Metadaten in SQL Azure Metadaten-Explorer müssen Sie stattdessen die SQL Azure Metadaten manuell aktualisieren. Weitere Informationen finden Sie im Abschnitt "Synchronisieren von SQL Azure Metadaten" weiter unten in diesem Thema.  
  
## <a name="required-sql-azure-permissions"></a>Erforderliche SQL Azure Berechtigungen  
Das Konto, das zum Herstellen einer Verbindung mit SQL Azure verwendet wird, erfordert abhängig von den Aktionen, die das Konto ausführt, unterschiedliche Berechtigungen:  
  
-   Um MySQL-Objekte in [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax zu konvertieren, um Metadaten aus SQL Azure zu aktualisieren oder um konvertierte Syntax in Skripts zu speichern, muss das Konto über die Berechtigung verfügen, sich bei der Instanz von SQL Azure anzumelden.  
  
-   Zum Laden von Datenbankobjekten in SQL Azure ist die Mindestanforderung für Berechtigungen die Mitgliedschaft in der Daten Bank Rolle **db_owner** in der Zieldatenbank.  
  
## <a name="establishing-a-sql-azure-connection"></a>Einrichten einer SQL Azure Verbindung  
Bevor Sie MySQL-Datenbankobjekte in SQL Azure-Syntax konvertieren, müssen Sie eine Verbindung mit der Instanz von herstellen, SQL Azure der Sie die MySQL-Datenbank oder die Datenbanken migrieren möchten.  
  
Wenn Sie die Verbindungs Eigenschaften definieren, geben Sie auch die Datenbank an, in die Objekte und Daten migriert werden. Sie können diese Zuordnung auf der MySQL-Schema Ebene anpassen, nachdem Sie eine Verbindung mit SQL Azure hergestellt haben. Weitere Informationen finden Sie unter [Mapping MySQL-Datenbanken zu SQL Server Schemas &#40;mysqldesql&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
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
> SSMA für MySQL unterstützt keine Verbindung mit der **Master** -Datenbank in SQL Azure.  
  
## <a name="synchronizing-sql-azure-metadata"></a>Synchronisieren von SQL Azure-Metadaten  
Metadaten zu Datenbanken in Azure SQL-Datenbank werden nicht automatisch aktualisiert. Bei den Metadaten in SQL Azure Metadaten-Explorer handelt es sich um eine Momentaufnahme der Metadaten, wenn Sie zum ersten Mal eine Verbindung mit SQL Azure hergestellt haben oder wenn Sie die Metadaten zuletzt manuell aktualisiert haben. Sie können Metadaten für alle Datenbanken oder für eine einzelne Datenbank oder ein Datenbankobjekt manuell aktualisieren.  
  
**So synchronisieren Sie Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit SQL Azure verbunden sind.  
  
2.  Aktivieren Sie in SQL Azure metadatenexplorer das Kontrollkästchen neben dem zu aktualisierenden Datenbankschema oder Datenbankschema.  
  
    Wenn Sie z. b. die Metadaten für alle Datenbanken aktualisieren möchten, aktivieren Sie das Kontrollkästchen neben Datenbanken.  
  
3.  Klicken Sie mit der rechten Maustaste auf Datenbanken oder die einzelne Datenbank oder das Datenbankschema, und wählen Sie dann **mit Datenbank synchronisieren**aus.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:  
  
-   Informationen zum Anpassen der Zuordnung zwischen MySQL-Schemas und Azure SQL-Datenbank finden Sie unter [Mapping MySQL Database to SQL Server Schemas &#40;mysqlto SQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Festlegen von Projektoptionen &#40;mysqlto SQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   Informationen zum Anpassen der Zuordnung von Quell-und Ziel Datentypen finden Sie unter [Mapping MySQL and SQL Server Data Types &#40;mysqltosql&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Wenn Sie diese Aufgaben nicht ausführen müssen, können Sie die MySQL-Datenbankobjekt Definitionen in SQL Azure Objekt Definitionen konvertieren. Weitere Informationen finden Sie unter [umstellen von MySQL-Datenbanken &#40;mysqlto SQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von MySQL-Datenbanken zu SQL Server Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
