---
title: Laden von konvertierten Datenbankobjekten in SQL Server (mysqlto SQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ac993a6d-0283-4823-8793-6b217677dfa3
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 57a6f527da05c4f62d9055b70193af6ce74275f7
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935525"
---
# <a name="loading-converted-database-objects-into-sql-server-mysqltosql"></a>Laden konvertierter Datenbankobjekte in SQL Server (MySqlToSql)
Nachdem Sie MySQL-Datenbanken in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure konvertiert haben, können Sie die resultierenden Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure laden. Sie können entweder das SSMA-Objekt erstellen, oder Sie können Skripts für die Objekte erstellen und die Skripts selbst ausführen. Außerdem können Sie mit SSMA Ziel Metadaten mit dem tatsächlichen Inhalt von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank aktualisieren.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Zwischen Synchronisierung und Skripts auswählen  
Wenn Sie die konvertierten Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure ohne Änderungen laden möchten, können Sie die Datenbankobjekte von SSMA direkt erstellen oder neu erstellen. Diese Methode ist schnell und einfach, ermöglicht jedoch keine Anpassung des Transact-SQL-Codes, der die- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder-SQL Azure Objekte definiert.  
  
Wenn Sie Transact-SQL zum Erstellen von Objekten ändern möchten, oder wenn Sie mehr Kontrolle über die Objekt Erstellung haben möchten, verwenden Sie SSMA zum Erstellen von Skripts. Anschließend können Sie diese Skripts ändern, jedes Objekt einzeln erstellen und sogar SQL Server-Agent verwenden, um die Erstellung dieser Objekte zu planen.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>Verwenden von SSMA zum Synchronisieren von Objekten mit SQL Server  
Wenn Sie SSMA zum Erstellen SQL Server oder von Azure SQL-Datenbankobjekten verwenden möchten, wählen Sie die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure Metadaten-Explorer aus, und synchronisieren Sie dann die Objekte mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure, wie im folgenden Verfahren gezeigt. Wenn die Objekte bereits in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure vorhanden sind und die SSMA-Metadaten über lokale Änderungen oder Aktualisierungen der Definition dieser Objekte verfügen, ändert SSMA standardmäßig die Objekt Definitionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Sie können das Standardverhalten ändern, indem Sie die **Projekteinstellungen**bearbeiten.  
  
> [!NOTE]  
> Sie können vorhandene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbankobjekte auswählen, die nicht aus MySQL-Datenbanken konvertiert wurden. Diese Objekte werden jedoch nicht von SSMA neu erstellt oder geändert.  
  
##### <a name="to-synchronize-objects-with-sql-server-or-sql-azure"></a>So synchronisieren Sie Objekte mit SQL Server oder SQL Azure  
  
1.  Erweitern Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure metadatenexplorer den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Knoten oben oder SQL Azure, und erweitern Sie dann **Datenbanken**.  
  
2.  Wählen Sie die zu verarbeitenden Objekte aus:  
  
    -   Aktivieren Sie das Kontrollkästchen neben dem Datenbanknamen, um eine komplette Datenbank zu synchronisieren.  
  
    -   Aktivieren bzw. deaktivieren Sie das Kontrollkästchen neben dem Objekt oder Ordner, um einzelne Objekte oder Kategorien von Objekten zu synchronisieren oder auszulassen.  
  
3.  Nachdem Sie die zu verarbeitenden Objekte in SQL Server oder SQL Azure Metadaten-Explorer ausgewählt haben, klicken Sie mit der rechten Maustaste auf **Datenbanken**, und klicken Sie dann auf **mit Datenbank synchronisieren**.  
  
    Sie können einzelne Objekte oder Objektkategorien auch synchronisieren, indem Sie mit der rechten Maustaste auf das Objekt oder seinen übergeordneten Ordner klicken und dann auf **mit Datenbank synchronisieren**klicken.  
  
    Danach zeigt SSMA das Dialogfeld **mit Datenbank synchronisieren an** , in dem Sie zwei Gruppen von Elementen sehen können. Auf der linken Seite zeigt SSMA ausgewählte Datenbankobjekte an, die in einer Struktur dargestellt werden. Auf der rechten Seite sehen Sie eine Baumstruktur, die die gleichen Objekte in SSMA-Metadaten darstellt. Sie können die Struktur erweitern, indem Sie auf die Schaltfläche mit der rechten oder linken Schaltfläche klicken. Die Richtung der Synchronisierung wird in der Aktionsspalte angezeigt, die zwischen den beiden Strukturen platziert ist.  
  
    Ein Aktions Vorzeichen kann sich in den folgenden drei Zuständen befinden:  
  
    -   Der nach-links-Pfeil bedeutet, dass der Inhalt der Metadaten in der Datenbank gespeichert wird (Standardeinstellung).  
  
    -   Ein Pfeil nach rechts bedeutet, dass der Daten Bank Inhalt die SSMA-Metadaten überschreibt.  
  
    -   Ein Kreuzzeichen bedeutet, dass keine Aktion ausgeführt wird.  
  
    -   Klicken Sie auf das Aktions Zeichen, um den Status zu ändern. Die eigentliche Synchronisierung wird durchgeführt, wenn Sie im Dialogfeld **mit Datenbank synchronisieren** auf die Schaltfläche **OK** klicken.  
  
## <a name="scripting-objects"></a>Skripterstellung für Objekte  
Zum Speichern der [!INCLUDE[tsql](../../includes/tsql-md.md)] Definitionen der konvertierten Datenbankobjekte oder zum Ändern der Objekt Definitionen und zum Ausführen von Skripts können Sie die konvertierten Datenbankobjekt Definitionen in [!INCLUDE[tsql](../../includes/tsql-md.md)] Skripts speichern.  
  
**So speichern Sie Objekte als Skripts**  
  
1.  Nachdem Sie die zu speichernden Objekte in einem Skript ausgewählt haben, klicken Sie mit der rechten Maustaste auf **Datenbanken**, und klicken Sie dann auf **als Skript speichern**.  
  
    Sie können auch Skripts für einzelne Objekte oder Kategorien von Objekten erstellen, indem Sie mit der rechten Maustaste auf das Objekt oder seinen übergeordneten Ordner klicken und dann auf **als Skript speichern**klicken.  
  
2.  Suchen Sie im Dialogfeld **Speichern** unter den Ordner, in dem Sie das Skript speichern möchten, und geben Sie im Feld **Dateiname** einen Dateinamen ein. [!INCLUDE[clickOK](../../includes/clickok-md.md)] die Dateinamenerweiterung wird dann von SSMA angefügt.  
  
### <a name="modifying-scripts"></a>Ändern von Skripts  
Nachdem Sie die SQL Server oder SQL Azure Objekt Definitionen als Skript gespeichert haben, können Sie mit SQL Server Management Studio das Skript ändern.  
  
**So ändern Sie ein Skript**  
  
1.  Zeigen Sie im Menü Management Studio **Datei** auf **Öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  Suchen Sie im Dialogfeld Öffnen die Skriptdatei, und wählen Sie Sie aus, und klicken Sie dann auf **OK**.  
  
3.  Bearbeiten Sie die Skriptdatei mit dem Abfrage-Editor. Weitere Informationen zum Abfrage-Editor finden Sie unter "praktische Befehle und Features im Editor" in SQL Server-Onlinedokumentation.  
  
4.  Um das Skript zu speichern, wählen Sie im Menü Datei die Option **Speichern**aus.  
  
### <a name="running-scripts"></a>Ausführen von Skripts  
In SQL Server Management Studio können Sie ein Skript oder einzelne Anweisungen ausführen.  
  
**So führen Sie ein Skript aus**  
  
1.  Zeigen Sie im Menü SQL Server Management Studio **Datei** auf **Öffnen** , und klicken Sie dann auf **Datei**.  
  
2.  Suchen Sie im Dialogfeld Öffnen die Skriptdatei, und wählen Sie Sie aus, und klicken Sie dann auf **OK**.  
  
3.  Drücken Sie die Taste **F5** , um das komplette Skript auszuführen.  
  
4.  Um einen Satz von-Anweisungen auszuführen, wählen Sie die Anweisungen im Abfrage-Editor-Fenster aus, und drücken Sie dann die Taste **F5** .  
  
5.  Weitere Informationen zur Verwendung des Abfrage-Editors zum Ausführen von Skripts finden Sie unter "SQL Server Management Studio Transact-SQL-Abfrage" in SQL Server-Onlinedokumentation.  
  
6.  Sie können Skripts auch über die Befehlszeile ausführen, indem Sie das Hilfsprogramm **sqlcmd** und aus SQL Server-Agent verwenden. Weitere Informationen zu **sqlcmd**finden Sie unter "sqlcmd Utility" in SQL Server-Onlinedokumentation. Weitere Informationen zu SQL Server-Agent finden Sie im Thema zum Automatisieren administrativer Aufgaben (SQL Server-Agent) unter SQL Server-Onlinedokumentation.  
  
## <a name="securing-objects-in-sql-server"></a>Sichern von Objekten in SQL Server  
Nachdem Sie die konvertierten Datenbankobjekte in SQL Server geladen haben, können Sie Berechtigungen für diese Objekte erteilen und verweigern. Es empfiehlt sich, dies zu tun, bevor Sie Daten zu SQL Server migrieren. Informationen zum Sichern von Objekten in SQL Server finden Sie unter "Sicherheitsüberlegungen für Datenbanken und Datenbankanwendungen" in SQL Server-Onlinedokumentation.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrations Vorgangs ist das [Migrieren von MySQL-Daten in SQL Server Azure SQL-Datenbank &#40;mysqldesql&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von MySQL-Datenbanken zu SQL Server Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
