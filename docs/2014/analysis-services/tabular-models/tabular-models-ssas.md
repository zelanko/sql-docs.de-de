---
title: Tabellenmodellierung (SSAS – tabellarisch) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80027288-c203-4667-a3e1-40fa572b4975
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: df693d141f3a91c1c0b9b023a89d39c5f2c171ce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061474"
---
# <a name="tabular-modeling-ssas-tabular"></a>Tabellarische Modellierung (SSAS – tabellarisch)
  Tabellarische Modelle stellen in Analysis Services Datenbanken im Arbeitsspeicher dar. Für die xVelocity-Engine für Datenanalyse im Arbeitsspeicher (VertiPaq) werden modernste Komprimierungsalgorithmen und ein Multithreaded-Abfrageprozessor verwendet, um Berichterstellungsclientanwendungen wie Microsoft Excel und Microsoft [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] schnellen Zugriff auf Objekte und Daten tabellarischer Modelle zu gewähren.  
  
 Tabellarische Modelle unterstützen den Datenzugriff in zwei Modi: im Modus mit Zwischenspeicherung und im DirectQuery-Modus. Im Modus mit Zwischenspeicherung können Sie Daten aus mehreren Quellen einschließlich relationaler Datenbanken, Datenfeeds und einfacher Textdateien integrieren. Im DirectQuery-Modus können Sie das Modell im Arbeitsspeicher umgehen, sodass Clientanwendungen Daten direkt aus der (relationalen SQL Server-)Datenquelle abfragen können.  
  
 Tabellarische Modellen erstellt [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] neue Projektvorlagen für tabellarische Modelle verwenden. Sie können Daten aus mehreren Quellen importieren und das Modell erweitern, indem Sie Beziehungen, berechnete Spalten, Measures, KPIs und Hierarchien hinzufügen. Anschließend können die Modelle in einer Instanz von Analysis Services bereitgestellt werden, sodass Berichterstellungsclientanwendungen eine Verbindung mit den Modellen herstellen können. Bereitgestellte Modelle können genauso wie mehrdimensionale Modelle in SQL Server Management Studio verwaltet werden. Sie können partitioniert werden, um die Verarbeitung zu optimieren, und durch die Verwendung der rollenbasierten Sicherheit bis auf Zeilenebene gesichert werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Projektmappen für tabellarische Modelle &#40;SSAS – tabellarisch&#41;](../tabular-model-solutions-ssas-tabular.md)  
  
 [Tabellarische Modelldatenbanken &#40;SSAS – tabellarisch&#41;](tabular-model-databases-ssas-tabular.md)  
  
 [Zugriff auf Daten im tabellarischen Modell](tabular-model-data-access.md)  
  
  