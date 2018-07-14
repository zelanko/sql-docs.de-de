---
title: Tabellenmodellierung (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2fe54f13fb065b099983ae58934851af1a3f49a5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257216"
---
# <a name="tabular-modeling-ssas-tabular"></a>Tabellarische Modellierung (SSAS – tabellarisch)
  Tabellarische Modelle stellen in Analysis Services Datenbanken im Arbeitsspeicher dar. Für die xVelocity-Engine für Datenanalyse im Arbeitsspeicher (VertiPaq) werden modernste Komprimierungsalgorithmen und ein Multithreaded-Abfrageprozessor verwendet, um Berichterstellungsclientanwendungen wie Microsoft Excel und Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] schnellen Zugriff auf Objekte und Daten tabellarischer Modelle zu gewähren.  
  
 Tabellarische Modelle unterstützen den Datenzugriff in zwei Modi: im Modus mit Zwischenspeicherung und im DirectQuery-Modus. Im Modus mit Zwischenspeicherung können Sie Daten aus mehreren Quellen einschließlich relationaler Datenbanken, Datenfeeds und einfacher Textdateien integrieren. Im DirectQuery-Modus können Sie das Modell im Arbeitsspeicher umgehen, sodass Clientanwendungen Daten direkt aus der (relationalen SQL Server-)Datenquelle abfragen können.  
  
 Tabellarische Modelle werden erstellt, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] neue Projektvorlagen für tabellarische Modelle verwenden. Sie können Daten aus mehreren Quellen importieren und das Modell erweitern, indem Sie Beziehungen, berechnete Spalten, Measures, KPIs und Hierarchien hinzufügen. Anschließend können die Modelle in einer Instanz von Analysis Services bereitgestellt werden, sodass Berichterstellungsclientanwendungen eine Verbindung mit den Modellen herstellen können. Bereitgestellte Modelle können genauso wie mehrdimensionale Modelle in SQL Server Management Studio verwaltet werden. Sie können partitioniert werden, um die Verarbeitung zu optimieren, und durch die Verwendung der rollenbasierten Sicherheit bis auf Zeilenebene gesichert werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Projektmappen für tabellarische Modelle &#40;SSAS – tabellarisch&#41;](../tabular-model-solutions-ssas-tabular.md)  
  
 [Tabellarische Modelldatenbanken &#40;SSAS – tabellarisch&#41;](tabular-model-databases-ssas-tabular.md)  
  
 [Zugriff auf Daten im tabellarischen Modell](tabular-model-data-access.md)  
  
  
