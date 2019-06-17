---
title: Exportieren eines Access-Inventars (AccessToSQL) | Microsoft-Dokumentation
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
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: f35ae03cb6588bc7828349dd4a4beafcc5a7b2f3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62760831"
---
# <a name="exporting-an-access-inventory-accesstosql"></a>Exportieren eines Access-Inventars (AccessToSQL)
Wenn Sie mehrere Access-Datenbanken und nicht sicher, welche zum Migrieren sind in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], können Sie ein Inventar aller Access-Datenbanken in einem Projekt exportieren. Sie können dann überprüfen und Abfragen der Inventur-Metadaten, um zu bestimmen, welche Datenbanken und Objekte innerhalb dieser Datenbanken migrieren. Dieser Hardwareinventur können Sie schnell finden Sie Antworten auf Fragen, wie z. B. die folgenden:  
  
-   Was sind die größten Datenbanken?  
  
-   Wer besitzt die meisten Datenbanken?  
  
-   Welche Datenbanken die gleichen Tabellen enthalten?  
  
-   Welche Datenbanken in den letzten sechs Monaten nicht geändert wurden?  
  
-   Welche Datenbanken private Informationen enthalten?  
  
Beispiele für die Abfrage, die verwendet werden, zum Beantworten dieser Fragen werden am Ende dieses Themas bereitgestellt.  
  
## <a name="exported-metadata"></a>Exportierten Metadaten  
SSMA exportiert Metadaten über die Access-Datenbanken, Tabellen, Spalten, Indizes, Fremdschlüssel, Abfragen, Berichte, Forms, Makros und Module. Metadaten zu jeder dieser Kategorien der Elemente wird in einer separaten Tabelle exportiert. Schemas für diese Tabellen finden Sie unter [Access Inventory Schemas](access-inventory-schemas-accesstosql.md).  
  
## <a name="exporting-inventory-data"></a>Exportieren von Daten der Softwareinventur  
Zum Exportieren eines Access-Inventars müssen Sie zum ersten Mal öffnen oder erstellen Sie ein SSMA-Projekt, und klicken Sie dann hinzufügen die Access-Datenbank, die Sie analysieren möchten. Nachdem Sie Datenbanken zu einem SSMA-Projekt hinzugefügt haben, exportieren Sie Metadaten zu diesen Datenbanken mit einem angegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank und Schema. Bei Bedarf erstellt SSMA Tabellen zum Speichern der Metadaten. SSMA fügt dann die Metadaten über die Access-Datenbanken die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank.  
  
> [!NOTE]  
> Eine Access-Datenbank kann in mehrere Dateien aufgeteilt werden: ein Back-End-Datenbank mit Tabellen und Front-End-Datenbanken, die Abfragen, Formulare, Berichte, Makros, Modulen und Verknüpfungen enthalten. Sollten Sie Teilen zum Migrieren einer Datenbank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA die Front-End-Datenbank hinzufügen.  
  
Die folgenden Anweisungen beschreiben, wie Sie ein Projekt erstellen, Hinzufügen von Datenbanken zum Projekt, Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und klicken Sie dann Inventardaten.  
  
**Zum Erstellen eines Projekts**  
  
1.  Öffnen Sie SSMA für Access.  
  
2.  Wählen Sie im Menü **Datei** die Option **Neues Projekt** aus.  
  
    Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  In der **Namen** Geben Sie einen Namen für Ihr Projekt.  
  
4.  In der **Speicherort** Feld, geben Sie ein oder wählen Sie einen Ordner für das Projekt.  
  
5.  In der **Migrieren zu** Kombinationsfeld wählen die Zielversion, die auf die Sie migrieren möchten, und klicken Sie dann auf **OK**.  
  
Weitere Informationen zum Erstellen von Projekten finden Sie unter [erstellen und Verwalten von Projekten](creating-and-managing-projects-accesstosql.md).  
  
**Suchen und Hinzufügen von Datenbanken**  
  
1.  Auf der **Datei** Menü klicken Sie auf **Datenbanken suchen**.  
  
2.  Geben Sie im Assistenten Datenbanken finden Sie das Laufwerk, Pfad der Datei oder den UNC-Pfad, den Sie suchen möchten. Klicken Sie alternativ auf **Durchsuchen** um den Ordner oder auf ein Netzwerk auszuwählen.  
  
3.  Klicken Sie auf **hinzufügen** auf den Speicherort in das Listenfeld hinzufügen.  
  
    Wiederholen Sie die vorherigen beiden Schritte aus, um zusätzliche Suchbedingung Speicherorte hinzuzufügen.  
  
4.  Fügen Sie optional Suchkriterien, um die Liste der Datenbanken zu optimieren, die zurückgegeben werden.  
  
    > [!IMPORTANT]  
    > Die **alle oder einen Teil des Dateinamens** Textfeld unterstützt keine Platzhalterzeichen enthalten.  
  
