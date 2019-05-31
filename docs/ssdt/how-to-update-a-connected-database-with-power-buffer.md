---
title: 'Gewusst wie: Aktualisieren einer verbundenen Datenbank mit Power Buffer | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.commitpreview.dialog
ms.assetid: 4048b7f8-71a9-47ad-b812-3fc1e8066240
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9663829f679eeb0c829a94be00c86a7f1e0544af
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65098419"
---
# <a name="how-to-update-a-connected-database-with-power-buffer"></a>Gewusst wie: Aktualisieren einer verbundenen Datenbank mithilfe von Power Buffer
Mit der Power Buffer-Technologie von SQL Server Data Tools können Sie einfach Änderungen auf die verbundene Datenbank anwenden, indem Sie sämtliche Bearbeitungen in der aktuellen Sitzung speichern. Alle durch die Bearbeitung im Power Buffer-Fenster (im Transact\-SQL-Editor oder Tabellen-Designer) verursachten Fehler werden sofort im Bereich **Fehlerliste** angezeigt, sodass Sie die identifizierten Fehler zur weiteren Problembehandlung verfolgen können. Sie können die ausstehenden Änderungen überprüfen, bevor Sie diese auf die Datenbank anwenden. Während des Updates erstellt SSDT automatisch ein ALTER-Skript auf Grundlage der Bearbeitungen und weist Sie auf alle potenziellen Probleme hin. Sie können dann sämtliche Änderungen, die bisher in allen geöffneten Power Buffer-Fenstern vorgenommen wurden, auf dieselbe Datenbank anwenden oder das ALTER-Skript speichern, um die Änderungen bereitzustellen.  
  
SSDT berücksichtigt außerdem alle Änderungen, die außerhalb von Visual Studio am Datenbankschema vorgenommen wurden. Wenn Sie z.B. in SQL Server Management Studio einer vorhandenen Datenbank eine neue Tabelle hinzufügen, wird diese Änderung sofort im SQL Server-Objekt-Explorer in Visual Studio angezeigt, ohne dass eine manuelle Aktualisierung erforderlich ist. Die Abweichungserkennung stellt sicher, dass im SQL Server-Objekt-Explorer immer die aktuelle Schemadefinition einer Datenbank angezeigt wird. Beachten Sie, dass Datenbankobjekte, die im Tabellen-Designer oder Transact\-SQL-Editor zur Bearbeitung geöffnet sind, nicht anhand von Änderungen aktualisiert werden, die außerhalb von Visual Studio vorgenommen wurden.  
  
Bei den folgenden Vorgehensweisen werden die Entitäten verwendet, die in vorherigen Vorgehensweisen im Abschnitt [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) erstellt wurden.  
  
### <a name="to-apply-the-changes-made-in-the-previous-procedures"></a>So wenden Sie die in den vorherigen Prozeduren vorgenommenen Änderungen an  
  
1.  Klicken Sie auf der Symbolleiste auf die grüne Schaltfläche **Aktualisieren** (wenn Sie mit der Maus auf diese Schaltfläche zeigen, wird die QuickInfo „Datenbank aktualisieren“ angezeigt). Die Symbolleiste befindet sich über dem Spaltenraster des Tabellen-Designers.  
  
2.  Das Dialogfeld **Vorschau der Datenbankupdates** wird angezeigt. Im Hintergrund wird ein auf den Änderungen basierendes Bereitstellungsskript generiert. Anschließend wird im Dialogfeld eine Zusammenfassung der Aktionen angezeigt, die SSDT ausführt (z. B. das Erstellen oder Löschen von Datenbankentitäten), zusammen mit potenziellen Problemen, die von SSDT erkannt wurden (dies gilt nicht für die hier beschriebene Prozedur, ist jedoch hilfreich, wenn eine Datenbankdefinition Fehler enthält, die ein Update verhindern, solange sie nicht behoben sind).  
  
3.  Wenn Sie die Datenbank derzeit nicht aktualisieren möchten, klicken Sie auf die Schaltfläche **Abbrechen**, um das Dialogfeld **Vorschau der Datenbankupdates** zu schließen.  
  
4.  Wenn Sie die Änderungen übernehmen möchten, klicken Sie im Dialogfeld **Vorschau der Datenbankupdates** auf die Schaltfläche **Datenbank aktualisieren**. Das Bereitstellungsskript wird für Sie ausgeführt, und die angefallenen Änderungen werden jetzt auf die Datenbank angewendet.  
  
