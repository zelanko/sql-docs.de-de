---
title: Laden von konvertierten Datenbankobjekten in SQL Server (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7af5566094c9cc4c40ba2aa33f27e79bae1c7445
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68141027"
---
# <a name="loading-converted-database-objects-into-sql-server-db2tosql"></a>Laden von konvertierten Datenbankobjekten in SQL Server (DB2ToSQL)
Nachdem Sie DB2-Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]konvertiert haben, können Sie die resultierenden Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in laden. Sie können entweder das SSMA-Objekt erstellen, oder Sie können Skripts für die Objekte erstellen und die Skripts selbst ausführen. Außerdem können Sie mit SSMA Ziel Metadaten mit dem tatsächlichen Inhalt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank aktualisieren.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Zwischen Synchronisierung und Skripts auswählen  
Wenn Sie die konvertierten Datenbankobjekte ohne Änderungen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in laden möchten, können Sie die Datenbankobjekte von SSMA direkt erstellen oder neu erstellen. Diese Methode ist schnell und einfach, lässt jedoch nicht zu, dass der [!INCLUDE[tsql](../../includes/tsql-md.md)] Code, der die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte definiert, außer gespeicherten Prozeduren angepasst wird.  
  
Wenn Sie das ändern möchten, [!INCLUDE[tsql](../../includes/tsql-md.md)] das zum Erstellen von-Objekten verwendet wird, oder wenn Sie mehr Kontrolle über die Objekt Erstellung haben möchten, verwenden Sie SSMA zum Erstellen von-Skripts. Anschließend können Sie diese Skripts ändern, jedes Objekt einzeln erstellen und sogar den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent verwenden, um die Erstellung dieser Objekte zu planen.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>Verwenden von SSMA zum Synchronisieren von Objekten mit SQL Server  
Wenn Sie SSMA zum Erstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Datenbankobjekten verwenden möchten, wählen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie die Objekte im metadatenexplorer aus, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]und synchronisieren Sie dann die Objekte mit, wie im folgenden Verfahren gezeigt. Wenn die Objekte bereits in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vorhanden sind und die SSMA-Metadaten neuer als das Objekt in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]sind, ändert SSMA standardmäßig die Objekt Definitionen in. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie können das Standardverhalten ändern, indem Sie die **Projekteinstellungen**bearbeiten.  
  
> [!NOTE]  
> Sie können vorhandene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbankobjekte auswählen, die nicht aus DB2-Datenbanken konvertiert wurden. Diese Objekte werden jedoch nicht von SSMA neu erstellt oder geändert.  
  
**So synchronisieren Sie Objekte mit SQL Server**  
  
1.  Erweitern [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie im metadatenexplorer den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] obersten Knoten, und erweitern Sie dann **Datenbanken**.  
  
2.  Wählen Sie die zu verarbeitenden Objekte aus:  
  
    -   Aktivieren Sie das Kontrollkästchen neben dem Datenbanknamen, um eine komplette Datenbank zu synchronisieren.  
  
    -   Aktivieren bzw. deaktivieren Sie das Kontrollkästchen neben dem Objekt oder Ordner, um einzelne Objekte oder Kategorien von Objekten zu synchronisieren oder auszulassen.  
  
3.  Nachdem Sie die zu verarbeitenden Objekte im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] metadatenexplorer ausgewählt haben, klicken Sie mit der rechten Maustaste auf **Datenbanken**, und klicken Sie dann auf **mit Datenbank synchronisieren**.  
  
    Sie können einzelne Objekte oder Objektkategorien auch synchronisieren, indem Sie mit der rechten Maustaste auf das Objekt oder seinen übergeordneten Ordner klicken und dann auf **mit Datenbank synchronisieren**klicken.  
  
    Danach zeigt SSMA das Dialogfeld **mit Datenbank synchronisieren an** , in dem Sie zwei Gruppen von Elementen sehen können. Auf der linken Seite zeigt SSMA ausgewählte Datenbankobjekte an, die in einer Struktur dargestellt werden. Auf der rechten Seite sehen Sie eine Baumstruktur, die die gleichen Objekte in SSMA-Metadaten darstellt. Sie können die Struktur erweitern, indem Sie auf die Schaltfläche mit der rechten oder linken Schaltfläche klicken. Die Richtung der Synchronisierung wird in der Aktionsspalte angezeigt, die zwischen den beiden Strukturen platziert ist.  
  
    Ein Aktions Vorzeichen kann drei Zustände aufweisen:  
  
    -   Der nach-links-Pfeil bedeutet, dass der Inhalt der Metadaten in der Datenbank gespeichert wird (Standardeinstellung).  
  
    -   Ein Pfeil nach rechts bedeutet, dass der Daten Bank Inhalt die SSMA-Metadaten überschreibt.  
  
    -   Ein Kreuzzeichen bedeutet, dass keine Aktion ausgeführt wird.  
  
