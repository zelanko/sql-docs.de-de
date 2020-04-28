---
title: 'Aufgabe 6: überprüfen, ob das Domänen basierte Attribut mit Master Data Manager erstellt wurde | Microsoft-Dokumentation'
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
ms.openlocfilehash: 56418adbefec0dc996fd83ce70415e86ec9509a3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78171660"
---
# <a name="task-6-verify-that-the-domain-based-attribute-is-created-using-master-data-manager"></a>Aufgabe 6: Überprüfen, ob das domänenbasierte Attribut mithilfe von Master Data Manager erstellt wurde
  In dieser Aufgabe überprüfen Sie mit **Master Data Manager**, ob die Entität **Bundesland** in **MDS** erstellt wird und ob das Attribut **Bundesland** der Entität **Lieferant** ein domänenbasiertes Attribut ist, das von der Entität **Bundesland** abhängig ist.

1.  Wechseln Sie zur **Master Data Manger**-Webanwendung.

2.  Klicken Sie oben auf **SQL Server 2012 Master Data Services**, um zur Startseite zu gelangen.

3.  Stellen Sie sicher, dass das Modell **Lieferanten** ausgewählt ist, und klicken Sie auf **Explorer**. Sie können die Seite aktualisieren, wenn **Explorer** bereits geöffnet ist.

4.  Bewegen Sie die Maus über **Entitäten** in der Menüleiste. Es sind nun zwei Entitäten vorhanden: **Supplier** und **State**.

     ![Menü "Entitäten" mit Bundesland und Lieferant](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-01.jpg "Menü "Entitäten" mit Bundesland und Lieferant")

5.  Klicken Sie auf **Bundesland**, wenn die Entität noch nicht geöffnet ist.

6.  Wählen Sie **GA** aus der Liste aus.

7.  Ändern Sie im rechten Bereich **Details** den **Name**n im **rechten Bereich** in **Georgia**, und klicken Sie auf **OK**.

8.  Wiederholen Sie die vorherigen Schritte für andere Bundesländer.

    |Code|Name|
    |----------|----------|
    |CA|Kalifornien|
    |CO|Colorado|
    |BY|Illinois|
    |DC|District of Columbia|
    |FL|Florida|
    |AL|Alabama|
    |HE|Kentucky|
    |NI|Massachusetts|
    |RP|Arizona|
    |MI|Michigan|
    |BB|Minnesota|
    |NJ|New Jersey|
    |SH|Nevada|
    |NY|New York|
    |HH|Ohio|
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

     ![Attribut mit aktualisiertem Code und Namen von Bundesstaaten](../../2014/tutorials/media/et-verifythatthedbaiscreatedusingmdm-02.jpg "Attribut mit aktualisiertem Code und Namen von Bundesstaaten")

## <a name="next-step"></a>Nächster Schritt
 [Aufgabe 7: Anzeigen von Updates, die mit Master Data Manager in Excel durchgeführt wurden](../../2014/tutorials/task-7-viewing-updates-made-using-master-data-manager-in-excel.md)


