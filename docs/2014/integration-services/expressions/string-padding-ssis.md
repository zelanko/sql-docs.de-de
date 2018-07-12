---
title: Auffüllen von Zeichenfolgen (SSIS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b95eed3c086b0d9e07feb11c353e90cece56a18e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152881"
---
# <a name="string-padding-ssis"></a>Auffüllen von Zeichenfolgen (SSIS)
  Die Ausdrucksauswertung überprüft nicht, ob eine Zeichenfolge führende und nachfolgende Leerzeichen enthält, und Zeichenfolgen werden vor dem Vergleichen nicht auf die gleiche Länge aufgefüllt. Falls Ausdrücke das Auffüllen von Zeichenfolgen erfordern, können Sie mit dem +-Operator Spaltenwerte und leere Zeichenfolgen verketten. Weitere Informationen finden Sie unter [+ &#40;Verketten, SSIS-Ausdruck&#41;](concatenate-ssis-expression.md).  
  
 Wenn Sie andererseits Leerzeichen entfernen möchten, stellt die Ausdrucksauswertung die Funktionen LTRIM, RTRIM und TRIM bereit, die führende und/oder nachfolgende Leerzeichen entfernen. Weitere Informationen finden Sie unter [LTRIM &#40;SSIS-Ausdruck&#41;](trim-ssis-expression.md), [RTRIM &#40;SSIS-Ausdruck&#41;](rtrim-ssis-expression.md) und [TRIM &#40;SSIS-Ausdruck&#41;](trim-ssis-expression.md).  
  
> [!NOTE]  
>  Die LEN-Funktion berücksichtigt beim Zählen führende und nachfolgende Leerzeichen.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Technischer Artikel, [SSIS Expression Cheat Sheet](http://go.microsoft.com/fwlink/?LinkId=217683), auf pragmaticworks.com  
  
  
