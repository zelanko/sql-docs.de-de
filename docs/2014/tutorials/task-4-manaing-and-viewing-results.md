---
title: 'Aufgabe 4: Verwalten und Anzeigen der Ergebnisse | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.topic: conceptual
ms.assetid: ecc3ba7e-fecf-478f-8825-6e4764b00e99
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c298daa69c57c7771787c181cc0087927ff83f68
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163500"
---
# <a name="task-4-manaing-and-viewing-results"></a>Aufgabe 4: Verwalten und Anzeigen der Ergebnisse
  In dieser Aufgabe überprüfen Sie die Ergebnisse der computerunterstützten Bereinigung und führen auch die interaktive Bereinigung für Lieferantendaten aus. Finden Sie unter [interaktive Bereinigungsphase](http://msdn.microsoft.com/library/hh213061.aspx#Interactive) Weitere Details.  
  
1.  Wählen Sie **Contact Email** Domäne aus der Liste der Domänen.  
  
2.  Wechseln Sie zu der **ungültige** Registerkarte im rechten Bereich. Beachten Sie, dass zwei E-Mail-Adressen nicht das Zeichen "s" am Ende aufweisen. Diese beiden e-Mails, die gefunden wurden, ungültig werden gemäß der domänenregel, die alle e-Mail-Adressen mit erfordert **@adventure-works.com** (mit der "). DQS verwendet die Domänenregel bei der Bereinigung, um zu bestimmen, ob eine E-Mail gültig ist. Diese Registerkarte zeigt die Domänenwerte an, die in der Wissensdatenbank als ungültig markiert wurden oder die eine Domänenregel verletzt haben. In diesem Fall haben diese Werte die Domänenregel (E-Mail-Überprüfung) verletzt.  
  
3.  In der **korrigieren in** Spalte, die richtige e-Mail-Adresse enden, Typ **@adventure-works.com** (mit der ").  
  
     ![Korrekturen aus dem e-Mail-Überprüfungsregel](../../2014/tutorials/media/et-managingandviewingresults-01.jpg "Korrekturen aus dem e-Mail-Überprüfungsregel")  
  
4.  Klicken Sie auf **genehmigen** für beide Datensätze, die Änderungen zu genehmigen. Wenn Sie genehmigt haben, werden die Datensätze zum Verschieben der **korrigiert** Registerkarte. Statt jedes Element einzeln genehmigen, können Sie alle Änderungen gleichzeitig Genehmigen der **alle Begriffe genehmigen** Symbolleisten-Schaltfläche.  
  
5.  Wechseln Sie zu der **neu** Registerkarte im rechten Bereich. Die Werte in dieser Registerkarte sind die Werte, für die DQS noch nicht genug Informationen in der Wissensdatenbank hat, um zu bestimmen, ob die Werte richtig sind. Daher können keine Änderungen an Domänenwerten vorgenommen oder vorgeschlagen werden.  
  
6.  Überprüfen Sie die Werte, um sicherzustellen, dass alle e-Mails enden **@adventure-works.com** , und klicken Sie auf **alle Begriffe genehmigen** auf der Symbolleiste. Verschieben Sie die genehmigten Werte auf dieser Registerkarte auf die **richtig** Registerkarte.  
  
7.  Wählen Sie die **Land** Domäne aus der Liste der Domänen.  
  
8.  Wechseln Sie zu der **korrigiert** Registerkarte im rechten Bereich, und beachten Sie, dass **United State** Wert wird automatisch korrigiert, um die **USA** mit der "am Ende. Diese Regel ist es sich nicht um eine Regel, die Sie, für definiert die **Land** Domäne, aber DQS ist **83 %** davon überzeugt, dass der richtige Wert ist **USA**. Die **genehmigen** ausgewählt ist automatisch für alle der **korrigiert** Elemente. Sie können dieses Verhalten überschreiben und eine Änderung ablehnen.  
  
9. Beachten Sie, dass **USA** wird korrigiert, um **USA** , da sich um Synonyme handelt und **USA** ist der führende (bevorzugte) Wert.  
  
     ![Korrekturen auf der Grundlage von Synonymen](../../2014/tutorials/media/et-managingandviewingresults-02.jpg "Korrekturen auf der Grundlage von Synonymen")  
  
10. Beachten Sie, dass die **genehmigen** Schaltfläche bereits für diese korrigierten Werte ausgewählt ist. Dieses Verhalten ist der Standardwert für die korrigierten Werte. Sie können eine Änderung ablehnen, und wenn Sie dies tun, wird der Wert verschiebt, in der **ungültige** Registerkarte.  
  
11. Wählen Sie **Lieferantenname** aus der Liste der Domänen.  
  
12. Wechseln Sie zu der **korrigiert** Registerkarte im rechten Bereich.  
  
     ![Korrigierte Lieferantennamen](../../2014/tutorials/media/et-managingandviewingresults-03.jpg "korrigierte Lieferantennamen")  
  
    1.  Beachten Sie, dass **A. Datum Corp.** wird korrigiert, um **A. Datum Corporation** und **Grund** nastaven NA hodnotu **begriffsbasierte Beziehung. A. Datum Corporation** ist ein Domänenwert in DQS, da es während des wissensermittlungsprozesses ermittelt wurde. Daher ist DQS **100 % überzeugt** von diesen Korrektur.  
  
    2.  Beachten Sie, dass, **Lazy Country Storex** wird korrigiert, um **Lazy Country Store**, **Vertrauensgrad** nastaven NA hodnotu **100 %**, und die  **Grund** nastaven NA hodnotu **Domänenwert**. Während des wissensermittlungsprozesses, legen Sie **Lazy Country Storex** als Fehler mit **Lazy Country Store** als die **Korrektur**, sodass DQS **100 % sicher** dieser Korrektur.  
  
    3.  DQS ist nicht mit den anderen Werten in der Liste vertraut, aber sie finden die Korrekturen für diese Werte mithilfe der **Rechtschreibprüfung** und die entsprechenden Korrekturen vorschlägt. DQS ist **nicht 100 %** sicher hinsichtlich dieser Korrekturen, aber der Vertrauensgrad liegt über 80 %, dies der Schwellenwert ist für Korrekturen, sodass DQS Korrekturen vorschlägt.  
  
13. Beachten Sie, dass die **genehmigen** automatisch für alle Werte aktiviert ist. Sie können den korrigierten Wert überschreiben oder die Änderung nach Bedarf ablehnen. In der Standardeinstellung die **genehmigen** Schaltfläche ist für alle Werte ausgewählt, auf die **korrigiert** Registerkarte.  
  
14. Wechseln Sie zu der **neu** Registerkarte.  
  
15. Beachten Sie, dass **Corp.** wird korrigiert, um **Corporation**, **Co.** wird korrigiert, um **Unternehmen**, und **Inc.** wird korrigiert, um **Incorporated**. Z. B. **Consolidate Inc.** wird korrigiert, um **Consolidate Incorporated** und **Consolidated Co.** wird korrigiert, um **Consolidated Company**, und **Frabrikam Corp.** wird korrigiert, um **Fabrikam Corporation**.  Sie sehen, dass **begriffsbasierte Beziehung** als Ursache angegeben ist. Diese Änderungen werden mit den begriffsbasierten Beziehungen vorgeschlagen, die Sie während der Domänenverwaltungsaktivität definiert haben. Sie können ändern, die **korrigieren in** -Werte hier manuell.  
  
16. Scrollen Sie die Liste unter **Hunxgry Coyote Store** mit einer roten Wellenlinie. Mit der rechten Maustaste darauf, und klicken Sie auf **Hungy Coyote Store** (mit"keine" X"). Die **korrigieren in** Spalte sollte automatisch gefüllt werden, mit **Hungry Coyote Store**. Sie können einen Wert in der Spalte "Korrigieren in" auch manuell eingeben.  
  
17. Klicken Sie auf **alle Begriffe genehmigen** auf der Symbolleiste. Werte von die Domäne mit der **korrigieren in** angegebene Wert zu verschieben, um die **korrigiert** Registerkarte und die neuen Werte ohne zugeordnete **korrigieren in** Werte verschieben, auf die  **Richtige** Registerkarte.  
  
18. Wählen Sie die **Address Validation** verbunddomäne aus der Domänenliste aus.  
  
19. Wechseln Sie im rechten Bereich die **richtig** Registerkarte. Daraufhin sollte die Adressen, die gefunden werden, korrekt die **Melissa Data – Address Check** DQS-service die **Azure Marketplace**.  
  
20. Wechseln Sie zu der **korrigiert** Registerkarte.  
  
21. Beachten Sie, dass **Zustand** für den Datensatz mit **City** als **Berlin** nastaven NA hodnotu **Zertifizierungsstelle** jetzt. Beachten Sie in der **Grund** Feld ist, das **korrigiert von Regel "City-Regel"**.  
  
     ![Korrektur der City](../../2014/tutorials/media/et-managingandviewingresults-04.jpg "City Korrektur")  
  
22. Beachten Sie, dass die **genehmigen** Optionsfeld bereits für dieses Element in der Liste ausgewählt ist. Dies ist das Standardverhalten für Elemente auf der **korrigiert** Registerkarte.  
  
23. Wechseln Sie zu der **vorgeschlagen** Registerkarte. Überprüfen Sie die von vorgeschlagenen Änderungen die **Melissa Data – Address Check** Service.  
  
24. **Klicken Sie auf alle Begriffe genehmigen** Symbolleisten-Schaltfläche und auf **OK** auf die **Bestätigung** Meldungsfeld.  
  
     ![Genehmigen Sie alle Begriffe (Symbolleistenschaltfläche)](../../2014/tutorials/media/et-managingandviewingresults-05.jpg "genehmigen Sie alle Begriffe (Symbolleistenschaltfläche)")  
  
25. Klicken Sie auf **Weiter** zum Wechseln der **exportieren** Seite.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 5: Exportieren der Bereinigungsergebnisse in eine Excel-Datei](../../2014/tutorials/task-5-exporting-cleansing-results-to-an-excel-file.md)  
  
  
