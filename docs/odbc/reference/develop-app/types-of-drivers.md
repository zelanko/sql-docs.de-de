---
title: Treiber Typen | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304871"
---
# <a name="types-of-drivers"></a>Treibertypen
ODBC-Treiber können wie folgt klassifiziert werden:  
  
-   **32-Bit-ODBC 2.**  
     ** _x_ -Treiber** ein 32-Bit-Treiber für Folgendes:  
  
    -   Exportiert nur ODBC *2. x* -Funktionen.  
  
    -   Stellt das ODBC *2. x* -Verhalten für Verhaltensänderungen dar.  
  
-   **ISO und offener Gruppen kompatibler Treiber** Ein 32-Bit-Treiber, der Folgendes hat:  
  
    -   Exportiert alle Funktionen, die in den Dokumenten Open Group oder ISO CLI dokumentiert sind. Dies umfasst einige Funktionen, die in ODBC als veraltet eingestuft werden.  
  
    -   Stellt das ODBC 3,0-Verhalten für Verhaltensänderungen dar.  
  
    -   Der ODBC 3,0-Treiber-Manager wird nicht notwendigerweise durchlaufen.  
  
-   **ODBC 3,0-Treiber** Ein 32-Bit-Treiber, der Folgendes hat:  
  
    -   Exportiert nur Funktionen, die in ODBC 3,0 minus veralteten Funktionen sind.  
  
    -   Ist in der Lage, das ODBC *2. x* -Verhalten oder das ODBC 3,0-Verhalten in Bezug auf Verhaltensänderungen auf der Grundlage des SQL_ATTR_APP_ODBC_VERSION Environment-Attributs auszustellen.  
  
-   **ODBC 3,5 (oder höher) ANSI-Treiber** Ein 32-Bit-Treiber, der Folgendes hat:  
  
    -   Exportiert nur Funktionen, die in ODBC 3,5 minus veralteten Funktionen sind.  
  
    -   Ist in der Lage, das ODBC *2. x* -Verhalten oder das ODBC 3,0-Verhalten oder das ODBC 3,5-Verhalten in Bezug auf Verhaltensänderungen basierend auf dem SQL_ATTR_APP_ODBC_VERSION-Umgebungs Attribut auszustellen.  
  
-   **ODBC 3,5 (oder höher) Unicode-Treiber** Ein 32-Bit-Treiber, der Folgendes hat:  
  
    -   Unterstützt alle Features eines ODBC 3,5-ANSI-Treibers.  
  
    -   Exportiert Unicode-Versionen aller ODBC-Zeichen folgen-APIs.  
  
    -   Kann Unicode-Daten in der Datenquelle speichern und verarbeiten.  
  
> [!NOTE]  
>  16-Bit-ODBC-Treiber können nicht direkt mit dem ODBC *3. x* -Treiber-Manager verwendet werden. Es ist jedoch möglich, dass 16-Bit-Treiber mit dem 2,0-ODBC-Treiber-Manager verwendet werden, der anschließend mit dem *3. x* -Treiber-Manager zusammen läuft.
