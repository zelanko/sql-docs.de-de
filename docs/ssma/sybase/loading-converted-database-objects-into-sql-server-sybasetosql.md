---
title: Loading Converted Database Objects into SQLServer (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Loading Converted Database Objects
ms.assetid: 4c59256f-99a8-4351-9559-a455813dbd06
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: dc57e695f4c54c9e788b917fe6e9c6a3f698f4bf
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2018
ms.locfileid: "38984362"
---
# <a name="loading-converted-database-objects-into-sql-server-sybasetosql"></a>Loading Converted Database Objects into SQLServer (SybaseToSQL)
Nachdem Sie die Datenbankobjekte Sybase Adaptive Server Enterprise (ASE) konvertiert haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure, laden die daraus resultierende Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure. Sie können entweder SSMA, die die Objekte zu erstellen, oder Sie können Skripts für die Objekte und führen Sie die Skripts selbst. Darüber hinaus SSMA können Sie die Metadaten mit den eigentlichen Inhalt der aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure-Datenbank.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Auswählen zwischen Synchronisierung und Skripts  
Wenn Sie die konvertierten Datenbankobjekten in laden möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SQL Azure ohne Änderung, Sie können auch SSMA direkt zu erstellen oder Neuerstellen von Datenbankobjekten. Diese Methode ist schnell und einfach, sondern lässt sich nicht für die Anpassung der [!INCLUDE[tsql](../../includes/tsql_md.md)] Code, der definiert die [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure-Objekte, gespeicherte Prozeduren.  
  
Wenn Sie ändern möchten die [!INCLUDE[tsql](../../includes/tsql_md.md)] dient zum Erstellen der Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure, oder wenn Sie möchten mehr Kontrolle über die Objekte in, wann und wie erstellt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure, mit der SSMA erstellt [!INCLUDE[tsql](../../includes/tsql_md.md)] Skripts. Sie können dann ändern Sie diese Skripts, jedes Objekt einzeln erstellen und sogar [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure-Agent planen, erstellen diese Objekte.  
  
## <a name="using-ssma-to-load-objects-into-sql-server-or-sql-azure"></a>Verwenden SSMA zum Laden von Objekten in SQLServer oder SQL Azure  
Mit SSMA erstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure-Datenbankobjekten, Sie wählen die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure-Metadaten-Explorer, und klicken Sie dann zu synchronisieren der Objekte mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure, wie im folgenden Verfahren dargestellt. Standardmäßig, wenn die Objekte noch in vorhanden [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure, wenn der SSMA-Metadaten enthält, einige lokale Änderungen oder Updates für die Definition dieser Objekte sehr, SSMA ändern, die Objektdefinitionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure. Sie können das Standardverhalten ändern, indem Sie die Bearbeitung **Projekteinstellungen**.  
  
> [!NOTE]  
> Sie können auswählen, vorhandene [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure-Datenbankobjekte, die von der ASE-Datenbanken nicht konvertiert wurden. Aber werden diese Objekte nicht neu erstellt oder geändert werden von SSMA.  
  
**Zum Synchronisieren von Objekten mit SQL Server oder SQL Azure**  
  
1.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure-Metadaten-Explorer, erweitern im oberen Bereich [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure-Knoten, und erweitern Sie dann **Datenbanken**.  
  
2.  Wählen Sie die zu verarbeitenden Objekte aus:  
  
    -   Um eine vollständige Datenbank zu synchronisieren, wählen Sie das Kontrollkästchen neben dem Datenbanknamen.  
  
    -   Klicken Sie zum Synchronisieren, oder lassen Sie einzelne Objekte oder Kategorien von Objekten, aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben dem Objekt oder einen Ordner.  
  
3.  Nach Auswahl der Objekte in den Griff [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure-Metadaten-Explorer mit der rechten Maustaste **Datenbanken**, und klicken Sie dann auf **synchronisieren mit der Datenbank**.  
  
    Sie können auch die einzelne Objekte oder Kategorien von Objekten synchronisieren, indem Sie mit der rechten Maustaste das Objekt oder der übergeordnete Ordner, und klicken Sie dann auf **synchronisieren mit der Datenbank**.  
  
    Danach SSMA zeigt die **synchronisieren mit der Datenbank** Dialogfeld hier Sie zwei Gruppen von Elementen sehen. Klicken Sie auf der linken Seite zeigt SSMA ausgewählte Datenbankobjekte in einer Struktur dargestellt. Klicken Sie auf der rechten Seite sehen Sie eine Struktur, die dieselben Objekte in der SSMA-Metadaten darstellt. Sie können die Struktur durch Klicken auf Links oder rechts erweitern Schaltfläche "+". Die Richtung der Synchronisierung wird in der Aktionsspalte zwischen die beiden Strukturen angeordnet wurden, angezeigt.  
  
    Eine Aktion anmelden können drei Zustände aufweisen:  
  
    -   Ein Pfeil nach links bedeutet, dass der Inhalt der Metadaten in der Datenbank (Standard) gespeichert werden soll.  
  
    -   Ein Pfeil nach rechts bedeutet, dass es sich bei Datenbankinhalte die SSMA-Metadaten überschrieben werden.  
  
    -   Ein Kreuz bedeutet, dass keine weitere Aktion durchgeführt wird.  
  
Klicken Sie auf der Aktion zum Ändern des Zustands. Tatsächliche Synchronisierung wird durchgeführt, wenn Sie auf **OK** -Schaltfläche der **synchronisieren mit der Datenbank** Dialogfeld.  
  
## <a name="scripting-objects"></a>Skripterstellung für Objekte  
Wenn Sie speichern möchten [!INCLUDE[tsql](../../includes/tsql_md.md)] Definitionen von konvertierten Datenbankobjekten, oder Sie möchten, ändern die Objektdefinitionen und führen Sie Skripts selbst, können Sie die konvertierte Datenbank Objektdefinitionen zum Speichern [!INCLUDE[tsql](../../includes/tsql_md.md)] Skripts.  
  
**Zum Speichern von Objekten wie Skripts**  
  
1.  Nachdem Sie die Objekte, die in einem Skript speichern ausgewählt haben, mit der rechten Maustaste **Datenbanken**, und wählen Sie dann **speichern als Skript**.  
  
    Sie können auch die einzelne Objekte oder Kategorien von Objekten schreiben, durch Rechtsklick auf das Objekt oder den enthaltenden Ordner aus, und wählen Sie dann **speichern Skripts**.  
  
2.  In der **speichern unter** Dialogfeld Suchen den Ordner, in dem Sie speichert das Skript, einen Dateinamen in geben möchten, die **Dateiname** ein, und klicken Sie dann auf **OK**.  
  
    SSMA wird die SQL-Dateinamenerweiterung angefügt.  
  
### <a name="modifying-scripts"></a>Ändern von Skripts  
Nachdem Sie gespeichert haben die [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oder SQL Azure-Objektdefinitionen als ein oder mehrere Skripts, können Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] anzeigen und ändern Sie die Skripts.  
  
**Um ein Skript zu ändern.**  
  
1.  Auf der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **Datei** Startmenü **öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  In der **öffnen** im Dialogfeld navigieren Sie zu und wählen Sie die Skriptdatei, und klicken Sie dann auf **OK**.  
  
3.  Bearbeiten und die Skriptdatei mit dem abfrageeditor.  
  
    Weitere Informationen zu den Abfrage-Editor, finden Sie unter "-Editor der Einfachheit halber Befehle und Funktionen" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Onlinedokumentation.  
  
4.  Wählen Sie zum Speichern des Skripts im Menü Datei **speichern**.  
  
### <a name="running-scripts"></a>Ausführen von Skripts  
Sie können ein Skript oder einzelne Anweisungen in ausführen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**Zum Ausführen eines Skripts**  
  
1.  Auf der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **Datei** Startmenü **öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  In der **öffnen** im Dialogfeld navigieren Sie zu und wählen Sie die Skriptdatei, und klicken Sie dann auf **OK**.  
  
3.  Um das vollständige Skript auszuführen, drücken Sie die **F5** Schlüssel.  
  
4.  Um einen Satz von Anweisungen auszuführen, wählen Sie die Anweisungen im Abfrage-Editor-Fenster, und drücken Sie dann die **F5** Schlüssel.  
  
Weitere Informationen dazu, wie Sie den Abfrage-Editor verwenden, um Skripts auszuführen, finden Sie unter "[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] [!INCLUDE[tsql](../../includes/tsql_md.md)] Abfrage" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Onlinedokumentation.  
  
Sie können Skripts auch über die Befehlszeile ausführen, mit der **Sqlcmd** -Hilfsprogramm und [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Weitere Informationen zu **Sqlcmd**, finden Sie unter "Hilfsprogramms" Sqlcmd"" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Onlinedokumentation. Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Agent finden Sie unter "Automatisieren von Verwaltungsaufgaben ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Onlinedokumentation.  
  
## <a name="securing-objects-in-sql-server"></a>Sichern die Objekte in SQLServer  
Nachdem Sie die konvertierten Datenbankobjekten in geladen haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], Sie können die GRANT- und deny-Berechtigungen für diese Objekte. Es ist eine gute Idee, die vor der Migration dazu Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Weitere Informationen zum Schützen von in Objekten [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], finden Sie unter "Security Überlegungen zu Datenbanken und Datenbankanwendungen" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] -Onlinedokumentation.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrationsvorgangs besteht darin [Migrieren von Sybase ASE-Daten in SQL Server / SQL Azure(SybaseToSQL)](http://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Sybase ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
