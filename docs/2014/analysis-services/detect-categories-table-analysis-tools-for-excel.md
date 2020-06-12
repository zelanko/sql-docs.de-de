---
title: Kategorien erkennen (Tabellenanalyse Tools für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- clustering [data mining]
- mining model, decision tree
- category detection
ms.assetid: 3c7e9ebb-d0c9-498e-a9ba-cc13eaa43520
author: minewiskan
ms.author: owend
ms.openlocfilehash: a507e0d77cd81165b0220e3d09ec10227d32d853
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528706"
---
# <a name="detect-categories-table-analysis-tools-for-excel"></a>Kategorien erkennen (Tabellenanalysetool für Excel)
  ![Kategorien erkennen (Schaltfläche auf Menüband)](media/tat-detectcat.gif "Kategorien erkennen (Schaltfläche auf Menüband)")

 Das Tool **Kategorien erkennen** ermittelt automatisch Zeilen in einer Tabelle, die ähnliche Merkmale aufweisen.

 Bei Abschluss des Tools wird ein Bericht erstellt, in dem die gefundenen Kategorien zusammen mit ihren charakteristischen Merkmalen aufgeführt werden. Standardmäßig wird der Datentabelle, die die vorgeschlagene Kategorie enthält, für jede Zeile Ihrer Daten eine neue Spalte hinzugefügt. Sie können die Kategorien dann überprüfen und umbenennen.

## <a name="using-the-detect-categories-tool"></a>Verwenden des Tools Kategorien erkennen

1.  Öffnen Sie eine Excel-Tabelle.

2.  Klicken Sie auf **Kategorien erkennen**.

3.  Geben Sie die in der Analyse zu verwendenden Spalten an. Sie können die Auswahl von Spalten, die andere Werte aufweisen, wie Personennamen oder Datensatz-IDs, aufheben, wenn diese Spalten für die Analyse nicht nützlich sind.

4.  Geben Sie optional die maximale Anzahl der zu erstellenden Kategorien an. Standardmäßig werden vom Tool so viele Kategorien automatisch erstellt, wie von ihm gefunden werden.

5.  Klicken Sie auf **Ausführen**.

6.  Es wird ein neues Arbeitsblatt mit dem Namen Kategoriebericht vom Tool erstellt, in dem die Kategorien und deren Merkmale aufgelistet sind.

 Weitere Informationen zum Angeben von Optionen für das Tool finden Sie unter [Dialog Feld "Kategorien erkennen" (Tabellenanalyse Tools für Excel)](detect-categories-table-analysis-tools-for-excel.md).

## <a name="understanding-the-categories-report"></a>Grundlegendes zum Kategoriebericht
 Der **Kategoriebericht** enthält zwei Tabellen: **Kategorie** -und **Kategoriemerkmale**und ein Diagramm für **Kategorieprofile** .

### <a name="category-list"></a>Kategorieliste
 In der ersten Tabelle sind die Kategorien aufgeführt, die gefunden wurden. Die Spalte **Zeilen Anzahl** gibt an, wie viele Daten Zeilen jeder Kategorie zugewiesen wurden.

 Im Modell werden temporäre Namen für jede Kategorie erstellt, die Kategorien können aber nach Bedarf umbenannt werden. Im folgenden Beispiel wurde die erste Kategorie als **niedriges Einkommen**umbenannt, da dies das oberste Attribut des Clusters war.

 ![Mit dem Tool "Kategorien erkennen" erstellter Bericht](media/dm13-tat-detectcat-report1.gif "Mit dem Tool "Kategorien erkennen" erstellter Bericht")

 Sobald Sie die neue Bezeichnung eingeben, wird die Änderung an alle anderen Diagramme sowie an die Kategorieliste weitergegeben, die im Quelldatenarbeitsblatt hinzugefügt wird.

### <a name="category-characteristics"></a>Kategoriemerkmale
 In der zweiten Tabelle, **Kategorieeigenschaften**, werden Details über die Zusammensetzung der einzelnen Kategorien angezeigt. Klicken Sie oben in der Spalte **Kategorie** auf die Schaltfläche **Filter** , um den Fokus auf ein oder nur einige Kategorien zu überprüfen.

 ![Mit dem Tool "Kategorien erkennen" erstellter Bericht](media/dm13-tat-detectcat-report2.gif "Mit dem Tool "Kategorien erkennen" erstellter Bericht")

 Die Schattierung in der Spalte, **relative Wichtigkeit**, gibt an, wie wichtig diese Kombination von Attribut und Wert ist. Je länger der Balken, desto wahrscheinlicher ist es, dass das Attribut für seine Kategorie stark repräsentativ ist.

### <a name="categories-profile-chart"></a>Kategorieprofildiagramm
 Das abschließende Diagramm im Arbeits **Categories Report** Blatt " **kategorieberichte", "Kategorieprofile**", ist ein interaktives **PivotChart** , das Sie verwenden können, um Felder neu anzuordnen und auszublenden, nach Werten zu filtern und die Diagramm Darstellung anzupassen.

 Excel 2013 bietet jetzt **Diagramm Stile** und **Diagramm Elemente** -Steuerelemente direkt in der Entwurfs Oberfläche, die das verbessern des Diagramm Entwurfs erleichtern.

 ![Mit dem Tool "Kategorien erkennen" erstellter Bericht](media/dm13-tat-detectcat-report3.gif "Mit dem Tool "Kategorien erkennen" erstellter Bericht")

## <a name="requirements"></a>Requirements (Anforderungen)
 Das Tool **Kategorien erkennen** hat keine Anforderungen hinsichtlich der Menge oder des Datentyps.

> [!NOTE]
>  Wenn Sie das Tool **Kategorien erkennen** verwenden, wird in der ursprünglichen Datentabelle eine neue Spalte (Kategorie) erstellt. Wenn Sie diese Spalte in der Datentabelle belassen, beeinflusst sie möglicherweise die Ergebnisse von anschließend durchgeführten Data Mining-Vorgängen. Erstellen Sie daher eine Kopie der Datentabelle ohne die Spalte Kategorie, um sicherzustellen, dass diese Spalte sich nicht auf andere Vorgänge auswirkt, bevor Sie andere Data Mining-Tools verwenden.

## <a name="related-tools"></a>Verwandte Tools
 Wenn das Tool **Kategorien erkennen** Ihre Daten analysiert, erstellt es mithilfe des Clustering-Algorithmus eine Data Mining Struktur und Data Mining Modell [!INCLUDE[msCoName](../includes/msconame-md.md)] .

 Nachdem Sie mit dem Tool **wichtige Einflussfaktoren analysieren** ein Data Mining Modell erstellt haben, können Sie den Data Mining-Client für Excel verwenden, um das Modell zu durchsuchen und die Beziehungen ausführlicher zu untersuchen. Der Data Mining-Client für Excel stellt ein separates Add-In mit erweiterter Data Mining-Funktionalität dar. Weitere Informationen finden Sie unter durch [Suchen von Modellen in Excel &#40;SQL Server Data Mining-Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).

 Weitere Informationen zur Verwendung der Daten Modellierungsfunktionen im Data Mining-Client für Excel finden Sie unter [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md).

 Weitere Informationen zum Algorithmus, der vom Tool **Kategorien erkennen** verwendet wird, finden Sie im Thema "Microsoft Clustering-Algorithmus" in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Online Dokumentation.

## <a name="see-also"></a>Weitere Informationen
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)


