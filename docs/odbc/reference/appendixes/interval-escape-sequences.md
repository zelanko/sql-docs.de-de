---
title: Intervall-Escapesequenzen | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041641"
---
# <a name="interval-escape-sequences"></a>Intervall-Escapesequenzen
ODBC verwendet Escapesequenzen für intervallliterale. Die Syntax dieser Escapesequenz lautet wie folgt:  
  
 {*Interval-Literale*}  
  
 Die BNF-Syntax von *Interval-literalen*finden Sie im Abschnitt [Intervall Literalsyntax](../../../odbc/reference/appendixes/interval-literal-syntax.md) weiter unten in diesem Anhang.  
  
 Die Literale Escapesequenz für Intervalle wird unterstützt, wenn die Intervall Datentypen von der Datenquelle unterstützt werden. Eine Anwendung sollte **SQLGetTypeInfo** aufrufen, um zu bestimmen, ob diese Datentypen unterstützt werden.
