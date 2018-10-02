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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 218b5d1aba71e5905937bd5433f9f1316c473ab8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740608"
---
# <a name="string-padding-ssis"></a>Auffüllen von Zeichenfolgen (SSIS)
  Die Ausdrucksauswertung überprüft nicht, ob eine Zeichenfolge führende und nachfolgende Leerzeichen enthält, und Zeichenfolgen werden vor dem Vergleichen nicht auf die gleiche Länge aufgefüllt. Falls Ausdrücke das Auffüllen von Zeichenfolgen erfordern, können Sie mit dem +-Operator Spaltenwerte und leere Zeichenfolgen verketten. Weitere Informationen finden Sie unter [+ &#40;Verketten, SSIS-Ausdruck&#41;](../../integration-services/expressions/concatenate-ssis-expression.md).  
  
 Wenn Sie andererseits Leerzeichen entfernen möchten, stellt die Ausdrucksauswertung die Funktionen LTRIM, RTRIM und TRIM bereit, die führende und/oder nachfolgende Leerzeichen entfernen. Weitere Informationen finden Sie unter [LTRIM &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/ltrim-ssis-expression.md), [RTRIM &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/rtrim-ssis-expression.md) und [TRIM &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/trim-ssis-expression.md).  
  
> [!NOTE]  
>  Die LEN-Funktion berücksichtigt beim Zählen führende und nachfolgende Leerzeichen.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Technischer Artikel, [SSIS Expression Cheat Sheet](http://go.microsoft.com/fwlink/?LinkId=746575), auf pragmaticworks.com  
  
  
