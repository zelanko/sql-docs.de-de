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
manager: craigg
ms.openlocfilehash: 81481db74d973da0e54bc6bf9e70550fa3cc0c81
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188886"
---
# <a name="interval-escape-sequences"></a>Intervall-Escapesequenzen
ODBC verwendet Escape-Sequenzen, für die Intervall-Literale. Die Syntax dieser Escape-Sequenz lautet wie folgt aus:  
  
 {*interval-literal*}  
  
 Informationen zur BNF-Syntax von *Intervall-Literal*, finden Sie unter den [Intervall Literal-Syntax](../../../odbc/reference/appendixes/interval-literal-syntax.md) weiter unten in diesem Anhang.  
  
 Die Intervall-Literale-Escape-Sequenz wird unterstützt, wenn die Interval-Datentypen, die von der Datenquelle unterstützt werden. Es sollte eine Anwendung aufrufen **SQLGetTypeInfo** zu bestimmen, ob diese Datentypen unterstützt werden.
