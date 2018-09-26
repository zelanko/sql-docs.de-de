---
title: Tabellarische Modelle | Microsoft-Dokumentation
ms.date: 09/17/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1f894ad30f6344eb832cb9549a60c7f60071188c
ms.sourcegitcommit: e34e9cd1b1ec02393dc88b1f0471023a7f7f278b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/21/2018
ms.locfileid: "46506131"
---
# <a name="tabular-models"></a>Tabellarische Modelle
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Tabellarische Modelle in Analysis Services sind Datenbanken, die in-Memory- oder im DirectQuery-Modus zum Verbinden mit Daten direkt aus relationalen Daten von Back-End-Quellen ausgeführt. Mithilfe der modernen Komprimierungsalgorithmen und einen Multithreaded-Abfrageprozessor, bietet dem Analysis Services Vertipaq-Analysemodul schnellen Zugriff auf tabellenmodellobjekte und-Daten von Client-berichtsanwendungen wie Power BI und Excel.  
  
 Bei speicherinternen Modellen die Standardeinstellung, DirectQuery ist ein alternativer Abfragemodus für Modelle, die entweder zu groß für im Arbeitsspeicher, oder wenn datenflüchtigkeit eine angemessene verarbeitungsstrategie. DirectQuery erzielt Parität mit in-Memory-Modellen, durch die Unterstützung für eine Vielzahl von Datenquellen, Fähigkeit, berechnete Tabellen und Spalten in einem DirectQuery-Modell, Sicherheit auf Zeilenebene über DAX-Ausdrücke, die Back-End-Datenbank zu erreichen, und Abfragen zu verarbeiten Optimierungen, die zu einem höheren Durchsatz führen.
  
 In tabellarische Modellen erstellt [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] mithilfe der Projektvorlage für tabellarische Modelle. Die Projektvorlage bietet eine Entwurfsoberfläche zum Erstellen von semantic Model-Objekte wie Tabellen, Partitionen, Beziehungen, Hierarchien, Measures und KPIs an. 
  
 Tabellarische Modelle können zu Azure Analysis Services oder eine Instanz von SQL Server Analysis Services für den tabellarischen Servermodus konfiguriert, bereitgestellt werden. Bereitgestellte tabellarische Modelle können in SQL Server Management Studio verwaltet werden. 

Tabellarische Modellierung Dokumentation hier gilt, in den meisten Fällen sowohl für SQL Server Analysis Services als auch für Azure Analysis Services. Artikel zum Azure Analysis Services werden zusammen mit der Azure-Dokumentationen veröffentlicht. Weitere Informationen finden Sie unter [Dokumentation zu Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/).
  
