---
description: Grundlegendes zur SELECT-Anweisung (DMX)
title: Grundlegendes zur DMX-SELECT-Anweisung | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 93744da59ad7149203da8fd14179045b63dc798f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88395216"
---
# <a name="understanding-the-dmx-select-statement"></a>Grundlegendes zur SELECT-Anweisung (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Die [Select](../dmx/select-dmx.md) -Anweisung ist die Grundlage für die meisten Abfragen, die Sie mit Data Mining-Erweiterungen (DMX) in Erstellen [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Mit dieser Anweisung können Sie viele unterschiedliche Aufgaben ausführen, so z. B. Durchsuchen von Data Mining-Modellen und Erstellen von Vorhersagen für Data Mining-Modelle.  
  
 Die folgenden Aufgaben können Sie mit der **Select** -Anweisung ausführen:  
  
-   Durchsuchen eines Data Mining-Modells. Das Schemarowset definiert die Struktur eines Modells.  
  
-   Ermitteln der möglichen Werte einer Miningmodellspalte.  
  
-   Durchsuchen der Fälle, die Knoten in einem Miningmodell zugewiesen sind, oder Abrufen eines repräsentativen Falls.  
  
-   Erstellen von Vorhersagen auf der Basis verschiedener Eingaben.  
  
-   Kopieren von Miningmodellen.  
  
 Jede dieser Aufgaben verwendet einen anderen Satz von Daten, die wir als *Daten Domäne*bezeichnen. Sie definieren die Daten Domäne in der **from** -Klausel der-Anweisung.  
  
-   Sie möchten Objekte im Data Mining-Modell selbst suchen, z. B. die Regel, durch die ein Dataset definiert wird, oder eine Formel für Vorhersagen.  
  
     In diesem Fall müssen Sie die Metadaten untersuchen, die im Modell selbst gespeichert sind. Deshalb besteht die Datendomäne aus den Spalten, die durch das Data Mining-Schemarowset definiert sind.  
  
-   Sie möchten detaillierte Informationen zu den Fällen abrufen, auf deren Grundlage das Modell erstellt wird.  
  
     In diesem Fall müssen Sie einen Drillthrough zur Miningstruktur, d. h. Ihrer Datendomäne, durchführen und die einzelnen Zeilen in den Spalten (Gender, Bike Buyer usw.) untersuchen.  
  
 **Wichtig:** Alles, was in der Ausdrucks Liste oder in der **Where** -Klausel enthalten ist, muss aus der Daten Domäne stammen, die durch die **from** -Klausel definiert wird. Datendomänen können nicht gemischt werden.  
  
##  <a name="select-types"></a><a name="Select_Types"></a> Typen auswählen  
 Die Syntax der **Select** -Anweisung unterstützt viele verschiedene Tasks. Diese Aufgaben führen Sie mithilfe der folgenden Muster aus:  
  
