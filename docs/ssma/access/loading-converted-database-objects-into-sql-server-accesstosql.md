---
title: Loading Converted Database Objects into SQLServer (AccessToSQL) | Microsoft-Dokumentation
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
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9ab56815fa36f23a15bc646c69094c3ca2f5fa3e
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53204379"
---
# <a name="loading-converted-database-objects-into-sql-server-accesstosql"></a>Loading Converted Database Objects into SQLServer (AccessToSQL)
Nachdem Sie den Zugriff auf Datenbankobjekte, konvertiert haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, laden die daraus resultierende Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Sie können entweder SSMA, die die Objekte zu erstellen, oder Sie können Skripts für die Objekte und führen Sie die Skripts selbst. Darüber hinaus SSMA können Sie die Metadaten mit den eigentlichen Inhalt der aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbank.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Auswählen zwischen Synchronisierung und Skripts  
Wenn Sie die konvertierten Datenbankobjekten in laden möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure ohne Änderungen, können Sie SSMA direkt zu erstellen oder die Datenbankobjekte neu erstellt haben. Diese Methode ist schnell und einfach, aber es lässt sich nicht für die Anpassung der [!INCLUDE[tsql](../../includes/tsql-md.md)] Code, der definiert die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objekte, gespeicherte Prozeduren.  
  
Wenn Sie ändern möchten, die [!INCLUDE[tsql](../../includes/tsql-md.md)] , wird verwendet, um Objekte erstellen, oder wenn Sie mehr Kontrolle über die Objekte erstellen möchten, verwenden SSMA zum Erstellen von Skripts. Sie können dann ändern Sie diese Skripts, jedes Objekt einzeln erstellen und sogar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent planen, erstellen diese Objekte.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>Verwenden SSMA zum Synchronisieren von Objekten mit SQLServer  
Mit SSMA erstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbankobjekten, Sie wählen die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer, und klicken Sie dann zu synchronisieren der Objekte mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, wie im folgenden Verfahren dargestellt. Standardmäßig, wenn die Objekte noch in vorhanden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, wenn der SSMA-Metadaten enthält, einige lokale Änderungen oder Updates für die Definition dieser Objekte sehr, SSMA ändern, die Objektdefinitionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Sie können das Standardverhalten ändern, indem Sie die Bearbeitung **Projekteinstellungen**.  
  
> [!NOTE]  
> Sie können auswählen, vorhandene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbankobjekte, die aus Access-Datenbanken nicht konvertiert wurden. SSMA wird jedoch nicht neu erstellen oder ändern diese Objekte.  
  
**Zum Synchronisieren von Objekten mit SQL Server oder SQL Azure**  
  
1.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer, erweitern im oberen Bereich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Knoten, und erweitern Sie dann **Datenbanken**.  
  
2.  Wählen Sie die zu verarbeitenden Objekte aus:  
  
    -   Um eine vollständige Datenbank zu synchronisieren, wählen Sie das Kontrollkästchen neben dem Datenbanknamen.  
  
    -   Klicken Sie zum Synchronisieren, oder lassen Sie einzelne Objekte oder Kategorien von Objekten, aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben dem Objekt oder einen Ordner.  
  
