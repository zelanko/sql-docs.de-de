---
title: Hinzufügen und Entfernen von Access-Datenbankdateien (accesstosql) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Zugriffs Datenbanken zum oder aus dem SSMA-Projekt hinzufügen oder entfernen, um Zugriffsdaten zu SQL Server oder Azure SQL-Datenbank zu migrieren.
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
ms.openlocfilehash: 6806792fa828a5ebb4ea3a7a5a7e813626bff523
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293687"
---
# <a name="adding-and-removing-access-database-files-accesstosql"></a>Hinzufügen und Entfernen von Access-Datenbankdateien (accesstosql)
Zum Migrieren von Zugriffsdaten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure müssen Sie dem SSMA-Projekt eine oder mehrere Access-Datenbanken hinzufügen. Diese Datenbanken müssen auf 97 oder höhere Versionen zugreifen. Wenn Sie über Datenbanken aus einer früheren Zugriffs Version verfügen, müssen Sie die Datenbanken in eine neuere Version konvertieren. Hierzu öffnen und speichern Sie die Datenbanken in Access 97 oder einer höheren Version, bevor Sie Sie SSMA hinzufügen.  
  
## <a name="what-happens-when-you-add-access-database-files"></a>Was geschieht, wenn Sie Access-Datenbankdateien hinzufügen?  
Wenn Sie einem SSMA-Projekt eine Access-Datenbank hinzufügen, liest SSMA Daten Bank Metadaten und fügt diese Metadaten dann der Projektdatei hinzu. Diese Metadaten beschreiben die Datenbank und ihre Objekte. SSMA verwendet die Metadaten beim Konvertieren von-Objekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Syntax und beim Migrieren von Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Sie können diese Metadaten in Access Metadata Explorer durchsuchen und die Eigenschaften einzelner Datenbankobjekte überprüfen.  
  
> [!NOTE]  
> Eine Access-Datenbank kann in mehrere Dateien aufgeteilt werden: eine Back-End-Datenbank, die Tabellen enthält, und Front-End-Datenbanken, die Abfragen, Formulare, Berichte, Makros, Module und Verknüpfungen enthalten. Wenn Sie eine Split-Datenbank zu oder SQL Azure migrieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , fügen Sie die Front-End-Datenbank zu SSMA hinzu.  
  
## <a name="permissions-that-are-required-by-ssma"></a>Für SSMA erforderliche Berechtigungen  
Zum Migrieren einer Access-Datenbank zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure müssen die Benutzergruppe und der Administrator Benutzer über Berechtigungen zum Verwalten verfügen. Informationen zum Migrieren von Datenbanken mit dem Schutz von Arbeitsgruppen finden Sie unter [Vorbereiten von Access-Datenbanken für die Migration](preparing-access-databases-for-migration-accesstosql.md).  
  
## <a name="selecting-databases-to-add"></a>Hinzu zufügende Datenbanken auswählen  
Wenn Sie einem SSMA-Projekt eine oder mehrere Datenbanken hinzufügen möchten und sich die Dateien alle an einem bekannten Speicherort befinden, können Sie die Dateien mit dem folgenden Verfahren hinzufügen.  
  
**So fügen Sie einzelne Datenbankdateien hinzu**  
  
1.  Klicken Sie im Menü **Datei** auf **Datenbanken hinzufügen**.  
  
2.  Suchen Sie im Dialogfeld **Öffnen** den Ordner, der die Datenbankdateien enthält.  
  
3.  Wählen Sie die Dateien aus, die Sie hinzufügen möchten, und klicken Sie dann auf **Öffnen**.  
  
## <a name="finding-databases-to-add"></a>Hinzu zufügende Datenbanken suchen  
Wenn Sie einem SSMA-Projekt mehrere Zugriffs Datenbanken aus unterschiedlichen Ordnern hinzufügen möchten oder wenn Sie eine einzelne Datei hinzufügen möchten, aber die Datei finden möchten, können Sie die folgenden Schritte ausführen, um eine der weiteren Dateien zu suchen und Sie dem Projekt hinzuzufügen.  
  
**So suchen und fügen Sie Datenbanken hinzu**  
  
1.  Klicken Sie im Menü **Datei** auf **Datenbanken suchen**.  
  
2.  Geben Sie im Assistenten zum Suchen von Datenbanken den Namen des Laufwerks, den Dateipfad oder den UNC-Pfad ein, der durchsucht werden soll. Sie können auch auf **Durchsuchen** klicken, um das Laufwerk oder den Netzwerkordner zu suchen.  
  