Klicken Sie auf das Aktions Zeichen, um den Status zu ändern. Die eigentliche Synchronisierung wird durchgeführt, wenn Sie im Dialogfeld **mit Datenbank synchronisieren** auf die Schaltfläche **OK** klicken.  
  
## <a name="scripting-objects"></a>Skripterstellung für Objekte  
Zum Speichern [!INCLUDE[tsql](../../includes/tsql-md.md)] der Definitionen der konvertierten Datenbankobjekte oder zum Ändern der Objekt Definitionen und zum Ausführen von Skripts können Sie die konvertierten Daten Bank [!INCLUDE[tsql](../../includes/tsql-md.md)] Objekt Definitionen in Skripts speichern.  
  
**So speichern Sie Objekte als Skripts**  
  
1.  Nachdem Sie die zu speichernden Objekte in einem Skript ausgewählt haben, klicken Sie mit der rechten Maustaste auf **Datenbanken**, und klicken Sie dann auf **als Skript speichern**.  
  
    Sie können auch Skripts für einzelne Objekte oder Kategorien von Objekten erstellen, indem Sie mit der rechten Maustaste auf das Objekt oder seinen übergeordneten Ordner klicken und dann auf **als Skript speichern**klicken.  
  
2.  Suchen Sie im Dialogfeld **Speichern** unter den Ordner, in dem Sie das Skript speichern möchten, geben Sie im Feld **Dateiname** einen Dateinamen ein, [!INCLUDE[clickOK](../../includes/clickok-md.md)]und klicken Sie dann auf. SSMA fügt die Dateinamenerweiterung ". SQL" an.  
  
### <a name="modifying-scripts"></a>Ändern von Skripts  
Nachdem Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekt Definitionen als ein oder mehrere Skripts gespeichert haben, können Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden, um die Skripts anzuzeigen und zu ändern.  
  
**So ändern Sie ein Skript**  
  
1.  Zeigen Sie im Menü [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Datei** auf **Öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  Wählen Sie im Dialogfeld **Öffnen** die Skriptdatei aus, und klicken Sie dann auf OK.
  
3.  Bearbeiten Sie die Skriptdatei mit dem Abfrage-Editor.  
  
    Weitere Informationen zum Abfrage-Editor finden Sie in der-Online Dokumentation unter "praktische Befehle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Features im Editor".  
  
4.  Um das Skript zu speichern, klicken Sie im Menü Datei auf **Speichern**.  
  
### <a name="running-scripts"></a>Ausführen von Skripts  
Sie können in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ein Skript oder einzelne Anweisungen ausführen.  
  
**So führen Sie ein Skript aus**  
  
1.  Zeigen Sie im Menü [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Datei** auf **Öffnen**, und klicken Sie dann auf **Datei**.  
  
2.  Wählen Sie im Dialogfeld **Öffnen** die Skriptdatei aus, und klicken Sie dann auf[!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  Drücken Sie die Taste **F5** , um das komplette Skript auszuführen.  
  
4.  Um einen Satz von-Anweisungen auszuführen, wählen Sie die Anweisungen im Abfrage-Editor-Fenster aus, und drücken Sie dann die Taste **F5** .  
  
Weitere Informationen zur Verwendung des Abfrage-Editors zum Ausführen von Skripts finden Sie unter [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] "Abfrage" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der-Online Dokumentation.  
  
Sie können Skripts auch über die Befehlszeile ausführen, indem Sie das Hilfsprogramm **sqlcmd** und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Agent verwenden. Weitere Informationen zu **sqlcmd**finden Sie unter "sqlcmd Utility" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der-Online Dokumentation. Weitere Informationen zum- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent finden Sie unter "Automatisieren administrativer Aufgaben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (Agent)" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der-Online Dokumentation.  
  
## <a name="securing-objects-in-sql-server"></a>Sichern von Objekten in SQL Server  
Nachdem Sie die konvertierten Datenbankobjekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]geladen haben, können Sie Berechtigungen für diese Objekte erteilen und verweigern. Es empfiehlt sich, dies zu tun, bevor Sie Daten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]migrieren. Informationen zum Sichern von Objekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]finden Sie unter "Sicherheitsüberlegungen für Datenbanken und Datenbankanwendungen" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in der-Online Dokumentation.  
  
## <a name="next-step"></a>Nächster Schritt  
Der nächste Schritt des Migrations Vorgangs besteht darin, [DB2-Daten in SQL Server zu migrieren](https://msdn.microsoft.com/86cbd39f-6dac-409a-9ce1-7dd54403f84b).  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von DB2-Daten in SQL Server &#40;DB2ToSQL-&#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
