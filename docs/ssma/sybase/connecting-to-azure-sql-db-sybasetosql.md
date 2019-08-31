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
ms.openlocfilehash: 10be1dc3652c944b9de08a01b0f4cdff5ae5849a
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176240"
---
# <a name="connecting-to-azure-sql-db-sybasetosql"></a>Herstellen einer Verbindung mit Azure SQL-DB (SybaseToSQL)
Um Sybase-Datenbanken zu Azure SQL-Datenbank zu migrieren, müssen Sie eine Verbindung mit der Ziel Instanz von Azure SQL-Datenbank herstellen. Wenn Sie eine Verbindung herstellen, ruft SSMA Metadaten zu allen Datenbanken in der Instanz von Azure SQL-Datenbank ab und zeigt Daten Bank Metadaten im metadatenexplorer von Azure SQL-Datenbank an. SSMA speichert Informationen über die Instanz von Azure SQL-Datenbank, mit der Sie verbunden sind, speichert aber keine Kenn Wörter.  
  
Die Verbindung mit Azure SQL-Datenbank bleibt aktiv, bis Sie das Projekt schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie erneut eine Verbindung mit Azure SQL-Datenbank herstellen, wenn Sie eine aktive Verbindung mit dem Server herstellen möchten. Sie können offline arbeiten, bis Sie Datenbankobjekte in Azure SQL-Datenbank laden und Daten migrieren.  
  
Metadaten über die Instanz von Azure SQL-Datenbank werden nicht automatisch synchronisiert. Stattdessen müssen Sie die Metadaten der Azure SQL-Datenbank manuell aktualisieren, um die Metadaten im metadatenexplorer von Azure SQL-Datenbank zu aktualisieren. Weitere Informationen finden Sie im Abschnitt "Synchronisieren von Azure SQL-Daten Bank Metadaten" weiter unten in diesem Thema.  
  
## <a name="required-azure-sql-db-permissions"></a>Erforderliche Azure SQL-Daten Bank Berechtigungen  
Das Konto, das zum Herstellen einer Verbindung mit Azure SQL-Datenbank verwendet wird, erfordert abhängig von den Aktionen, die das Konto ausführt, unterschiedliche Berechtigungen:  
  
1.  Das Konto muss über die Berechtigung [!INCLUDE[tsql](../../includes/tsql-md.md)] zum Anmelden bei der Instanz von Azure SQL-Datenbank verfügen, um Sybase-Objekte in die Syntax zu konvertieren, um Metadaten aus Azure SQL-Datenbank zu aktualisieren oder um konvertierte Syntax in Skripts zu speichern.  
  
2.  Zum Laden von Datenbankobjekten in Azure SQL-Datenbank ist die Mindestanforderung für die Berechtigung die Mitgliedschaft in der Daten Bank Rolle **db_owner** in der Zieldatenbank.  
  
## <a name="establishing-an-azure-sql-db-connection"></a>Einrichten einer Azure SQL-Daten Bankverbindung  
Vor dem Konvertieren von Sybase-Datenbankobjekten in die Azure SQL-Daten Bank Syntax müssen Sie eine Verbindung mit der Instanz von Azure SQL-Datenbank herstellen, in der Sie die Sybase-Datenbank oder die Datenbanken migrieren möchten.  
  