3.  Klicken Sie auf **Hinzufügen** , um den Speicherort der Liste hinzuzufügen.  
  
    Wiederholen Sie die vorherigen beiden Schritte, um weitere Such Speicherorte hinzuzufügen.  
  
4.  Fügen Sie optional Suchkriterien hinzu, um die Liste der zurückgegebenen Datenbanken zu verfeinern.  
  
    > [!IMPORTANT]  
    > Der **ganz oder Teil des Textfelds "Dateiname** " unterstützt keine Platzhalter Zeichen.  
  
5.  Klicken Sie auf **Scannen**.  
  
    Die Seite Scannen wird angezeigt. Dadurch werden die Datenbanken, die gefunden wurden, und der Fortschritt der Suche angezeigt. Zum Abbrechen der Suche klicken Sie auf " **Abbrechen**".  
  
6.  Wählen Sie auf der Seite Dateien auswählen die Datenbanken aus, die Sie dem Projekt hinzufügen möchten.  
  
    Sie können die Schaltflächen **Alle auswählen** und **Alle löschen** am Anfang der Liste verwenden, um alle Datenbanken auszuwählen oder zu löschen. Sie können die STRG-Taste gedrückt halten, um mehrere Datenbanken auszuwählen, oder die UMSCHALTTASTE gedrückt halten, um einen Daten Bankbereich auszuwählen.  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Klicken Sie auf der Seite überprüfen auf **Fertig**stellen.  
  
## <a name="browsing-access-metadata"></a>Durchsuchen von Zugriffs Metadaten  
Nachdem Sie einem Projekt eine Access-Datenbank hinzugefügt haben, werden die Projekt Metadaten in Access Metadata Explorer angezeigt. Sie können die Hierarchie von Datenbanken und Datenbankobjekten im Explorer durchsuchen.  
  
**So durchsuchen Sie Metadaten**  
  
1.  Erweitern Sie in Access Metadata Explorer den Eintrag **Access-Metabase**, und erweitern Sie dann **Datenbanken**.  
  
2.  Erweitern Sie die Datenbank, die Sie überprüfen möchten, und erweitern Sie dann **Abfragen**.  
  
    Beachten Sie die Liste der Abfragen. Wenn Sie eine Abfrage auswählen, werden im rechten Bereich eine Registerkarte " **SQL** " und eine Registerkarte " **Eigenschaften** " angezeigt.  
  
3.  Erweitern Sie **Tabellen** , und wählen Sie dann eine Tabelle aus.  
  
    Beachten Sie, dass vier Registerkarten angezeigt werden: **Table**, **Type Mapping**, **Properties**und **Data**.  
  
4.  Erweitern Sie eine Tabelle, erweitern Sie **Schlüssel**, und wählen Sie dann einen Schlüssel aus.  
  
    Die Schlüsseleigenschaften werden im rechten Bereich angezeigt.  
  
5.  Erweitern Sie **Indizes**, und wählen Sie dann einen Index aus.  
  
    Die Index Eigenschaften werden im rechten Bereich angezeigt.  
  
## <a name="refreshing-databases"></a>Aktualisieren von Datenbanken  
Wenn sich eine Access-Datenbank ändert, nachdem Sie die zugehörige Datei hinzugefügt haben, können Sie Metadaten aus der Access-Datenbank aktualisieren.  
  
**So aktualisieren Sie Zugriffs Metadaten**  
  
-   Klicken Sie im Access Metadata Explorer mit der rechten Maustaste auf die Datenbank, und wählen Sie dann **aus Datenbank aktualisieren aus**.  
  
## <a name="removing-databases"></a>Entfernen von Datenbanken  
Sie können eine Access-Datenbank aus einem-Projekt entfernen, indem Sie die folgenden Schritte ausführen.  
  
**So entfernen Sie eine Datenbank aus einem Projekt**  
  
1.  Erweitern Sie in Access Metadata Explorer den Eintrag **Access-Metabase**, und erweitern Sie dann **Datenbanken**.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Datenbank, und wählen Sie dann **Datenbank entfernen**aus.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrations Vorgangs besteht darin, eine [Verbindung mit SQL Server herzustellen](https://msdn.microsoft.com/bb8c4bde-cfc2-4636-92ae-5dd24abe9536).  
  
## <a name="see-also"></a>Weitere Informationen  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Erstellen und Verwalten von Projekten](creating-and-managing-projects-accesstosql.md)  
  
