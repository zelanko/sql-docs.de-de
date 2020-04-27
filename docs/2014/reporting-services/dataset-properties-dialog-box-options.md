---
title: Dataseteigenschaften (Dialog Feld), Optionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10130"
- sql12.rtp.rptdesigner.datasetproperties.options.f1
ms.assetid: 95299049-71ba-427f-b723-775cb696243f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 778365e8fc7f40700b0f8c1683260f15c860a32a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109412"
---
# <a name="dataset-properties-dialog-box-options"></a>Dataseteigenschaften (Dialogfeld), Optionen
  Wählen Sie im Dialogfeld **datasetproperties** die **Option Optionen** aus, um Daten Optionen, z. b. Sortierungs Optionen und Teilergebnisse, für die Abfrage zu ändern. Weitere Informationen finden Sie unter [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="options"></a>Optionen  
 **Sortierung**  
 Wählen Sie ein Gebietsschema aus, das die zum Sortieren der Daten verwendete Sortierreihenfolge bestimmt. Der Wert**Standard** gibt an, dass der Bericht diesen Wert vom Datenanbieter herleiten soll, wenn der Bericht ausgeführt wird. Falls der Wert nicht hergeleitet werden kann, wird der Standardwert von der Gebietsschemaeinstellung des Computers hergeleitet.  
  
 **Berücksichtigung der groß-**  
 Wählen Sie einen Wert aus, um die Unterscheidung nach Groß-/Kleinschreibung zu bestimmen. Mithilfe dieser Option wird angegeben, ob bei den Daten die Groß-/Kleinschreibung unterschieden wird. Sie können die **Groß-/Kleinschreibung** auf **true**, **false**oder **Auto**festlegen. Der Standardwert **Auto**gibt an, dass der Berichts Server versuchen soll, den Wert vom Datenanbieter abzuleiten, wenn der Bericht ausgeführt wird. Falls der Datenanbieter keine Unterscheidung nach Groß- und Kleinschreibung unterstützt, wird der Bericht so ausgeführt, als sei **FALSE**festgelegt. Wenn Sie den Wert kennen und wissen, dass er unterstützt wird, wählen Sie **True**aus.  
  
 **Unterscheidung nach Akzent**  
 Wählen Sie einen Wert aus, um die Unterscheidung nach Akzent zu bestimmen. Unterscheidung nach **Akzent** gibt an, ob bei den Daten nach Akzent unterschieden wird, und kann auf **true**, **false**oder **Auto**festgelegt werden. Der Standardwert **Auto**gibt an, dass der Berichts Server versuchen soll, den Wert vom Datenanbieter abzuleiten, wenn der Bericht ausgeführt wird. Falls der Datenanbieter keine Unterscheidung nach Akzent unterstützt, wird der Bericht so ausgeführt, als sei **False**festgelegt. Wenn Sie den Wert kennen und wissen, dass er unterstützt wird, wählen Sie **True**aus.  
  
 **Unterscheidung nach Kanatyp**  
 Wählen Sie einen Wert aus, um die Unterscheidung nach Kanatyp zu bestimmen. Diese Option gibt an, ob bei den Daten nach Kanatyp unterschieden wird. Sie kann auf " **true**", " **false**" oder " **Auto**" festgelegt werden. Der Standardwert **Auto**gibt an, dass der Berichts Server versuchen soll, den Wert vom Datenanbieter abzuleiten, wenn der Bericht ausgeführt wird. Falls der Datenanbieter keine Unterscheidung nach Kanatyp unterstützt, wird der Bericht so ausgeführt, als sei **False**festgelegt. Wenn Sie den Wert kennen und wissen, dass er unterstützt wird, wählen Sie **True**aus.  
  
 **Unterscheidung nach Breite**  
 Wählen Sie einen Wert aus, um die Unterscheidung nach Breite zu bestimmen. Diese Option gibt an, ob bei den Daten nach Breite unterschieden wird, und kann auf **true**, **false**oder **Auto**festgelegt werden. Der Standardwert **Auto**gibt an, dass der Berichts Server versuchen soll, den Wert vom Datenanbieter abzuleiten, wenn der Bericht ausgeführt wird. Falls der Datenanbieter keine Unterscheidung nach Breite unterstützt, wird der Bericht so ausgeführt, als sei **False**festgelegt. Wenn Sie den Wert kennen und wissen, dass er unterstützt wird, wählen Sie **True**aus.  
  
 **Teilergebnisse als Detailzeilen interpretieren**  
 Wählen Sie einen Wert aus, der angibt, ob Teilergebniszeilen als Detailzeilen statt als Aggregatzeilen interpretiert werden sollen. Der Standardwert **Auto**gibt an, dass die Teil Ergebniszeilen als Detail Zeilen behandelt werden sollen, wenn der Bericht die `Aggregate`()-Funktion nicht für den Zugriff auf Felder im DataSet verwendet. Wenn Teilergebniszeilen als Aggregatzeilen interpretiert werden sollen, wählen Sie **False**aus. Wenn die Teil Ergebniszeilen als Detail Zeilen interpretiert werden sollen und Sie wissen, dass Sie die `Aggregate`()-Funktion nicht verwenden, wählen Sie **true**aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen des Gebiets Schemas für einen Bericht oder ein Textfeld &#40;Reporting Services&#41;](report-design/set-the-locale-for-a-report-or-text-box-reporting-services.md)   
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Name der Windows-Sortierung &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql)   
 [SQL Server-Sortierungsname &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql)   
 [Aggregatfunktion (Berichts-Generator und SSRS)](report-design/report-builder-functions-aggregate-function.md)  
  
  
