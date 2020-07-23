---
title: SELECT INTO (DMX) | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: a0a245d152ddd9946142f5f115ee1db64ee5998b
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86970513"
---
# <a name="select-into-dmx"></a>SELECT INTO (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Erstellt ein neues Miningmodell, das auf der Miningstruktur eines vorhandenen Miningmodells basiert. Die **SELECT INTO** -Anweisung erstellt das neue Mining Modell, indem das Schema und andere Informationen kopiert werden, die nicht für den eigentlichen Algorithmus spezifisch sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SELECT INTO <new model>   
USING <algorithm> [(<parameter list>)] [WITH DRILLTHROUGH[,] [FILTER(<expression>)]]  
FROM <existing model>  
```  
  
## <a name="arguments"></a>Argumente  
 *new model*  
 Ein eindeutiger Name für das neue Modell, das erstellt wird.  
  
 *projiziert*  
 Der vom Anbieter definierte Name eines Data Mining-Algorithmus.  
  
 *Parameterliste*  
 Dies ist optional. Eine durch Trennzeichen getrennte Liste mit anbieterdefinierten Parametern für den Algorithmus.  
  
 *expression*  
 Ein Ausdruck, der auf den Trainingsdaten eine gültige Filterbedingung ergibt. Weitere Informationen zu Ausdrücken, die als Filter verwendet werden können, finden Sie unter [Filter für Mining Modelle &#40;Analysis Services Data Mining-&#41;](https://docs.microsoft.com/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining).  
  
 *vorhandenes Modell*  
 Der Name des vorhandenen Modells, das kopiert werden soll.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn das vorhandene Modell trainiert ist, wird das neue Modell automatisch verarbeitet, wenn diese Anweisung ausgeführt wird. Anderenfalls bleibt das neue Modell unverarbeitet.  
  
 Die **SELECT INTO** -Anweisung funktioniert nur, wenn die Struktur des vorhandenen Modells mit dem Algorithmus des neuen Modells kompatibel ist. Daher ist diese Anweisung sehr zweckmäßig, um Modelle, die auf dem gleichen Algorithmus basieren, schnell zu erstellen und zu testen. Wenn Sie den Algorithmustyp ändern, muss der neue Algorithmus den Datentyp einer jeden Spalte unterstützen, die sich im vorhandenen Modell befindet, andernfalls tritt bei der Verarbeitung des Modells möglicherweise ein Fehler auf.  
  
 Die **with Drillthrough** -Klausel ermöglicht einen Drillthrough für das neue Mining Modell. Drillthrough kann nur aktiviert werden, wenn das Modell erstellt wird.  
  
## <a name="example-1-altering-the-parameters-of-the-model"></a>Beispiel 1: Ändern der Parameter des Modells  
 Im folgenden Beispiel wird ein neues Mining Modell erstellt, das auf einem vorhandenen Mining Modell basiert, `TM_Clustering` das Sie im Lernprogramm zu [Data Mining-Grundlagen](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)erstellen. In dem neuen Modell wird der CLUSTER_COUNT-Parameter geändert, sodass das neue Modell maximal fünf Cluster enthält. Demgegenüber verwendet das vorhandene Modell den Standardwert 10.  
  
```  
SELECT * INTO [New_Clustering]  
USING [Microsoft_Clustering] (CLUSTER_COUNT = 5)   
FROM [TM Clustering]  
```  
  
## <a name="example-2-adding-a-filter-to-the-model"></a>Beispiel 2: Hinzufügen eines Filters zu dem Modell  
 Im folgenden Beispiel wird ein neues Miningmodell auf der Grundlage eines vorhandenen Miningmodells erstellt und dem Modell ein Filter hinzugefügt. Der Filter beschränkt die Trainingsdaten auf die Kunden, die in einer bestimmten Region wohnen.  
  
```  
SELECT * INTO [Clustering Europe Region]  
USING [Microsoft_Clustering] WITH FILTER(Region='Europe')  
FROM [TM Clustering]  
```  
  
> [!NOTE]  
>  Filter, die auf die Falltabelle angewendet werden, können mithilfe der SELECT INTO-Anweisung geändert werden, wie in diesem Beispiel erläutert wird. Wenn das ursprüngliche Modell jedoch einen Filter für eine geschachtelte Tabelle enthält, kann dieser Filter nicht mithilfe dieser Syntax geändert oder entfernt werden, er wird stattdessen unverändert aus dem ursprünglichen Modell kopiert. Um ein Modell mit einem anderen Filter für eine geschachtelte Tabelle zu erstellen, verwenden Sie stattdessen die ALTER STRTUCTURE...ADD MODEL-Syntax.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Definitions Anweisungen](../dmx/dmx-statements-data-definition.md)   
 [Data Mining-Erweiterungen &#40;DMX-&#41; Daten Bearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
