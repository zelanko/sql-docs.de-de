---
title: Tabellarische Modelle | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8e85a618379b5b3c6da010c8b25782ed6836edb4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="tabular-models"></a>Tabellarische Modelle
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Tabellarische Modelle sind Analysis Services-Datenbanken, die im In-Memory- oder im DirectQuery-Modus ausgeführt werden. Sie greifen in relationalen Back-End-Datenquellen direkt auf Daten zu. Mithilfe der Technik Komprimierungsalgorithmen und einen Multithreaded-Abfrageprozessor, das Analysemodul bietet schnellen Zugriff auf tabellenmodellobjekte und-Daten berichterstellungsclientanwendungen wie Power BI und Excel.  
  
 Während bei speicherinternen Modellen die Standardeinstellung sind, ist DirectQuery ein alternativer Abfragemodus für Modelle, die entweder zu groß für im Arbeitsspeicher, oder wenn datenflüchtigkeit eine angemessene verarbeitungsstrategie möglich. DirectQuery erzielt wie bei speicherinternen Modellen unterstützt eine Vielzahl von Datenquellen, zur Behandlung von berechneten Tabellen und Spalten in einem DirectQuery-Modell, Sicherheit auf Zeilenebene über DAX-Ausdrücke, die die Back-End-Datenbank zu erreichen, und Fragen Optimierungen, die zu einem höheren Durchsatz führen.
  
 In tabellarische Modellen erstellt [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] mithilfe der Projektvorlage für tabellarische Modelle, die bietet eine Entwurfsoberfläche zum Erstellen eines Modells, Tabellen, Beziehungen und DAX-Ausdrücke. Sie können Daten aus mehreren Quellen importieren und das Modell erweitern, indem Sie Beziehungen, berechnete Tabellen und Spalten, Measures, KPIs, Hierarchien und Übersetzungen hinzufügen.  
  
 Modelle können dann mit Azure Analysis Services bereitgestellt werden, oder eine Instanz von SQL Server Analysis Services für den tabellarischen Servermodus konfiguriert. Bereitgestellte tabellarische Modelle können in SQL Server Management Studio verwaltet werden. Wie die Modelle zunehmen, können sie für die optimierte Verarbeitung partitioniert und auf die Zeilenebene mithilfe rollenbasierter Sicherheit gesichert werden.  

  
  
