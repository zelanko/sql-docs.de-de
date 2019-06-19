---
title: Auffüllen von Zeichenfolgen (SSIS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: cddc755a958850c7042ec59c7c4703ee77716c76
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65724946"
---
# <a name="string-padding-ssis"></a>Auffüllen von Zeichenfolgen (SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Die Ausdrucksauswertung überprüft nicht, ob eine Zeichenfolge führende und nachfolgende Leerzeichen enthält, und Zeichenfolgen werden vor dem Vergleichen nicht auf die gleiche Länge aufgefüllt. Falls Ausdrücke das Auffüllen von Zeichenfolgen erfordern, können Sie mit dem +-Operator Spaltenwerte und leere Zeichenfolgen verketten. Weitere Informationen finden Sie unter [+ &#40;Verketten, SSIS-Ausdruck&#41;](../../integration-services/expressions/concatenate-ssis-expression.md).  
  
 Wenn Sie andererseits Leerzeichen entfernen möchten, stellt die Ausdrucksauswertung die Funktionen LTRIM, RTRIM und TRIM bereit, die führende und/oder nachfolgende Leerzeichen entfernen. Weitere Informationen finden Sie unter [LTRIM &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/ltrim-ssis-expression.md), [RTRIM &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/rtrim-ssis-expression.md) und [TRIM &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/trim-ssis-expression.md).  
  
> [!NOTE]  
>  Die LEN-Funktion berücksichtigt beim Zählen führende und nachfolgende Leerzeichen.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Technischer Artikel, [SSIS Expression Cheat Sheet](https://go.microsoft.com/fwlink/?LinkId=746575), auf pragmaticworks.com  
  
  
