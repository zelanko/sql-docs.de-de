---
title: Data Mining Extensions (DMX)-Anweisungs Verweis | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7a7a9c18599d13c4db510793a1d75c85bbb7a829
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68070864"
---
# <a name="data-mining-extensions-dmx-statements"></a>Data Mining-Erweiterungen (DMX) – Anweisungen
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Das Arbeiten mit Data Mining Modellen [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in umfasst die folgenden Hauptaufgaben:  
  
-   Erstellen von Miningstrukturen und Miningmodellen  
  
-   Verarbeiten von Miningstrukturen und Miningmodellen  
  
-   Löschen von Miningstrukturen oder Miningmodellen  
  
-   Kopieren von Mining Modellen  
  
-   Durchsuchen von Miningmodellen  
  
-   Vorhersagen anhand von Miningmodellen  
  
 Mithilfe von DMX-Anweisungen (Data Mining-Erweiterungen) können Sie jede dieser Aufgaben programmgesteuert ausführen.  
  
 Erstellen von Miningstrukturen und Miningmodellen  
 Verwenden Sie die Anweisung [CREATE MINING STRUCTURE &#40;DMX&#41;](../dmx/create-mining-structure-dmx.md) , um einer Datenbank eine neue Mining Struktur hinzuzufügen. Anschließend können Sie die [ALTER MINING STRUCTURE &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md) -Anweisung verwenden, um der Mining Struktur Mining Modelle hinzuzufügen.  
  
 Verwenden Sie die Anweisung [Create Mining Model &#40;DMX&#41;](../dmx/create-mining-model-dmx.md) , um ein neues Mining Modell und eine zugehörige Mining Struktur zu erstellen.  
  
 Verarbeiten von Miningstrukturen und Miningmodellen  
 Verwenden Sie die Anweisung [INSERT INTO &#40;DMX&#41;](../dmx/insert-into-dmx.md) , um eine Mining Struktur und ein Mining Modell zu verarbeiten.  
  
 Löschen von Miningstrukturen oder Miningmodellen  
 Verwenden Sie die [Delete &#40;DMX&#41;](../dmx/delete-dmx.md) -Anweisung, um alle trainierten Daten aus einem Mining Modell oder einer Mining Struktur zu entfernen. Verwenden Sie die Anweisungen [Drop Mining Structure &#40;DMX&#41;](../dmx/drop-mining-structure-dmx.md) oder [Drop Mining Model &#40;DMX&#41;](../dmx/drop-mining-model-dmx.md) , um eine Mining Struktur oder ein Mining Modell vollständig aus einer Datenbank zu entfernen.  
  
 Kopieren von Mining Modellen  
 Verwenden Sie die Anweisung [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md) , um die Struktur eines vorhandenen Mining Modells in ein neues Mining Modell zu kopieren und das neue Modell mit denselben Daten zu trainieren.  
  
 Durchsuchen von Miningmodellen  
 Verwenden Sie die Anweisung [Select &#40;DMX&#41;](../dmx/select-dmx.md) , um die Informationen zu durchsuchen, die vom Data Mining Algorithmus beim Modell Training berechnet und im Data Mining Modell gespeichert werden. Ähnlich wie bei [!INCLUDE[tsql](../includes/tsql-md.md)]können Sie mit der SELECT-Anweisung mehrere-Klauseln verwenden, um die Leistung zu erweitern. Diese Klauseln unter [scheiden sich \<von Modell>](../dmx/select-distinct-from-model-dmx.md)und [ \<Modell>. Fälle](../dmx/select-from-model-cases-dmx.md), [von \<Modell>. SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md) [aus \<Modell>. Inhalt](../dmx/select-from-model-content-dmx.md) und [aus \<Modell>. DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md).  
  
 Vorhersagen anhand von Miningmodellen  
 Verwenden Sie die [Vorhersage Join](../dmx/select-from-model-prediction-join-dmx.md) -Klausel der SELECT-Anweisung, um Vorhersagen zu erstellen, die auf einem vorhandenen Mining Modell basieren.  
  
 Sie können Modelle auch importieren und exportieren, indem Sie die Anweisungen [Import &#40;DMX&#41;](../dmx/import-dmx.md) und [Export &#40;DMX&#41;](../dmx/export-dmx.md) verwenden.  
  
 Diese Aufgaben gehören zu den beiden Kategorien Datendefinitionsanweisungen und Datenbearbeitungsanweisungen, die in der folgenden Tabelle beschrieben sind.  
  
|Thema|BESCHREIBUNG|  
|-----------|-----------------|  
|[Data Mining-Erweiterungen &#40;DMX&#41; – Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)|Gehören zur Datendefinitionssprache (Data Definition Language, DDL). Werden dazu verwendet, ein neues Miningmodell (samt Training) zu definieren oder ein vorhandenes Miningmodell aus einer Datenbank zu löschen.|  
|[Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)|Gehören zur Datenbearbeitungssprache (Data Manipulation Language, DML). Werden zum Arbeiten mit vorhandenen Miningmodellen verwendet, wozu auch das Durchsuchen eines Modells und das Erstellen von Vorhersagen gehören.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Operator Verweis](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Konventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Elemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)  
  
  
