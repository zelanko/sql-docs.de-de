---
title: 'Anhang G: Treiber-Richtlinien für die Abwärtskompatibilität | Microsoft-Dokumentation'
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63f999fa01623898be6561c9f5a450c6ec81487d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654228"
---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>Anhang G: Treiberrichtlinien für Abwärtskompatibilität
Dieser Anhang enthält Informationen für Autoren von Treiber ODBC 3. an. *x* Treiber, die ODBC 2. unterstützt werden müssen. *X* Anwendungen. Weitere Informationen zur Abwärtskompatibilität finden Sie unter [Abwärtskompatibilität und zur Einhaltung von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Blockcursor, scrollbare Cursor und Abwärtskompatibilität für ODBC 3.x-Treiber](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) – neue Features sind Funktionen, die in ODBC 3. vorhanden sind. *X* und nicht in der ODBC-2. *X*. ODBC 3. *x* Treiber in der Regel keine Abwärtskompatibilität mit neuen Funktionen kümmern können, da ODBC 2. *X* Anwendungen verwenden nie diese. Die einzigen Ausnahmen hierfür sind Funktionen, die im Zusammenhang mit **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**, und **SQLExtendedFetch**; Weitere Informationen Informationen finden Sie unter weiter unten in diesem Anhang.  
  
-   [Zuordnen von Funktionen als veraltet markiert](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) – doppelte Funktionen sind Funktionen, die in ODBC 3. unterschiedlich implementiert sind. *X* und ODBC-2. *X*. ODBC 3. *x* Treiber keine Abwärtskompatibilität mit doppelte Funktionen kümmern, da der Treiber-Manager die ODBC 2. immer zugeordnet. *X* Funktionen ODBC 3. *X* Funktionen, wenn eine ODBC 3. aufrufen. *X* Treiber. Daher werden diese Informationen mit einer ODBC 3. *x* Treiber erkennt nur ODBC 3. *X* Funktionen. Weitere Informationen zu diesen Zuordnungen, finden Sie unter weiter unten in diesem Anhang.  
  
-   [Verhaltensänderungen und ODBC 3.x-Treiber](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) – verhaltensänderungen sind Funktionen, die in ODBC 3. anders behandelt werden. *X* und ODBC-2. *X*. ODBC 3. *x* Treiber zu kümmern, verhaltensänderungen und fungieren als Reaktion auf SQL_ATTR_ODBC_VERSION umgebungsattributs durch die Anwendung festgelegt haben.
