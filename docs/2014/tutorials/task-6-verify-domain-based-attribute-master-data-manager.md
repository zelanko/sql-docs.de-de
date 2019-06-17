---
title: 'Aufgabe 6: Stellen Sie sicher, dass das domänenbasierte Attribut erstellt wird, mithilfe von Master Data Manager | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 6e90517a-910c-4c33-8f11-92ac3cff4fdc
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: fe3f404d4f41e2977ef389216dcbc9106327266a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65488953"
---
# <a name="task-6-verify-that-the-domain-based-attribute-is-created-using-master-data-manager"></a>Aufgabe 6: Überprüfen, ob das domänenbasierte Attribut mithilfe von Master Data Manager erstellt wurde
  In dieser Aufgabe überprüfen Sie mit **Master Data Manager**, ob die Entität **Bundesland** in **MDS** erstellt wird und ob das Attribut **Bundesland** der Entität **Lieferant** ein domänenbasiertes Attribut ist, das von der Entität **Bundesland** abhängig ist.  
  
1.  Wechseln Sie zur **Master Data Manger**-Webanwendung.  
  
2.  Klicken Sie oben auf **SQL Server 2012 Master Data Services**, um zur Startseite zu gelangen.  
  
3.  Stellen Sie sicher, dass das Modell **Lieferanten** ausgewählt ist, und klicken Sie auf **Explorer**. Sie können die Seite aktualisieren, wenn **Explorer** bereits geöffnet ist.  
  
4.  Der Mauszeiger über **Entitäten** auf der Menüleiste und nun zwei Entitäten vorhanden sind: **Lieferanten** und **Zustand**.  
  
     ![Menü "Entitäten" mit Bundesland und Lieferant](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-01.jpg "Menü \"Entitäten\" mit Bundesland und Lieferant")  
  
5.  Klicken Sie auf **Bundesland**, wenn die Entität noch nicht geöffnet ist.  
  
6.  Wählen Sie **GA** aus der Liste aus.  
  
7.  Ändern Sie im rechten Bereich **Details** den **Name**n im **rechten Bereich** in **Georgia**, und klicken Sie auf **OK**.  
  
8.  Wiederholen Sie die vorherigen Schritte für andere Bundesländer.  
  
    |Code|Name|  
    |----------|----------|  
    |CA|California|  
    |CO|Baden-Württemberg|  
    |BY|Bayern|  
    |SL|Saarland|  
    |SN|Sachsen|  
    |AL|Thüringen|  
    |HE|Hessen|  
    |NI|Niedersachsen|  
    |RP|Rheinland-Pfalz|  
    |ST|Sachsen-Anhalt|  
    |BB|Brandenburg|  
    |MV|Mecklenburg-Vorpommern|  
    |SH|Schleswig-Holstein|  
    |BER|Berlin|  
    |HH|Hamburg|  
    |OK|Oklahoma|  
    |oder|Oregon|  
    |PA|Pennsylvania|  
    |SC|South Carolina|  
    |KS|Kansas|  
    |TN|Tennessee|  
    |TX|Texas|  
    |UT|Utah|  
    |VA|Virginia|  
    |WA|Washington|  
    |WI|Wisconsin|  
    |HI|Hawaii|  
    |MD|Maryland|  
    |CT|Connecticut|  
  
9. Wählen Sie ein beliebiges Bundesland aus, und klicken Sie auf **Transaktionen anzeigen** in der Symbolleiste. Es sollte die Transaktion für das gerade vorgenommene Update in der Liste der Transaktionen angezeigt werden.  
  
10. Bewegen Sie die Maus über das Menü **Entitäten**, und klicken Sie auf **Lieferant**.  
  
11. Der Wert für das Feld **Bundesland** kann im Bereich **Details** über die Dropdownliste geändert werden. Sie können auch sehen, dass in der Liste links und in der Dropdownliste im Bereich **Details** zuerst Code und dann der Name in geschweiften Klammern angezeigt wird. Sie können auch jeden beliebigen anderen Wert im Bereich **Details** ändern.  
  
     ![Status-Attribut mit aktualisiertem Code und Namen](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-02.jpg "Attribut mit aktualisiertem Code und Namen angeben")  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 7: Anzeigen von Updates vorgenommen, mit der Master Data Manager in Excel](../../2014/tutorials/task-7-viewing-updates-made-using-master-data-manager-in-excel.md)  
  
  
