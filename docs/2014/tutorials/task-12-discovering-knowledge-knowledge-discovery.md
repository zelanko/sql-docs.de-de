---
title: 'Aufgabe 12: Ermitteln von Kenntnissen (Wissens Ermittlung) | Microsoft-Dokumentation'
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "65484682"
---
# <a name="task-12-discovering-knowledge-knowledge-discovery"></a>Aufgabe 12: Ermitteln von Wissen (Wissensermittlung)
  In dieser Aufgabe führen Sie die **Wissens** Ermittlungs Aktivität für die Domänen **Supplier ID** und **Supplier Name** aus. In diesem Szenario importiert der Wissensermittlungsprozess hauptsächlich Werte für diese zwei Domänen.  
  
 In diesem Lernprogramm haben Sie eine Wissensdatenbank von Grund auf neu erstellt. Sie können eine Wissensdatenbank auch durch Ausführen einer Wissensermittlungsaktivität erstellen. Wenn Sie auf der Hauptseite auf **Wissensdatenbank erstellen** klicken, führt der DQS-Client Sie zu einer Seite, auf der die **Domänen Verwaltungs** Aktivität für die Aktivität ausgewählt ist. Sie können die **Aktivität** in **Wissens** Ermittlung ändern und dann auf der nächsten Seite Domänen als Teil des Wissens Ermittlungs Prozesses erstellen. Weitere Informationen finden Sie unter [Durchführen der Wissens](https://msdn.microsoft.com/library/hh510398.aspx) Ermittlung.  
  
1.  Klicken Sie auf der Hauptseite des DQS-Clients im Abschnitt **Letzte Wissensdatenbank** auf den **Pfeil nach rechts** neben der Wissensdatenbank **Suppliers** , und klicken Sie auf **Wissens**Ermittlung. Sie können auch auf **Wissensdatenbank öffnen**klicken, in der **Liste der Wissensdatenbanken** **Lieferanten** auswählen, als **Aktivität** **Wissens** Ermittlung auswählen und auf **weiter**klicken.  
  
     ![Menü "Wissensermittlung" auf der Hauptseite](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "Menü "Wissensermittlung" auf der Hauptseite")  
  
2.  Wählen Sie **Excel-Datei** für **Datenquelle**aus.  
  
3.  Klicken Sie auf **Durchsuchen**, navigieren Sie zu **Suppliers. xls**, und klicken Sie auf **Öffnen**.  
  
4.  Wählen Sie **Suppliers für** die Ermittlung für das **Arbeitsblatt**aus.  
  
5.  Ordnen Sie **im Abschnitt "** Zuordnungen" die Spalte " **SupplierID** " aus der **Excel** -Datei der Domäne " **Supplier ID** " und der Spalte " **Supplier Name** " mithilfe von **Dropdown Listen**der Domäne des **Lieferanten namens** zu. Die Excel-Datei enthält Beispiel Daten für die Domänen **Supplier ID** und **Supplier Name** . Im Ermittlungsprozess können Sie die Domänen auswählen, für die Werte ermittelt werden sollen. Sie können Domänen auf dieser Seite erstellen und dann die Quellspalten diesen Domänen zuordnen. Es ist nicht ungewöhnlich, Domänen während der Wissensermittlungsaktivität zu erstellen, anstatt während der Domänenverwaltungsaktivität.  
  
     ![Seite "Zuordnen" im Ermittlungsprozess](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "Seite "Zuordnen" im Ermittlungsprozess")  
  
6.  Klicken Sie auf **weiter** , um zur Seite **ermitteln** zu wechseln.  
  
7.  Klicken Sie auf der Seite **ermitteln** auf **Start** , um den Ermittlungsprozess zu starten. Die Ermittlung erfolgt in den Spalten **SupplierID** und **Supplier Name** in der Datei **Suppliers. xls** . Die Domänen **Supplier ID** und **Supplier Name** müssen mit den von der Ermittlung erstellten Kenntnissen aufgefüllt werden.  
  
     ![Seite "Ermitteln" im Ermittlungsprozess](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "Seite "Ermitteln" im Ermittlungsprozess")  
  
8.  Nachdem die Analyse abgeschlossen ist, überprüfen Sie die **Quell Statistik** auf der **Registerkarte Profiler** unten auf der Seite. Beachten Sie, dass 10 neue Datensätze mit den Gesamtwerten 20 Werte (**SupplierID** und **Supplier Name** aus dem **Excel-Arbeitsblatt**) ermittelt wurden. Sie sehen auch, wie viele der Werte neu, eindeutig, neu und eindeutig und gültig sind. Im Listenfeld auf der rechten Seite werden weitere Details für jede Domäne angezeigt, die am Ermittlungsprozess beteiligt ist. Wenn Sie mit der Maus auf die Statusleiste in der Spalte "Vollständigkeit" zeigen, können Sie feststellen, ob Werte in den Spalten in der Quelle fehlen.  
  
     ![Ergebnisse der Wissensermittlung](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "Ergebnisse der Wissensermittlung")  
  
9. Klicken Sie auf **weiter** , um zur Seite **Domänen Werte verwalten** zu wechseln.  
  
10. Klicken Sie auf der Seite **Domänen Werte verwalten** in der Liste der Domänen auf **Lieferanten Name** Domäne.  
  
11. Klicken Sie im rechten Bereich mit der rechten Maustaste auf **Lazy Country Storex** (Beachten Sie "x" am Ende), und wählen Sie " **Lazy Country Store**". DQS schlägt diese Änderung vor, nachdem die Rechtschreibprüfung in der Domäne ausgeführt wurde. Standardmäßig ist die Rechtschreibprüfung in den Domänen aktiviert, die Sie erstellen.  
  
     ![Richtiger Lieferantenname – Lazy Country Store](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "Richtiger Lieferantenname – Lazy Country Store")  
  
12. Vergewissern Sie sich in der Liste Domänen Werte, dass der Wert **Lazy Country Storex** als Fehler (rote **X** -Markierung) mit **Lazy Country Store** als Korrektur festgelegt ist und dass auch der **Lazy Country-Speicher** als gültiger Wert hinzugefügt wird.  
  
     ![Domänenwert und "Korrigieren in"-Wert](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "Domänenwert und "Korrigieren in"-Wert")  
  
13. Klicken Sie auf **Fertig stellen**.  
  
14. Klicken Sie im Dialogfeld **SQL Server Data Quality Services** auf **veröffentlichen**.  
  
15. Klicken Sie im Feld Erfolgsmeldung auf **OK** .  
  
     Sie haben die erste Lektion des Lernprogramms abgeschlossen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 2: Bereinigung von Lieferantendaten mithilfe der Wissensdatenbank 'Suppliers'](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)  
  
  
