---
title: Data Mining-Erweiterungen (DMX)-Anweisungsreferenz | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1baab80455cc5267686bf26251629a1d47065344
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38042118"
---
# <a name="data-mining-extensions-dmx-statements"></a>Data Mining-Erweiterungen (DMX)-Anweisungen
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Arbeiten mit Data Mining-Modelle in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] umfasst die folgenden Hauptaufgaben:  
  
-   Erstellen von Miningstrukturen und Miningmodellen  
  
-   Verarbeiten von Miningstrukturen und Miningmodellen  
  
-   Löschen von Miningstrukturen oder Miningmodellen  
  
-   Kopieren von Miningmodellen  
  
-   Durchsuchen von Miningmodellen  
  
-   Vorhersagen anhand von Miningmodellen  
  
 Mithilfe von DMX-Anweisungen (Data Mining-Erweiterungen) können Sie jede dieser Aufgaben programmgesteuert ausführen.  
  
 Erstellen von Miningstrukturen und Miningmodellen  
 Verwenden der [CREATE MINING STRUCTURE &#40;DMX&#41; ](../dmx/create-mining-structure-dmx.md) Anweisung, um eine neue Miningstruktur in einer Datenbank hinzufügen. Anschließend können Sie die [ALTER MINING STRUCTURE &#40;DMX&#41; ](../dmx/alter-mining-structure-dmx.md) Anweisung, um der Miningstruktur Miningmodelle hinzuzufügen.  
  
 Verwenden der [CREATE MINING MODEL &#40;DMX&#41; ](../dmx/create-mining-model-dmx.md) Anweisung, um eine neue Miningstruktur und eine zugeordnete Miningmodell zu erstellen.  
  
 Verarbeiten von Miningstrukturen und Miningmodellen  
 Verwenden der [INSERT INTO &#40;DMX&#41; ](../dmx/insert-into-dmx.md) -Anweisung eine Miningstruktur und das Miningmodell verarbeitet.  
  
 Löschen von Miningstrukturen oder Miningmodellen  
 Verwenden der [löschen &#40;DMX&#41; ](../dmx/delete-dmx.md) -Anweisung zum Entfernen aller trainierten Daten aus einem Miningmodell oder Miningstruktur. Verwenden der [DROP MINING STRUCTURE &#40;DMX&#41; ](../dmx/drop-mining-structure-dmx.md) oder [DROP MINING MODEL &#40;DMX&#41; ](../dmx/drop-mining-model-dmx.md) Anweisungen, um eine Miningstruktur oder Miningmodell vollständig aus einer Datenbank zu entfernen.  
  
 Kopieren von Miningmodellen  
 Verwenden der [SELECT INTO &#40;DMX&#41; ](../dmx/select-into-dmx.md) Anweisung, um die Struktur eines vorhandenen Miningmodells in ein neues Miningmodell kopieren und das neue Modell mit denselben Daten trainieren.  
  
 Durchsuchen von Miningmodellen  
 Verwenden der [wählen &#40;DMX&#41; ](../dmx/select-dmx.md) Anweisung, um die Informationen zu durchsuchen, die Datamining-Algorithmus berechnet und speichert im Datamining-Modells, während des modelltrainings. Ähnlich wie bei [!INCLUDE[tsql](../includes/tsql-md.md)], können Sie mehrere Klauseln mit der SELECT-Anweisung, um deren Möglichkeiten zu erweitern. Diesen Klauseln zählen [DISTINCT FROM \<Modell >](../dmx/select-distinct-from-model-dmx.md), [FROM \<Modell >. Fällen](../dmx/select-from-model-cases-dmx.md), [FROM \<Modell >. SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md), [FROM \<Modell >. Inhalt](../dmx/select-from-model-content-dmx.md) und [FROM \<Modell >. DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md).  
  
 Vorhersagen anhand von Miningmodellen  
 Verwenden der [PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) -Klausel der SELECT-Anweisung zum Erstellen von Vorhersagen, die auf einem vorhandenen Miningmodell basieren.  
  
 Sie können auch importieren und Exportieren von Modellen mithilfe der [importieren &#40;DMX&#41; ](../dmx/import-dmx.md) und [EXPORTIEREN &#40;DMX&#41; ](../dmx/export-dmx.md) Anweisungen.  
  
 Diese Aufgaben gehören zu den beiden Kategorien Datendefinitionsanweisungen und Datenbearbeitungsanweisungen, die in der folgenden Tabelle beschrieben sind.  
  
|Thema|Description|  
|-----------|-----------------|  
|[Datamining-Erweiterungen &#40;DMX&#41; Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)|Gehören zur Datendefinitionssprache (Data Definition Language, DDL). Werden dazu verwendet, ein neues Miningmodell (samt Training) zu definieren oder ein vorhandenes Miningmodell aus einer Datenbank zu löschen.|  
|[Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)|Gehören zur Datenbearbeitungssprache (Data Manipulation Language, DML). Werden zum Arbeiten mit vorhandenen Miningmodellen verwendet, wozu auch das Durchsuchen eines Modells und das Erstellen von Vorhersagen gehören.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; Funktionsreferenz](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Operator (Referenz)](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Syntaxkonventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; Syntaxelemente](../dmx/data-mining-extensions-dmx-syntax-elements.md)  
  
  
