---
title: Testsatz erstellen (Data Mining-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.holdout.f1
ms.assetid: d0a44b59-ffbd-45fc-baa8-6b8046b1a2f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 84dd9e307279c83b955d6569571772414123f0f5
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84526463"
---
# <a name="create-testing-set-data-mining-wizard"></a>Erstellen eines Testsatzes (Data Mining-Assistent)
  Auf der Seite **Testsatz erstellen** können Sie angeben, welche Daten für das Training verwendet werden sollen und welche Daten für die Verwendung als Testsatz reserviert werden sollen. Durch das Aufteilen von Daten in einen Trainings- und Testsatz beim Erstellen einer Miningstruktur wird die Beurteilung der Genauigkeit von Miningmodellen, die Sie zu einem späteren Zeitpunkt erstellen, erheblich vereinfacht.  
  
 Sie können den Betrag der Testdaten als Prozentsatz angeben, oder Sie können eine Zahl angeben, um die Anzahl der zum Testen verwendeten Fälle zu beschränken. Wenn Sie sowohl einen Prozentsatz als auch eine Höchstanzahl an Fällen für das Testen angeben, werden beide Einstellungen verwendet, und der Testdatensatz enthält die niedrigere Anzahl an Fällen. Standardmäßig werden 30 % zum Testen und 70 % für das Training verwendet, und es ist keine maximale Anzahl an Testfällen festgelegt.  
  
 Standardmäßig generiert [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] einen numerischen Ausgangswert, der zum Starten der Partitionierung verwendet wird. Dieser Ausgangswert basiert auf dem Namen der Miningstruktur. Wenn Sie sicherstellen möchten, dass die Partition unverändert bleibt, auch wenn der Name der Miningstruktur geändert wird, können Sie einen Wert für den Ausgangswert angeben, indem Sie die HoldoutSeed-Eigenschaft der Miningstruktur festlegen. Wenn Sie den Zurückhaltungsausgangswert ändern, müssen Sie die Struktur erneut verarbeiten.  
  
 Wenn Sie die Menge der Test-oder Trainingsdaten später ändern möchten, können Sie die `HoldoutMaxCases` -Eigenschaft und die-Eigenschaft `HoldoutMaxPercent` für die Data Mining Struktur ändern, indem Sie das **Eigenschaften** Fenster verwenden. Wenn Sie die Änderung vorgenommen haben, müssen Sie die Miningstruktur und alle zugeordneten Miningmodelle jedoch erneut verarbeiten. Außerdem gelten die folgenden Einschränkungen:  
  
-   Die Partitionierung einer Data Mining-Struktur wird nur unterstützt, wenn die Data Mining-Struktur in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]gespeichert ist. Frühere Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützen das Zwischenspeichern von Partitionsinformationen für Mining Strukturen nicht.  
  
-   Sie können eine Miningstruktur nicht partitionieren, wenn die Miningstruktur die Spalte Key Time enthält, die für Zeitreihenminingmodelle erforderlich ist.  
  
-   Sie können Daten nicht partitionieren, wenn Sie versuchen, einen Wert vorherzusagen, der in einer geschachtelten Tabelle gespeichert ist.  
  
 **Weitere Informationen: ** [Tests und Überprüfung &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md), [Erstellen einer relationalen Miningstruktur](data-mining/create-a-relational-mining-structure.md), [Tutorial zu Data Mining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)  
  
## <a name="options"></a>Optionen  
 **Prozentsatz der Testdaten**  
 Klicken Sie auf die Nach-oben- und Nach-unten-Pfeile, um den Prozentsatz der Daten, die als Trainingssatz verwendet werden sollen, herauf- oder herabzusetzen, oder geben Sie einen Wert zwischen 0 und 100 in das Textfeld ein.  
  
 **Maximale Anzahl von Fällen in Testdatensatz**  
 Geben Sie eine Zahl ein, um die Anzahl der Fälle einzuschränken, die für Tests verwendet werden können.  
  
 Wenn Sie eine Zahl angeben, die größer ist als die Anzahl der tatsächlichen Fälle in den Daten, werden alle Fälle verwendet.  
  
 Die Standardeinstellung ist NULL. Dies bedeutet, dass es keine Beschränkung gibt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Assistent (F1-Hilfe &#40;Analysis Services-Data Mining-&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Verwandte Spalten &#40;Data Mining-Assistenten vorschlagen&#41;](suggest-related-columns-data-mining-wizard.md)   
 [Geben Sie die Tabellentypen &#40;Data Mining-Assistenten an&#41;](specify-table-types-data-mining-wizard.md)   
 [Geben Sie den Inhalt und den Datentyp der Spalte &#40;Data Mining-Assistenten an&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
