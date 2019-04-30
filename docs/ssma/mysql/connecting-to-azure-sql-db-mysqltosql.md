---
title: Eine Verbindung mit Azure Sqldb (MySQLToSQL)) | Microsoft-Dokumentation
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
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 23d018a8d551a5c3a7f2978339b6cf7612f378fd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63253280"
---
# <a name="connecting-to-azure-sql-db-mysqltosql"></a>Herstellen einer Verbindung mit der Azure SQL-DB (MySqlToSql)
Um MySQL-Datenbanken zu SQL Azure zu migrieren, müssen Sie mit der Zielinstanz von SQL Azure verbinden. Wenn Sie eine Verbindung herstellen, wird SSMA Ruft Metadaten zu allen Datenbanken in der Instanz von SQL Azure-und Datenbank-Metadaten in der SQL Azure-Metadaten-Explorer angezeigt. SSMA speichert Informationen von der Instanz von SQL Azure Sie verbunden sind, jedoch werden keine Kennwörter gespeichert werden.  
  
Die Verbindung mit SQL Azure bleibt aktiv, bis Sie das Projekt zu schließen. Wenn Sie das Projekt erneut öffnen, müssen Sie auf SQL Azure erneut, wenn Sie möchten, dass eine aktive Verbindung mit dem Server verbinden. Sie können offline arbeiten, bis Sie die Datenbankobjekte in SQL Azure laden und Migrieren von Daten.  
  
Metadaten zu der Instanz von SQL Azure wird nicht automatisch synchronisiert. Um die Metadaten in SQL Azure-Metadaten-Explorer zu aktualisieren, müssen Sie stattdessen manuell die SQL Azure-Metadaten aktualisieren. Weitere Informationen finden Sie unter "Synchronisieren von SQL Azure-Metadaten" im Abschnitt weiter unten in diesem Thema.  
  
## <a name="required-sql-azure-permissions"></a>SQL Azure erforderliche Berechtigungen  
Das Konto, das verwendet wird, zur Verbindung mit SQL Azure erfordert unterschiedliche Berechtigungen abhängig von den Aktionen, die das Konto ausführt:  
  
-   So konvertieren Sie Objekte von MySQL auf [!INCLUDE[tsql](../../includes/tsql-md.md)] Syntax so aktualisieren Sie Metadaten aus SQL Azure oder Speichern der konvertierten Syntax, um Skripts, das Konto muss die Berechtigung zum Anmelden mit der Instanz von SQL Azure verfügen.  
  
-   Um Datenbankobjekte in SQL Azure zu laden, ist die Anforderung mindestens die Mitgliedschaft in der **Db_owner** Datenbankrolle in der Zieldatenbank.  
  
## <a name="establishing-a-sql-azure-connection"></a>Einrichten einer SQL Azure-Verbindung  
Bevor Sie Objekte des MySQL-Datenbank in SQL Azure-Syntax konvertieren, müssen Sie eine Verbindung mit der Instanz von SQL Azure einrichten, die MySQL-Datenbank oder Datenbanken migriert werden sollen.  
  
Wenn Sie die Verbindungseigenschaften definieren, geben Sie auch die Datenbank, in dem Objekte und Daten migriert werden. Sie können diese Zuordnung auf der Schemaebene MySQL anpassen, nach dem Herstellen einer Verbindung mit SQL Azure. Weitere Informationen finden Sie unter [Zuordnen von MySQL-Datenbanken in SQL Server-Schemas &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
> [!IMPORTANT]  
> Bevor Sie versuchen, eine Verbindung mit SQL Azure, stellen Sie sicher, dass die Instanz von SQL Azure ausgeführt wird und Verbindungen akzeptieren.  
  
**Verbindung mit SQL Azure**  
  
1.  Auf der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit SQL Azure** (diese Option ist aktiviert, nach der Erstellung eines Projekts).  
  
    Wenn Sie zuvor mit SQL Azure verbunden haben, gibt der Namen des Befehls werden **Wiederherstellen der Verbindung zu SQL Azure**.  
  
2.  Klicken Sie im Dialogfeld Verbindung geben Sie ein, oder wählen Sie den Namen des SQL Azure.  
  
3.  Geben Sie ein, wählen oder **Durchsuchen** der Name der Datenbank.  
  
4.  Geben Sie ein oder wählen Sie **Benutzername**.  
  
5.  Geben Sie die **Kennwort**.  
  
6.  SSMA empfiehlt verschlüsselte Verbindung für SQL Azure.  
  
7.  Klicken Sie auf **Verbinden**.  
  
> [!IMPORTANT]  
> SSMA für MySQL unterstützt keine Verbindung mit **master** Datenbank in SQL Azure.  
  
## <a name="synchronizing-sql-azure-metadata"></a>Synchronisieren von SQL Azure-Metadaten  
Metadaten zu SQL Azure-Datenbanken wird nicht automatisch aktualisiert. Die Metadaten in SQL Azure-Metadaten-Explorer ist, dass eine Momentaufnahme der Metadaten, wenn Sie zunächst mit SQL Azure verbunden ist, oder der letzten Ausführung, die Sie manuell die Metadaten aktualisiert werden. Sie können die Metadaten für alle Datenbanken oder für jede einzelne Datenbank oder Datenbankobjekt, das manuell aktualisieren.  
  
**Zum Synchronisieren von Metadaten**  
  
1.  Stellen Sie sicher, dass Sie mit SQL Azure verbunden sind.  
  
2.  Wählen Sie in SQL Azure-Metadaten-Explorer das Kontrollkästchen neben der Datenbank oder das Datenbankschema, die Sie aktualisieren möchten.  
  
    Z. B. um die Metadaten für alle Datenbanken zu aktualisieren, wählen Sie das Kontrollkästchen neben den Datenbanken an.  
  
3.  Mit der rechten Maustaste, Datenbanken, oder die einzelne Datenbank oder das Datenbankschema, und wählen Sie dann **synchronisieren mit der Datenbank**.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt bei der Migration hängt von den Anforderungen Ihrer Projekte:  
  
-   Informationen zum Anpassen der Zuordnung zwischen Schemas von MySQL und SQL Azure-Datenbanken und Schemas finden Sie unter [Mapping MySQL-Datenbanken in SQL Server-Schemas &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   Informationen zum Anpassen der Konfigurationsoptionen für die Projekte finden Sie unter [Setting Project Options Projektoptionen &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   Wenn die Zuordnung von Datentypen für Quell- und zieleinstellungen anpassen möchten, finden Sie unter [Mapping MySQL und SQL Server-Datentypen &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Wenn Sie nicht zum Ausführen dieser Aufgaben verfügen, können Sie die Objektdefinitionen für MySQL-Datenbank in SQL Azure-Objektdefinitionen konvertieren. Weitere Informationen finden Sie unter [MySQL-Datenbanken konvertieren &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von MySQL-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
