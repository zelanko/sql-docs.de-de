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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9fe7f6941e9ec9fba8b6698faaa18a678732dd6f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304955"
---
# <a name="interval-escape-sequences"></a>Intervall-Escapesequenzen
ODBC verwendet Escapesequenzen für intervallliterale. Die Syntax dieser Escapesequenz lautet wie folgt:  
  
 {*Interval-Literale*}  
  
 Die BNF-Syntax von *Interval-literalen*finden Sie im Abschnitt [Intervall Literalsyntax](../../../odbc/reference/appendixes/interval-literal-syntax.md) weiter unten in diesem Anhang.  
  
 Die Literale Escapesequenz für Intervalle wird unterstützt, wenn die Intervall Datentypen von der Datenquelle unterstützt werden. Eine Anwendung sollte **SQLGetTypeInfo** aufrufen, um zu bestimmen, ob diese Datentypen unterstützt werden.
