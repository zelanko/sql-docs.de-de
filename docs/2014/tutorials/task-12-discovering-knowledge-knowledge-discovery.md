---
title: 'Aufgabe 12: Ermitteln von wissen (Wissensermittlung) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: dd80a8e6-1e41-4c49-9898-02b1d2505a10
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 6dd54475ee63b2f6ef5e1b56b94c11aafd5996ff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65484682"
---
# <a name="task-12-discovering-knowledge-knowledge-discovery"></a>Aufgabe 12: Wissensermittlung
  In dieser Aufgabe führen Sie die **Wissensermittlung** auf **Supplier ID** und **Lieferantenname** Domänen. In diesem Szenario importiert der Wissensermittlungsprozess hauptsächlich Werte für diese zwei Domänen.  
  
 In diesem Lernprogramm haben Sie eine Wissensdatenbank von Grund auf neu erstellt. Sie können eine Wissensdatenbank auch durch Ausführen einer Wissensermittlungsaktivität erstellen. Beim Klicken auf **Erstellen einer Wissensdatenbank** in der Hauptseite des DQS-Client gelangen Sie auf eine Seite mit **Domänenverwaltung** -Aktivität für die Aktivität ausgewählt. Sie können ändern, die **Aktivität** zu **Wissensermittlung** , und klicken Sie dann Sie auf der nächsten Seite Domänen, als Teil des wissensermittlungsprozesses erstellen. Finden Sie unter [Durchführen der Wissensermittlung](https://msdn.microsoft.com/library/hh510398.aspx) Weitere Details.  
  
1.  Auf der Hauptseite der DQS-Client in der **zuletzt verwendete Wissensdatenbank** auf **nach rechts weisenden Pfeil** neben der **Lieferanten** Knowledge Base, und klicken Sie auf **Knowledge Ermittlung**. Alternativ können Sie klicken **Wissensdatenbank öffnen**Option **Lieferanten** aus der **Liste der Wissensdatenbanken**Option **Wissensermittlung**als **Aktivität** , und klicken Sie auf **Weiter**.  
  
     ![Knowledge Discovery-Menü auf der Hauptseite Seite](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "Knowledge Discovery-Menü auf der Hauptseite Seite")  
  
2.  Wählen Sie **Excel-Datei** für **Datenquelle**.  
  
3.  Klicken Sie auf **Durchsuchen**, navigieren Sie, und wählen Sie **Suppliers.xls**, und klicken Sie auf **öffnen**.  
  
4.  Wählen Sie **Suppliers for Discovery** für **Arbeitsblatt**.  
  
5.  In der **Zuordnungen** ordnen **SupplierID** Spalte aus der **Excel** -Datei in die **Supplier ID** Domäne und  **Lieferantenname** Spalte, um die **Lieferantenname** Domäne mithilfe von **Dropdownlisten**. Die Excel-Datei enthält Beispieldaten für die **Supplier ID** und **Lieferantenname** Domänen. Im Ermittlungsprozess können Sie die Domänen auswählen, für die Werte ermittelt werden sollen. Sie können Domänen auf dieser Seite erstellen und dann die Quellspalten diesen Domänen zuordnen. Es ist nicht ungewöhnlich, Domänen während der Wissensermittlungsaktivität zu erstellen, anstatt während der Domänenverwaltungsaktivität.  
  
     ![Ordnen Sie auf der Seite Ermittlungsprozess](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "Seite Ermittlungsprozess \"zuordnen\"")  
  
6.  Klicken Sie auf **Weiter** zum Wechseln der **Discover** Seite.  
  
7.  Auf der **Discover** auf **starten** um den Discovery-Prozess zu starten. Ermittlung wird ausgeführt, für die Spalten **SupplierID** und **Lieferantenname** in die **Suppliers.xls** Datei. Die **Supplier ID** und **Lieferantenname** Domänen mit dem die aus der Ermittlung gewonnenen wissen aufgefüllt werden soll.  
  
     ![Ermitteln Sie auf der Seite Ermittlungsprozess](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "ermitteln Sie auf der Seite Ermittlungsprozess")  
  
8.  Nachdem die Analyse abgeschlossen ist, überprüfen Sie die **Quellstatistik** in die **Registerkarte "Profiler"** am unteren Rand der Seite. Beachten Sie, dass 10 neue Datensätze mit 20 Werten insgesamt (**SupplierID** und **Lieferantenname** Werte aus der **Excel-Arbeitsblatt**) wurden gefunden. Sie sehen auch, wie viele der Werte neu, eindeutig, neu und eindeutig und gültig sind. Im Listenfeld auf der rechten Seite werden weitere Details für jede Domäne angezeigt, die am Ermittlungsprozess beteiligt ist. Wenn Sie mit der Maus auf die Statusleiste in der Spalte "Vollständigkeit" zeigen, können Sie feststellen, ob Werte in den Spalten in der Quelle fehlen.  
  
     ![Ergebnisse der Wissensermittlung](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "Ergebnisse der Wissensermittlung")  
  
9. Klicken Sie auf **Weiter** zum Wechseln der **Domänenwerte verwalten** Seite.  
  
10. In der **Domänenwerte verwalten** auf **Lieferantenname** Domäne aus der Liste der Domänen.  
  
11. Klicken Sie im rechten Bereich mit der Maustaste **Lazy Country Storex** (Beachten Sie, dass "X" am Ende), und wählen Sie **Lazy Country Store**. DQS schlägt diese Änderung vor, nachdem die Rechtschreibprüfung in der Domäne ausgeführt wurde. Standardmäßig ist die Rechtschreibprüfung in den Domänen aktiviert, die Sie erstellen.  
  
     ![Richtiger Lieferantenname – Lazy Country Store](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "richtiger Lieferantenname – Lazy Country Store")  
  
12. Der domänenwerteliste sicher, dass der Wert **Lazy Country Storex** festgelegt ist, als Fehler (Rot **X** markieren) mit **Lazy Country Store** als die Korrektur und auch die **Lazy Country Store** wird auch als gültiger Wert hinzugefügt.  
  
     ![Domäne Wert ein, und beheben Sie Wert](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "Domäne Wert ein, und beheben Sie Wert")  
  
13. Klicken Sie auf **Fertig stellen**.  
  
14. Auf **SQL Server Data Quality Services** Dialogfeld klicken Sie auf **veröffentlichen**.  
  
15. Klicken Sie auf **OK** im Meldungsfeld, Erfolg.  
  
     Sie haben die erste Lektion des Lernprogramms abgeschlossen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Lektion 2: Bereinigung von Lieferantendaten mithilfe der Wissensdatenbank ' Suppliers '](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)  
  
  