3.  Nach Auswahl der Objekte in den Griff [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer mit der rechten Maustaste **Datenbanken**, und klicken Sie dann auf **synchronisieren mit der Datenbank**.  
  
    Sie können auch die einzelne Objekte oder Kategorien von Objekten synchronisieren, indem Sie mit der rechten Maustaste das Objekt oder der übergeordnete Ordner, und klicken Sie dann auf **synchronisieren mit der Datenbank**.  
  
    Danach SSMA zeigt die **synchronisieren mit der Datenbank** Dialogfeld hier Sie zwei Gruppen von Elementen sehen. Klicken Sie auf der linken Seite zeigt SSMA ausgewählte Datenbankobjekte in einer Struktur dargestellt. Klicken Sie auf der rechten Seite sehen Sie eine Struktur, die dieselben Objekte in der SSMA-Metadaten darstellt. Sie können die Struktur durch Klicken auf Links oder rechts erweitern Schaltfläche "+". Die Richtung der Synchronisierung wird in der Aktionsspalte zwischen die beiden Strukturen angeordnet wurden, angezeigt.  
  
    Eine Aktion anmelden können drei Zustände aufweisen:  
  
    -   Ein Pfeil nach links bedeutet, dass der Inhalt der Metadaten in der Datenbank (Standard) gespeichert werden soll.  
  
    -   Ein Pfeil nach rechts bedeutet, dass es sich bei Datenbankinhalte die SSMA-Metadaten überschrieben werden.  
  
    -   Ein Kreuz bedeutet, dass keine weitere Aktion durchgeführt wird.  
  
    Klicken Sie auf der Aktion zum Ändern des Zustands. Tatsächliche Synchronisierung wird durchgeführt, wenn Sie auf **OK** -Schaltfläche der **synchronisieren mit der Datenbank** Dialogfeld.  
  
## <a name="scripting-objects"></a>Skripterstellung für Objekte  
Wenn Sie speichern möchten [!INCLUDE[tsql](../../includes/tsql-md.md)] Definitionen von konvertierten Datenbankobjekten, oder Sie möchten, ändern die Objektdefinitionen und führen Sie Skripts selbst, können Sie die konvertierte Datenbank Objektdefinitionen zum Speichern [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts.  
  
**Um ein oder mehrere Objekte in ein Skript zu speichern.**  
  
1.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, erweitern Sie den obersten Knoten (Servername) und dann **Datenbanken**.  
  
2.  Führen Sie eine oder mehrere der folgenden:  
  
    -   Wählen Sie das Kontrollkästchen neben dem Datenbanknamen, damit ein Skript erstellt eine vollständige Datenbank.  
  
    -   Um das Skript aus, oder lassen Sie einzelne Ansichten, erweitern Sie die Datenbank und **Ansichten**, und klicken Sie dann aktivieren oder deaktivieren Sie das Kontrollkästchen neben der Ansicht.  
  
    -   Um das Skript aus, oder lassen Sie einzelne Tabellen, erweitern Sie die Datenbank und **Tabellen**, und klicken Sie dann aktivieren oder deaktivieren Sie das Kontrollkästchen neben der Tabelle.  
  
    -   Um das Skript aus, oder lassen Sie die einzelnen Indizes für eine Tabelle, erweitern Sie in der Tabelle und **Indizes**, und klicken Sie dann aktivieren oder deaktivieren den Index.  
  
3.  Mit der rechten Maustaste **Datenbanken** , und wählen Sie **speichern als Skript**.  
  
    Sie können auch Skripts für einzelne Objekte. Um das Skript für ein Objekt, unabhängig davon, welche Objekte ausgewählt sind, mit der rechten Maustaste in des Objekts, und wählen Sie **speichern als Skript**.  
  
4.  In der **speichern unter** Dialogfeld Suchen den Ordner, in dem Sie speichert das Skript, einen Dateinamen in geben möchten, die **Dateiname** ein, und klicken Sie dann auf **OK**.  
  
    SSMA wird die SQL-Dateinamenerweiterung angefügt.  
  
### <a name="modifying-scripts"></a>Ändern von Skripts  
Nachdem Sie gespeichert haben die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Objektdefinitionen als Skript enthält, können Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] das Skript ändern.  
  
**Um ein Skript zu ändern.**  
  
1.  Auf der [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] **Datei** Startmenü **öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  In der **öffnen** Dialogfeld Suchen wählen Sie die Skriptdatei, und klicken Sie dann auf **OK**.  
  
3.  Bearbeiten Sie die Skriptdatei mit dem abfrageeditor.  
  
    Weitere Informationen zu den Abfrage-Editor, finden Sie unter "-Editor der Einfachheit halber Befehle und Funktionen" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
4.  Wählen Sie zum Speichern des Skripts im Menü Datei **speichern**.  
  
### <a name="running-scripts"></a>Ausführen von Skripts  
Sie können ein Skript oder einzelne Anweisungen in ausführen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
**Zum Ausführen eines Skripts**  
  
1.  Auf der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Datei** Startmenü **öffnen** , und klicken Sie dann auf **Datei**.  
  
2.  In der **öffnen** Dialogfeld Suchen wählen Sie die Skriptdatei, und klicken Sie dann auf **OK**.  
  
3.  Um das vollständige Skript auszuführen, drücken Sie die **F5** Schlüssel.  
  
4.  Um einen Satz von Anweisungen auszuführen, wählen Sie die Anweisungen im Abfrage-Editor-Fenster, und drücken Sie dann die **F5** Schlüssel.  
  
Weitere Informationen dazu, wie Sie den Abfrage-Editor verwenden, um Skripts auszuführen, finden Sie unter " [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfrage" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
Sie können Skripts auch über die Befehlszeile ausführen, mit der **Sqlcmd** -Hilfsprogramm und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Weitere Informationen zu **Sqlcmd**, finden Sie unter "Hilfsprogramms" Sqlcmd"" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation. Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent finden Sie unter "Automatisieren von Verwaltungsaufgaben ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="securing-objects-in-sql-server"></a>Sichern die Objekte in SQLServer  
Nachdem Sie die konvertierten Datenbankobjekten in geladen haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Sie können die GRANT- und deny-Berechtigungen für diese Objekte. Es ist eine gute Idee, die vor der Migration dazu Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen zum Schützen von in Objekten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], finden Sie unter "Security Überlegungen zu Datenbanken und Datenbankanwendungen" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="next-step"></a>Nächster Schritt  
Im nächsten Schritt des Migrationsvorgangs [Migrieren von Daten in SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
