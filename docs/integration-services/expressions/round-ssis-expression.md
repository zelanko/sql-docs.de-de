---
title: ROUND (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- rounding expressions
- ROUND function [SSIS]
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 74b18ed725b70e1086b22515a0a051d2521383b7
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "71288322"
---
# <a name="round-ssis-expression"></a>ROUND (SSIS-Ausdruck)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Gibt einen numerischen Ausdruck zurück, der auf die angegebene Länge oder Genauigkeit gerundet wurde. Der length-Parameter muss zu einer ganzen Zahl ausgewertet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## <a name="arguments"></a>Argumente  
 *numeric_expression*  
 Ein Ausdruck eines gültigen numerischen Datentyps. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
 *length*  
 Ein ganzzahliger Ausdruck. Dies ist die Genauigkeit, auf die *numeric_expression* gerundet wird.  
  
## <a name="result-types"></a>Ergebnistypen  
 Der Typ entspricht dem Typ von *numeric*_*expression*.  
  
## <a name="remarks"></a>Bemerkungen  
 Das *length* -Argument muss zu einer positiven ganzen Zahl oder 0 (null) ausgewertet werden.  
  
 ROUND gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 Diese Beispiele runden numerische Literale auf eine Länge von drei. Als erstes Ergebnis wird 137.1570 zurückgegeben und als zweites Ergebnis 137.1580.  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
