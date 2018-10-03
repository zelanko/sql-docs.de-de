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
ms.openlocfilehash: 0f619c519bd5ec6a3ebb3567fc39e73d63e8b68f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47619688"
---
# <a name="types-of-drivers"></a>Treibertypen
ODBC-Treiber können wie folgt klassifiziert werden:  
  
-   **32-Bit-ODBC-2.**  
     ***X* Treiber** ein 32-Bit-Treiber, die:  
  
    -   Exportiert nur die ODBC 2.*.x* Funktionen.  
  
    -   Zeigt die ODBC-2. *x* Verhalten bei Änderungen am Verhalten.  
  
-   **ISO- und Open Group-kompatiblen Treiber** ein 32-Bit-Treiber, die:  
  
    -   Exportiert alle Funktionen, die in den Dokumenten, Open Group oder ISO-CLI dokumentiert sind. Dazu gehören einige der Funktionen, die veraltet sind in ODBC.  
  
    -   Ist das Verhalten der ODBC 3.0 verhaltensänderungen.  
  
    -   Wird nicht unbedingt über den ODBC-3.0-Treiber-Manager übertragen.  
  
-   **ODBC 3.0-Treibers** ein 32-Bit-Treiber, die:  
  
    -   Exportiert nur Funktionen, die in ODBC 3.0 minus sind veraltete Funktionen.  
  
    -   Mit der ODBC 2. kann. *x* Verhalten oder die ODBC 3.0-Verhalten in Bezug auf Änderungen am Systemverhalten auf Grundlage des SQL_ATTR_APP_ODBC_VERSION umgebungsattributs.  
  
-   **ODBC-Treiber mit dem ANSI 3.5 (oder höher)** ein 32-Bit-Treiber, die:  
  
    -   Exportiert nur Funktionen, die in ODBC 3.5 minus sind veraltete Funktionen.  
  
    -   Mit der ODBC 2. kann. *x* Verhalten oder ODBC 3.0 Verhalten oder ODBC 3.5-Verhalten in Bezug auf Änderungen am Systemverhalten auf umgebungsattributs SQL_ATTR_APP_ODBC_VERSION basiert.  
  
-   **ODBC-Treiber mit dem Unicode-Version 3.5 (oder höher)** ein 32-Bit-Treiber, die:  
  
    -   Unterstützt alle Funktionen von einem ODBC 3.5-ANSI-Treiber.  
  
    -   Exportiert alle ODBC-APIs-Zeichenfolge Unicode-Versionen.  
  
    -   Speichern und Verarbeiten von Unicode-Daten in der Datenquelle.  
  
> [!NOTE]  
>  16-Bit-ODBC-Treiber funktioniert nicht direkt mit der ODBC-3. *x* -Treiber-Manager. Allerdings ist es möglich, für die 16-Bit-Treiber, arbeiten mit der 2.0-ODBC-Treiber-Manager, die anschließend bis zu 3 Thunks. *x* -Treiber-Manager.
