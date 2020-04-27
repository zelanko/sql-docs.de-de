---
title: Anfügen von Abfragehinweisen an eine Planhinweisliste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 2131f796-6359-4f9e-9047-da0b3d4dedaf
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 89af21c2c591db2dff678be7aaf8c064e728b9ab
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63151074"
---
# <a name="attach-query-hints-to-a-plan-guide"></a>Anfügen von Abfragehinweisen an eine Planhinweisliste
  In einer Planhinweisliste können beliebige Kombinationen gültiger Abfragehinweise verwendet werden. Wenn eine Planhinweisliste mit einer Abfrage übereinstimmt, wird die in der Hinweisklausel einer Planhinweisliste angegebene OPTION-Klausel vor dem Kompilieren und Optimieren zur Abfrage hinzugefügt. Wenn eine mit einer Planhinweisliste übereinstimmende Abfrage bereits eine OPTION-Klausel besitzt, ersetzen die in der Planhinweisliste angegebenen Abfragehinweise die in der Abfrage enthaltenen. Damit eine Planhinweisliste mit einer Abfrage übereinstimmt, die bereits eine OPTION-Klausel besitzt, müssen Sie die OPTION-Klausel der Abfrage aufnehmen, wenn Sie den Text der Abfrage angeben, der mit der sp_create_plan_guide-Anweisung übereinstimmen soll. Wenn Sie möchten, dass die in der Planhinweisliste angegebenen Abfragehinweise den bereits in der Abfrage vorhandenen Hinweisen hinzugefügt werden, statt diese zu ersetzen, müssen Sie in der OPTION-Klausel der Planhinweisliste sowohl die ursprünglichen Hinweise als auch die zusätzlichen Hinweise angeben.  
  
> [!CAUTION]  
>  Bei falscher Verwendung von Abfragehinweisen in Planhinweislisten kann es zu Kompilierungs-, Ausführungs- oder Leistungsproblemen kommen. Daher sollten Planhinweislisten nur von erfahrenen Entwicklern und Datenbankadministratoren verwendet werden.  
  
## <a name="common-query-hints-used-in-plan-guides"></a>Allgemeine Abfragehinweise in Planhinweislisten  
 Abfragen, für die sich Planhinweislisten eignen, basieren im Allgemeinen auf Parametern und weisen möglicherweise eine unzureichende Leistung auf, weil sie zwischengespeicherte Abfragepläne verwenden, deren Parameterwerte nicht das passende repräsentative (oder Worst-Case-) Szenario darstellen. Um dieses Problem zu lösen, können der OPTIMIZE FOR-Abfragehinweis und der RECOMPILE-Abfragehinweis verwendet werden. Durch OPTIMIZE FOR wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angewiesen, bei der Abfrageoptimierung einen bestimmten Parameterwert zu verwenden. Durch RECOMPILE wird der Server angewiesen, einen Abfrageplan nach der Ausführung wieder zu verwerfen. Hierdurch wird der Abfrageoptimierer gezwungen, den Abfrageplan erneut zu kompilieren, wenn dieselbe Abfrage das nächste Mal ausgeführt wird. Ein Beispiel hierzu finden Sie unter [Planhinweislisten](plan-guides.md).  
  
 Darüber hinaus können Sie die Tabellenhinweise INDEX, FORCESCAN und FORCESEEK als Abfragehinweise angeben. Wenn diese Hinweise als Abfragehinweise angegeben werden, verhalten sie sich genauso wie eine Inline-Tabelle oder ein Sichthinweis. Der INDEX-Hinweis zwingt den Abfrageoptimierer, nur die angegebenen Indizes zu verwenden, um auf die Daten in der referenzierten Tabelle oder Sicht zuzugreifen. Der FORCESEEK-Hinweis zwingt den Abfrageoptimierer, nur einen Indexsuchvorgang zu verwenden, um auf die Daten in der referenzierten Tabelle oder Sicht zuzugreifen. Diese Hinweise stellen zusätzliche Planhinweislistenfunktionen bereit und ermöglichen einen größeren Einfluss auf die Optimierung von Abfragen, die die Planhinweisliste verwenden.  
  
  
