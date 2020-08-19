---
description: Intervall-Escapesequenzen
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
ms.openlocfilehash: e2ef792403352568ce5f8d92c07a5b0e1027b507
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483293"
---
# <a name="interval-escape-sequences"></a>Intervall-Escapesequenzen
ODBC verwendet Escapesequenzen für intervallliterale. Die Syntax dieser Escapesequenz lautet wie folgt:  
  
 {*Interval-Literale*}  
  
 Die BNF-Syntax von *Interval-literalen*finden Sie im Abschnitt [Intervall Literalsyntax](../../../odbc/reference/appendixes/interval-literal-syntax.md) weiter unten in diesem Anhang.  
  
 Die Literale Escapesequenz für Intervalle wird unterstützt, wenn die Intervall Datentypen von der Datenquelle unterstützt werden. Eine Anwendung sollte **SQLGetTypeInfo** aufrufen, um zu bestimmen, ob diese Datentypen unterstützt werden.
