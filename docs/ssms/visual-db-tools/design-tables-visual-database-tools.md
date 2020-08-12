---
title: Entwerfen und Aktualisieren von Tabellen
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Visual Database Tools [SQL Server], Table Designer
- Table Designer, designing tables
- opening tables
- opening Table Designer
- tables [SQL Server], opening
- Table Designer, opening
ms.assetid: c49e0155-5dcb-481f-9538-e1bde77105e2
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 08/25/2017
ms.openlocfilehash: 026080e2eedf38cb65b3c8860335ab5432504a0a
ms.sourcegitcommit: 01297f2487fe017760adcc6db5d1df2c1234abb4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86196854"
---
# <a name="create-and-update-database-tables"></a>Erstellen und Aktualisieren von Datenbanktabellen

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Der Tabellen-Designer ist ein visuelles Tool, in dem [Datenbanktabellen](../../relational-databases/tables/tables.md) entworfen und visualisiert werden können. Mit dem Tabellen-Designer von SQL Server Management Studio (SSMS) können Sie Tabellen, Spalten, Schlüssel, Indizes, Beziehungen und Einschränkungen erstellen, bearbeiten oder löschen.  

## <a name="create-a-table"></a>Erstellen einer Tabelle

1. Klicken Sie mit der rechten Maustaste in der Datenbank auf den Knoten **Tabellen**, und klicken Sie auf **Neu** > **Tabelle**:

    ![Neue Tabelle](../media/design-tables/new-table.png)

2. Fügen Sie Ihrer Tabelle [Spalten](column-properties-visual-database-tools.md) hinzu:

    ![Tabelle entwerfen](../media/design-tables/new-table2.png)

3. Schließen Sie den Designer, und speichern Sie die Änderungen.

## <a name="update-a-table"></a>Aktualisieren einer Tabelle

1. Klicken Sie mit der rechten Maustaste auf die Tabelle unter dem Knoten **Tabellen** Ihrer Datenbank, und klicken Sie auf **Entwerfen**:

    ![Tabelle aktualisieren](../media/design-tables/update-table.png)

2. Aktualisieren Sie die gewünschten Tabelleneinstellungen:

    ![Erstellen einer Tabelle](../media/design-tables/update-table2.png)

3. Schließen Sie den Designer, und speichern Sie die Änderungen.

## <a name="see-also"></a>Weitere Informationen

- [Tabellen](../../relational-databases/tables/tables.md)
- [Tabelleneigenschaften &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/table-properties-visual-database-tools.md)
- [Spalteneigenschaften](column-properties-visual-database-tools.md)
- [Hinzufügen von Spalten zu einer Tabelle](../../relational-databases/tables/add-columns-to-a-table-database-engine.md)
- [Primärschlüssel- und Fremdschlüsseleinschränkungen](../../relational-databases/tables/primary-and-foreign-key-constraints.md)
- [Indizes](../../relational-databases/indexes/indexes.md)
- [Data types (Transact-SQL) (Datentypen (Transact-SQL))](../../t-sql/data-types/data-types-transact-sql.md)
- [Herunterladen von SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md)
- [Create a database and add tables in Visual Studio (Erstellen einer Datenbank und Hinzufügen von Tabellen in Visual Studio)](/visualstudio/data-tools/create-a-sql-database-by-using-a-designer)
