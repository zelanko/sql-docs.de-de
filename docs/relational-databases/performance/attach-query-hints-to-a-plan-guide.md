---
title: Anfügen von Abfragehinweisen an eine Planhinweisliste | Microsoft-Dokumentation
description: In einer Planhinweisliste können beliebige Kombinationen gültiger Abfragehinweise verwendet werden. Informationen zum Anfügen von Hinweisen an eine Planhinweisliste in SQL Server.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 2131f796-6359-4f9e-9047-da0b3d4dedaf
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 6d2980803fb7a3361d74ccd86c0bcef4da734317
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505387"
---
# <a name="attach-query-hints-to-a-plan-guide"></a>Anfügen von Abfragehinweisen an eine Planhinweisliste
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  In einer Planhinweisliste können beliebige Kombinationen gültiger Abfragehinweise verwendet werden. Wenn eine Planhinweisliste mit einer Abfrage übereinstimmt, wird die in der Hinweisklausel einer Planhinweisliste angegebene OPTION-Klausel vor dem Kompilieren und Optimieren zur Abfrage hinzugefügt. Wenn eine mit einer Planhinweisliste übereinstimmende Abfrage bereits eine OPTION-Klausel besitzt, ersetzen die in der Planhinweisliste angegebenen Abfragehinweise die in der Abfrage enthaltenen. Damit eine Planhinweisliste mit einer Abfrage übereinstimmt, die bereits eine OPTION-Klausel besitzt, müssen Sie die OPTION-Klausel der Abfrage aufnehmen, wenn Sie den Text der Abfrage angeben, der mit der sp_create_plan_guide-Anweisung übereinstimmen soll. Wenn Sie möchten, dass die in der Planhinweisliste angegebenen Abfragehinweise den bereits in der Abfrage vorhandenen Hinweisen hinzugefügt werden, statt diese zu ersetzen, müssen Sie in der OPTION-Klausel der Planhinweisliste sowohl die ursprünglichen Hinweise als auch die zusätzlichen Hinweise angeben.  
  
> [!CAUTION]  
>  Bei falscher Verwendung von Abfragehinweisen in Planhinweislisten kann es zu Kompilierungs-, Ausführungs- oder Leistungsproblemen kommen. Daher sollten Planhinweislisten nur von erfahrenen Entwicklern und Datenbankadministratoren verwendet werden.  
  
## <a name="common-query-hints-used-in-plan-guides"></a>Allgemeine Abfragehinweise in Planhinweislisten  
 Abfragen, für die sich Planhinweislisten eignen, basieren im Allgemeinen auf Parametern und weisen möglicherweise eine unzureichende Leistung auf, weil sie zwischengespeicherte Abfragepläne verwenden, deren Parameterwerte nicht das passende repräsentative (oder Worst-Case-) Szenario darstellen. Um dieses Problem zu lösen, können der OPTIMIZE FOR-Abfragehinweis und der RECOMPILE-Abfragehinweis verwendet werden. Durch OPTIMIZE FOR wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angewiesen, bei der Abfrageoptimierung einen bestimmten Parameterwert zu verwenden. Durch RECOMPILE wird der Server angewiesen, einen Abfrageplan nach der Ausführung wieder zu verwerfen. Hierdurch wird der Abfrageoptimierer gezwungen, den Abfrageplan erneut zu kompilieren, wenn dieselbe Abfrage das nächste Mal ausgeführt wird. Ein Beispiel hierzu finden Sie unter [Planhinweislisten](../../relational-databases/performance/plan-guides.md).  
  
 Darüber hinaus können Sie die Tabellenhinweise INDEX, FORCESCAN und FORCESEEK als Abfragehinweise angeben. Wenn diese Hinweise als Abfragehinweise angegeben werden, verhalten sie sich genauso wie eine Inline-Tabelle oder ein Sichthinweis. Der INDEX-Hinweis zwingt den Abfrageoptimierer, nur die angegebenen Indizes zu verwenden, um auf die Daten in der referenzierten Tabelle oder Sicht zuzugreifen. Der FORCESEEK-Hinweis zwingt den Abfrageoptimierer, nur einen Indexsuchvorgang zu verwenden, um auf die Daten in der referenzierten Tabelle oder Sicht zuzugreifen. Diese Hinweise stellen zusätzliche Planhinweislistenfunktionen bereit und ermöglichen einen größeren Einfluss auf die Optimierung von Abfragen, die die Planhinweisliste verwenden.  
  
  