-   [Sagt](#Predicting)  
  
-   [Browsen](#Browsing)  
  
-   [Wird kopiert](#Copying)  
  
-   [Drillthrough ausführen](#Drillthrough)  
  
###  <a name="predicting"></a><a name="Predicting"></a> Sagt  
 Mit folgenden Abfragetypen können Sie Vorhersagen ausführen, die auf einem Miningmodell basieren.  
  
 Sie können eine **der SELECT-Anweisungen für** das Durchsuchen oder Vorhersagen in den **from** -und **Where** -Klauseln einer **Select** -Anweisung für einen Vorhersage Join einschließen.  
  
|Abfragetyp|Beschreibung|  
|----------------|-----------------|  
|Select from [Natural] Vorhersage Join|Gibt eine Vorhersage zurück, die erstellt wurde, indem die Spalten des Miningmodells mit den Spalten einer internen Datenquelle verknüpft wurden.<br /><br /> Die Datendomäne für diesen Abfragetyp besteht aus den vorhersagbaren Spalten aus dem Modell und den Spalten aus der Eingabedatenquelle.<br /><br /> [Wählen Sie aus &#60;Modell&#62; Vorhersage Join &#40;DMX aus&#41;](../dmx/select-from-model-prediction-join-dmx.md)<br /><br /> [Vorhersageabfragen &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/prediction-queries-data-mining)|  
|Select from *\<model>*|Gibt nur auf Basis des Miningmodells den wahrscheinlichsten Status der vorhersagbaren Spalte zurück. Dieser Abfragetyp ist eine Abkürzung für das Erstellen einer Vorhersage mit einem leeren PREDICTION JOIN.<br /><br /> Die Datendomäne für diesen Abfragetyp besteht aus den vorhersagbaren Spalten aus dem Modell.<br /><br /> [Wählen Sie aus &#60;Modell&#62; &#40;DMX aus&#41;](../dmx/select-from-model-dmx.md)<br /><br /> [Vorhersageabfragen &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/prediction-queries-data-mining)|  
  
 [Zurück zu SELECT-Typen](#Select_Types)  
  
###  <a name="browsing"></a><a name="Browsing"></a> Browser  
 Mit folgenden Abfragetypen können Sie die Inhalte eines Miningmodells durchsuchen.  
  
|Abfragetyp|Beschreibung|  
|----------------|-----------------|  
|SELECT verschieden von *\<model>*|Gibt alle Statuswerte vom Miningmodell für die angegebene Spalte zurück.<br /><br /> Die Datendomäne für diesen Abfragetyp entspricht dem Data Mining-Modell.<br /><br /> [Wählen Sie unterschiedliche &#60;Modell &#62; &#40;DMX aus&#41;](../dmx/select-distinct-from-model-dmx.md)<br /><br /> [Inhaltsabfragen &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-queries-data-mining)|  
|Wählen Sie aus *\<model>* . Inhaltliche|Gibt Inhalte mit Beschreibungen zum Miningmodell zurück.<br /><br /> Die Datendomäne für diesen Abfragetyp entspricht dem CONTENT-Schemarowset.<br /><br /> [Wählen Sie aus &#60;Modell&#62; aus. Inhalt &#40;DMX-&#41;](../dmx/select-from-model-content-dmx.md)<br /><br /> [Inhaltsabfragen &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/content-queries-data-mining)|  
|Wählen Sie aus *\<model>* . DIMENSION_CONTENT|Gibt Inhalte mit Beschreibungen zum Miningmodell zurück.<br /><br /> Die Datendomäne für diesen Abfragetyp entspricht dem CONTENT-Schemarowset.<br /><br /> [Wählen Sie aus &#60;Modell&#62; aus. DIMENSION_CONTENT &#40;DMX-&#41;](../dmx/select-from-model-dimension-content-dmx.md)|  
|Wählen Sie aus *\<model>* . PMML|Gibt für Algorithmen, die diese Funktionalität unterstützen, die PMML-Darstellung (Predictive Model Markup Language) des Miningmodells zurück.<br /><br /> Die Datendomäne für diesen Abfragetyp besteht aus dem PMML-Schemarowset.<br /><br /> [DMSCHEMA_MINING_MODEL_CONTENT_PMML-Rowset](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/ms126283(v=sql.110))|  
  
 [Zurück zu SELECT-Typen](#Select_Types)  
  
###  <a name="copying"></a><a name="Copying"></a> Vorgänge  
 Sie können ein Miningmodell sowie dessen zugeordnete Miningstruktur in ein neues Modell kopieren und das Modell anschließend innerhalb der Anweisung umbenennen.  
  
|Abfragetyp|Beschreibung|  
|----------------|-----------------|  
|SELECT INTO *\<new model>*|Erstellt eine Kopie des Miningmodells.<br /><br /> Die Datendomäne für diesen Abfragetyp besteht aus dem Data Mining-Modell.<br /><br /> [Wählen Sie in &#40;DMX-&#41;](../dmx/select-into-dmx.md)|  
  
 [Zurück zu SELECT-Typen](#Select_Types)  
  
###  <a name="drillthrough"></a><a name="Drillthrough"></a> Drillthrough  
 Mit folgenden Abfragetypen können Sie die Fälle oder eine Darstellung der Fälle durchsuchen, die dazu verwendet wurden, das Modell zu trainieren.  
  
|Abfragetyp|Beschreibung|  
|----------------|-----------------|  
|Wählen Sie aus *\<model>* . Denen|Gibt die Fälle zurück, die zum Trainieren des Miningmodells verwendet werden.<br /><br /> Die Datendomäne für diesen Abfragetyp besteht aus dem Data Mining-Modell.<br /><br /> [Wählen Sie aus &#60;Modell&#62; aus. Fälle &#40;DMX-&#41;](../dmx/select-from-model-cases-dmx.md)<br /><br /> [Erstellen von Drillthroughabfragen mit DMX](https://docs.microsoft.com/analysis-services/data-mining/create-drillthrough-queries-using-dmx)|  
|Wählen Sie aus *\<model>* . SAMPLE_CASES|Gibt einen Beispielfall zurück, der repräsentativ für die Fälle ist, die zum Trainieren des Miningmodells verwendet werden.<br /><br /> Die Datendomäne für diesen Abfragetyp besteht aus dem Data Mining-Modell.<br /><br /> [Wählen Sie aus &#60;Modell&#62; aus. SAMPLE_CASES &#40;DMX-&#41;](../dmx/select-from-model-sample-cases-dmx.md)|  
|Wählen Sie aus *\<structure>* . Denen|Gibt die detaillierten Datenzeilen aus der zugrunde liegenden Miningstruktur zurück, auch wenn einige Details nicht zum Trainieren des Miningmodells verwendet wurden.<br /><br /> [Wählen Sie aus &#60;Struktur&#62; aus. Denen](../dmx/select-from-structure-cases.md)<br /><br /> [Drillthroughabfragen &#40;Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/drillthrough-queries-data-mining)|  
  
 [Zurück zu SELECT-Typen](#Select_Types)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Referenz](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41;-Anweisungs Referenz](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Syntax Konventionen](../dmx/data-mining-extensions-dmx-syntax-conventions.md)  
  
  
