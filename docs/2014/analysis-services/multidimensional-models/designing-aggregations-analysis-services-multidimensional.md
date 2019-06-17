---
title: Entwerfen von Aggregationen (Analysis Services – mehrdimensional) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- aggregations [Analysis Services], partitions
- partitions [Analysis Services], aggregations
ms.assetid: 3072b7e0-6961-42ad-a287-16f391f2cec4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 307d2ff0419cf5def9f422f08daf349b80bcad2e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66075210"
---
# <a name="designing-aggregations-analysis-services---multidimensional"></a>Entwerfen von Aggregationen (Analysis Services – Mehrdimensional)
  Aggregationen sind vorausberechnete Zusammenfassungen von Cubedaten, die die Abfrageantwortzeiten in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] beschleunigen.  
  
 Verwenden Sie den Aggregationsentwurfs-Assistenten, um Speicheroptionen und Entwurfsaggregationen für eine Partition zu speichern. Jede Ausführung des Assistenten bezieht sich immer nur auf eine einzige Partition einer Measuregruppe, sodass Sie für jede Partition andere Optionen und Entwürfe auswählen können. Der Assistent führt Sie durch mehrere Schritte, in denen Sie die Speicher- und Aggregationsoptionen für eine Partition konfigurieren können. Weitere Informationen zum Konfigurieren von Speicher finden Sie unter:  
  
 Wählen Sie eine Methode zur Steuerung der Anzahl der Aggregationen aus, die der Assistent entwerfen soll. Anschließend werden die Aggregationen vom Assistenten entworfen.  
  
 Das Ziel ist es, die optimale Anzahl an Aggregationen zu entwerfen. Diese Anzahl sollte nicht nur eine zufrieden stellende Antwortzeit ermöglichen, sondern auch zur Vermeidung unverhältnismäßig großer Partitionen beitragen. Mit einer größeren Anzahl an Aggregationen können Sie schnellere Antwortzeiten erreichen. Jedoch wird mehr Speicherplatz benötigt, und der Computer kann zum Berechnen mehr Zeit beanspruchen. Mit zunehmender Anzahl der vom Assistenten entworfenen Aggregationen erreichen frühere Aggregationen zudem bedeutend größere Leistungssteigerungen als spätere Aggregationen. Durch die Reduzierung von weniger nützlichen Aggregationen wird auch die Leistung gesteigert. Mithilfe der folgenden vom Assistenten bereitgestellten Methoden können Sie die Anzahl der Aggregationen steuern, die der Assistent entwirft:  
  
-   Angeben einer Speicherplatzgrenze für die Aggregationen.  
  
-   Angeben einer Grenze für die Leistungssteigerung.  
  
-   Manuelles Beenden des Assistenten, wenn sich die Kurve, mit der Leistung und Größe im Verhältnis angezeigt werden, bei einer zufrieden stellenden Leistungssteigerung einpendelt.  
  
-   Auswahl, Aggregationen nicht zu entwerfen.  
  
 Um Speicher zu entwerfen, muss der Assistent in der Lage sein, eine Verbindung zu [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] auf dem Zielserver herzustellen. Der Assistent zeigt eine Fehlermeldung an, wenn [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nicht auf dem Zielserver ausgeführt wird oder wenn andernfalls der Speicherentwurfsprozess keine Verbindung zum Zielserver herstellen kann.  
  
 Der letzte Schritt des Assistenten ermöglicht Ihnen die Durchführung der Verarbeitung oder das Aufschieben der Verarbeitung. Durch die Verarbeitung werden die Aggregationen erstellt, die Sie mit dem Assistenten entwerfen. Ein Aufschub der Verarbeitung speichert die entworfenen Aggregationen, sodass sie später verarbeitet werden können. Diese Option ermöglicht es Ihnen, die Entwurfsaktivitäten fortzusetzen, ohne eine Verarbeitung vornehmen zu müssen. Je nach Größe der Partition kann die Verarbeitung sehr viel Zeit in Anspruch nehmen. Sie können die Verarbeitung einer Partition unterbrechen, wenn Sie möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Aggregationen und Aggregationsentwürfe](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
