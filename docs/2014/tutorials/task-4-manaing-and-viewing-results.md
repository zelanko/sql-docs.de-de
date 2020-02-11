---
title: 'Aufgabe 4: Management-und Anzeigeergebnisse | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: ecc3ba7e-fecf-478f-8825-6e4764b00e99
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 8b97b0129a7cc4ffa21b4a82ad0208a2c1890b27
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "72313648"
---
# <a name="task-4-manaing-and-viewing-results"></a>Aufgabe 4: Verwalten und Anzeigen der Ergebnisse
  In dieser Aufgabe überprüfen Sie die Ergebnisse der computerunterstützten Bereinigung und führen auch die interaktive Bereinigung für Lieferantendaten aus. Weitere Informationen finden Sie in der interaktiven Bereinigungs [Phase](https://msdn.microsoft.com/library/hh213061.aspx#Interactive) .  
  
1.  Wählen Sie in der Liste der Domänen **Contact Email** Domain aus.  
  
2.  Wechseln Sie im rechten Bereich zur Registerkarte **ungültig** . Beachten Sie, dass zwei e-Mail-Adressen, für die das Zeichen ' ' am Ende fehlt. Diese beiden e-Mails sind von der Domänen Regel ungültig, die erfordert, dass alle e-Mail-Adressen mit ** \@Adventure-Works.com** (mit ' ') enden. DQS verwendet die Domänenregel bei der Bereinigung, um zu bestimmen, ob eine E-Mail gültig ist. Diese Registerkarte zeigt die Domänenwerte an, die in der Wissensdatenbank als ungültig markiert wurden oder die eine Domänenregel verletzt haben. In diesem Fall haben diese Werte die Domänenregel (E-Mail-Überprüfung) verletzt.  
  
3.  Geben Sie in der Spalte **korrigieren in** die richtige e-Mail-Adresse ein, die mit ** \@Adventure-Works.com** endet (mit "s").  
  
     ![Korrekturen der E-Mail-Überprüfungsregel](../../2014/tutorials/media/et-managingandviewingresults-01.jpg "Korrekturen der E-Mail-Überprüfungsregel")  
  
4.  Klicken Sie für beide Datensätze auf **genehmigen** , um beide Änderungen zu genehmigen. Wenn Sie genehmigen, werden die Datensätze auf die Registerkarte **korrigiert** verschoben. Anstatt jedes Element einzeln zu genehmigen, können Sie alle Änderungen gleichzeitig mithilfe der Symbolleisten Schaltfläche **alle Begriffe genehmigen** genehmigen.  
  
5.  Wechseln Sie zur Registerkarte **neu** im rechten Bereich. Die Werte in dieser Registerkarte sind die Werte, für die DQS noch nicht genug Informationen in der Wissensdatenbank hat, um zu bestimmen, ob die Werte richtig sind. Daher können keine Änderungen an Domänenwerten vorgenommen oder vorgeschlagen werden.  
  
6.  Überprüfen Sie die Werte, um zu bestätigen, dass alle e-Mails mit ** \@Adventure-Works.com** enden, und klicken Sie auf der Symbolleiste auf **alle Bedingungen genehmigen** . Die genehmigten Werte aus dieser Registerkarte werden auf die Registerkarte **richtig** verschoben.  
  
7.  Wählen Sie die Domäne **Country** aus der Liste der Domänen aus.  
  
8.  Wechseln Sie zur Registerkarte **korrigiert** im rechten Bereich, und beachten Sie, dass der Wert des **Vereinigten Zustands** automatisch in den **USA** mit "es" am Ende korrigiert wird. Diese Regel ist keine Regel, die Sie für die Domäne " **Country** " definiert haben, aber DQS ist **83%** sicher, dass der richtige Wert **USA**ist. Die Schaltfläche **genehmigen** wird automatisch für alle **korrigierten** Elemente ausgewählt. Sie können dieses Verhalten überschreiben und eine Änderung ablehnen.  
  
9. Beachten Sie, dass die **USA** in **USA** korrigiert werden, weil es sich um Synonyme handelt und **USA** der führende (bevorzugte) Wert ist.  
  
     ![Korrekturen auf der Grundlage von Synonymen](../../2014/tutorials/media/et-managingandviewingresults-02.jpg "Korrekturen auf der Grundlage von Synonymen")  
  
10. Beachten Sie, dass die Schaltfläche **genehmigen** bereits für diese korrigierten Werte ausgewählt ist. Dieses Verhalten ist der Standardwert für die korrigierten Werte. Sie können eine Änderung ablehnen. Wenn Sie dies tun, wird der Wert auf die Registerkarte **ungültig** verschoben.  
  
11. Wählen Sie **Lieferanten Name** aus der Liste der Domänen aus.  
  
12. Wechseln Sie zur Registerkarte **korrigiert** im rechten Bereich.  
  
     ![Korrigierte Lieferantennamen](../../2014/tutorials/media/et-managingandviewingresults-03.jpg "Korrigierte Lieferantennamen")  
  
    1.  Beachten Sie, dass **a. Datum Corp.** in **a. Datum Corporation** korrigiert wird und der **Grund** auf **Begriffs basierte Beziehung festgelegt ist. A. Datum Corporation** ist ein bekannter Domänen Wert für DQS, weil er während des Wissens Ermittlungs Prozesses erkannt wurde. Daher ist DQS für diese Korrektur **100% sicher** .  
  
    2.  Beachten Sie, dass **Lazy Country Storex** in **Lazy Country Store**korrigiert wird, der **Vertrauensgrad** auf **100%** festgelegt ist und der **Grund** auf den **Domänen Wert**festgelegt ist. Während des Wissens Ermittlungs Prozesses legen Sie **Lazy Country Storex** als Fehler bei **Lazy Country Store** als **Korrektur**fest, sodass die Korrektur durch DQS **100% sicher** ist.  
  
    3.  DQS ist nicht mit den anderen Werten in der Liste vertraut, aber es wurden die Korrekturen für diese Werte mithilfe der **Rechtschreib** Prüfung gefunden, und es werden die entsprechenden Korrekturen vorgeschlagen. DQS ist für diese Korrekturen **nicht 100%** sicher, aber der Vertrauensgrad liegt über 80%. Dies ist der Schwellenwert für Korrekturen, daher schlägt DQS die Korrekturen vor.  
  
13. Beachten Sie, dass die Option **genehmigen** automatisch für alle Werte aktiviert ist. Sie können den korrigierten Wert überschreiben oder die Änderung nach Bedarf ablehnen. Standardmäßig wird die Schaltfläche **genehmigen** für alle Werte auf der Registerkarte **korrigiert** ausgewählt.  
  
14. Wechseln Sie zur Registerkarte **neu** .  
  
15. Beachten Sie, dass **Corp.** in **Corporation**korrigiert, **Co.** in **Company**und **Inc.** korrigiert **wurde.** Beispielsweise wird " **konsolidiert Inc.** " korrigiert, um das integrierte und **konsolidierte Co** zu **konsolidieren** . wird in **konsolidiertes Unternehmen**korrigiert und **frabrikam Corp.** wird in **Fabrikam Corporation**korrigiert.  Sie können sehen, dass die **Begriffs basierte Beziehung** als Grund angegeben wird. Diese Änderungen werden mit den begriffsbasierten Beziehungen vorgeschlagen, die Sie während der Domänenverwaltungsaktivität definiert haben. Sie können die Werte **für korrigieren in** manuell ändern.  
  
16. Führen Sie einen Bildlauf in der Liste durch, um den " **hunxgry Coyote Store** " mit einer roten Wellenlinie anzuzeigen. Klicken Sie mit der rechten Maustaste darauf, und klicken Sie auf " **Hungy Coyote Store** " (ohne "x"). Die Spalte " **korrigieren in** " sollte automatisch mit dem **hungrigen Coyote-Speicher**aufgefüllt werden. Sie können einen Wert in der Spalte "Korrigieren in" auch manuell eingeben.  
  
17. Klicken Sie in der Symbolleiste auf **alle Bedingungen genehmigen** . Die Domänen Werte, bei denen der Wert " **richtig** " angegeben ist, werden auf die Registerkarte **korrigiert** verschoben, und die neuen Werte ohne zugeordnete **korrekte** Werte werden auf die Registerkarte **richtig** verschoben.  
  
18. Wählen Sie in der Liste Domäne die Verbund Domäne **Address Validation** aus.  
  
19. Wechseln Sie im rechten Bereich zur Registerkarte **richtig** . Es sollten die Adressen angezeigt werden, die durch den DQS-Dienst " **Melissa-Daten Adressüberprüfung** " auf der **Azure Marketplace**korrekt gefunden werden.  
  
20. Wechseln Sie zur Registerkarte **korrigiert** .  
  
21. Beachten Sie, dass der **Status** für den Datensatz, der **City** als **Los Angeles** hat, jetzt auf **ca** festgelegt ist. Beachten Sie, dass das Feld " **Grund** **" durch die Regel "City-State Rule" korrigiert wurde**.  
  
     ![Korrektur der "City-State"-Regel](../../2014/tutorials/media/et-managingandviewingresults-04.jpg "Korrektur der "City-State"-Regel")  
  
22. Beachten Sie, dass das Optionsfeld **genehmigen** bereits für dieses Element in der Liste ausgewählt ist. Dies ist das Standardverhalten für Elemente auf der Registerkarte **korrigiert** .  
  
23. Wechseln Sie zur Registerkarte **vorgeschlagen** . Überprüfen Sie die vom **Melissa-Daten Adress Überprüfungs** Dienst empfohlenen Änderungen.  
  
24. Klicken Sie in der Symbolleisten Schaltfläche auf **alle Bedingungen genehmigen** , und klicken Sie im **Bestätigungs** Meldungs Feld auf **OK**  
  
     ![Alle Begriffe genehmigen (Symbolleistenschaltfläche)](../../2014/tutorials/media/et-managingandviewingresults-05.jpg "Alle Begriffe genehmigen (Symbolleistenschaltfläche)")  
  
25. Klicken Sie auf **weiter** , um zur Seite **exportieren** zu wechseln.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 5: Exportieren der Bereinigungsergebnisse in eine Excel-Datei](../../2014/tutorials/task-5-exporting-cleansing-results-to-an-excel-file.md)  
  
  
