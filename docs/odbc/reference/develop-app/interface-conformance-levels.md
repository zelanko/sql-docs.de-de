---
title: Schnittstellenkonformitätsstufen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fff555324746fcb92641126ddf11ea91ce5e3f89
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304600"
---
# <a name="interface-conformance-levels"></a>Ebenen der Schnittstellenübereinstimmung
Der Zweck des Abgleichs besteht darin, die Anwendung darüber zu informieren, welche Funktionen dem Treiber vom Treiber zur Verfügung stehen. Ein auf Funktionen basierendes Abgleichsschema wird dieses Ziel nicht ausreichend erreicht. In ODBC 3. *x*werden Treiber basierend auf den Funktionen klassifiziert, die sie besitzen. Die Unterstützung der Funktion kann die Unterstützung der Funktion umfassen. Sie kann auch die Unterstützung eines Deskriptorfelds, ein Anweisungsattribut, einen "Y"-Wert für einen von **SQLGetInfo**zurückgegebenen Informationstyp usw. umfassen.  
  
 Um die Spezifikation der Schnittstellenkonformität zu vereinfachen, definiert ODBC drei Konformitätsstufen. Um ein bestimmtes Konformitätsniveau zu erfüllen, muss ein Fahrer alle Anforderungen dieser Konformitätsstufe erfüllen. Die Übereinstimmung mit einem bestimmten Level impliziert die vollständige Übereinstimmung mit allen unteren Ebenen.  
  
 Konformitätsebenen teilen sich nicht immer sauber in die Unterstützung für eine bestimmte Liste von ODBC-Funktionen auf, geben jedoch unterstützte Features an, wie in den folgenden Abschnitten aufgeführt. Um Unterstützung für ein Feature bereitzustellen, muss ein Treiber einige oder alle Formen von Aufrufen bestimmter ODBC-Funktionen unterstützen (weitere Informationen finden Sie unter [Funktionskonformität](../../../odbc/reference/develop-app/function-conformance.md)), Festlegen bestimmter Attribute (siehe [Attributkonformität](../../../odbc/reference/develop-app/attribute-conformance.md)) und bestimmter Deskriptorfelder (siehe [Deskriptorfeldkonformität](../../../odbc/reference/develop-app/descriptor-field-conformance.md)).  
  
 Die Anwendung erkennt die Schnittstellenkonformitätsstufe eines Treibers, indem sie eine Verbindung zu einer Datenquelle herstellt und **SQLGetInfo** mit der Option SQL_ODBC_INTERFACE_CONFORMANCE aufruft.  
  
 Den Fahrern steht es frei, Funktionen zu implementieren, die über das Niveau hinausgehen, auf dem sie die vollständige Konformität beanspruchen. Anwendungen ermitteln solche zusätzlichen Funktionen, indem sie **SQLGetFunctions** (um zu bestimmen, welche ODBC-Funktionen vorhanden sind) und **SQLGetInfo** (zum Abfragen verschiedener anderer ODBC-Funktionen) aufrufen.  
  
 Es gibt drei ODBC-Schnittstellenkonformitätsstufen: Core, Level 1 und Level 2.  
  
> [!NOTE]
>  Diese Konformitätsstufen haben andere Anforderungen als die ODBC-API-Konformitätsstufen mit dem gleichen Namen in ODBC 2 *.x*. Insbesondere sind alle Funktionen, die von ODBC 2 *.x* API-Konformitätsstufe 1 impliziert werden, jetzt Teil der Core-Schnittstellenkonformitätsebene. Daher können viele ODBC-Treiber Schnittstellenkonformität auf Core-Ebene melden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Schnittstellenübereinstimmung auf Kernebene](../../../odbc/reference/develop-app/core-interface-conformance.md)  
  
-   [Schnittstellenübereinstimmung auf Ebene 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md)  
  
-   [Schnittstellenübereinstimmung auf Ebene 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md)  
  
-   [Funktionsübereinstimmung](../../../odbc/reference/develop-app/function-conformance.md)  
  
-   [Attributübereinstimmung](../../../odbc/reference/develop-app/attribute-conformance.md)  
  
-   [Deskriptorfeldübereinstimmung](../../../odbc/reference/develop-app/descriptor-field-conformance.md)