5.  Klicken Sie auf **Scannen**.  
  
    Die Seite "Überprüfung" wird angezeigt. Es werden die Datenbanken, die gefunden wurden und den Suchstatus meldet. Um die Suche zu beenden, klicken Sie auf **beenden**.  
  
6.  Wählen Sie auf der Seite für Dateien auswählen die jede Datenbank, die Sie dem Projekt hinzufügen möchten.  
  
    Können Sie die **Alles markieren** und **deaktivieren Sie alle** Schaltflächen am oberen Rand der Liste aktivieren oder deaktivieren Sie alle Datenbanken. Sie können auch die STRG-Taste gedrückt, um mehrere Zeilen auswählen, oder halten Sie die UMSCHALTTASTE gedrückt, wählen Sie einen Bereich von Zeilen.  
  
7.  Klicken Sie auf **Weiter**.  
  
8.  Klicken Sie auf der Seite "Überprüfen" auf **Fertig stellen**.  
  
Weitere Informationen zum Hinzufügen von Datenbanken zu Projekten finden Sie unter [hinzufügen und Entfernen von Access-Datenbankdateien](adding-and-removing-access-database-files-accesstosql.md).  
  
**Verbindung mit SQL Server**  
  
1.  Auf der **Datei** , wählen Sie im Menü **Herstellen einer Verbindung mit SQL Server**.  
  
2.  Klicken Sie im Dialogfeld "Verbindung" eingeben, oder wählen Sie den Namen der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Wenn Sie mit der Standardinstanz auf dem lokalen Computer herstellen, geben Sie **"localhost"** oder einen Punkt ( **.** ).  
  
    -   Wenn Sie mit der Standardinstanz auf einem anderen Computer herstellen, geben Sie den Namen des Computers ein.  
  
    -   Wenn Sie die zu einer benannten Instanz herstellen, geben Sie den Namen des Computers, einen umgekehrten Schrägstrich und den Namen der Instanz. Zum Beispiel: MyServer\MyInstance.  
  
3.  In der **Datenbank** Geben Sie den Namen der Zieldatenbank für die exportierten Metadaten.  
  
4.  Wenn Ihre Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konfiguriert ist annehmen von Verbindungen über einen nicht-Standardport, geben die Portnummer für die verwendeten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindungen in der **Serverport** Feld. Für die Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die Standardportnummer ist 1433. Für benannte Instanzen SSMA versucht, erhalten die Portnummer der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst.  
  
5.  In der **Authentifizierung** Dropdown-Menü Wählen Sie im Menü, Authentifizierungstyp, der für die Verbindung verwendet. Um das aktuelle Windows-Konto verwenden möchten, wählen **Windows-Authentifizierung**. Verwenden einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anmeldung wählen **SQL Server-Authentifizierung**, und geben Sie einen Benutzernamen und Kennwort.  
  
