---
title: Konformitäts Ebenen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
- conformance levels [ODBC]
- conformance levels [ODBC], about conformance levels
ms.assetid: f776d467-5d5d-4761-9043-3dad5f73c610
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 507d23e6f7a344e9d3fe4a17cf34903235803426
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083168"
---
# <a name="conformance-levels"></a>Übereinstimmungsebenen
ODBC-Treiber erhalten der Anwendung Zugriff auf verschiedene Datenquellen. Mit jedem Treiber kann die Anwendung zur Laufzeit bestimmen, welche ODBC-Funktionen und welche SQL-Grammatik der Treiber und die einzelnen Datenquellen unterstützen. Dies ist keine Voraussetzung für Anwendungen, die für die Arbeit mit einem einzelnen Treiber oder einem kleinen, bekannten Satz von Treibern entwickelt wurden, da diese Anwendungen einfach in die Funktionen dieses Treibers oder der Treiber geschrieben werden können. Damit Anwendungen Treiber-und Datenquellen Funktionen entdecken können, sind zwei Bereiche der Konformität verfügbar: die ODBC-Schnittstelle und die SQL-Grammatik.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Ebenen der Schnittstellenübereinstimmung](../../../odbc/reference/develop-app/interface-conformance-levels.md)  
  
-   [SQL-Übereinstimmungsebenen](../../../odbc/reference/develop-app/sql-conformance-levels.md)
