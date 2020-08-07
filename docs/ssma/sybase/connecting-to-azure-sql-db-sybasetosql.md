---
title: Herstellen einer Verbindung mit Azure SQL-Datenbank (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9e77e4b0-40c0-455c-8431-ca5d43849aa7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: a16ade8d212d3d197b858488dde05b439d8e989f
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87864757"
---
# <a name="connecting-to-azure-sql-database-sybasetosql"></a>Herstellen einer Verbindung mit Azure SQL-Datenbank (sybaseto SQL)
Um Sybase-Datenbanken zu Azure SQL-Datenbank zu migrieren, müssen Sie eine Verbindung mit der Ziel Instanz von Azure SQL-Datenbank herstellen. Wenn Sie eine Verbindung herstellen, ruft SSMA Metadaten zu allen Datenbanken in der Instanz von Azure SQL-Datenbank ab und zeigt Daten Bank Metadaten im metadatenexplorer von Azure SQL-Datenbank an. SSMA speichert Informationen über die Instanz von Azure SQL-Datenbank, mit der Sie verbunden sind, speichert aber keine Kenn Wörter.  
  
Die Verbindung mit Azure SQL-Datenbank bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung mit Azure SQL-Datenbank herstellen, wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte in Azure SQL-Datenbank laden und Daten migrieren.  
  
Metadaten über die Instanz von Azure SQL-Datenbank werden nicht automatisch synchronisiert. Stattdessen müssen Sie die Metadaten der Azure SQL-Datenbank manuell aktualisieren, um die Metadaten im metadatenexplorer von Azure SQL-Datenbank zu aktualisieren. Weitere Informationen finden Sie im Abschnitt "Synchronisieren von Metadaten von Azure SQL-Datenbank" weiter unten in diesem Thema.  
  
## <a name="required-azure-sql-database-permissions"></a>Erforderliche Azure SQL-Daten Bank Berechtigungen  
Das Konto, das zum Herstellen einer Verbindung mit Azure SQL-Datenbank verwendet wird, erfordert abhängig von den Aktionen, die das Konto ausführt, unterschiedliche Berechtigungen:  
  
1.  [!INCLUDE[tsql](../../includes/tsql-md.md)]Das Konto muss über die Berechtigung verfügen, sich bei der Instanz von Azure SQL-Datenbank anzumelden, um Sybase-Objekte in die Syntax zu konvertieren, um Metadaten aus Azure SQL-Datenbank zu aktualisieren oder um konvertierte Syntax in Skripts zu speichern.  
  
2.  Zum Laden von Datenbankobjekten in Azure SQL-Datenbank ist die Mindestanforderung für Berechtigungen die Mitgliedschaft in der Daten Bank Rolle **db_owner** in der Zieldatenbank.  
  
## <a name="establishing-an-azure-sql-database-connection"></a>Einrichten einer Azure SQL-Datenbankverbindung  
Vor dem Konvertieren von Sybase-Datenbankobjekten in die Azure SQL-Daten Bank Syntax müssen Sie eine Verbindung mit der Instanz von Azure SQL-Datenbank herstellen, in der Sie die Sybase-Datenbank oder die Datenbanken migrieren möchten.  
  
Wenn Sie die Verbindungs Eigenschaften definieren, geben Sie auch die Datenbank an, in die Objekte und Daten migriert werden. Sie können diese Zuordnung auf der Sybase-Schema Ebene anpassen, nachdem Sie eine Verbindung mit Azure SQL-Datenbank hergestellt haben. Weitere Informationen finden Sie unter [Mapping Sybase ASE Schemas to SQL Server Schemas &#40;sybasedesql&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
> [!WARNING]  
> Bevor Sie versuchen, eine Verbindung mit Azure SQL-Datenbank herzustellen, stellen Sie sicher, dass die Instanz von Azure SQL-Datenbank ausgeführt wird und Verbindungen akzeptieren kann.  
  
**Herstellen einer Verbindung mit Azure SQL-Datenbank**  
  
1.  Wählen Sie im Menü **Datei** die Option **mit Azure SQL-Datenbank verbinden**aus. (diese Option wird nach der Projekt Erstellung aktiviert.)  
  
    Wenn Sie zuvor eine Verbindung mit Azure SQL-Datenbank hergestellt haben, wird der Befehls Name **erneut mit Azure SQL-Datenbank** verbunden.  
  
2.  Geben Sie im Dialogfeld Verbindung den Servernamen der Azure SQL-Datenbank ein, oder wählen Sie ihn aus.  
  
3.  Geben Sie den Datenbanknamen ein, oder **Suchen** Sie ihn.  
  
4.  Geben Sie **username**ein, oder wählen Sie  
  
5.  Geben Sie das **Kennwort ein**.  
  
6.  SSMA empfiehlt eine verschlüsselte Verbindung mit Azure SQL-Datenbank.  
  
7.  Klicken Sie auf **Verbinden**.  
  
> [!IMPORTANT]  
> SSMA für Sybase unterstützt keine Verbindung mit der **Master** -Datenbank in Azure SQL-Datenbank.  
  
## <a name="synchronizing-azure-sql-database-metadata"></a>Synchronisieren von Metadaten von Azure SQL-Datenbank  
Metadaten zu Azure SQL-Daten Bank Datenbanken werden nicht automatisch aktualisiert. Bei den Metadaten im metadatenexplorer von Azure SQL-Datenbank handelt es sich um eine Momentaufnahme der Metadaten, wenn Sie zum ersten Mal eine Verbindung mit Azure SQL-Datenbank hergestellt haben oder wenn Sie die Metadaten zuletzt manuell aktualisiert Sie können Metadaten für alle Datenbanken oder für eine einzelne Datenbank oder ein Datenbankobjekt manuell aktualisieren.  
  
**So synchronisieren Sie Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit Azure SQL-Datenbank verbunden sind.  
  
2.  Aktivieren Sie im metadatenexplorer von Azure SQL-Datenbank das Kontrollkästchen neben der Datenbank oder dem Datenbankschema, das Sie aktualisieren möchten.  
  
    Wenn Sie z. b. die Metadaten für alle Datenbanken aktualisieren möchten, aktivieren Sie das Kontrollkästchen neben Datenbanken.  
  
3.  Klicken Sie mit der rechten Maustaste auf Datenbanken oder die einzelne Datenbank oder das Datenbankschema, und wählen Sie dann **mit Datenbank synchronisieren**aus.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:  
  
-   Informationen zum Anpassen der Zuordnung zwischen Sybase-Schemas und Azure SQL-Datenbank-Datenbanken und-Schemas finden Sie unter [Mapping von Sybase-ASE-Schemas zu SQL Server Schemas &#40;Sybase&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
-   Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Festlegen von Projektoptionen &#40;sybasedesql&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md)  
  
-   Informationen zum Anpassen der Zuordnung von Quell-und Ziel Datentypen finden Sie unter [Mapping Sybase ASE und SQL Server Datentypen &#40;sybasetosql&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)  
  
-   Wenn Sie diese Aufgaben nicht ausführen müssen, können Sie die Sybase-Datenbankobjekt Definitionen in Azure SQL-Datenbankobjekt Definitionen konvertieren. Weitere Informationen finden Sie unter [umstellen von Sybase ASE-Datenbankobjekten &#40;sybasedesql&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von Sybase ASE-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
