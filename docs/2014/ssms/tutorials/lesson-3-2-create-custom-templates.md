---
title: Erstellen von benutzerdefinierten Vorlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- tql
- templates [Transact-SQL], creating
- templates [Transact-SQL]
ms.assetid: 41098e78-b482-410e-bfe8-2ac10769ac4a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 495b03b98e6c497bfd7a1527d9e2e2d81f25b762
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62805579"
---
# <a name="create-custom-templates"></a>Erstellen von benutzerdefinierten Vorlagen
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] kommt mit einer Reihe von Vorlagen für viele häufig ausgeführten Aufgaben. Der größte Vorteil von Vorlagen besteht jedoch darin, dass Sie für ein komplexes Skript, das Sie häufig erstellen müssen, eine benutzerdefinierte Vorlage anlegen können. Sie werden nun ein einfaches Skript mit wenigen Parametern erstellen. Vorlagen sind jedoch auch bei umfangreichen Skripts mit vielen Wiederholungen nützlich.  
  
## <a name="using-custom-templates"></a>Verwenden benutzerdefinierter Vorlagen  
  
#### <a name="to-create-a-custom-template"></a>So erstellen Sie eine benutzerdefinierte Vorlage  
  
1.  Erweitern Sie **SQL Server-Vorlagen**im Vorlagen-Explorer, klicken Sie mit der rechten Maustaste auf **Gespeicherte Prozedur**, zeigen Sie auf **Neu**, und klicken Sie anschließend auf **Ordner**.  
  
2.  Geben Sie **Custom** als Namen für den neuen Vorlagenordner ein, und drücken Sie anschließend die EINGABETASTE.  
  
3.  Klicken Sie mit der rechten Maustaste auf **Custom**, zeigen Sie auf **Neu**, und klicken Sie anschließend auf **Vorlage**.  
  
4.  Geben Sie **WorkOrdersProc** als Namen für die neue Vorlage ein, und drücken Sie anschließend die **EINGABETASTE**.  
  
5.  Klicken Sie mit der rechten Maustaste auf **WorkOrdersProc**und anschließend auf **Bearbeiten**.  
  
6.  Überprüfen Sie im Dialogfeld **Verbindung mit Datenbank-Engine herstellen** die Verbindungseinstellungen, und klicken Sie anschließend auf **Verbinden**.  
  
7.  Geben Sie im Abfrage-Editor das folgende Skript ein, um eine gespeicherte Prozedur zu erstellen, über die Bestellungen für ein bestimmtes Teil gesucht werden. In diesem Fall handelt es sich um Klingen (Blade). (Sie können den Code im Fenster des Lernprogramms kopieren und dann einfügen.)  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersForBlade')  
       DROP PROCEDURE dbo.WorkOrdersForBlade;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersForBlade  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = 'Blade';  
    GO  
    ```  
  
8.  Drücken Sie F5, um das Skript auszuführen. Damit wird die Prozedur **WorkOrdersForBlade** erstellt.  
  
9. Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf Ihren Server und anschließend auf **Neue Abfrage**. Ein neues Abfrage-Editorfenster wird geöffnet.  
  
10. Geben Sie im Abfrage-Editor **EXECUTE dbo.WorkOrdersForBlade**ein, und drücken Sie anschließend F5, um die Abfrage auszuführen. Überprüfen Sie, ob im Bereich **Ergebnisse** eine Liste mit Bestellungen für Klingen zurückgegeben wird.  
  
11. Bearbeiten Sie das Vorlagenskript (das Skript in Schritt 7), und Ersetzen Sie dabei den Produktnamen "Blade" mit dem Parameter  <strong> *<* Product_name</strong>, `nvarchar(50)`, <strong>Namen *>* </strong> , an vier Stellen.  
  
    > [!NOTE]  
    >  Für Parameter sind drei Elemente erforderlich: der Name des zu ersetzenden Parameters, der Datentyp des Parameters und ein Standardwert für den Parameter.  
  
12. Das Skript sollte nun wie folgt aussehen:  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersFor<product_name, nvarchar(50), name>')  
       DROP PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = '<product_name, nvarchar(50), name>';  
    GO  
    ```  
  
13. Klicken Sie im Menü **Datei** auf **WorkOrdersProc.sql speichern** , um Ihre Vorlage zu speichern.  
  
#### <a name="to-test-the-custom-template"></a>So testen Sie die benutzerdefinierte Vorlage  
  
1.  Erweitern Sie im Vorlagen-Explorer **Gespei6cherte Prozeduren**, erweitern Sie **Benutzerdefiniert**, und doppelklicken Sie anschließend auf **WorkOrderProc**.  
  
2.  Vervollständigen Sie im Dialogfeld **Verbindung mit Datenbank-Engine herstellen** die Verbindungseinstellungen, und klicken Sie anschließend auf **Verbinden**. Ein neues Fenster des Abfrage-Editors wird geöffnet, in dem der Inhalt der Vorlage **WorkOrderProc** angezeigt wird.  
  
3.  Klicken Sie im Menü **Abfrage** auf **Werte für Vorlagenparameter angeben**.  
  
4.  In der **Vorlagenparameter** im Dialogfeld für die `product_name` -Wert, geben Sie **FreeWheel** (überschreiben dabei den Standardinhalt), und klicken Sie dann auf **OK** zu schließen die **Vorlagenparameter** Dialogfeld ein, und ändern Sie das Skript im Abfrage-Editor.  
  
5.  Drücken Sie F5, um das Skript auszuführen. Damit wird die Prozedur erstellt.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Speichern von Skripts als Projekte oder Lösungen](lesson-3-3-save-scripts-as-projects-or-solutions.md)  
  
  
