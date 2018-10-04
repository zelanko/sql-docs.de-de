---
title: Eine Verbindung mit Azure Sqldb (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9e77e4b0-40c0-455c-8431-ca5d43849aa7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ac8b97e36338a280b6f78a0e6bb73eeab882655d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632098"
---
# <a name="connecting-to-azure-sql-db-sybasetosql"></a>Herstellen einer Verbindung mit Azure SQL-DB (SybaseToSQL)
Zum Migrieren von Sybase-Datenbanken in Azure SQL-Datenbank müssen Sie mit der Zielinstanz von Azure SQL-Datenbank verbinden. Wenn Sie eine Verbindung herstellen, wird SSMA Ruft Metadaten zu allen Datenbanken in der Instanz von Azure SQL-Datenbank ab und zeigt Datenbank-Metadaten in der Azure SQL DB-Metadaten-Explorer. SSMA speichert Informationen von der Instanz von Azure SQL-Datenbank Sie verbunden sind, jedoch werden keine Kennwörter gespeichert werden.  
  
Die Verbindung mit Azure SQL-Datenbank bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie zur Azure SQL-Datenbank erneut, wenn Sie möchten, dass eine aktive Verbindung mit dem Server verbinden. Sie können offline arbeiten, bis Sie die Datenbankobjekte in Azure SQL-Datenbank laden und Migrieren von Daten.  
  
Metadaten zu der Instanz von Azure SQL-Datenbank wird nicht automatisch synchronisiert. Um die Metadaten in Azure SQL-DB-Metadaten-Explorer zu aktualisieren, müssen Sie stattdessen manuell die Azure SQL-Datenbank-Metadaten aktualisieren. Weitere Informationen finden Sie unter "Synchronisieren von Azure SQL DB Metadata" im Abschnitt weiter unten in diesem Thema.  
  
## <a name="required-azure-sql-db-permissions"></a>Die erforderlichen Berechtigungen für Azure SQL-DB  
Das Konto, das verwendet wird, zur Verbindung mit Azure SQL-Datenbank erfordert unterschiedliche Berechtigungen abhängig von den Aktionen, die das Konto ausführt:  
  
1.  Konvertieren von Sybase-Objekten, [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax, um Metadaten aus Azure SQL-Datenbank zu aktualisieren oder zum Speichern der konvertierten Syntax, um Skripts, das Konto muss die Berechtigung zum Anmelden mit der Instanz von Azure SQL-Datenbank verfügen.  
  
2.  Um Datenbankobjekte in Azure SQL-Datenbank zu laden, ist die Anforderung mindestens die Mitgliedschaft in der **Db_owner** Datenbankrolle in der Zieldatenbank.  
  
## <a name="establishing-a-azure-sql-db-connection"></a>Herstellen einer Azure SQL-DB-Verbindung  
Bevor Sie Objekte des Sybase-Datenbank in Azure SQL-Datenbank-Syntax konvertieren, müssen Sie eine Verbindung mit der Instanz von Azure SQL-Datenbank einrichten, die Sybase-Datenbank oder Datenbanken migriert werden sollen.  
  
Wenn Sie die Verbindungseigenschaften definieren, geben Sie auch die Datenbank, in dem Objekte und Daten migriert werden. Sie können diese Zuordnung auf der Ebene des Sybase anpassen, nach dem Herstellen einer Verbindung mit Azure SQL-Datenbank. Weitere Informationen finden Sie unter [Mapping Sybase ASE Schemas in SQL Server-Schemas &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
> [!WARNING]  
> Bevor Sie versuchen, die mit Azure SQL-Datenbank herstellen, stellen Sie sicher, dass die Instanz von Azure SQL-Datenbank ausgeführt wird und Verbindungen akzeptieren.  
  
**Verbindung mit Azure SQL-Datenbank**  
  
1.  Auf der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit Azure SQL-Datenbank**(diese Option ist aktiviert, nach der Erstellung eines Projekts).  
  
    Wenn Sie zuvor mit Azure SQL-Datenbank verbunden haben, gibt der Namen des Befehls werden **Wiederherstellen der Verbindung zur Azure SQL-Datenbank**  
  
2.  Klicken Sie im Dialogfeld Verbindung geben Sie ein, oder wählen Sie den Namen des Azure SQL-Datenbank.  
  
3.  Geben Sie ein, wählen oder **Durchsuchen** der Name der Datenbank.  
  
4.  Geben Sie ein oder wählen Sie **Benutzername**.  
  
5.  Geben Sie die **Kennwort**.  
  
6.  SSMA empfiehlt verschlüsselte Verbindung für Azure SQL-Datenbank.  
  
7.  Klicken Sie auf **Verbinden**.  
  
> [!IMPORTANT]  
> SSMA für Sybase unterstützt keine Verbindung mit **master** Datenbank in Azure SQL-Datenbank.  
  
## <a name="synchronizing-azure-sql-db-metadata"></a>Synchronisieren von Azure SQL-DB-Metadaten  
Metadaten zu Azure SQL-Datenbanken wird nicht automatisch aktualisiert. Die Metadaten in Azure SQL-DB-Metadaten-Explorer ist eine Momentaufnahme der Metadaten aus, wenn Sie zuerst mit Azure SQL-Datenbank oder dem letzten, dass Sie manuell die Metadaten aktualisiert verbunden. Sie können die Metadaten für alle Datenbanken oder für jede einzelne Datenbank oder Datenbankobjekt, das manuell aktualisieren.  
  
**Zum Synchronisieren von Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit Azure SQL-Datenbank verbunden sind.  
  
2.  Wählen Sie in Azure SQL DB-Metadaten-Explorer das Kontrollkästchen neben der Datenbank oder das Datenbankschema, die Sie aktualisieren möchten.  
  
    Z. B. um die Metadaten für alle Datenbanken zu aktualisieren, wählen Sie das Kontrollkästchen neben den Datenbanken an.  
  
3.  Mit der rechten Maustaste, Datenbanken, oder die einzelne Datenbank oder das Datenbankschema, und wählen Sie dann **synchronisieren mit der Datenbank**.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt bei der Migration hängt von den Anforderungen Ihrer Projekte:  
  
-   Informationen zum Anpassen der Zuordnung zwischen Sybase-Schemas und Azure SQL-Datenbanken und Schemas finden Sie unter [Zuordnen von Sybase ASE Schemas in SQL Server-Schemas &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
-   Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Setting Project Options Projektoptionen &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md)  
  
-   Wenn die Zuordnung von Datentypen für Quell- und zieleinstellungen anpassen möchten, finden Sie unter [Mapping Sybase ASE als auch SQL Server-Datentypen &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)  
  
-   Wenn Sie nicht zum Ausführen dieser Aufgaben verfügen, können Sie die Objektdefinitionen für Sybase-Datenbank in Azure SQL-Datenbank-Objektdefinitionen konvertieren. Weitere Informationen finden Sie unter [Konvertieren von Sybase ASE Database Objects &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Sybase ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
