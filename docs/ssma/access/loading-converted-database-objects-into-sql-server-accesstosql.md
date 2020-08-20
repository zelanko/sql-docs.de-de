---
description: Laden von konvertierten Datenbankobjekten in SQL Server (accesstosql)
title: Laden von konvertierten Datenbankobjekten in SQL Server (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases, loading converted objects into SQL Azure
- Access databases, loading converted objects into SQL Server
- data, securing
- loading objects into SQL Azure
- loading objects into SQL Server
- migrating objects into SQL Azure
- migrating objects into SQL Server
- moving objects into SQL Azure
- moving objects into SQL Server
- schemas, loading into SQL Azure
- schemas, loading into SQL Server
- scripting converted objects
- securing data
- SQL Azure, loading objects into
- SQL Server, loading objects into
- synchronizing metadata with SQL Azure
- synchronizing metadata with SQL Server
- uploading objects into SQL Azure
- uploading objects into SQL Server
ms.assetid: 4e854eee-b10c-4f0b-9d9e-d92416e6f2ba
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 41a1613a879579e809c8fd6a85d5c9b58c7b2b9c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472575"
---
# <a name="loading-converted-database-objects-into-sql-server-accesstosql"></a>Laden von konvertierten Datenbankobjekten in SQL Server (accesstosql)
Nachdem Sie Access-Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure konvertiert haben, können Sie die resultierenden Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure laden. Sie können entweder das SSMA-Objekt erstellen, oder Sie können Skripts für die Objekte erstellen und die Skripts selbst ausführen. Außerdem können Sie mit SSMA Ziel Metadaten mit dem tatsächlichen Inhalt von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank aktualisieren.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Zwischen Synchronisierung und Skripts auswählen  
Wenn Sie die konvertierten Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure ohne Änderungen laden möchten, können Sie die Datenbankobjekte von SSMA direkt erstellen oder neu erstellen. Diese Methode ist schnell und einfach, lässt jedoch nicht zu, dass der Code, der [!INCLUDE[tsql](../../includes/tsql-md.md)] die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder-SQL Azure Objekte definiert, außer gespeicherten Prozeduren angepasst wird.  
  
Wenn Sie das ändern möchten, [!INCLUDE[tsql](../../includes/tsql-md.md)] das zum Erstellen von-Objekten verwendet wird, oder wenn Sie mehr Kontrolle über die Objekt Erstellung haben möchten, verwenden Sie SSMA zum Erstellen von-Skripts. Anschließend können Sie diese Skripts ändern, jedes Objekt einzeln erstellen und sogar den-Agent verwenden, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] um die Erstellung dieser Objekte zu planen.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>Verwenden von SSMA zum Synchronisieren von Objekten mit SQL Server  
Wenn Sie SSMA zum Erstellen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbankobjekten verwenden möchten, wählen Sie die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Metadaten-Explorer aus, und synchronisieren Sie dann die Objekte mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, wie im folgenden Verfahren gezeigt. Wenn die Objekte bereits in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure vorhanden sind und die SSMA-Metadaten über lokale Änderungen oder Aktualisierungen der Definition dieser Objekte verfügen, ändert SSMA standardmäßig die Objekt Definitionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Sie können das Standardverhalten ändern, indem Sie die **Projekteinstellungen**bearbeiten.  
  
> [!NOTE]  
> Sie können vorhandene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbankobjekte auswählen, die nicht aus Access-Datenbanken konvertiert wurden. Diese Objekte werden von SSMA jedoch nicht neu erstellt oder geändert.  
  
**So synchronisieren Sie Objekte mit SQL Server oder SQL Azure**  
  
1.  Erweitern Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure metadatenexplorer den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Knoten oben oder SQL Azure, und erweitern Sie dann **Datenbanken**.  
  
2.  Wählen Sie die zu verarbeitenden Objekte aus:  
  
    -   Aktivieren Sie das Kontrollkästchen neben dem Datenbanknamen, um eine komplette Datenbank zu synchronisieren.  
  
    -   Aktivieren bzw. deaktivieren Sie das Kontrollkästchen neben dem Objekt oder Ordner, um einzelne Objekte oder Kategorien von Objekten zu synchronisieren oder auszulassen.  
  
3.  Nachdem Sie die zu verarbeitenden Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Metadaten-Explorer ausgewählt haben, klicken Sie mit der rechten Maustaste auf **Datenbanken**, und klicken Sie dann auf **mit Datenbank synchronisieren**.  
  
    Sie können einzelne Objekte oder Objektkategorien auch synchronisieren, indem Sie mit der rechten Maustaste auf das Objekt oder seinen übergeordneten Ordner klicken und dann auf **mit Datenbank synchronisieren**klicken.  
  
    Danach zeigt SSMA das Dialogfeld **mit Datenbank synchronisieren an** , in dem Sie zwei Gruppen von Elementen sehen können. Auf der linken Seite zeigt SSMA ausgewählte Datenbankobjekte an, die in einer Struktur dargestellt werden. Auf der rechten Seite sehen Sie eine Baumstruktur, die die gleichen Objekte in SSMA-Metadaten darstellt. Sie können die Struktur erweitern, indem Sie auf die Schaltfläche mit der rechten oder linken Schaltfläche klicken. Die Richtung der Synchronisierung wird in der Aktionsspalte angezeigt, die zwischen den beiden Strukturen platziert ist.  
  
    Ein Aktions Vorzeichen kann drei Zustände aufweisen:  
  
    -   Der nach-links-Pfeil bedeutet, dass der Inhalt der Metadaten in der Datenbank gespeichert wird (Standardeinstellung).  
  
    -   Ein Pfeil nach rechts bedeutet, dass der Daten Bank Inhalt die SSMA-Metadaten überschreibt.  
  
    -   Ein Kreuzzeichen bedeutet, dass keine Aktion ausgeführt wird.  
  
    Klicken Sie auf das Aktions Zeichen, um den Status zu ändern. Die eigentliche Synchronisierung wird durchgeführt, wenn Sie im Dialogfeld **mit Datenbank synchronisieren** auf die Schaltfläche **OK** klicken.  
  
