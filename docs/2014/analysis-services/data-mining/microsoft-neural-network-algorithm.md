---
title: Microsoft Neural Network-Algorithmus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- training neural networks
- output neurons [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- neurons [Analysis Services]
- classification algorithms [Analysis Services]
- neural networks
- multilayer perceptron network of neurons [Analysis Services]
- hidden neurons
- Back-Propagated Delta Rule network
- input neurons [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 61eb4861-8a6a-4214-a4b8-1dd278ad7a68
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a7330fab8b4c0ecdff296e0daa5e529442fd8b94
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66083871"
---
# <a name="microsoft-neural-network-algorithm"></a>Microsoft Neural Network Algorithm
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network-Algorithmus jeden mögliche Status des Eingabeattributs mit jedem möglichen Status des vorhersagbaren Attributs kombiniert und nutzt die Trainingsdaten, der Berechnung der Wahrscheinlichkeiten. Sie können diese Wahrscheinlichkeiten später für die Klassifizierung oder Regression und für die Vorhersage eines Ergebnisses des vorhergesagten Attributs auf Basis der Eingabeattribute verwenden.  
  
 Ein Miningmodell, das mit dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network-Algorithmus erstellt wurde, kann mehrere Netzwerke enthalten, abhängig von der Anzahl an Spalten, die für die Eingabe und Vorhersage verwendet wird, und von der Spaltenanzahl, die nur für die Vorhersage verwendet wird. Die Anzahl von Netzwerken in einem einzelnen Miningmodell hängt von der Anzahl der in den Eingabe- und vorhersagbaren Spalten enthaltenen Status, die das Miningmodell verwendet, ab.  
  
## <a name="example"></a>Beispiel  
 Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network-Algorithmus ist hilfreich zum Analysieren komplexer Eingabedaten, z. B. die eines Produktions- oder Handelsprozesses oder von Geschäftsproblemen. Für diese Daten sind zwar bedeutende Trainingsdatenmengen verfügbar, jedoch können für diese Daten Regeln mithilfe anderer Algorithmen nicht einfach abgeleitet werden.  
  
 Das Verwenden des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network-Algorithmus wird in folgenden Szenarien empfohlen:  
  
-   Marketing- und Werbeanalysen, z. B. zur Erfolgsermittlung einer Werbung per E-Mail oder einer Radiowerbekampagne.  
  
-   Vorhersagen von Lagerbewegungen, Kursschwankungen oder von anderen hoch liquiden Finanzinformationen aus Vergangenheitsdaten.  
  
-   Analysieren von Produktions- und Gewerbeprozessen.  
  
-   Text Mining.  
  
-   Ein beliebiges Vorhersagemodell, das komplexe Beziehungen zwischen vielen Eingaben und relativ wenigen Ausgaben analysiert.  
  
## <a name="how-the-algorithm-works"></a>Funktionsweise des Algorithmus  
 Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network-Algorithmus erstellt ein Netzwerk, das aus bis zu drei Neuronenebenen besteht. Zu diesen Ebenen gehört eine Eingabeebene, eine optionale verborgene Ebene und eine Ausgabeebene.  
  
 **Eingabeebene:** Eingabeneuronen definieren alle eingabeattributwerte für Datamining-Modell und deren Wahrscheinlichkeiten.  
  
 **Verborgene Ebene:** Verborgene Neuronen empfangen die von Eingabeneuronen bereitgestellten Eingaben und stellen Ausgabeneuronen die empfangenen Ausgaben zur Verfügung. In der verborgenen Ebene werden den verschiedenen Wahrscheinlichkeiten der Eingaben Gewichtungen zugewiesen. Eine Gewichtung beschreibt die Relevanz oder Wichtigkeit einer bestimmten Eingabe zum verborgenen Neuron. Je größer die Gewichtung ist, die einer Eingabe zugewiesen wird, desto wichtiger ist der Wert dieser Eingabe. Gewichtungen können negativ sein, was bedeutet, dass ein bestimmtes Ergebnis durch die Eingabe eher unterdrückt als begünstigt werden kann.  
  
 **Ausgabeebene:** Ausgabeneuronen stellen Ausgabeattributwerte des Data Mining-Modells dar.  
  
 Eine ausführliche Erklärung dazu, wie die Eingabeebene, die verborgene Ebene und die Ausgabeebene erstellt und eingestuft werden, finden Sie unter [Technische Referenz für den Microsoft Neural Network-Algorithmus](microsoft-neural-network-algorithm-technical-reference.md).  
  
## <a name="data-required-for-neural-network-models"></a>Erforderliche Daten für neuronale Netzwerkmodelle  
 Ein neuronales Netzwerkmodell muss eine Schlüsselspalte, mindestens eine Eingabespalte und mindestens eine vorhersagbare Spalte enthalten.  
  
 Data Mining-Modelle, die den [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network-Algorithmus verwenden, hängen stark von den Werten ab, die Sie für die im Algorithmus verfügbaren Parameter festlegen. Die Parameter legen fest, wie Daten als Stichprobe genommen werden, wie die Daten in jeder Spalte verteilt werden oder werden sollen und wann die Funktionsauswahl aufgerufen wird, um die im endgültigen Modell zu verwendenden Werte einzugrenzen.  
  
 Weitere Informationen zum Festlegen der Parameter für das Anpassen des Modellverhaltens finden Sie unter [Technische Referenz für den Microsoft Neural Network-Algorithmus](microsoft-neural-network-algorithm-technical-reference.md).  
  
## <a name="viewing-a-neural-network-model"></a>Anzeigen eines neuronalen Netzwerkmodells  
 Um mit den Daten zu arbeiten und zu sehen, wie das Modell Eingaben mit Ausgaben korreliert, können Sie den **Microsoft-Viewer für neuronale Netzwerke**verwenden. Über diesen benutzerdefinierten Viewer können Sie Eingabeattribute und deren Werte filtern und Diagramme einsehen, die darstellen, welche Auswirkungen diese auf die Ausgaben haben. Die QuickInfos im Viewer zeigen Ihnen die Wahrscheinlichkeit und Prognose für jedes Paar an Eingabe- und Ausgabewerten an. Weitere Informationen finden Sie unter [Modell mit dem Microsoft-Viewer für neuronale Netzwerke durchsuchen](browse-a-model-using-the-microsoft-neural-network-viewer.md).  
  
 Die einfachste Art und Weise, die Struktur des Modells zu durchsuchen, erfolgt über den **Microsoft Generic Content Tree-Viewer**. Hier können Sie die Eingaben, Ausgaben und Netzwerke einsehen, die vom Modell erstellt wurden, und auf jeden beliebigen Knoten klicken, um diesen zu erweitern und Statistiken in Bezug auf die Knoten der Eingabe-, Ausgabeebene und der verborgenen Ebene einzusehen. Weitere Informationen finden Sie unter [Durchsuchen eines Modells mit dem Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).  
  
## <a name="creating-predictions"></a>Erstellen von Vorhersagen  
 Nachdem das Modell verarbeitet wurde, können Sie das Netzwerk und die innerhalb eines jeden Knotens gespeicherten Gewichtungen verwenden, um Vorhersagen zu erstellen. Ein neuronales Netzwerkmodell unterstützt Regression, Zuordnung und Klassifikationsanalyse. Daher können die Bedeutungen der einzelnen Vorhersagen unterschiedlich sein. Darüber hinaus können Sie das Modell selbst abfragen, um die gefundenen Korrelationen zu prüfen und die entsprechenden Statistiken abzurufen. Beispiele dazu, wie Abfragen für ein Modell für ein neuronales Netzwerk erstellt werden, finden Sie unter [Abfragebeispiele für neuronale Netzwerkmodelle](neural-network-model-query-examples.md).  
  
 Allgemeine Informationen zur Erstellung von Abfragen für ein Data Mining-Modell finden Sie unter [Data Mining-Abfragen](data-mining-queries.md).  
  
## <a name="remarks"></a>Hinweise  
  
-   Unterstützt nicht Drillthrough oder Data Mining-Dimensionen. Grund hierfür ist, dass die Struktur der Knoten im Miningmodell nicht zwangsläufig den zugrunde liegenden Daten direkt entspricht.  
  
-   Unterstützt nicht die Erstellung von Modellen im PMML-Format (Predictive Model Markup Language).  
  
-   Unterstützt die Verwendung von OLAP-Miningmodellen.  
  
-   Unterstützt nicht die Erstellung von Data Mining-Dimensionen.  
  
## <a name="see-also"></a>Siehe auch  
 [Technische Referenz für den Microsoft Neural Network-Algorithmus](microsoft-neural-network-algorithm-technical-reference.md)   
 [Miningmodellinhalt von neuronalen Netzwerkmodellen &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)   
 [Abfragebeispiele für neuronale Netzwerkmodelle](neural-network-model-query-examples.md)   
 [Microsoft Logistic Regression-Algorithmus](microsoft-logistic-regression-algorithm.md)  
  
  
