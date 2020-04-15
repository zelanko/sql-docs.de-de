---
title: Arten von Treibern | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
ms.assetid: 864c53c1-b68a-48b6-b6bc-5ecb520bb9dc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: de6d8e1473f127d28c69969e0fc298afd69d3023
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304871"
---
# <a name="types-of-drivers"></a>Treibertypen
ODBC-Treiber können wie folgt klassifiziert werden:  
  
-   **32-Bit ODBC 2.**  
     ** _x_ Treiber** Ein 32-Bit-Treiber, der:  
  
    -   Exportiert nur ODBC *2.x-Funktionen.*  
  
    -   Zeigt ODBC *2.x-Verhalten* für Verhaltensänderungen an.  
  
-   **ISO- und Open Group-Compliant Driver** Ein 32-Bit-Treiber, der:  
  
    -   Exportiert alle Funktionen, die in den Dokumenten "Offene Gruppe" oder "ISO CLI" dokumentiert sind. Dies schließt einige Funktionen ein, die in ODBC veraltet sind.  
  
    -   Zeigt ODBC 3.0-Verhalten für Verhaltensänderungen an.  
  
    -   Geht nicht unbedingt durch den ODBC 3.0-Treiber-Manager.  
  
-   **ODBC 3.0 Treiber** Ein 32-Bit-Treiber, der:  
  
    -   Exportiert nur Funktionen, die in ODBC 3.0 minus veraltete Funktionen sind.  
  
    -   Ist in der Lage, ODBC *2.x-Verhalten* oder ODBC 3.0-Verhalten in Bezug auf Verhaltensänderungen basierend auf dem SQL_ATTR_APP_ODBC_VERSION Umgebungsattribut auszustellen.  
  
-   **ODBC 3.5 (oder höher) ANSI-Treiber** Ein 32-Bit-Treiber, der:  
  
    -   Exportiert nur Funktionen, die in ODBC 3.5 minus veralteten Funktionen sind.  
  
    -   Ist in der Lage, ODBC *2.x-Verhalten* oder ODBC 3.0-Verhalten oder ODBC 3.5-Verhalten in Bezug auf Verhaltensänderungen basierend auf dem SQL_ATTR_APP_ODBC_VERSION Umgebungsattribut auszustellen.  
  
-   **ODBC 3.5 (oder höher) Unicode-Treiber** Ein 32-Bit-Treiber, der:  
  
    -   Unterstützt alle Funktionen eines ODBC 3.5 ANSI Treibers.  
  
    -   Exportiert Unicode-Versionen aller ODBC-Zeichenfolgen-APIs.  
  
    -   Kann Unicode-Daten in der Datenquelle speichern und verarbeiten.  
  
> [!NOTE]  
>  16-Bit-ODBC-Treiber funktionieren nicht direkt mit dem ODBC *3.x* Driver Manager. Es ist jedoch möglich, dass 16-Bit-Treiber mit dem 2.0 ODBC Driver Manager arbeiten, der anschließend bis zum *3.x* Driver Manager abläuft.
