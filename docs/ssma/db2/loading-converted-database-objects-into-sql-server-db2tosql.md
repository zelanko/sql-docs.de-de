---
title: Loading Converted Database Objects into SQLServer (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 21962c8849204db6f3e5f114b6f8f86994d53b35
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63298844"
---
# <a name="loading-converted-database-objects-into-sql-server-db2tosql"></a>Loading Converted Database Objects into SQLServer (DB2ToSQL)
Nachdem Sie die DB2-Schemas zu konvertiert haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], können Sie die resultierende Datenbankobjekte in laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können entweder SSMA, die die Objekte zu erstellen, oder Sie können Skripts für die Objekte und führen Sie die Skripts selbst. Darüber hinaus SSMA können Sie die Metadaten mit den eigentlichen Inhalt der aktualisieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Auswählen zwischen Synchronisierung und Skripts  
Wenn Sie die konvertierten Datenbankobjekten in laden möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ohne Änderung können Sie SSMA direkt zu erstellen oder die Datenbankobjekte neu erstellt haben. Diese Methode ist schnell und einfach, aber es lässt sich nicht für die Anpassung der [!INCLUDE[tsql](../../includes/tsql-md.md)] Code, der definiert die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte, gespeicherte Prozeduren.  
  
Wenn Sie ändern möchten, die [!INCLUDE[tsql](../../includes/tsql-md.md)] , wird verwendet, um Objekte erstellen, oder wenn Sie mehr Kontrolle über die Objekte erstellen möchten, verwenden SSMA zum Erstellen von Skripts. Sie können dann ändern Sie diese Skripts, jedes Objekt einzeln erstellen und sogar [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent planen, erstellen diese Objekte.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>Verwenden SSMA zum Synchronisieren von Objekten mit SQLServer  
Mit SSMA erstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbankobjekte, die Sie auswählen, dass die Objekte im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, und klicken Sie dann zu synchronisieren der Objekte mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], wie im folgenden Verfahren dargestellt. Standardmäßig, wenn die Objekte noch in vorhanden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und wenn die SSMA-Metadaten neuer ist als das Objekt im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA ändern, die Objektdefinitionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können das Standardverhalten ändern, indem Sie die Bearbeitung **Projekteinstellungen**.  
  
> [!NOTE]  
> Sie können auswählen, vorhandene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankobjekten, die vom DB2-Datenbanken nicht konvertiert wurden. Aber werden diese Objekte nicht neu erstellt oder geändert werden von SSMA.  
  
**Zum Synchronisieren von Objekten mit SQL Server**  
  
1.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, erweitern Sie im oberen Bereich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Knoten, und erweitern Sie dann **Datenbanken**.  
  
2.  Wählen Sie die zu verarbeitenden Objekte aus:  
  
    -   Um eine vollständige Datenbank zu synchronisieren, wählen Sie das Kontrollkästchen neben dem Datenbanknamen.  
  
    -   Klicken Sie zum Synchronisieren, oder lassen Sie einzelne Objekte oder Kategorien von Objekten, aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben dem Objekt oder einen Ordner.  
  
