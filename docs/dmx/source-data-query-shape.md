---
title: FORM (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8e5c86484252d45c8c7edbd79690159e116d9b3a
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841673"
---
# <a name="ltsource-data-querygt---shape"></a>&lt;quelldatenabfrage&gt; -Form
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Kombiniert Abfragen aus mehreren Datenquellen in einer hierarchischen Tabelle (eine Tabelle mit geschachtelten Tabellen), die zur Falltabelle für das Miningmodell wird.  
  
 Die vollständige Syntax eines der **Form** Befehl finden Sie der [!INCLUDE[msCoName](../includes/msconame-md.md)] Data Access Components (MDAC) Software Development Kit (SDK).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
SHAPE {<master query>}  
APPEND ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>Argumente  
 *Master-Abfrage*  
 Die Abfrage, die die übergeordnete Tabelle zurückgibt.  
  
 *Abfrage der untergeordneten Tabelle*  
 Die Abfrage, die die geschachtelte Tabelle zurückgibt.  
  
 *Master-Spalte*  
 Die Spalte in der übergeordneten Tabelle, die die untergeordneten Zeilen aus dem Ergebnis einer Abfrage der untergeordneten Tabelle (child table query) kennzeichnet.  
  
 *untergeordnete Spalte*  
 Die Spalte in der untergeordneten Tabelle, die die übergeordneten Zeilen aus dem Ergebnis einer Masterabfrage (master query) kennzeichnet.  
  
 *Spaltenname für die Tabelle*  
 Der neu angefügte Spaltenname in der übergeordneten Tabelle für die geschachtelte Tabelle.  
  
## <a name="remarks"></a>Hinweise  
 Sie müssen die Abfragen nach der Spalte sortieren, die die übergeordnete Tabelle und die untergeordnete Tabelle verknüpft.  
  
## <a name="examples"></a>Beispiele  
 Sie können das folgende Beispiel in einer [INSERT INTO &#40;DMX&#41; ](../dmx/insert-into-dmx.md) Anweisung zum Trainieren eines Modells, das eine geschachtelte Tabelle enthält. Die beiden Tabellen in der **Form** Anweisung beziehen sich über die **OrderNumber** Spalte.  
  
```  
SHAPE {  
    OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
```  
  
## <a name="see-also"></a>Siehe auch  
 [&#60;quelldatenabfrage&#62;](../dmx/source-data-query.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datendefinitionsanweisungen](../dmx/dmx-statements-data-definition.md)   
 [Datamining-Erweiterungen &#40;DMX&#41; -Datenbearbeitungsanweisungen](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
