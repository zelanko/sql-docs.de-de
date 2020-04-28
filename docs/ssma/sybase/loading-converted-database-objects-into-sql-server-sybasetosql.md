---
title: Laden von konvertierten Datenbankobjekten in SQL Server (sybaseto SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Loading Converted Database Objects
ms.assetid: 4c59256f-99a8-4351-9559-a455813dbd06
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5185e8b1364fe2a5bae92c40c99e8f52bcd32ba7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68028929"
---
# <a name="loading-converted-database-objects-into-sql-server-sybasetosql"></a>Laden von konvertierten Datenbankobjekten in SQL Server (SybaseToSQL)
Nachdem Sie die Datenbankobjekte von Sybase Adaptive Server Enterprise (ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ) in oder SQL Azure konvertiert haben, können Sie die resultierenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbankobjekte in oder SQL Azure laden. Sie können entweder das SSMA-Objekt erstellen, oder Sie können Skripts für die Objekte erstellen und die Skripts selbst ausführen. Außerdem können Sie mit SSMA Ziel Metadaten mit dem tatsächlichen Inhalt von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Datenbank aktualisieren.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Zwischen Synchronisierung und Skripts auswählen  
Wenn Sie die konvertierten Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure ohne Änderungen laden möchten, können Sie die Datenbankobjekte von SSMA direkt erstellen oder neu erstellen. Diese Methode ist schnell und einfach, lässt jedoch nicht zu, dass der [!INCLUDE[tsql](../../includes/tsql-md.md)] Code, der die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -oder-SQL Azure Objekte definiert, außer gespeicherten Prozeduren angepasst wird.  
  
Wenn Sie [!INCLUDE[tsql](../../includes/tsql-md.md)] das ändern möchten, das zum Erstellen der Objekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in oder SQL Azure wird, oder wenn Sie mehr Kontrolle darüber haben möchten, wann und wie die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure erstellt werden, verwenden Sie SSMA [!INCLUDE[tsql](../../includes/tsql-md.md)] zum Erstellen von Skripts. Anschließend können Sie diese Skripts ändern, jedes Objekt einzeln erstellen und sogar oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure-Agent verwenden, um die Erstellung dieser Objekte zu planen.  
  
## <a name="using-ssma-to-load-objects-into-sql-server-or-sql-azure"></a>Verwenden von SSMA zum Laden von Objekten in SQL Server oder SQL Azure  
Wenn Sie SSMA zum Erstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure von Datenbankobjekten verwenden möchten, wählen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie die Objekte in oder SQL Azure Metadaten-Explorer aus, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und synchronisieren Sie dann die Objekte mit oder SQL Azure, wie im folgenden Verfahren gezeigt. Wenn die Objekte bereits in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure vorhanden sind und die SSMA-Metadaten über lokale Änderungen oder Aktualisierungen der Definition dieser Objekte verfügen, ändert SSMA standardmäßig die Objekt Definitionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Sie können das Standardverhalten ändern, indem Sie die **Projekteinstellungen**bearbeiten.  
  
> [!NOTE]  
> Sie können vorhandene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Datenbankobjekte auswählen, die nicht aus ASE-Datenbanken konvertiert wurden. Diese Objekte werden jedoch nicht von SSMA neu erstellt oder geändert.  
  
**So synchronisieren Sie Objekte mit SQL Server oder SQL Azure**  
  
1.  Erweitern [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie in oder SQL Azure metadatenexplorer den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Knoten oben oder SQL Azure, und erweitern Sie dann **Datenbanken**.  
  
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
Wenn Sie Definitionen der konvertierten Datenbankobjekte speichern [!INCLUDE[tsql](../../includes/tsql-md.md)] oder die Objekt Definitionen ändern und Skripts selbst ausführen möchten, können Sie die konvertierten Datenbankobjekt Definitionen in [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts speichern.  
  
**So speichern Sie Objekte als Skripts**  
  
1.  Nachdem Sie die zu speichernden Objekte in einem Skript ausgewählt haben, klicken Sie mit der rechten Maustaste auf **Datenbanken**, und wählen Sie dann **als Skript speichern**aus.  
  
    Sie können auch Skripts für einzelne Objekte oder Kategorien von Objekten erstellen, indem Sie mit der rechten Maustaste auf das Objekt oder den enthaltenden Ordner klicken und anschließend **Skript speichern**auswählen.  
  
2.  Suchen Sie im Dialogfeld **Speichern** unter den Ordner, in dem Sie das Skript speichern möchten, geben Sie im Feld **Dateiname** einen Dateinamen ein, und klicken Sie dann auf **OK**.  
  
    SSMA fügt die Dateinamenerweiterung ". SQL" an.  
  
### <a name="modifying-scripts"></a>Ändern von Skripts  
Nachdem Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -oder-SQL Azure Objekt Definitionen als ein oder mehrere Skripts gespeichert haben, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] können Sie verwenden, um die Skripts anzuzeigen und zu ändern.  
  
**So ändern Sie ein Skript**  
  
1.  Zeigen Sie im Menü [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Datei** auf **Öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  Navigieren Sie im Dialogfeld **Öffnen** zu Ihrer Skriptdatei, und wählen Sie Sie aus, und klicken Sie dann auf **OK**.  
  
3.  Bearbeiten Sie die Skriptdatei mit dem-Abfrage-Editor.  
  
    Weitere Informationen zum Abfrage-Editor finden Sie in der-Online Dokumentation unter "praktische Befehle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Features im Editor".  
  
4.  Um das Skript zu speichern, wählen Sie im Menü Datei die Option **Speichern**aus.  
  
### <a name="running-scripts"></a>Ausführen von Skripts  
Sie können in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ein Skript oder einzelne Anweisungen ausführen.  
  
**So führen Sie ein Skript aus**  
  
1.  Zeigen Sie im Menü [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Datei** auf **Öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  Navigieren Sie im Dialogfeld **Öffnen** zu Ihrer Skriptdatei, und wählen Sie Sie aus, und klicken Sie dann auf **OK**.  
  
3.  Drücken Sie die Taste **F5** , um das komplette Skript auszuführen.  
  
4.  Um einen Satz von-Anweisungen auszuführen, wählen Sie die Anweisungen im Abfrage-Editor-Fenster aus, und drücken Sie dann die Taste **F5** .  
  
Weitere Informationen zur Verwendung des Abfrage-Editors zum Ausführen von Skripts finden Sie unter [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] "Abfrage" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der-Online Dokumentation.  
  
Sie können Skripts auch über die Befehlszeile ausführen, indem Sie das Hilfsprogramm **sqlcmd** und den- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent verwenden. Weitere Informationen zu **sqlcmd**finden Sie unter "sqlcmd Utility" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der-Online Dokumentation. Weitere Informationen zum- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent finden Sie unter "Automatisieren administrativer Aufgaben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Agent)" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der-Online Dokumentation.  
  
## <a name="securing-objects-in-sql-server"></a>Sichern von Objekten in SQL Server  
Nachdem Sie die konvertierten Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]geladen haben, können Sie Berechtigungen für diese Objekte erteilen und verweigern. Es empfiehlt sich, dies zu tun, bevor Sie Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]migrieren. Informationen zum Sichern von Objekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]finden Sie unter "Sicherheitsüberlegungen für Datenbanken und Datenbankanwendungen" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der-Online Dokumentation.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrations Vorgangs ist die Migration von [Sybase ASE-Daten in SQL Server/SQL Azure (sybasedesql)](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von Sybase ASE-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;sybaseto SQL-&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
