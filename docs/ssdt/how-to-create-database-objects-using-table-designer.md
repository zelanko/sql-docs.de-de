---
title: 'Gewusst wie: Erstellen von Datenbankobjekten mit dem Tabellen-Designer | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql.data.tools.design.table.scriptpanel
- sql.data.tools.design.table.context.view
ms.assetid: 9c9479c1-9bfc-4039-837e-e53fce67723d
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ddd5f0cb14b3216e8b6acc4eb18d35d70fca149e
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094276"
---
# <a name="how-to-create-database-objects-using-table-designer"></a>Vorgehensweise: Erstellen von Datenbankobjekten mit dem Tabellen-Designer
Der neue Knoten **SQL Server** im **SQL Server-Objekt-Explorer** ähnelt dem in SSMS nicht nur visuell. Sie können neue Objekte auch mit Kontextmenüs erstellen, die wie ihre Äquivalente in SSMS funktionieren.  
  
Sie können z.B. unter dem Knoten **Datenbanken** eine neue Datenbank erstellen. Ebenso können Sie im neuen Tabellen-Designer eine bestimmte Datenbank auswählen und erstellen sowie Tabellendefinitionen und die zugehörigen Programmierobjekte direkt bearbeiten. Vom Tabellen-Designer können Sie in einen Skriptbereich wechseln, in dem Sie das Skript direkt bearbeiten können, von dem diese Tabelle definiert wird.  
  
### <a name="to-create-a-new-database"></a>So erstellen Sie eine neue Datenbank  
  
1.  Erweitern Sie im **SQL Server-Objekt-Explorer** unter dem Knoten **SQL Server** die verbundene Serverinstanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Knoten **Datenbanken**, und wählen Sie **Neue Datenbank hinzufügen** aus.  
  
3.  Benennen Sie die neue Datenbank in **Trade** um.  
  
### <a name="to-create-new-tables-using-the-table-designer"></a>So erstellen Sie neue Tabellen mithilfe des Tabellen-Designers  
  
1.  Erweitern Sie den neu erstellten Knoten **Trade**. Klicken Sie mit der rechten Maustaste auf den Knoten **Tabellen**, und wählen Sie **Neue Tabelle hinzufügen** aus.  
  
2.  Der Tabellen-Designer wird in einem neuen Fenster geöffnet. Der Designer besteht aus dem Spaltenraster, dem Skriptbereich und dem Kontextbereich. Im Spaltenraster werden alle Spalten in der Tabelle aufgelistet. Andere Komponenten des Designers werden in späteren Prozeduren behandelt.  
  
3.  Benennen Sie im Skriptbereich die neue Tabelle in `Suppliers` um. Ersetzen Sie insbesondere  
  
    ```  
    CREATE TABLE [dbo].[Table1]  
    ```  
  
    durch  
  
    ```  
    CREATE TABLE [dbo].[Suppliers]  
    ```  
  
4.  Klicken Sie auf die leere Zeile im Spaltenraster, um der Tabelle eine neue Spalte hinzuzufügen.  Geben Sie **CompanyName** im Feld **Name** und **nvarchar (128)** im Feld **Datentyp** ein, und deaktivieren Sie die Option **NULL-Werte zulassen**. Der Skriptbereich wird beim Verlassen der Felder sofort aktualisiert.  
  
5.  Fügen Sie eine weitere neue Spalte hinzu. Geben Sie **Address** im Feld **Name** und **nvarchar (MAX)** im Feld **Datentyp** ein, und deaktivieren Sie die Option **NULL-Werte zulassen**.  
  
    > [!WARNING]  
    > Wenn Sie Objekte aus einer verbundenen Datenbank bearbeiten, speichern Sie sie nicht auf dem lokalen Laufwerk. Um die Änderungen ordnungsgemäß in der Datenbank zu speichern, führen Sie die Schritte im nächsten Verfahren [Gewusst wie: Aktualisieren einer verbundenen Datenbank mit Power Buffer](../ssdt/how-to-update-a-connected-database-with-power-buffer.md) aus.  
  