Weitere Informationen zum Verbinden mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], finden Sie unter [Herstellen einer Verbindung mit SQL Server &#40;AccessToSQL&#41;](../../ssma/access/connecting-to-sql-server-accesstosql.md).  
  
**So exportieren Sie die Inventarinformationen**  
  
1.  Erweitern Sie im Metadaten-Explorer für den Zugriff, **Access-Metabase**.  
  
2.  Aktivieren Sie das Kontrollkästchen neben **Datenbanken**.  
  
    Um einzelne Datenbanken oder Datenbankobjekte zu unterdrücken, erweitern Sie die **Datenbanken** Ordner, und klicken Sie dann löschen Sie das Kontrollkästchen neben der Datenbank oder ein Datenbankobjekt.  
  
3.  Mit der rechten Maustaste **Datenbanken** , und wählen Sie **Schema exportieren**.  
  
4.  In der **Schema auswählen, für den Export** Dialogfeld Wählen Sie das Zielschema für die exportierten Metadaten, und klicken Sie dann auf **OK**.  
  
Jedes Mal, die Sie exportieren Sie Metadaten, die Daten mit dem Bestand SSMA angefügt. Vorhandene Daten bei der Inventur nicht aktualisiert oder gelöscht.  
  
## <a name="querying-the-exported-metadata"></a>Abfragen der exportierten Metadaten  
Nachdem Sie Metadaten für den Zugriff auf Datenbanken exportiert haben, können Sie die Metadaten Abfragen. Die folgenden Anweisungen beschreiben das Abfrage-Editor-Fenster in Verwendung [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] zum Ausführen von Abfragen.  
  
**Zum Abfragen von Metadaten**  
  
1.  Von der **starten** Startmenü **Programme**, zeigen Sie auf **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005** oder **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008**oder **Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012**, und klicken Sie dann auf **SQL Server Management Studio**.  
  
2.  In der **Herstellen einer Verbindung mit Server** (Dialogfeld), überprüfen Sie die Einstellungen, und klicken Sie dann auf **Connect**.  
  
3.  Klicken Sie auf der Symbolleiste von Management Studio auf **neue Abfrage** Abfrage-Editor geöffnet.  
  
4.  Geben Sie im Fenster Abfrage-Editor eine Abfrage aus. Einige Beispiele sind im folgenden Abschnitt gezeigt.  
  
5.  Drücken Sie F5, um die Abfrage auszuführen.  
  
## <a name="query-examples"></a>Beispiele für Abfragen  
Bevor Sie einen der folgenden Abfragen ausführen, führen Sie eine Verwendung *Database_name* Abfrage, um sicherzustellen, dass die Abfragen ausgeführt werden, für die Datenbank, die die exportierte Metadaten enthält. Sie z. B., wenn Sie Metadaten in einer Datenbank mit dem Namen MyAccessMetadata exportiert haben, würden hinzufügen Folgendes am Anfang der [!INCLUDE[tsql](../../includes/tsql-md.md)] Code:  
  
```  
USE MyAccessMetadata;  
GO  
```  
Verwenden Sie die folgenden Beispielen die **Dbo** Schema. Wenn Sie die Metadaten in ein anderes Schema exportiert haben, stellen Sie sicher, dass das Schema ändern, wenn Sie diese Abfragen ausführen.  
  
### <a name="what-tables-and-columns-are-in-these-databases"></a>Welche Tabellen und Spalten sind in diesen Datenbanken?  
Die folgende Abfrage verknüpft die Tabellen, die Spalte, Tabellen- und Datenbank-Metadaten enthalten, und klicken Sie dann die Namen aller Datenbanken, Tabellen und Spalten, sortiert nach Spaltennamen zurückgegeben:  
  
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
Die folgende Abfrage gibt den Datenbanknamen, Größe und Anzahl von Tabellen in jeder Access-Datenbank, sortiert nach Dateigröße:  
  
```  
SELECT DatabaseName, FileSize, TablesCount  
FROM dbo.SSMA_Access_InventoryDatabases  
ORDER BY FileSize DESC;  
```  
  
### <a name="who-is-the-owner-of-most-of-the-databases"></a>Wer ist der Besitzer der meisten Datenbanken?  
Die folgende Abfrage gibt den Datenbanknamen und den Besitzer der einzelnen Access-Datenbanken, die nach Besitzer sortiert.  
  
```  
SELECT DatabaseName, FileOwner  
FROM dbo.SSMA_Access_InventoryDatabases  
ORDER BY FileOwner;  
```  
  
### <a name="which-databases-contain-the-same-tables"></a>Welche Datenbanken die gleichen Tabellen enthalten?  
Die folgende Abfrage wird eine Unterabfrage verwendet, um alle Tabellennamen zu finden, die mehr als einmal in der Liste der Tabellen angezeigt werden, und verwendet dann diese Liste von Tabellen, um den Datenbanknamen abzurufen. Die Ergebnisse werden als Name der Datenbank, und klicken Sie dann den Namen der Tabelle zurückgegeben, und anhand des Tabellennamens sortiert werden.  
  
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
  
### <a name="which-databases-were-not-modified-in-the-last-six-months"></a>Welche Datenbanken in den letzten sechs Monaten nicht geändert wurden?  
Die folgende Abfrage ruft das aktuelle Datum ab, ruft den Monatswert für sechs Monate später wurde und dann eine Liste von Datenbanken mit einem Datum der Änderung von mehr als sechs Monate später wurde zurückgegeben.  
  
```  
SELECT DatabaseName, DateModified  
FROM dbo.SSMA_Access_InventoryDatabases  
WHERE DATEDIFF(month, DateModified, GETDATE()) > 6  
ORDER BY DateModified;  
```  
  
### <a name="which-databases-contain-private-information"></a>Welche Datenbanken private Informationen enthalten?  
Die Access-Datenbanken möglicherweise vertrauliche oder persönliche Informationen enthalten. Möglicherweise möchten Sie dieser Datenbanken zu verschieben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Nutzen der Sicherheitsfunktionen zu nutzen. Wenn Sie wissen, dass Spalten mit sensiblen Daten einen bestimmten Namen haben, oder bestimmte Zeichen enthalten, können Sie eine Abfrage, um alle Spalten zu suchen, die diese Informationen enthalten. Beispielsweise finden Sie alle Spalten, die die Zeichenfolge "Salary".  Die Abfrage gibt dann zurück, der Datenbankname, Tabellenname und Spaltenname.  
  
```  
SELECT DatabaseName, TableName, ColumnName   
FROM dbo.SSMA_Access_InventoryColumns C  
JOIN dbo.SSMA_Access_InventoryTables T  
ON C.TableId = T.TableId  
JOIN dbo.SSMA_Access_InventoryDatabases D  
ON T.DatabaseId = D. DatabaseId  
WHERE ColumnName LIKE '%salary%';  
```  
Wenn Sie den Namen der Spalte nicht kennen, können Sie eine Abfrage zum Zurückgeben aller Spalten schreiben. Entfernen Sie zu diesem Zweck die WHERE-Klausel aus der vorherigen Abfrage.  
  
## <a name="see-also"></a>Siehe auch  
[Access-Datenbanken vorbereitet für die Migration.](preparing-access-databases-for-migration-accesstosql.md)  
  
