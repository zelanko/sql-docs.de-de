---
title: Tabellenmodellierung (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 11a5a9332c7fa85fd6407523ffd9c7c48a2c0514
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62794576"
---
# <a name="tabular-modeling-ssas-tabular"></a>Tabellarische Modellierung (SSAS – tabellarisch)
  Tabellarische Modelle stellen in Analysis Services Datenbanken im Arbeitsspeicher dar. Für die xVelocity-Engine für Datenanalyse im Arbeitsspeicher (VertiPaq) werden modernste Komprimierungsalgorithmen und ein Multithreaded-Abfrageprozessor verwendet, um Berichterstellungsclientanwendungen wie Microsoft Excel und Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] schnellen Zugriff auf Objekte und Daten tabellarischer Modelle zu gewähren.  
  
 Tabellarische Modelle unterstützen den Datenzugriff in zwei Modi: Modus mit Zwischenspeicherung und DirectQuery-Modus. Im Modus mit Zwischenspeicherung können Sie Daten aus mehreren Quellen einschließlich relationaler Datenbanken, Datenfeeds und einfacher Textdateien integrieren. Im DirectQuery-Modus können Sie das Modell im Arbeitsspeicher umgehen, sodass Clientanwendungen Daten direkt aus der (relationalen SQL Server-)Datenquelle abfragen können.  
  
 Tabellarische Modelle werden in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] unter Verwendung neuer Projektvorlagen für tabellarische Modelle erstellt. Sie können Daten aus mehreren Quellen importieren und das Modell erweitern, indem Sie Beziehungen, berechnete Spalten, Measures, KPIs und Hierarchien hinzufügen. Anschließend können die Modelle in einer Instanz von Analysis Services bereitgestellt werden, sodass Berichterstellungsclientanwendungen eine Verbindung mit den Modellen herstellen können. Bereitgestellte Modelle können genauso wie mehrdimensionale Modelle in SQL Server Management Studio verwaltet werden. Sie können partitioniert werden, um die Verarbeitung zu optimieren, und durch die Verwendung der rollenbasierten Sicherheit bis auf Zeilenebene gesichert werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Tabellenmodelllösungen &#40;SSAS – tabellarisch&#41;](../tabular-model-solutions-ssas-tabular.md)  
  
 [Tabellarische Modelldatenbanken &#40;SSAS – tabellarisch&#41;](tabular-model-databases-ssas-tabular.md)  
  
 [Zugriff auf Daten im tabellarischen Modell](tabular-model-data-access.md)  
  
  