6.  Führen Sie die obigen Schritte erneut aus, um eine weitere Tabelle mit dem Namen **Customer** zu erstellen. Fügen Sie der Tabelle "Customer" mithilfe des Spaltenrasters die folgenden Spalten hinzu. Achten Sie darauf, dass Sie das Skript so ändern, dass der Name der Tabelle `[dbo].[Customer]` lautet.  
  
    |Name|Datentyp|**NULL-Werte zulassen**|  
    |--------|-------------|-------------------|  
    |ID|ssNoversion|Nicht aktiviert|  
    |Name|nvarchar (128)|Nicht aktiviert|  
  
7.  Erstellen Sie eine weitere Tabelle mit dem Namen **Products**. Fügen Sie der Tabelle "Products" mithilfe des Spaltenrasters die folgenden Spalten hinzu. Achten Sie darauf, dass Sie das Skript so ändern, dass der Name der Tabelle `[dbo].[Products]` lautet.  
  
    |Name|Datentyp|**NULL-Werte zulassen**|  
    |--------|-------------|-------------------|  
    |ID|ssNoversion|Nicht aktiviert|  
    |Name|nvarchar (128)|Nicht aktiviert|  
    |ShelfLife|ssNoversion|Überprüft|  
    |SupplierId|ssNoversion|Überprüft|  
    |CustomerId|ssNoversion|Überprüft|  
  
### <a name="to-create-a-new-check-constraint-using-the-table-designer"></a>So erstellen Sie mithilfe des Tabellen-Designers eine neue CHECK-Einschränkung  
  
1.  Im Kontextbereich des Tabellen-Designers erhalten Sie eine logische Sicht der Tabellendefinition und (Schlüssel, Einschränkungen, Trigger usw.). Hier können Sie ein Objekt auswählen, um dessen Beziehungen zu einzelnen Spalten hervorzuheben.  
  
    Klicken Sie für die Tabelle „Products“ im Kontextbereich des Tabellen-Designers mit der rechten Maustaste auf den Knoten **CHECK-Einschränkungen**, und klicken Sie auf **Neue CHECK-Einschränkung hinzufügen**.  
  
2.  Beachten Sie, dass die Knotenanzahl automatisch um 1 inkrementiert wird.  
  
3.  Klicken Sie auf den Skriptbereich, und ersetzen Sie die Standarddefinition der Einschränkung durch Folgendes.  
  
    ```  
    CONSTRAINT [CK_Products_ShelfLife] CHECK ([ShelfLife] <5),  
    ```  
  
    Diese Einschränkung schränkt den Wert von ShelfLife für eine Zeile auf einen Wert kleiner als 5 ein.  
  
### <a name="to-create-new-foreign-key-references-using-the-table-designer"></a>So erstellen Sie mithilfe des Tabellen-Designers neue Fremdschlüsselverweise  
  
1.  Klicken Sie für die Tabelle „Products“ im Kontextbereich mit der rechten Maustaste auf den Knoten **Fremdschlüssel**, und klicken Sie auf **Neuen Fremdschlüssel hinzufügen**.  
  
2.  Beachten Sie, dass die Knotenanzahl automatisch um 1 inkrementiert wird.  
  
3.  Klicken Sie auf den Skriptbereich, und ersetzen Sie die Standarddefinition des Fremdschlüsselverweises durch Folgendes.  
  
    ```  
    CONSTRAINT [FK_Products_SupplierId] FOREIGN KEY ([SupplierId]) REFERENCES [dbo].[Suppliers] ([Id]),  
    ```  
  
4.  Führen Sie die obigen Schritte erneut aus, um einen weiteren Fremdschlüsselverweis auf die Tabelle "Products" hinzuzufügen. Ersetzen Sie dieses Mal die Standarddefinition durch Folgendes.  
  
    ```  
    CONSTRAINT [FK_Products_CustomerId] FOREIGN KEY ([CustomerId]) REFERENCES [dbo].[Customer] ([Id])  
    ```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Verwalten von Tabellen, Beziehungen und Beheben von Fehlern](../ssdt/manage-tables-relationships-and-fix-errors.md)  
  
