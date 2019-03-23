---
title: Numerische Datenformate | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- integer data types [Integration Services]
- numeric data formats for fast parse
- locale-sensitive parsing [Integration Services]
- fast parse [Integration Services]
ms.assetid: fa3975ce-9d21-408a-857d-f85e30af27b0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a89b37f2210b2a80d22747a816e4f937cbc54ee1
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58375638"
---
# <a name="numeric-data-formats"></a>Numerische Datenformate
  Die schnelle Analyse stellt schnelle, einfache und gebietsschemabezogene Routinen zum Analysieren von Daten bereit. Nur bestimmte Formate für integer-Datentypen werden von der schnellen Analyse unterstützt.  
  
## <a name="integer-data-types"></a>Integer-Datentypen  
 Die integer-Datentypen von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sind DT_I1, DT_UI1, DT_I2, DT_UI2, DT_I4, DT_UI4, DT_I8 und DT_UI8. Weitere Informationen finden Sie unter [Integration Services Datentypen](data-flow/integration-services-data-types.md).  
  
 Die schnelle Analyse unterstützt die folgenden Formate für integer-Datentypen:  
  
-   Null oder mehr führende und nachfolgende Leerzeichen oder Tabstopps. Beispielsweise ist der Wert "  123  " gültig. Ein Wert, der nur aus Leerzeichen besteht, wird zu Null ausgewertet.  
  
-   Ein führendes Pluszeichen, Minuszeichen oder keines von beiden. Beispielsweise sind die Werte +123, -123 und 123 gültig.  
  
-   Mindestens eine hindu-arabische Ziffer (0-9). Beispielsweise ist der Wert 345 gültig. Ziffern aus anderen Sprachen werden nicht unterstützt.  
  
 Folgende Datenformate werden nicht unterstützt:  
  
-   Sonderzeichen. Beispielsweise wird das Währungszeichen $ nicht unterstützt, und der Wert $20 kann nicht analysiert werden.  
  
-   Leerzeichen, wie z. B. ein Zeilenvorschub, ein Wagenrücklauf und ein geschütztes Leerzeichen. Beispielsweise kann der Wert " 123" nicht analysiert werden.  
  
-   Hexadezimale Darstellungen von ganzen Zahlen. Beispielsweise kann der Wert 2EE nicht analysiert werden.  
  
-   Darstellung von ganzen Zahlen in wissenschaftlicher Schreibweise. Beispielsweise kann der Wert 1E+10 nicht analysiert werden.  
  
 Die folgenden Formate sind Ausgabedatenformate für ganze Zahlen:  
  
-   Ein Minuszeichen für negative Zahlen und kein Zeichen für positive Zahlen.  
  
-   Keine Leerzeichen.  
  
-   Mindestens eine hindu-arabische Ziffer (0-9).  
  
  
