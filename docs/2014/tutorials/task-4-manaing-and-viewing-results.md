---
title: 'Aufgabe 4: Verwalten und Anzeigen der Ergebnisse | Microsoft Docs'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ecc3ba7e-fecf-478f-8825-6e4764b00e99
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0e045d9722d380af19147746944c842f97ac9843
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162390"
---
# <a name="task-4-manaing-and-viewing-results"></a>Aufgabe 4: Verwalten und Anzeigen der Ergebnisse
  In dieser Aufgabe überprüfen Sie die Ergebnisse der computerunterstützten Bereinigung und führen auch die interaktive Bereinigung für Lieferantendaten aus. Finden Sie unter [interaktive Bereinigungsphase](http://msdn.microsoft.com/library/hh213061.aspx#Interactive) Weitere Details.  
  
1.  Wählen Sie **Contact Email** Domäne aus der Liste der Domänen.  
  
2.  Wechseln Sie zu der **ungültige** Registerkarte im rechten Bereich. Beachten Sie, dass zwei E-Mail-Adressen nicht das Zeichen "s" am Ende aufweisen. Diese beiden e-Mails, die gefunden wurden, werden ungültige gemäß der domänenregel, die alle e-Mail-Adressen endet nicht mit erfordert **@adventure-works.com** (mit der "). DQS verwendet die Domänenregel bei der Bereinigung, um zu bestimmen, ob eine E-Mail gültig ist. Diese Registerkarte zeigt die Domänenwerte an, die in der Wissensdatenbank als ungültig markiert wurden oder die eine Domänenregel verletzt haben. In diesem Fall haben diese Werte die Domänenregel (E-Mail-Überprüfung) verletzt.  
  
3.  In der **korrigieren in** Spalte, die richtige e-Mail-Adresse, die diesem Ende mit, Typ **@adventure-works.com** (mit der ").  
  
     ![Korrekturen aus dem e-Mail-Überprüfungsregel](../../2014/tutorials/media/et-managingandviewingresults-01.jpg "Korrekturen aus dem e-Mail-Überprüfungsregel")  
  
4.  Klicken Sie auf **genehmigen** für beide Datensätze, die Änderungen zu genehmigen. Wenn Sie genehmigt haben, die Datensätze zu verschieben die **korrigiert** Registerkarte. Statt jedes Element einzeln genehmigen, können Sie alle Änderungen, die gleichzeitig mit Genehmigen der **alle Begriffe genehmigen** Symbolleisten-Schaltfläche.  
  
5.  Wechseln Sie zu der **neu** Registerkarte im rechten Bereich. Die Werte in dieser Registerkarte sind die Werte, für die DQS noch nicht genug Informationen in der Wissensdatenbank hat, um zu bestimmen, ob die Werte richtig sind. Daher können keine Änderungen an Domänenwerten vorgenommen oder vorgeschlagen werden.  
  
6.  Überprüfen Sie die Werte, um sicherzustellen, dass alle e-Mails enden **@adventure-works.com** , und klicken Sie auf **alle Begriffe genehmigen** auf der Symbolleiste. Verschieben Sie die genehmigten Werte aus dieser Registerkarte auf die **richtig** Registerkarte.  
  
7.  Wählen Sie die **Land** Domäne aus der Liste der Domänen.  
  
8.  Wechseln Sie zu der **korrigiert** Registerkarte im rechten Bereich, und beachten Sie, dass **United State** Wert wird automatisch korrigiert, um die **United States** mit der "am Ende. Diese Regel ist es sich nicht um eine Regel, die Sie, für definiert die **Land** Domäne, aber DQS ist **83 %** sicher, dass der richtige Wert **United States**. Die **genehmigen** Schaltfläche wird automatisch ausgewählt, für alle der **korrigiert** Elemente. Sie können dieses Verhalten überschreiben und eine Änderung ablehnen.  
  
9. Beachten Sie, dass **USA** korrigiert wird, um **United States** , da sie Synonyme sind und **United States** der führende (bevorzugte) Wert ist.  
  
     ![Korrekturen auf der Grundlage von Synonymen](../../2014/tutorials/media/et-managingandviewingresults-02.jpg "Korrekturen auf der Grundlage von Synonymen")  
  
10. Beachten Sie, dass die **genehmigen** Schaltfläche bereits für diese korrigierten Werte ausgewählt ist. Dieses Verhalten ist der Standardwert für die korrigierten Werte. Sie können eine Änderung ablehnen und wenn Sie dies tun, verschiebt der Wert in der **ungültige** Registerkarte.  
  
11. Wählen Sie **Lieferantenname** aus der Liste der Domänen.  
  
12. Wechseln Sie zu der **korrigiert** Registerkarte im rechten Bereich.  
  
     ![Korrigierte Lieferantennamen](../../2014/tutorials/media/et-managingandviewingresults-03.jpg "korrigierte Lieferantennamen")  
  
    1.  Beachten Sie, dass **A. Datum Corp.** korrigiert wird, um **A. Datum Corporation** und **Grund** festgelegt ist, um **begriffsbasierte Beziehung. A. Datum Corporation** ist ein Domänenwert, DQS, da es während des wissensermittlungsprozesses ermittelt wurde. Daher ist DQS **100 % überzeugt** zu dieser Korrektur.  
  
    2.  Beachten Sie, dass, **Lazy Country Storex** korrigiert wird, um **Lazy Country Store**, **Vertrauensgrad** festgelegt ist, um **100 %**, und die  **Grund** festgelegt ist, um **Domänenwert**. Legen Sie während des wissensermittlungsprozesses **Lazy Country Storex** als Fehler mit **Lazy Country Store** als die **Korrektur**, sodass DQS **100 % zuversichtlich** dieser Korrektur.  
  
    3.  DQS ist nicht mit den anderen Werten in der Liste vertraut, aber gefundenen die Korrekturen für diese Werte mithilfe der **Rechtschreibprüfung** und die entsprechenden Korrekturen vorschlägt. DQS ist **nicht 100 %** sicher hinsichtlich dieser Korrekturen, aber der Vertrauensgrad liegt über 80 %, dies der Schwellenwert ist für Korrekturen, sodass DQS Korrekturen vorschlägt.  
  
13. Beachten Sie, dass die **genehmigen** automatisch für alle Werte aktiviert ist. Sie können den korrigierten Wert überschreiben oder die Änderung nach Bedarf ablehnen. Standardmäßig die **genehmigen** Schaltfläche "ist für alle Werte ausgewählt, auf die **korrigiert** Registerkarte.  
  
14. Wechseln Sie zu der **neu** Registerkarte.  
  
15. Beachten Sie, dass **Corp.** korrigiert wird, um **Corporation**, **Co.** korrigiert wird, um **Unternehmen**, und **Inc.** korrigiert wird, um **Incorporated**. Beispielsweise **Consolidate Inc.** korrigiert wird, um **Consolidate Incorporated** und **Consolidated Co.** korrigiert wird, um **Consolidated Company**, und **Frabrikam Corp.** korrigiert wird, um **Fabrikam Corporation**.  Sie sehen, dass **begriffsbasierte Beziehung** als Ursache angegeben ist. Diese Änderungen werden mit den begriffsbasierten Beziehungen vorgeschlagen, die Sie während der Domänenverwaltungsaktivität definiert haben. Sie können ändern, die **korrigieren in** -Werte hier manuell.  
  
16. Führen Sie einen Bildlauf die Liste, um finden Sie unter **Hunxgry Coyote Store** mit einer roten Wellenlinie. Mit der rechten Maustaste darauf, und klicken Sie auf **Hungy Coyote Store** (mit "X"). Die **korrigieren in** Spalte automatisch mit aufgefüllt werden soll **Hungry Coyote Store**. Sie können einen Wert in der Spalte "Korrigieren in" auch manuell eingeben.  
  
17. Klicken Sie auf **alle Begriffe genehmigen** aus der Symbolleiste. Die "Domänenwerte" mit der **korrigieren in** angegebene Wert zu verschieben, um die **korrigiert** Registerkarte und die neuen Werte ohne zugeordnete **korrigieren in** Werte ans der  **Richtige** Registerkarte.  
  
18. Wählen Sie die **Address Validation** verbunddomäne aus der Domänenliste aus.  
  
19. Wechseln Sie im rechten Bereich in der **richtig** Registerkarte. Daraufhin sollte die Adressen, die gefunden wurden, korrekt die **Melissa Data – Address Check** DQS-Dienst auf die **Azure Marketplace**.  
  
20. Wechseln Sie zu der **korrigiert** Registerkarte.  
  
21. Beachten Sie, dass **Status** für den Datensatz mit **City** als **Los Angeles** festgelegt ist, um **Zertifizierungsstelle** jetzt. Beachten Sie der **Grund** Feld ist, das **korrigiert durch Regel 'City Rule'**.  
  
     ![Korrektur der City-Regel](../../2014/tutorials/media/et-managingandviewingresults-04.jpg "City Regel Korrektur")  
  
22. Beachten Sie, dass die **genehmigen** Optionsfeld bereits für dieses Element in der Liste ausgewählt ist. Dies ist das Standardverhalten für Elemente auf der **korrigiert** Registerkarte.  
  
23. Wechseln Sie zu der **vorgeschlagen** Registerkarte. Überprüfen Sie die vorgeschlagene Änderungen der **Melissa Data – Address Check** Dienst.  
  
24. **Klicken Sie auf alle Begriffe genehmigen** auf die Symbolleisten-Schaltfläche, und klicken Sie auf **OK** auf die **Bestätigung** Meldungsfeld.  
  
     ![Genehmigen Sie alle Begriffe (Symbolleistenschaltfläche)](../../2014/tutorials/media/et-managingandviewingresults-05.jpg "genehmigen Sie alle Begriffe (Symbolleistenschaltfläche)")  
  
25. Klicken Sie auf **Weiter** So wechseln Sie zu der **exportieren** Seite.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 5: Exportieren der Bereinigungsergebnisse in eine Excel-Datei](../../2014/tutorials/task-5-exporting-cleansing-results-to-an-excel-file.md)  
  
  