---
description: 'Anhang G: Treiberrichtlinien für Abwärtskompatibilität'
title: 'Anhang G: Treiber Richtlinien für Abwärtskompatibilität | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 911cd335-f2c0-4d03-9739-1078308a678a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e2c09485879c2f0d16518dcfc0a17f4bf3a13943
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411406"
---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>Anhang G: Treiberrichtlinien für Abwärtskompatibilität
Dieser Anhang enthält Informationen für Treiber Schreiber, die auf ODBC 3 arbeiten. *x* -Treiber, die ODBC 2 unterstützen müssen. *x* -Anwendungen. Weitere Informationen zur Abwärtskompatibilität finden Sie unter abwärts [Kompatibilität und Einhaltung von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Block Cursor, scrollfähige Cursor und Abwärtskompatibilität für ODBC 3. x-Treiber](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) : neue Features sind Features, die in ODBC 3 vorhanden sind. *x* und nicht in ODBC 2. *x*. ODBC 3. *x* -Treiber müssen sich in der Regel nicht um die Abwärtskompatibilität mit neuen Features kümmern, da ODBC 2. von *x* -Anwendungen werden Sie niemals verwendet. Die einzige Ausnahme hiervon sind Funktionen im Zusammenhang mit **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**und **SQLExtendedFetch**;. Weitere Informationen finden Sie unter weiter unten in diesem Anhang.  
  
-   [Mapping als veraltet markierte Funktionen](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) : doppelte Features sind Features, die in ODBC 3 anders implementiert werden. *x* und ODBC 2. *x*. ODBC 3. *x* -Treiber müssen sich keine Gedanken über die Abwärtskompatibilität mit duplizierten Features machen, da der Treiber-Manager immer ODBC 2 zuordnet. *x* -Funktionen für ODBC 3. *x* -Funktionen beim Aufrufen von ODBC 3. *x* -Treiber Dies ist also ein ODBC 3. der *x* -Treiber sieht nur ODBC 3. *x* -Funktionen. Weitere Informationen zu diesen Zuordnungen finden Sie unter weiter unten in diesem Anhang.  
  
-   [Verhaltensänderungen und ODBC 3. x-Treiber](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) : Verhaltensänderungen sind Features, die in ODBC 3 anders behandelt werden. *x* und ODBC 2. *x*. ODBC 3. *x* -Treiber müssen sich Gedanken über Verhaltensänderungen machen und als Reaktion auf das von der Anwendung festgelegte SQL_ATTR_ODBC_VERSION-Umgebungs Attribut agieren.