3.  Nach Auswahl der Objekte in den Griff [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer mit der rechten Maustaste **Datenbanken**, und klicken Sie dann auf **synchronisieren mit der Datenbank**.  
  
    Sie können auch die einzelne Objekte oder Kategorien von Objekten synchronisieren, indem Sie mit der rechten Maustaste das Objekt oder der übergeordnete Ordner, und klicken Sie dann auf **synchronisieren mit der Datenbank**.  
  
    Danach SSMA zeigt die **synchronisieren mit der Datenbank** Dialogfeld hier Sie zwei Gruppen von Elementen sehen. Klicken Sie auf der linken Seite zeigt SSMA ausgewählte Datenbankobjekte in einer Struktur dargestellt. Klicken Sie auf der rechten Seite sehen Sie eine Struktur, die dieselben Objekte in der SSMA-Metadaten darstellt. Sie können die Struktur durch Klicken auf Links oder rechts erweitern Schaltfläche "+". Die Richtung der Synchronisierung wird in der Aktionsspalte zwischen die beiden Strukturen angeordnet wurden, angezeigt.  
  
    Eine Aktion anmelden können drei Zustände aufweisen:  
  
    -   Ein Pfeil nach links bedeutet, dass der Inhalt der Metadaten in der Datenbank (Standard) gespeichert werden soll.  
  
    -   Ein Pfeil nach rechts bedeutet, dass es sich bei Datenbankinhalte die SSMA-Metadaten überschrieben werden.  
  
    -   Ein Kreuz bedeutet, dass keine weitere Aktion durchgeführt wird.  
  
Klicken Sie auf der Aktion zum Ändern des Zustands. Tatsächliche Synchronisierung wird durchgeführt, wenn Sie auf **OK** -Schaltfläche der **synchronisieren mit der Datenbank** Dialogfeld.  
  
## <a name="scripting-objects"></a>Skripterstellung für Objekte  
Zum Speichern [!INCLUDE[tsql](../../includes/tsql-md.md)] Definitionen der konvertierten Datenbankobjekte, um die Objektdefinitionen ändern und Ausführen von Skripts selbst, können Sie speichern die konvertierte Datenbank Objektdefinitionen, [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts.  
  
**Zum Speichern von Objekten wie Skripts**  
  
1.  Nachdem Sie die Objekte, die in einem Skript speichern ausgewählt haben, mit der rechten Maustaste **Datenbanken**, und klicken Sie dann auf **speichern als Skript**.  
  
    Sie können auch einzelne Objekte oder Kategorien von Objekten von der rechten Maustaste auf das Objekt oder der übergeordnete Ordner, und klicken Sie dann auf Skripts **speichern als Skript**.  
  
2.  In der **speichern** Dialogfeld Suchen den Ordner, in der Sie speichert das Skript, einen Dateinamen in eingeben möchten, die **Dateiname** Feld, und klicken Sie dann [!INCLUDE[clickOK](../../includes/clickok-md.md)]. SSMA wird die SQL-Dateinamenerweiterung angefügt.  
  
### <a name="modifying-scripts"></a>Ändern von Skripts  
Nachdem Sie gespeichert haben die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objektdefinitionen als ein oder mehrere Skripts, können Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] anzeigen und ändern Sie die Skripts.  
  
**Um ein Skript zu ändern.**  
  
1.  Auf der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Datei** Startmenü **öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  In der **öffnen** Dialogfeld Wählen Sie die Skriptdatei, und klicken Sie dann auf OK.
  
3.  Bearbeiten Sie die Skriptdatei mit dem abfrageeditor.  
  
    Weitere Informationen zu den Abfrage-Editor, finden Sie unter "-Editor der Einfachheit halber Befehle und Funktionen" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
4.  Speichern Sie das Skript auf im Menü Datei auf **speichern**.  
  
### <a name="running-scripts"></a>Ausführen von Skripts  
Sie können ein Skript oder einzelne Anweisungen in ausführen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
**Zum Ausführen eines Skripts**  
  
1.  Auf der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Datei** Startmenü **öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  In der **öffnen** Dialogfeld Wählen Ihre Skriptdatei, und klicken Sie dann [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  Um das vollständige Skript auszuführen, drücken Sie die **F5** Schlüssel.  
  
4.  Um einen Satz von Anweisungen auszuführen, wählen Sie die Anweisungen im Abfrage-Editor-Fenster, und drücken Sie dann die **F5** Schlüssel.  
  
Weitere Informationen dazu, wie Sie den Abfrage-Editor verwenden, um Skripts auszuführen, finden Sie unter " [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfrage" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
Sie können Skripts auch über die Befehlszeile ausführen, mit der **Sqlcmd** -Hilfsprogramm und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Weitere Informationen zu **Sqlcmd**, finden Sie unter "Hilfsprogramms" Sqlcmd"" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation. Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent finden Sie unter "Automatisieren von Verwaltungsaufgaben ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="securing-objects-in-sql-server"></a>Sichern die Objekte in SQLServer  
Nachdem Sie die konvertierten Datenbankobjekten in geladen haben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Sie können die GRANT- und deny-Berechtigungen für diese Objekte. Es ist eine gute Idee, die vor der Migration dazu Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen zum Schützen von in Objekten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], finden Sie unter "Security Überlegungen zu Datenbanken und Datenbankanwendungen" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrationsvorgangs besteht darin [DB2-Daten in SQL Server Migration](https://msdn.microsoft.com/86cbd39f-6dac-409a-9ce1-7dd54403f84b).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von DB2-Daten in SQLServer &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
