---
title: Schnittstellen Übereinstimmungs Ebenen | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304600"
---
# <a name="interface-conformance-levels"></a>Ebenen der Schnittstellenübereinstimmung
Der Zweck der Durchsetzung besteht darin, die Anwendung darüber zu informieren, welche Features Ihnen vom Treiber zur Verfügung stehen. Ein auf Funktionen basierendes Ausgleichs Schema erreicht dieses Ziel nicht ausreichend. In ODBC 3. *x*, die Treiber werden basierend auf den Features klassifiziert, die Sie besitzen. Die Unterstützung der Funktion kann das unterstützen der Funktion einschließen. Sie kann auch das unterstützen eines deskriptorfelds, eines Anweisungs Attributs, eines "Y"-Werts für einen von **SQLGetInfo**zurückgegebenen Informationstyp usw. einschließen.  
  
 Um die Spezifikation der Schnittstellen Konformität zu vereinfachen, definiert ODBC drei Konformitäts Ebenen. Um einen bestimmten Konformitäts Grad zu erreichen, muss ein Treiber alle Anforderungen dieser Konformitätsstufe erfüllen. Die Konformität mit einer bestimmten Ebene impliziert vollständige Konformität mit allen niedrigeren Ebenen.  
  
 Konformitätsstufen unterstützen nicht immer die Unterstützung für eine bestimmte Liste von ODBC-Funktionen, aber Sie geben die unterstützten Funktionen an, die in den folgenden Abschnitten aufgeführt sind. Um Unterstützung für eine Funktion bereitzustellen, muss ein Treiber einige oder alle Formen von Aufrufen bestimmter ODBC-Funktionen unterstützen (Weitere Informationen finden Sie unter [Funktions](../../../odbc/reference/develop-app/function-conformance.md)Übereinstimmung), bestimmte Attribute festlegen (siehe [Attribut Konformität](../../../odbc/reference/develop-app/attribute-conformance.md)) und bestimmte Deskriptorfelder (siehe [Deskriptorfeld Konformität](../../../odbc/reference/develop-app/descriptor-field-conformance.md)).  
  
 Die Anwendung ermittelt die Schnittstellen Übereinstimmungs Ebene eines Treibers, indem eine Verbindung mit einer Datenquelle hergestellt und **SQLGetInfo** mit der Option SQL_ODBC_INTERFACE_CONFORMANCE aufgerufen wird.  
  
 Treiber können Funktionen außer der Ebene implementieren, auf die Sie eine komplette Konformität beanspruchen. Anwendungen entdecken diese zusätzlichen Funktionen, indem Sie **SQLGetFunctions** aufrufen (um zu ermitteln, welche ODBC-Funktionen vorhanden sind) und **SQLGetInfo** (um verschiedene andere ODBC-Funktionen abzufragen).  
  
 Es gibt drei Übereinstimmungs Ebenen der ODBC-Schnittstelle: Core, Level 1 und Level 2.  
  
> [!NOTE]
>  Diese Konformitätsstufen haben unterschiedliche Anforderungen als die Konformitäts Ebenen der ODBC-API mit demselben Namen in ODBC 2 *. x*. Insbesondere sind alle Features, die von der ODBC 2 *. x* -API-Konformitätsstufe 1 impliziert werden, nun Bestandteil der Kern Schnittstellen-Konformitäts Ebene. Daher können viele ODBC-Treiber die Schnittstellen Konformität auf Kern Ebene melden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Schnittstellenübereinstimmung auf Kernebene](../../../odbc/reference/develop-app/core-interface-conformance.md)  
  
-   [Schnittstellenübereinstimmung auf Ebene 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md)  
  
-   [Schnittstellenübereinstimmung auf Ebene 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md)  
  
-   [Funktionsübereinstimmung](../../../odbc/reference/develop-app/function-conformance.md)  
  
-   [Attributübereinstimmung](../../../odbc/reference/develop-app/attribute-conformance.md)  
  
-   [Deskriptorfeldübereinstimmung](../../../odbc/reference/develop-app/descriptor-field-conformance.md)
