---
title: Ebenen der Schnittstellenübereinstimmung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: 2c470e54-0600-4b2b-b1f3-9885cb28a01a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 74d4ceb4532ee09004f035958860833aef488aaa
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206207"
---
# <a name="interface-conformance-levels"></a>Ebenen der Schnittstellenübereinstimmung
Der Zweck der Lastenausgleich ist auf die Anwendung zu informieren, welche Features, aus dem Treiber verfügbar sind. Eine leveling-Schema anhand von Funktionen erreichen dieses Ziels nicht ausreichend. In ODBC 3. *x*, Treiber klassifiziert sind, basierend auf den Features, die sie besitzen. Unterstützung der Funktions, kann die Unterstützung der Funktion enthalten; Er kann auch die Unterstützung von einem Beschreibungsfeld, ein Anweisungsattribut, einen Wert "Y" für ein zurückgegebenes Informationstyp enthalten **SQLGetInfo**und so weiter.  
  
 Zur Vereinfachung der Spezifikation der schnittstellenübereinstimmung definiert ODBC drei Ebenen der schnittstellenübereinstimmung. Um einen bestimmten Konformitätsgrad erfüllen zu können, muss ein Treiber alle Anforderungen von diesen Grad der Übereinstimmung mit Standards erfüllen. Übereinstimmung mit einer bestimmten Ebene weist darauf hin, vollständige Übereinstimmung mit alle niedrigeren Ebenen.  
  
 Ebenen der schnittstellenübereinstimmung sind nicht immer ordentlich in unterteilen Unterstützung für eine bestimmte Liste von ODBC-Funktionen, aber geben Sie unterstützte Funktionen, wie in den folgenden Abschnitten aufgeführt. Um ein Feature unterstützen, muss ein Treiber einige oder alle Formen der Aufrufe von bestimmten ODBC-Funktionen unterstützen (Weitere Informationen finden Sie unter [Funktionsübereinstimmung](../../../odbc/reference/develop-app/function-conformance.md)), Festlegen bestimmter Attribute (finden Sie unter [Attributübereinstimmung ](../../../odbc/reference/develop-app/attribute-conformance.md)), und bestimmte deskriptorfeldern (finden Sie unter [Deskriptorfeldübereinstimmung](../../../odbc/reference/develop-app/descriptor-field-conformance.md)).  
  
 Die Anwendung ermittelt Schnittstelle-Konformitätsgrad des Treibers durch Herstellen einer Verbindung mit einer Datenquelle und Aufrufen **SQLGetInfo** mit der Option SQL_ODBC_INTERFACE_CONFORMANCE.  
  
 Treiber können-Funktionen jenseits der Ebene zu implementieren, zu dem er die vollständige Übereinstimmung mit Standards vorgibt. Anwendungen ermitteln Sie alle zusätzlichen Funktionen durch Aufrufen von **SQLGetFunctions** (um zu ermitteln, welche ODBC-Funktionen vorhanden sind) und **SQLGetInfo** (zum Abfragen von verschiedenen anderen ODBC-Funktionen).  
  
 Es gibt drei Konformitätsgrad des ODBC-Schnittstelle: Core, Ebene 1 und Ebene 2.  
  
> [!NOTE]
>  Diese Ebenen der schnittstellenübereinstimmung haben unterschiedliche Anforderungen an als der ODBC-API-Ebenen der schnittstellenübereinstimmung mit dem gleichen Namen in ODBC 2.*.x*. Insbesondere alle Funktionen, die durch ODBC 2. impliziert *.x* -API-Übereinstimmung mit Standards Level 1 sind jetzt Bestandteil der Konformitätsgrad des Core-Schnittstelle. Daher können viele ODBC-Treiber-Kernebenen-schnittstellenübereinstimmung melden.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Kernschnittstellenübereinstimmung](../../../odbc/reference/develop-app/core-interface-conformance.md)  
  
-   [Schnittstellenübereinstimmung der ersten Ebene](../../../odbc/reference/develop-app/level-1-interface-conformance.md)  
  
-   [Ebene 2-Schnittstellenübereinstimmung](../../../odbc/reference/develop-app/level-2-interface-conformance.md)  
  
-   [Funktionsübereinstimmung](../../../odbc/reference/develop-app/function-conformance.md)  
  
-   [Attributübereinstimmung](../../../odbc/reference/develop-app/attribute-conformance.md)  
  
-   [Deskriptorfeldübereinstimmung](../../../odbc/reference/develop-app/descriptor-field-conformance.md)
