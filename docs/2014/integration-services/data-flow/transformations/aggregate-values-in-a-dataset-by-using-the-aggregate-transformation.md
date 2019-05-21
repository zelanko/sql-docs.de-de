---
title: Aggregieren von Werten in einem Dataset mithilfe der Transformation für das Aggregieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Aggregate transformation [Integration Services]
- aggregate values [Integration Services]
- datasets [Integration Services], aggregate values
ms.assetid: 01b81c0f-d5e0-483b-81b2-73800a6945ac
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 10b14aa8a1f68b32c00ecb321c1af36fb15b868e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900939"
---
# <a name="aggregate-values-in-a-dataset-by-using-the-aggregate-transformation"></a>Aggregieren von Werten in einem Dataset mithilfe der Transformation für das Aggregieren
  Um eine Transformation für das Aggregieren hinzuzufügen und zu konfigurieren, muss das Paket bereits mindestens einen Datenflusstask und eine Quelle enthalten.  
  
### <a name="to-aggregate-values-in-a-dataset"></a>So aggregieren Sie Werte in einem Dataset  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Datenfluss** , und ziehen Sie dann aus dem Bereich **Toolbox**die Transformation für das Aggregieren auf die Entwurfsoberfläche.  
  
4.  Verbinden Sie die Transformation für das Aggregieren mit dem Datenfluss, indem Sie einen Konnektor von der Quelle oder der vorherigen Transformation auf die Transformation für das Aggregieren ziehen.  
  
5.  Doppelklicken Sie auf die Transformation.  
  
6.  Klicken Sie im Dialogfeld **Transformations-Editor für Aggregieren** auf die Registerkarte **Aggregationen** .  
  
7.  Aktivieren Sie in der Liste **Verfügbare Eingabespalten** das Kontrollkästchen neben den Spalten, für die Sie Werte aggregieren wollen. Die ausgewählten Spalten werden in der Tabelle angezeigt.  
  
    > [!NOTE]  
    >  Sie können eine Spalte mehrmals auswählen und mehrere Transformationen auf die Spalte anwenden. Um Aggregationen eindeutig zu identifizieren, wird an den Standardnamen des Ausgabealias der Spalte eine Zahl angefügt.  
  
8.  Optional können Sie den Wert in den **Ausgabealias** -Spalten ändern.  
  
9. Um den Standardaggregationsvorgang, **GROUP BY**, zu ändern, wählen Sie in der Liste **Vorgang** einen anderen Vorgang aus.  
  
10. Wählen Sie zum Ändern des Standardvergleichs die jeweiligen in der **Vergleichsflags** -Spalte aufgelisteten Vergleichsflags aus. Beim Vergleichen werden standardmäßig die Groß-/Kleinschreibung, der Kanatyp, Zeichen ohne Zwischenraum und die Zeichenbreite ignoriert.  
  
11. Geben Sie optional für die **COUNT DISTINCT** -Aggregation die genaue Anzahl von unterschiedlichen Werten in der **COUNT DISTINCT-Schlüssel** -Spalte an, oder wählen Sie die geschätzte Anzahl in der **COUNT DISTINCT-Skala** -Spalte aus.  
  
    > [!NOTE]  
    >  Durch Bereitstellen der genauen oder geschätzten Anzahl von unterschiedlichen Werten wird die Leistung optimiert, da die Transformation die hierfür erforderliche Arbeitsspeichermenge zuordnen kann.  
  
12. Klicken Sie optional auf **Erweitert** , und aktualisieren Sie den Namen der Ausgabe für die Transformation für das Aggregieren. Wenn die Aggregationen enthalten eine `Group By` -Vorgang können Sie auswählen, geschätzte Anzahl von gruppierungsschlüsselwerten in der **Schlüsselskala** Spalte, oder geben Sie die genaue Anzahl von gruppierungsschlüsselwerten in der **Schlüssel** die Spalte.  
  
    > [!NOTE]  
    >  Durch Bereitstellen der genauen oder geschätzten Anzahl von unterschiedlichen Werten wird die Leistung optimiert, da die Transformation die hierfür erforderliche Arbeitsspeichermenge zuordnen kann.  
  
    > [!NOTE]  
    >  Die Optionen **Schlüsselskala** und **Schlüssel** schließen sich gegenseitig aus. Wenn Sie in beide Spalten Werte eingeben, wird der jeweils größere Wert der **Schlüsselskala** -Spalte bzw. der **Schlüssel** -Spalte verwendet.  
  
13. Klicken Sie optional auf die Registerkarte **Erweitert** , und legen Sie die Attribute fest, die zum Optimieren aller Vorgänge gelten, die die Transformation für das Aggregieren ausführt.  
  
14. Klicken Sie auf **OK**.  
  
15. Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Siehe auch  
 [Transformation für das Aggregieren](aggregate-transformation.md)   
 [SQL Server Integration Services-Transformationen](integration-services-transformations.md)   
 [SQL Server Integration Services-Pfade](../integration-services-paths.md)   
 [Datenflusstask](../../control-flow/data-flow-task.md)  
  
  