## <a name="scripting-objects"></a>Skripterstellung für Objekte  
Wenn Sie [!INCLUDE[tsql](../../includes/tsql-md.md)] Definitionen der konvertierten Datenbankobjekte speichern oder die Objekt Definitionen ändern und Skripts selbst ausführen möchten, können Sie die konvertierten Datenbankobjekt Definitionen in [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts speichern.  
  
**So speichern Sie ein oder mehrere Objekte in einem Skript**  
  
1.  Erweitern Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] metadatenexplorer den obersten Knoten (Servername), und erweitern Sie dann **Datenbanken**.  
  
2.  Führen Sie eine oder mehrere der folgenden Aktionen aus:  
  
    -   Aktivieren Sie das Kontrollkästchen neben dem Datenbanknamen, um ein Skript für eine komplette Datenbank zu erstellen.  
  
    -   Zum Erstellen eines Skripts oder auslassen einzelner Ansichten erweitern Sie die Datenbank, erweitern Sie **Sichten**, und aktivieren bzw. deaktivieren Sie das Kontrollkästchen neben der Ansicht.  
  
    -   Zum Erstellen eines Skripts oder auslassen einzelner Tabellen erweitern Sie die Datenbank, erweitern Sie **Tabellen**, und aktivieren bzw. deaktivieren Sie das Kontrollkästchen neben der Tabelle.  
  
    -   Zum Erstellen eines Skripts oder auslassen einzelner Indizes für eine Tabelle erweitern Sie die Tabelle, erweitern Sie **Indizes**, und wählen Sie dann den Index aus, oder löschen Sie ihn.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Datenbanken** , und wählen Sie **Speichern**unter  
  
    Sie können auch Skripts für einzelne Objekte erstellen. Wenn Sie ein Skript für ein Objekt erstellen möchten, klicken Sie mit der rechten Maustaste auf das Objekt, und wählen Sie **als Skript speichern**aus.  
  
4.  Suchen Sie im Dialogfeld **Speichern** unter den Ordner, in dem Sie das Skript speichern möchten, geben Sie im Feld **Dateiname** einen Dateinamen ein, und klicken Sie dann auf **OK**.  
  
    SSMA fügt die Dateinamenerweiterung ". SQL" an.  
  
### <a name="modifying-scripts"></a>Ändern von Skripts  
Nachdem Sie die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder-SQL Azure Objekt Definitionen als Skript gespeichert haben, können Sie verwenden, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] um das Skript zu ändern.  
  
**So ändern Sie ein Skript**  
  
1.  Zeigen Sie im Menü [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Datei** auf **Öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  Suchen Sie im Dialogfeld **Öffnen** die Skriptdatei, und wählen Sie Sie aus, und klicken Sie dann auf **OK**.  
  
3.  Bearbeiten Sie die Skriptdatei mit dem Abfrage-Editor.  
  
    Weitere Informationen zum Abfrage-Editor finden Sie in der-Online Dokumentation unter "praktische Befehle und Features im Editor" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
4.  Um das Skript zu speichern, wählen Sie im Menü Datei die Option **Speichern**aus.  
  
### <a name="running-scripts"></a>Ausführen von Skripts  
Sie können in ein Skript oder einzelne Anweisungen ausführen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
**So führen Sie ein Skript aus**  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Zeigen Sie im Menü **Datei** auf **Öffnen** , und klicken Sie dann auf **Datei**.  
  
2.  Suchen Sie im Dialogfeld **Öffnen** die Skriptdatei, und wählen Sie Sie aus, und klicken Sie dann auf **OK**.  
  
3.  Drücken Sie die Taste **F5** , um das komplette Skript auszuführen.  
  
4.  Um einen Satz von-Anweisungen auszuführen, wählen Sie die Anweisungen im Abfrage-Editor-Fenster aus, und drücken Sie dann die Taste **F5** .  
  
Weitere Informationen zur Verwendung des Abfrage-Editors zum Ausführen von Skripts finden Sie unter " [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfrage" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Online Dokumentation.  
  
Sie können Skripts auch über die Befehlszeile ausführen, indem Sie das Hilfsprogramm **sqlcmd** und den- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent verwenden. Weitere Informationen zu **sqlcmd**finden Sie unter "sqlcmd Utility" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Online Dokumentation. Weitere Informationen zum- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent finden Sie unter "Automatisieren administrativer Aufgaben ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent)" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Online Dokumentation.  
  
## <a name="securing-objects-in-sql-server"></a>Sichern von Objekten in SQL Server  
Nachdem Sie die konvertierten Datenbankobjekte in geladen haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , können Sie Berechtigungen für diese Objekte erteilen und verweigern. Es empfiehlt sich, dies zu tun, bevor Sie Daten zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Informationen zum Sichern von Objekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter "Sicherheitsüberlegungen für Datenbanken und Datenbankanwendungen" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Online Dokumentation.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrations Vorgangs besteht darin, [Daten in SQL Server zu migrieren](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
