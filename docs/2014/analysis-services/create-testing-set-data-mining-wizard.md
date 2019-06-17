---
title: Erstellen eines Testsatzes (Datamining-Assistent) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 9f0e4d1a384995c0c49c346102f8fddbcdf47f68
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66086792"
---
# <a name="create-testing-set-data-mining-wizard"></a>Erstellen eines Testsatzes (Data Mining-Assistent)
  Auf der Seite **Testsatz erstellen** können Sie angeben, welche Daten für das Training verwendet werden sollen und welche Daten für die Verwendung als Testsatz reserviert werden sollen. Durch das Aufteilen von Daten in einen Trainings- und Testsatz beim Erstellen einer Miningstruktur wird die Beurteilung der Genauigkeit von Miningmodellen, die Sie zu einem späteren Zeitpunkt erstellen, erheblich vereinfacht.  
  
 Sie können den Betrag der Testdaten als Prozentsatz angeben, oder Sie können eine Zahl angeben, um die Anzahl der zum Testen verwendeten Fälle zu beschränken. Wenn Sie sowohl einen Prozentsatz als auch eine Höchstanzahl an Fällen für das Testen angeben, werden beide Einstellungen verwendet, und der Testdatensatz enthält die niedrigere Anzahl an Fällen. Standardmäßig werden 30 % zum Testen und 70 % für das Training verwendet, und es ist keine maximale Anzahl an Testfällen festgelegt.  
  
 Standardmäßig generiert [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] einen numerischen Ausgangswert, der zum Starten der Partitionierung verwendet wird. Dieser Ausgangswert basiert auf dem Namen der Miningstruktur. Wenn Sie sicherstellen möchten, dass die Partition unverändert bleibt, auch wenn der Name der Miningstruktur geändert wird, können Sie einen Wert für den Ausgangswert angeben, indem Sie die HoldoutSeed-Eigenschaft der Miningstruktur festlegen. Wenn Sie den Zurückhaltungsausgangswert ändern, müssen Sie die Struktur erneut verarbeiten.  
  
 Wenn Sie später die Menge der Test- oder Trainingsdaten ändern möchten, können Sie ändern die `HoldoutMaxCases` und `HoldoutMaxPercent` Eigenschaften für Datamining-Struktur mithilfe der **Eigenschaften** Fenster. Wenn Sie die Änderung vorgenommen haben, müssen Sie die Miningstruktur und alle zugeordneten Miningmodelle jedoch erneut verarbeiten. Außerdem gelten die folgenden Einschränkungen:  
  
-   Die Partitionierung einer Data Mining-Struktur wird nur unterstützt, wenn die Data Mining-Struktur in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]gespeichert ist. Frühere Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützen das Zwischenspeichern von Partitionsinformationen für Miningstrukturen nicht.  
  
-   Sie können eine Miningstruktur nicht partitionieren, wenn die Miningstruktur die Spalte Key Time enthält, die für Zeitreihenminingmodelle erforderlich ist.  
  
-   Sie können Daten nicht partitionieren, wenn Sie versuchen, einen Wert vorherzusagen, der in einer geschachtelten Tabelle gespeichert ist.  
  
 **Weitere Informationen finden Sie unter** [Tests und Überprüfung &#40;Datamining-&#41;](data-mining/testing-and-validation-data-mining.md), [Erstellen einer relationalen Miningstruktur](data-mining/create-a-relational-mining-structure.md), [Lernprogramm zu Datamining-Grundlagen](../../2014/tutorials/basic-data-mining-tutorial.md)  
  
## <a name="options"></a>Optionen  
 **Prozentsatz der Testdaten**  
 Klicken Sie auf die Nach-oben- und Nach-unten-Pfeile, um den Prozentsatz der Daten, die als Trainingssatz verwendet werden sollen, herauf- oder herabzusetzen, oder geben Sie einen Wert zwischen 0 und 100 in das Textfeld ein.  
  
 **Maximale Anzahl von Fällen in Testdatensatz**  
 Geben Sie eine Zahl ein, um die Anzahl der Fälle einzuschränken, die für Tests verwendet werden können.  
  
 Wenn Sie eine Zahl angeben, die größer ist als die Anzahl der tatsächlichen Fälle in den Daten, werden alle Fälle verwendet.  
  
 Die Standardeinstellung ist NULL. Dies bedeutet, dass es keine Beschränkung gibt.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Assistent F1-Hilfe &#40;Analysis Services – Datamining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Verbundene Spalten vorschlagen &#40;Datamining-Assistent&#41;](suggest-related-columns-data-mining-wizard.md)   
 [Tabellentypen angeben &#40;Datamining-Assistent&#41;](specify-table-types-data-mining-wizard.md)   
 [Geben Sie Inhalt und Datentyp der Spaltenwerts &#40;Datamining-Assistent&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
