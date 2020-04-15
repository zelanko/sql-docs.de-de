---
title: 'Anhang G: Treiberrichtlinien für die Abwärtskompatibilität | Microsoft Docs'
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
ms.openlocfilehash: 1055f94cb54bba9262f210e5df5f028029aebf5b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292400"
---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>Anhang G: Treiberrichtlinien für Abwärtskompatibilität
Dieser Anhang enthält Informationen für Treiberautoren, die an ODBC 3 arbeiten. *x-Treiber,* die ODBC 2 unterstützen müssen. *x-Anwendungen.* Weitere Informationen zur Abwärtskompatibilität finden Sie unter [Abwärtskompatibilität und Konformität von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Blockcursor, Scrollable Cursors und Backward Compatibility for ODBC 3.x Drivers](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) - Neue Features sind Features, die in ODBC 3 vorhanden sind. *x* und nicht in ODBC 2. *x*. ODBC 3. *x-Treiber* müssen sich in der Regel keine Gedanken über die Abwärtskompatibilität mit neuen Funktionen machen, da ODBC 2. *x-Anwendungen* verwenden sie niemals. Die einzigen Ausnahmen hierfür sind Features im Zusammenhang mit **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**und **SQLExtendedFetch**; Weitere Informationen finden Sie weiter unten in diesem Anhang.  
  
-   [Mapping Veraltete Funktionen](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) - Duplizierte Features sind Features, die in ODBC 3 unterschiedlich implementiert sind. *x* und ODBC 2. *x*. ODBC 3. *x-Treiber* müssen sich keine Sorgen um die Abwärtskompatibilität mit duplizierten Features machen, da der Treiber-Manager ODBC 2 immer zuordnet. *x-Funktionen* zu ODBC 3. *x-Funktionen* beim Aufrufen eines ODBC 3. *x-Treiber.* Somit ist ein ODBC 3. *x-Treiber* sieht nur ODBC 3. *x-Funktionen.* Weitere Informationen zu diesen Zuordnungen finden Sie weiter unten in diesem Anhang.  
  
-   [Verhaltensänderungen und ODBC 3.x-Treiber](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) - Verhaltensänderungen sind Features, die in ODBC 3 unterschiedlich behandelt werden. *x* und ODBC 2. *x*. ODBC 3. *x-Treiber* müssen sich um Verhaltensänderungen kümmern und als Reaktion auf das von der Anwendung festgelegte SQL_ATTR_ODBC_VERSION Umgebungsattribut handeln.
