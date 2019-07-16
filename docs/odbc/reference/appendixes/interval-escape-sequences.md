---
title: Intervallescapesequenzen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 69c674ee8838273af9bf4ed91ddcead7e1768fb9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041641"
---
# <a name="interval-escape-sequences"></a>Intervall-Escapesequenzen
ODBC verwendet Escape-Sequenzen, für die Intervall-Literale. Die Syntax dieser Escape-Sequenz lautet wie folgt aus:  
  
 {*Intervall-Literal*}  
  
 Informationen zur BNF-Syntax von *Intervall-Literal*, finden Sie unter den [Intervall Literal-Syntax](../../../odbc/reference/appendixes/interval-literal-syntax.md) weiter unten in diesem Anhang.  
  
 Die Intervall-Literale-Escape-Sequenz wird unterstützt, wenn die Interval-Datentypen, die von der Datenquelle unterstützt werden. Es sollte eine Anwendung aufrufen **SQLGetTypeInfo** zu bestimmen, ob diese Datentypen unterstützt werden.
