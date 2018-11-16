---
title: Hinzufügen und entfernen Sie den Zugriff von Datenbankdateien (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases
- adding Access files
- adding and removing Access databases
- browsing Access metadata
- browsing metadata, Access databases
- connecting, Access databases
- databases
- files, adding and removing
- finding Access databases
- finding database files
- locating database files
- metadata
- metadata, browsing
- metadata, refreshing
- refreshing metadata
- removing Access files
- scanning for database files
- searching for database files
ms.assetid: e944c740-4c8a-4bc1-b0ed-be57bc06dced
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8de9b27a58d277191a4d40da6b34dbcbbd43e497
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51655639"
---
# <a name="adding-and-removing-access-database-files-accesstosql"></a>Hinzufügen und Entfernen von Access-Datenbankdateien (AccessToSQL)
Migrieren von Access-Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, müssen Sie mindestens eine Access-Datenbanken in der SSMA-Projekt hinzufügen. Diese Datenbanken müssen Access 97 oder höher sein. Wenn Sie Datenbanken aus einer früheren Version von Zugriff haben, müssen Sie die Datenbanken auf eine neuere Version konvertieren. Hierzu öffnen und speichern die Datenbanken in Access 97 oder höher, bevor Sie sie SSMA hinzufügen.  
  
## <a name="what-happens-when-you-add-access-database-files"></a>Was geschieht, wenn Sie die Access-Datenbankdateien hinzufügen?  
Wenn Sie eine Access-Datenbank zu einem SSMA-Projekt hinzufügen, SSMA liest Datenbankmetadaten und fügt dann diese Metadaten zu der Projektdatei. Diese Metadaten beschreiben die Datenbank und die Objekte an. SSMA verwendet die Metadaten aus, wenn Objekte konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Syntax, und wenn es Daten migriert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Sie können diese Metadaten in der Access-Metadaten-Explorer durchsuchen und überprüfen Sie die Eigenschaften einzelner Datenbankobjekte.  
  
> [!NOTE]  
> Eine Access-Datenbank kann in mehrere Dateien aufgeteilt werden: eine Back-End-Datenbank, Tabellen enthält, und Front-End-Datenbanken, die Abfragen, Formulare, Berichte, Makros, Modulen und Verknüpfungen enthalten. Sollten Sie Teilen zum Migrieren einer Datenbank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, die Front-End-Datenbank SSMA hinzuzufügen.  
  
## <a name="permissions-that-are-required-by-ssma"></a>Berechtigungen, die von SSMA erforderlich sind  
Migrieren eine Access-Datenbank zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, die Benutzergruppe und der Administratorbenutzer müssen über Verwaltungsberechtigungen verfügen. Weitere Informationen zum Migrieren von Datenbanken mit Arbeitsgruppe Schutz, finden Sie unter [Access-Datenbanken für die Migration vorbereiten](preparing-access-databases-for-migration-accesstosql.md).  
  
## <a name="selecting-databases-to-add"></a>Auswählen Hinzuzufügender Datenbanken  
Wenn Sie eine oder mehrere Datenbanken zu einem SSMA-Projekt hinzufügen möchten, und die Dateien, die an einem bekannten Ort sind, können Sie die Dateien mithilfe des folgenden Verfahrens hinzufügen.  
  
**Hinzufügen der einzelnen Datenbankdateien**  
  
1.  Auf der **Datei** Menü klicken Sie auf **Datenbanken hinzufügen**.  
  
2.  In der **öffnen** Dialogfeld Suchen den Ordner, die Datenbank-Dateien enthält.  
  
3.  Wählen Sie die Dateien, die Sie hinzufügen möchten, und klicken Sie dann auf **öffnen**.  
  
## <a name="finding-databases-to-add"></a>Suchen die Datenbanken hinzufügen  
Wenn Sie mehrere Access-Datenbanken aus unterschiedlichen Ordnern zu einem SSMA-Projekt hinzufügen möchten, oder Sie möchten eine einzelne Datei hinzufügen, jedoch müssen Sie die Datei nicht finden, können Sie die folgenden Schritte durchführen, um eine von mehreren Dateien suchen, und fügen sie dem Projekt hinzu.  
  
**Suchen und Hinzufügen von Datenbanken**  
  
1.  Auf der **Datei** Menü klicken Sie auf **Datenbanken suchen**.  
  
2.  Geben Sie den Namen des Laufwerks, Dateipfad oder den UNC-Pfad, den Sie suchen möchten, im Assistenten Datenbanken gefunden. Klicken Sie alternativ auf **Durchsuchen** auf dem Laufwerk oder Ordner zu suchen.  
  
3.  Klicken Sie auf **hinzufügen** den Speicherort der Liste hinzu.  
  
    Wiederholen Sie die vorherigen beiden Schritte aus, um weitere Suche Speicherorte hinzuzufügen.  
  
4.  Fügen Sie optional Suchkriterien, um die Liste der Datenbanken zu optimieren, die zurückgegeben werden.  
  
    > [!IMPORTANT]  
    > Die **alle oder einen Teil des Dateinamens** Textfeld unterstützt keine Platzhalterzeichen enthalten.  
  
5.  Klicken Sie auf **Scannen**.  
  
    Die Seite "Überprüfung" wird angezeigt. Es werden die Datenbanken, die gefunden wurden und den Fortschritt der Suche. Um die Suche zu beenden, klicken Sie auf **beenden**.  
  
6.  Wählen Sie die Datenbanken, die Sie dem Projekt hinzufügen möchten, klicken Sie auf der Seite "Dateien auswählen".  
  
    Können Sie die **Alles markieren** und **deaktivieren Sie alle** Schaltflächen am oberen Rand der Liste aktivieren oder deaktivieren Sie alle Datenbanken. Sie können die STRG-Taste gedrückt, um mehrere Datenbanken auszuwählen, oder halten die UMSCHALTTASTE gedrückt, wählen Sie einen Bereich von Datenbanken.  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Klicken Sie auf der Seite "Überprüfen" auf **Fertig stellen**.  
  
## <a name="browsing-access-metadata"></a>Durchsuchen von Metadaten für den Zugriff  
Nachdem Sie eine Access-Datenbank zu einem Projekt hinzugefügt haben, wird die Projektmetadaten in Access-Metadaten-Explorer angezeigt. Sie können die Hierarchie der Datenbanken und Datenbankobjekte im Explorer navigieren.  
  
**Durchsuchen von Metadaten**  
  
1.  Erweitern Sie im Metadaten-Explorer für den Zugriff, **Access-Metabase**, und erweitern Sie dann **Datenbanken**.  
  
2.  Erweitern Sie die Datenbank, die Sie überprüfen möchten, und erweitern dann **Abfragen**.  
  
    Beachten Sie, dass die Liste der Abfragen. Wenn Sie eine Abfrage, wählen Sie eine **SQL** Registerkarte und eine **Eigenschaften** Registerkarte im rechten Bereich angezeigt.  
  
3.  Erweitern Sie **Tabellen** und wählen Sie dann auf eine Tabelle.  
  
    Beachten Sie, dass vier Registerkarten angezeigt: **Tabelle**, **Type Mapping**, **Eigenschaften**, und **Daten**.  
  
4.  Erweitern Sie eine Tabelle und **Schlüssel**, und wählen Sie dann auf einen Schlüssel.  
  
    Die wichtigsten Eigenschaften werden im rechten Bereich angezeigt.  
  
5.  Erweitern Sie **Indizes**, und wählen Sie dann einen Index.  
  
    Die Indexeigenschaften werden im rechten Bereich angezeigt.  
  
## <a name="refreshing-databases"></a>Aktualisieren von Datenbanken  
Wenn es sich bei eine Access-Datenbank ändert, nachdem Sie die Datei hinzugefügt haben, können Sie Metadaten aus der Access-Datenbank aktualisieren.  
  
**So aktualisieren Sie Metadaten für den Zugriff**  
  
-   Access-Metadaten-Explorer mit der rechten Maustaste in der Datenbank, und wählen Sie dann **Refresh from Database aktualisieren**.  
  
## <a name="removing-databases"></a>Entfernen von Datenbanken  
Sie können eine Access-Datenbank aus einem Projekt entfernen, indem Sie diese Schritte.  
  
**So entfernen Sie eine Datenbank aus einem Projekt**  
  
1.  Erweitern Sie im Metadaten-Explorer für den Zugriff, **Access-Metabase**, und erweitern Sie dann **Datenbanken**.  
  
2.  Mit der rechten Maustaste in der Datenbank, und wählen Sie dann **Remove Database**.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrationsvorgangs besteht darin [Verbinden mit SQL Server](https://msdn.microsoft.com/bb8c4bde-cfc2-4636-92ae-5dd24abe9536).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Erstellen und Verwalten von Projekten](creating-and-managing-projects-accesstosql.md)  
  
