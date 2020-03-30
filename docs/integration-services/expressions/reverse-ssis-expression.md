---
title: REVERSE (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d7a0e8974f781f5f69817cf3374416de7bc32580
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "71288386"
---
# <a name="reverse-ssis-expression"></a>REVERSE (SSIS-Ausdruck)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Gibt einen Zeichenausdruck in umgekehrter Reihenfolge zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
REVERSE(character_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *character_expression*  
 Der Zeichenausdruck, dessen Reihenfolge umgekehrt werden soll.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_WSTR  
  
## <a name="remarks"></a>Bemerkungen  
 Das *character_expression* -Argument muss den Datentyp „DT_WSTR“ aufweisen.  
  
 REVERSE gibt ein NULL-Ergebnis zurück, wenn *character_expression* NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird ein Zeichenfolgenliteral verwendet. Als Ergebnis wird "ekiB niatnuoM" zurückgegeben.  
  
```  
REVERSE("Mountain Bike")  
```  
  
 In diesem Beispiel wird eine Variable verwendet. Falls **Name** Touring Bike enthält, wird als Ergebnis "ekiB gniruoT" zurückgegeben.  
  
```  
REVERSE(@Name)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
