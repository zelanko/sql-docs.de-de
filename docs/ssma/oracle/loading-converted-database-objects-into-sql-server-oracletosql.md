---
title: Loading Converted Database Objects into SQLServer (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Synchronization, Securing Objects in SQL Server
- Synchronization,Scripting Objects
ms.assetid: a8ae33b2-1883-4785-922b-ea0e31c0b37a
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 57d66d48591304d5481cb86c7418ed0ac27051db
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53204939"
---
# <a name="loading-converted-database-objects-into-sql-server-oracletosql"></a>Laden konvertierter Datenbankobjekte in SQL Server (OracleToSQL)
Nachdem Sie die Oracle-Schemas zu SQL Server konvertiert haben, können Sie die resultierenden Datenbankobjekte in SQL Server laden. Sie können entweder SSMA, die die Objekte zu erstellen, oder Sie können Skripts für die Objekte und führen Sie die Skripts selbst. Darüber hinaus können mit SSMA Sie Metadaten mit den eigentlichen Inhalt der SQL Server-Datenbank zu aktualisieren.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Auswählen zwischen Synchronisierung und Skripts  
Wenn Sie die konvertierten Datenbankobjekten in SQL Server ohne Änderungen zu laden möchten, haben Sie SSMA direkt zu erstellen oder die Datenbankobjekte neu erstellt. Dass die Methode kann schnell und einfach, aber es lässt sich nicht für die Anpassung der [!INCLUDE[tsql](../../includes/tsql-md.md)] Code, der die SQL Server-Objekte, gespeicherter Prozeduren definiert.  
  
Wenn Sie ändern möchten, die [!INCLUDE[tsql](../../includes/tsql-md.md)] , wird verwendet, um Objekte erstellen, oder wenn Sie mehr Kontrolle über die Objekte erstellen möchten, verwenden SSMA zum Erstellen von Skripts. Sie können dann diese Skripts ändern, jedes Objekt einzeln erstellen und sogar Verwenden von SQL Server-Agent planen, erstellen diese Objekte.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>Verwenden SSMA zum Synchronisieren von Objekten mit SQLServer  
Um SSMA verwenden, um SQL Server-Datenbankobjekte zu erstellen, wählen Sie die Objekte in SQL Server-Metadaten-Explorer, und synchronisieren Sie die Objekte mit SQL Server, wie im folgenden Verfahren dargestellt. Standardmäßig wird, wenn die Objekte in SQL Server bereits vorhanden sind, und wenn die SSMA-Metadaten neuer ist als das Objekt in SQL Server SSMA die Objektdefinitionen in SQL Server geändert werden. Sie können das Standardverhalten ändern, indem Sie die Bearbeitung **Projekteinstellungen**.  
  
> [!NOTE]  
> Sie können vorhandene SQL Server-Datenbankobjekte auswählen, die aus Oracle-Datenbanken nicht konvertiert wurden. Aber werden diese Objekte nicht neu erstellt oder geändert werden von SSMA.  
  
**Zum Synchronisieren von Objekten mit SQL Server**  
  
1.  In SQL Server-Metadaten-Explorer, erweitern Sie den obersten Knoten des SQL Server, und dann **Datenbanken**.  
  
2.  Wählen Sie die zu verarbeitenden Objekte aus:  
  
    -   Um eine vollständige Datenbank zu synchronisieren, wählen Sie das Kontrollkästchen neben dem Datenbanknamen.  
  
    -   Klicken Sie zum Synchronisieren, oder lassen Sie einzelne Objekte oder Kategorien von Objekten, aktivieren Sie oder deaktivieren Sie das Kontrollkästchen neben dem Objekt oder einen Ordner.  
  
3.  Nachdem Sie die zu verarbeitenden in SQL Server-Metadaten-Explorer Objekte ausgewählt haben, mit der rechten Maustaste **Datenbanken**, und klicken Sie dann auf **synchronisieren mit der Datenbank**.  
  
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
  
2.  In der **speichern** Dialogfeld Suchen den Ordner, in der Sie speichert das Skript, einen Dateinamen in eingeben möchten, die **Dateiname** ein, und klicken Sie dann auf OK SSMA wird die SQL-Dateinamenerweiterung angefügt.  
  
### <a name="modifying-scripts"></a>Ändern von Skripts  
Nachdem Sie die SQL Server-Objektdefinitionen als ein oder mehrere Skripts gespeichert haben, können Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] anzeigen und ändern Sie die Skripts.  
  
**Um ein Skript zu ändern.**  
  
1.  Auf der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Datei** Startmenü **öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  In der **öffnen** Dialogfeld Wählen Sie die Skriptdatei und dann auf OK.
  
3.  Bearbeiten Sie die Skriptdatei mit dem abfrageeditor.  
  
    Weitere Informationen zu den Abfrage-Editor finden Sie unter "-Editor der Einfachheit halber Befehle und Funktionen" in SQL Server-Onlinedokumentation.  
  
4.  Speichern Sie das Skript auf im Menü Datei auf **speichern**.  
  
### <a name="running-scripts"></a>Ausführen von Skripts  
Sie können ein Skript oder einzelne Anweisungen in ausführen [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
**Zum Ausführen eines Skripts**  
  
1.  Auf der [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Datei** Startmenü **öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  In der **öffnen** Dialogfeld Wählen Sie die Skriptdatei, und klicken Sie dann auf OK  
  
3.  Um das vollständige Skript auszuführen, drücken Sie die **F5** Schlüssel.  
  
4.  Um einen Satz von Anweisungen auszuführen, wählen Sie die Anweisungen im Abfrage-Editor-Fenster, und drücken Sie dann die **F5** Schlüssel.  
  
Weitere Informationen dazu, wie Sie den Abfrage-Editor verwenden, um Skripts auszuführen, finden Sie unter " [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfrage" in SQL Server-Onlinedokumentation.  
  
Sie können Skripts auch über die Befehlszeile ausführen, mit der **Sqlcmd** -Hilfsprogramm, und von SQL Server-Agent. Weitere Informationen zu **Sqlcmd**, finden Sie unter "Hilfsprogramms" Sqlcmd"" in SQL Server-Onlinedokumentation. Weitere Informationen zu SQL Server-Agent finden Sie unter "Automatisieren von administrativen Tasks (SQL Server-Agent)" in SQL Server-Onlinedokumentation.  
  
## <a name="securing-objects-in-sql-server"></a>Sichern die Objekte in SQLServer  
Nachdem Sie die konvertierten Datenbankobjekten in SQL Server geladen haben, können Sie erteilen und Verweigern von Berechtigungen für diese Objekte. Es ist eine gute Idee, klicken Sie hierzu vor dem Migrieren von Daten in SQL Server. Informationen dazu, wie Sie sichere Objekte in SQL Server-Hilfe finden Sie unter "Security Überlegungen zu Datenbanken und Datenbankanwendungen" in SQL Server-Onlinedokumentation.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrationsvorgangs besteht darin [Migrieren von Daten in SQL Server](migrating-oracle-data-into-sql-server-oracletosql.md).  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Oracle zu SQLServer-Datenbanken &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
