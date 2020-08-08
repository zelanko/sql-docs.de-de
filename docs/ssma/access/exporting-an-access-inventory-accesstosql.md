---
title: Exportieren einer Zugriffs Inventur (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases
- Access databases, exporting metadata
- exporting
- exporting Access metadata
- exporting, Access metadata
- exporting, querying exported metadata
- inventories of Access databases
- querying exported metadata
ms.assetid: 7e1941fb-3d14-4265-aff6-c77a4026d0ed
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 7d7a87d45807c749477da7a7158f3a63fc56ec4b
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87934019"
---
# <a name="exporting-an-access-inventory-accesstosql"></a>Exportieren einer Zugriffs Inventur (accesstosql)
Wenn Sie über mehrere Access-Datenbanken verfügen und nicht sicher sind, in welche migriert werden sollen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , können Sie ein Inventar aller Access-Datenbanken in einem Projekt exportieren. Sie können dann die Inventar Metadaten überprüfen und Abfragen, um zu bestimmen, welche Datenbanken und Objekte innerhalb dieser Datenbanken migriert werden sollen. Diese Inventur ermöglicht Ihnen das schnelle Auffinden von Antworten auf Fragen wie die folgenden:  
  
-   Was sind die größten Datenbanken?  
  
-   Wer besitzt die meisten Datenbanken?  
  
-   Welche Datenbanken enthalten dieselben Tabellen?  
  
-   Welche Datenbanken wurden in den letzten sechs Monaten nicht geändert?  
  
-   Welche Datenbanken enthalten private Informationen?  
  
Abfrage Beispiele, die zum Beantworten dieser Fragen verwendet werden, werden am Ende dieses Themas bereitgestellt.  
  
## <a name="exported-metadata"></a>Exportierte Metadaten  
SSMA exportiert Metadaten zu Zugriffs Datenbanken, Tabellen, Spalten, Indizes, Fremdschlüsseln, Abfragen, Berichten, Formularen, Makros und Modulen. Metadaten zu den einzelnen Kategorien von Elementen werden in eine separate Tabelle exportiert. Informationen zu Schemas für diese Tabellen finden Sie unter [zugreifen auf Inventar Schemas](access-inventory-schemas-accesstosql.md).  
  
## <a name="exporting-inventory-data"></a>Exportieren von Inventur Daten  
Zum Exportieren einer Zugriffs Inventur müssen Sie zunächst ein SSMA-Projekt öffnen oder erstellen und dann die Zugriffs Datenbank hinzufügen, die Sie analysieren möchten. Nachdem Sie einem SSMA-Projektdaten Banken hinzugefügt haben, exportieren Sie Metadaten zu diesen Datenbanken in eine angegebene [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank und ein bestimmtes Schema. Ggf. erstellt SSMA Tabellen zum Speichern der Metadaten. SSMA fügt der Datenbank dann die Metadaten zu den Access-Datenbanken hinzu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
> Eine Access-Datenbank kann in mehrere Dateien aufgeteilt werden: eine Back-End-Datenbank, die Tabellen und Front-End-Datenbanken enthält, die Abfragen, Formulare, Berichte, Makros, Module und Verknüpfungen enthalten. Wenn Sie eine Split-Datenbank zu migrieren möchten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , fügen Sie SSMA die Front-End-Datenbank hinzu.  
  
In den folgenden Anweisungen wird beschrieben, wie Sie ein Projekt erstellen, dem Projektdaten Banken hinzufügen, eine Verbindung mit dem Projekt herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und anschließend Inventur Daten exportieren.  
  
**So erstellen Sie ein Projekt**  
  
1.  Öffnen Sie SSMA für den Zugriff.  
  
2.  Wählen Sie im Menü **Datei** die Option **Neues Projekt** aus.  
  
    Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  Geben Sie im Feld **Name** einen Namen für das Projekt ein.  
  
4.  Geben Sie im Feld **Speicherort** einen Ordner für das Projekt ein, oder wählen Sie einen Ordner aus.  
  
5.  Wählen Sie im Kombinations Feld **Migrieren zu** die Zielversion aus, zu der Sie migrieren möchten, und klicken Sie dann auf **OK**.  
  
Weitere Informationen zum Erstellen von Projekten finden Sie unter [Erstellen und Verwalten von Projekten](creating-and-managing-projects-accesstosql.md).  
  
**So suchen und fügen Sie Datenbanken hinzu**  
  
1.  Klicken Sie im Menü **Datei** auf **Datenbanken suchen**.  
  
2.  Geben Sie im Assistenten zum Suchen von Datenbanken das Laufwerk, den Dateipfad oder den UNC-Pfad ein, der durchsucht werden soll. Sie können auch auf **Durchsuchen** klicken, um das Laufwerk oder den Netzwerkordner auszuwählen.  
  
3.  Klicken Sie auf **Hinzufügen** , um den Speicherort zum Listenfeld hinzuzufügen.  
  
    Wiederholen Sie die vorherigen beiden Schritte, um zusätzliche Such Speicherorte hinzuzufügen.  
  
4.  Fügen Sie optional Suchkriterien hinzu, um die Liste der zurückgegebenen Datenbanken zu verfeinern.  
  
    > [!IMPORTANT]  
    > Der **ganz oder Teil des Textfelds "Dateiname** " unterstützt keine Platzhalter Zeichen.  
  
5.  Klicken Sie auf **Scannen**.  
  
    Die Seite Scannen wird angezeigt. Dadurch werden die Datenbanken, die gefunden wurden, und der Such Fortschritt angezeigt. Zum Abbrechen der Suche klicken Sie auf " **Abbrechen**".  
  
6.  Wählen Sie auf der Seite Dateien auswählen die einzelnen Datenbanken aus, die Sie dem Projekt hinzufügen möchten.  
  
    Sie können die Schaltflächen **Alle auswählen** und **Alle löschen** am Anfang der Liste verwenden, um alle Datenbanken auszuwählen oder zu löschen. Sie können auch die STRG-Taste gedrückt halten, um mehrere Zeilen auszuwählen, oder die UMSCHALTTASTE gedrückt halten, um einen Zeilen Bereich auszuwählen.  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Klicken Sie auf der Seite überprüfen auf **Fertig**stellen.  
  
Weitere Informationen zum Hinzufügen von Datenbanken zu Projekten finden Sie unter [Hinzufügen und Entfernen von Access-Datenbankdateien](adding-and-removing-access-database-files-accesstosql.md).  
  
**So stellen Sie eine Verbindung mit SQL Server her**  
  
1.  Wählen Sie im Menü **Datei** die Option **mit SQL Server verbinden**aus.  
  
2.  Geben Sie im Dialogfeld Verbindung den Namen der Instanz von ein, oder wählen Sie ihn aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    -   Wenn Sie eine Verbindung mit der Standard Instanz auf dem lokalen Computer herstellen, können Sie **localhost** oder einen Punkt (**.**) eingeben.  
  
    -   Wenn Sie eine Verbindung mit der Standard Instanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers ein.  
  
    -   Wenn Sie eine Verbindung mit einer benannten Instanz herstellen, geben Sie den Computernamen, einen umgekehrten Schrägstrich und den Instanznamen ein. Beispiel: MyServer\MyInstance.  
  
3.  Geben Sie im Feld **Datenbank** den Namen der Zieldatenbank für exportierte Metadaten ein.  
  
4.  Wenn die Instanz von für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Annahme von Verbindungen an einem nicht standardmäßigen Port konfiguriert ist, geben Sie die Portnummer ein, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Feld **Serverport** für Verbindungen verwendet wird. Die Standard Portnummer für die Standard Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist 1433. Bei benannten Instanzen wird von SSMA versucht, die Portnummer vom- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser Dienst abzurufen.  
  
5.  Wählen Sie im Dropdown Menü **Authentifizierung** den Authentifizierungstyp aus, der für die Verbindung verwendet werden soll. Um das aktuelle Windows-Konto zu verwenden, wählen Sie **Windows-Authentifizierung**aus. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Wählen Sie **SQL Server Authentifizierung**aus, und geben Sie einen Benutzernamen und ein Kennwort ein, um einen Anmelde Namen zu verwenden.  
  
Weitere Informationen zum Herstellen einer Verbindung mit finden Sie unter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Herstellen einer Verbindung mit SQL Server &#40;accesstosql&#41;](../../ssma/access/connecting-to-sql-server-accesstosql.md).  
  
**So exportieren Sie Inventur Informationen**  
  
1.  Erweitern Sie in Access Metadata Explorer den Eintrag **Access-Metabase**.  
  
2.  Aktivieren Sie das Kontrollkästchen neben **Datenbanken**.  
  
    Wenn Sie einzelne Datenbanken oder Datenbankobjekte weglassen möchten, erweitern Sie den Ordner **Datenbanken** , und deaktivieren Sie dann das Kontrollkästchen neben der Datenbank oder dem Datenbankobjekt.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Datenbanken** , und wählen Sie **Schema**  
  
4.  Wählen Sie im Dialogfeld **Schema für Export auswählen** das Ziel Schema für die exportierten Metadaten aus, und klicken Sie dann auf **OK**.  
  
Jedes Mal, wenn Sie Metadaten exportieren, fügt SSMA die Daten an den Bestand an. Vorhandene Daten im Inventar werden nicht aktualisiert oder gelöscht.  
  
## <a name="querying-the-exported-metadata"></a>Abfragen der exportierten Metadaten  
Nachdem Sie Metadaten zu Access-Datenbanken exportiert haben, können Sie die Metadaten Abfragen. In den folgenden Anweisungen wird beschrieben, wie das Abfrage-Editor-Fenster in verwendet wird [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , um Abfragen auszuführen.  
  
**So Fragen Sie Metadaten ab**  
  
1.  Zeigen Sie im **Startmenü** auf **Alle Programme**, zeigen Sie auf **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005** oder **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008** oder auf **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012**, und klicken Sie dann auf **SQL Server Management Studio**.  
  
2.  Überprüfen Sie im Dialogfeld **Verbindung mit Server herstellen** die Einstellungen, und klicken Sie dann auf **verbinden**.  
  
3.  Klicken Sie auf der Management Studio Symbolleiste auf **neue Abfrage** , um den Abfrage-Editor zu öffnen.  
  
4.  Geben Sie im Abfrage-Editor-Fenster eine Abfrage ein. Einige Beispiele werden im folgenden Abschnitt gezeigt.  
  
5.  Drücken Sie die Taste F5, um die Abfrage auszuführen.  
  
## <a name="query-examples"></a>Abfragebeispiele  
Bevor Sie eine der folgenden Abfragen ausführen, sollten Sie eine use *database_name* -Abfrage ausführen, um sicherzustellen, dass die Abfragen für die Datenbank ausgeführt werden, die die exportierten Metadaten enthält. Wenn Sie z. b. Metadaten in eine Datenbank mit dem Namen myaccessmetadata exportiert haben, würden Sie am Anfang des Codes Folgendes hinzufügen [!INCLUDE[tsql](../../includes/tsql-md.md)] :  
  
```  
USE MyAccessMetadata;  
GO  
```  
In den folgenden Beispielen wird das **dbo** -Schema verwendet. Wenn Sie die Metadaten in ein anderes Schema exportiert haben, stellen Sie sicher, dass Sie das Schema beim Ausführen dieser Abfragen ändern.  
  
### <a name="what-tables-and-columns-are-in-these-databases"></a>Welche Tabellen und Spalten befinden sich in diesen Datenbanken?  
Die folgende Abfrage verbindet die Tabellen, die Spalten-, Tabellen-und Daten Bank Metadaten enthalten, und gibt dann die Namen aller Datenbanken, Tabellen und Spalten zurück, sortiert nach Spaltenname:  
  
```  
SELECT DatabaseName, TableName, ColumnName   
FROM dbo.SSMA_Access_InventoryColumns C  
JOIN dbo.SSMA_Access_InventoryTables T  
ON C.TableId = T.TableId  
JOIN dbo.SSMA_Access_InventoryDatabases D  
ON T.DatabaseId = D.DatabaseId  
ORDER BY ColumnName;  
```  
  
### <a name="what-are-the-largest-databases"></a>Was sind die größten Datenbanken?  
Die folgende Abfrage gibt den Datenbanknamen, die Dateigröße und die Anzahl der Tabellen in jeder Access-Datenbank nach Dateigröße sortiert zurück:  
  
```  
SELECT DatabaseName, FileSize, TablesCount  
FROM dbo.SSMA_Access_InventoryDatabases  
ORDER BY FileSize DESC;  
```  
  
### <a name="who-is-the-owner-of-most-of-the-databases"></a>Wer ist der Besitzer der meisten Datenbanken?  
Die folgende Abfrage gibt den Datenbanknamen und den Besitzer der einzelnen Zugriffs Datenbanken nach Besitzer sortiert zurück.  
  
```  
SELECT DatabaseName, FileOwner  
FROM dbo.SSMA_Access_InventoryDatabases  
ORDER BY FileOwner;  
```  
  
### <a name="which-databases-contain-the-same-tables"></a>Welche Datenbanken enthalten dieselben Tabellen?  
In der folgenden Abfrage wird eine Unterabfrage verwendet, um alle Tabellennamen zu suchen, die mehr als einmal in der Liste der Tabellen angezeigt werden. Anschließend wird diese Liste von Tabellen zum Abrufen des Daten Banknamens verwendet. Die Ergebnisse werden als Datenbankname und dann als Tabellenname zurückgegeben und nach Tabellenname sortiert.  
  
```  
SELECT DatabaseName, TableName   
FROM dbo.SSMA_Access_InventoryTables T  
JOIN dbo.SSMA_Access_InventoryDatabases D  
ON D.DatabaseId = T.DatabaseId  
WHERE TableName IN (  
SELECT TableName   
FROM dbo.SSMA_Access_InventoryTables  
GROUP BY TableName   
HAVING count(*)>1  
)  
ORDER BY TableName;  
```  
  
### <a name="which-databases-were-not-modified-in-the-last-six-months"></a>Welche Datenbanken wurden in den letzten sechs Monaten nicht geändert?  
Die folgende Abfrage ruft das aktuelle Datum ab, Ruft den Monatswert für sechs Monate ab und gibt dann eine Liste mit Datenbanken zurück, deren Änderungsdatum vor mehr als sechs Monaten liegt.  
  
```  
SELECT DatabaseName, DateModified  
FROM dbo.SSMA_Access_InventoryDatabases  
WHERE DATEDIFF(month, DateModified, GETDATE()) > 6  
ORDER BY DateModified;  
```  
  
### <a name="which-databases-contain-private-information"></a>Welche Datenbanken enthalten private Informationen?  
Ihre Access-Datenbanken können vertrauliche oder persönliche Informationen enthalten. Möglicherweise möchten Sie diese Datenbanken zu verschieben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um von den Sicherheitsfeatures zu profitieren. Wenn Sie wissen, dass Spalten, die sensible Daten enthalten, einen bestimmten Namen aufweisen oder bestimmte Zeichen enthalten, können Sie eine Abfrage verwenden, um alle Spalten zu suchen, die diese Informationen enthalten. Beispielsweise können Sie alle Spalten suchen, die die Zeichenfolge "Gehalt" enthalten.  Die Abfrage gibt dann den Datenbanknamen, den Tabellennamen und den Spaltennamen zurück.  
  
```  
SELECT DatabaseName, TableName, ColumnName   
FROM dbo.SSMA_Access_InventoryColumns C  
JOIN dbo.SSMA_Access_InventoryTables T  
ON C.TableId = T.TableId  
JOIN dbo.SSMA_Access_InventoryDatabases D  
ON T.DatabaseId = D. DatabaseId  
WHERE ColumnName LIKE '%salary%';  
```  
Wenn Sie den Spaltennamen nicht kennen, können Sie eine Abfrage schreiben, um alle Spalten zurückzugeben. Entfernen Sie zu diesem Zweck die WHERE-Klausel aus der vorherigen Abfrage.  
  
## <a name="see-also"></a>Weitere Informationen  
[Vorbereiten der Zugriffs Datenbanken für die Migration](preparing-access-databases-for-migration-accesstosql.md)  
  