5.  Wenn Sie das Bereitstellungsskript anzeigen möchten, um es zu überprüfen, oder vor dem Aktualisieren Änderungen vornehmen möchten, klicken Sie im Dialogfeld **Vorschau der Datenbankupdates** auf die Schaltfläche **Skript generieren**. Das generierte Skript wird in einem neuen Transact\-SQL-Editor-Fenster geöffnet. Sie können auf der Transact\-SQL-Editor-Symbolleiste auf die Schaltfläche **Abfrage ausführen** klicken, um diese Abfrage auszuführen. Dies entspricht der Aktion, die in Schritt 4 mit der Schaltfläche **Datenbank aktualisieren** ausgeführt wurde.  
  
    > [!WARNING]  
    > Wenn Sie Änderungen am Bereitstellungsskript vornehmen und das Skript ausführen, werden diese Änderungen in keinen geöffneten Datenbankentitäten angezeigt. Wenn Sie z.B. im Bereitstellungsskript eine Spalte der Tabelle `Customers` umbenennen und zum Aktualisieren der Datenbank das Skript ausführen, und im Tabellen-Designer ist die Tabelle `Customers` geöffnet, wird nach dem Klicken auf die Schaltfläche **Datenbank aktualisieren** immer noch der alte Spaltenname angezeigt. Sie müssen den Tabellen-Designer manuell schließen, ohne die Tabelle lokal als Skript zu speichern. Wenn Sie die Tabelle im **SQL Server-Objekt-Explorer** erneut öffnen, werden Sie feststellen, dass die Datenbank mit den Änderungen aktualisiert wurde, die Sie im Bereitstellungsskript vorgenommen haben.  
  
6.  Beachten Sie im Bereich **Ausgabe** des Transact\-SQL-Editors (bzw. im Bereich **Meldung**, falls Sie das Bereitstellungsskript selbst ausführen) die folgenden Meldungen, die angeben, dass das Update erfolgreich ausgeführt wurde.  
  
**[dbo].[Customers] wird erstellt... [dbo].[Products] wird erstellt... [dbo].[Suppliers] wird erstellt... FK_Products_SupplierId wird erstellt... FK_Products_CustomerId wird erstellt... CK_Products_ShelfLife wird erstellt... Der von der Transaktion betroffene Teil des Datenbankupdates wurde erfolgreich durchgeführt. Vorhandene Daten werden auf neu erstellte Einschränkungen hin überprüft. Update abgeschlossen.**  
  
7.  Beachten Sie, dass im **SQL Server-Objekt-Explorer** die neuen Tabellen unter dem Knoten **Tabellen** der Datenbank **Trade** angezeigt werden.  
  
### <a name="to-view-changes-made-to-a-database-outside-visual-studio"></a>So zeigen Sie Änderungen an, die außerhalb von Visual Studio an einer Datenbank vorgenommen wurden  
  
1.  Öffnen Sie SQL Server Management Studio. Geben Sie im Dialogfeld **Verbindung mit Server herstellen** den Namen des Datenbankservers ein, mit dem in Visual Studio eine Verbindung bestanden hat, und klicken Sie auf **Verbinden**.  
  
2.  Erweitern Sie im **SQL Server-Objekt-Explorer** die Option **Datenbanken**, und navigieren Sie zu der Datenbank **Trade**.  
  
3.  Klicken Sie unter **Trade** mit der rechten Maustaste auf **Tabellen**, und wählen Sie **Neue Tabelle** aus. Geben Sie im Tabellen-Designer als Spaltennamen **id** und als Datentyp **int** ein.  
  
4.  Klicken Sie auf der Symbolleiste auf das Symbol **Speichern**, um die Tabelle zu speichern. Übernehmen Sie den Standardnamen, und klicken Sie auf **OK**.  
  
    Kehren Sie zu Visual Studio zurück. Untersuchen Sie im **SQL Server-Objekt-Explorer** unter der Datenbank **Trade** den Knoten **Tabellen**. Beachten Sie die Darstellung der neu erstellten Tabelle **Table_1**.  
  
5.  Klicken Sie mit der rechten Maustaste auf **Table_1**, und klicken Sie auf **Löschen**. Klicken Sie im Dialogfeld **Vorschau der Datenbankupdates** auf **Datenbank aktualisieren**.  
  
## <a name="see-also"></a>Weitere Informationen  
[Vorgehensweise: Beheben von Fehlern](../ssdt/how-to-fix-errors.md)  
  
