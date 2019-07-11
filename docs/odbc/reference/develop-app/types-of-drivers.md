---
title: Typen von Treibern | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 08c1c9b4338502f20e5f99885d371d713971aa38
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792703"
---
# <a name="types-of-drivers"></a>Treibertypen
ODBC-Treiber können wie folgt klassifiziert werden:  
  
-   **32-Bit-ODBC-2.**  
     **_X_ Treiber** ein 32-Bit-Treiber, die:  
  
    -   Exportiert nur ODBC *2.x* Funktionen.  
  
    -   ODBC weist *2.x* Verhalten bei Änderungen am Verhalten.  
  
-   **ISO- und Open Group-kompatiblen Treiber** ein 32-Bit-Treiber, die:  
  
    -   Exportiert alle Funktionen, die in den Dokumenten, Open Group oder ISO-CLI dokumentiert sind. Dazu gehören einige der Funktionen, die veraltet sind in ODBC.  
  
    -   Ist das Verhalten der ODBC 3.0 verhaltensänderungen.  
  
    -   Wird nicht unbedingt über den ODBC-3.0-Treiber-Manager übertragen.  
  
-   **ODBC 3.0-Treibers** ein 32-Bit-Treiber, die:  
  
    -   Exportiert nur Funktionen, die in ODBC 3.0 minus sind veraltete Funktionen.  
  
    -   Kann mit ODBC *2.x* Verhalten oder die ODBC 3.0-Verhalten in Bezug auf Änderungen am Systemverhalten auf Grundlage des SQL_ATTR_APP_ODBC_VERSION umgebungsattributs.  
  
-   **ODBC-Treiber mit dem ANSI 3.5 (oder höher)** ein 32-Bit-Treiber, die:  
  
    -   Exportiert nur Funktionen, die in ODBC 3.5 minus sind veraltete Funktionen.  
  
    -   Kann mit ODBC *2.x* Verhalten oder ODBC 3.0 Verhalten oder ODBC 3.5-Verhalten in Bezug auf Änderungen am Systemverhalten auf umgebungsattributs SQL_ATTR_APP_ODBC_VERSION basiert.  
  
-   **ODBC-Treiber mit dem Unicode-Version 3.5 (oder höher)** ein 32-Bit-Treiber, die:  
  
    -   Unterstützt alle Funktionen von einem ODBC 3.5-ANSI-Treiber.  
  
    -   Exportiert alle ODBC-APIs-Zeichenfolge Unicode-Versionen.  
  
    -   Speichern und Verarbeiten von Unicode-Daten in der Datenquelle.  
  
> [!NOTE]  
>  16-Bit-ODBC-Treiber funktioniert nicht direkt mit der ODBC *3.x* -Treiber-Manager. Es ist jedoch möglich, dass 16-Bit-Treiber mit der 2.0-ODBC-Treiber-Manager arbeiten, die anschließend bis zu Thunks der *3.x* -Treiber-Manager.