Wenn Sie die Verbindungs Eigenschaften definieren, geben Sie auch die Datenbank an, in die Objekte und Daten migriert werden. Sie können diese Zuordnung auf der Sybase-Schema Ebene anpassen, nachdem Sie eine Verbindung mit Azure SQL-Datenbank hergestellt haben. Weitere Informationen finden Sie unter [Mapping Sybase ASE Schemas to SQL Server Schemas &#40;sybaseto SQL&#41; ](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
> [!WARNING]  
> Bevor Sie versuchen, eine Verbindung mit Azure SQL-Datenbank herzustellen, stellen Sie sicher, dass die Instanz der Azure SQL-Datenbank ausgeführt wird und Verbindungen akzeptieren kann.  
  
**So stellen Sie eine Verbindung mit Azure SQL DB her**  
  
1.  Wählen Sie im Menü Datei die Option **mit Azure SQL**- **Datenbank** verbinden aus. (diese Option wird nach der Projekt Erstellung aktiviert.)  
  
    Wenn Sie zuvor eine Verbindung mit Azure SQL-Datenbank hergestellt haben, stellt der Befehls Name **erneut eine Verbindung mit der Azure SQL** -Datenbank her.  
  
2.  Geben Sie im Dialogfeld Verbindung den Servernamen der Azure SQL-Datenbank ein, oder wählen Sie ihn aus.  
  
3.  Geben Sie den Datenbanknamen ein, oder **Suchen** Sie ihn.  
  
4.  Geben Sie **username**ein, oder wählen Sie  
  
5.  Geben Sie das **Kennwort ein**.  
  
6.  SSMA empfiehlt eine verschlüsselte Verbindung mit Azure SQL-Datenbank.  
  
7.  Klicken Sie auf **Verbinden**.  
  
> [!IMPORTANT]  
> SSMA für Sybase unterstützt keine Verbindung mit der **Master** -Datenbank in Azure SQL-Datenbank.  
  
## <a name="synchronizing-azure-sql-db-metadata"></a>Synchronisieren von Azure SQL-Daten Bank Metadaten  
Metadaten zu Azure SQL-Datenbanken werden nicht automatisch aktualisiert. Bei den Metadaten im metadatenexplorer von Azure SQL-Datenbank handelt es sich um eine Momentaufnahme der Metadaten, wenn Sie zum ersten Mal eine Verbindung mit Azure SQL-Datenbank hergestellt haben oder wenn Sie die Metadaten zuletzt manuell aktualisiert Sie können Metadaten für alle Datenbanken oder für eine einzelne Datenbank oder ein Datenbankobjekt manuell aktualisieren.  
  
**So synchronisieren Sie Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit Azure SQL-Datenbank verbunden sind.  
  
2.  Aktivieren Sie im Metadaten-Explorer von Azure SQL-Datenbank das Kontrollkästchen neben dem zu aktualisierenden Datenbankschema oder Datenbankschema.  
  
    Wenn Sie z. b. die Metadaten für alle Datenbanken aktualisieren möchten, aktivieren Sie das Kontrollkästchen neben Datenbanken.  
  
3.  Klicken Sie mit der rechten Maustaste auf Datenbanken oder die einzelne Datenbank oder das Datenbankschema, und wählen Sie dann **mit Datenbank synchronisieren**aus.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt der Migration hängt von Ihren Projektanforderungen ab:  
  
-   Informationen zum Anpassen der Zuordnung zwischen Sybase-Schemas und Azure SQL-Datenbanken und Schemas finden Sie unter [Mapping von Sybase-ASE &#40;-Schemas zu&#41; SQL Server Schemas sybaseto SQL](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md) .  
  
-   Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Festlegen von Projekt &#40;Optionen&#41; (sybasedesql](../../ssma/sybase/setting-project-options-sybasetosql.md) ).  
  
-   Informationen zum Anpassen der Zuordnung von Quell-und Ziel Datentypen finden Sie unter [Mapping Sybase ASE &#40;und SQL Server Datentypen&#41; sybasetosql](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)  
  
-   Wenn Sie diese Aufgaben nicht ausführen müssen, können Sie die Sybase-Datenbankobjekt Definitionen in Azure SQL-Datenbankobjekt Definitionen konvertieren. Weitere Informationen finden Sie unter [umstellen von Sybase ASE- &#40;Datenbankobjekten sybasedesql&#41; ](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Sybase ASE-Datenbanken zu SQL Server &#40;-Azure SQL-Datenbank sybaseto SQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
