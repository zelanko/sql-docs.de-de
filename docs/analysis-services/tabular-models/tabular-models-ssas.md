---
title: Tabellarische Modelle in Analysis Services | Microsoft-Dokumentation
ms.date: 09/17/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ae7dfd78e71c41ab5b826a27742923445117417d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68162434"
---
# <a name="tabular-models"></a>Tabellarische Modelle
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Tabellarische Modelle in Analysis Services sind Datenbanken, die in-Memory- oder im DirectQuery-Modus zum Verbinden mit Daten direkt aus relationalen Daten von Back-End-Quellen ausgeführt. Mithilfe der modernen Komprimierungsalgorithmen und einen Multithreaded-Abfrageprozessor, bietet dem Analysis Services Vertipaq-Analysemodul schnellen Zugriff auf tabellenmodellobjekte und-Daten von Client-berichtsanwendungen wie Power BI und Excel.  
  
 Bei speicherinternen Modellen die Standardeinstellung, DirectQuery ist ein alternativer Abfragemodus für Modelle, die entweder zu groß für im Arbeitsspeicher, oder wenn datenflüchtigkeit eine angemessene verarbeitungsstrategie. DirectQuery erzielt Parität mit in-Memory-Modellen, durch die Unterstützung für eine Vielzahl von Datenquellen, Fähigkeit, berechnete Tabellen und Spalten in einem DirectQuery-Modell, Sicherheit auf Zeilenebene über DAX-Ausdrücke, die Back-End-Datenbank zu erreichen, und Abfragen zu verarbeiten Optimierungen, die zu einem höheren Durchsatz führen.
  
 In tabellarische Modellen erstellt [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] mithilfe der Projektvorlage für tabellarische Modelle. Die Projektvorlage bietet eine Entwurfsoberfläche zum Erstellen von semantic Model-Objekte wie Tabellen, Partitionen, Beziehungen, Hierarchien, Measures und KPIs an. 
  
 Tabellarische Modelle können zu Azure Analysis Services oder eine Instanz von SQL Server Analysis Services für den tabellarischen Servermodus konfiguriert, bereitgestellt werden. Bereitgestellte tabellarische Modelle können in SQL Server Management Studio verwaltet werden. 

Tabellarische Modellierung Dokumentation hier gilt, in den meisten Fällen sowohl für SQL Server Analysis Services als auch für Azure Analysis Services. Artikel zum Azure Analysis Services werden zusammen mit der Azure-Dokumentationen veröffentlicht. Weitere Informationen finden Sie unter [Dokumentation zu Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/).
  
