---
description: Anwendungstypen
title: Anwendungs Typen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- upgrading applications [ODBC], application types
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application upgrades [ODBC], application types
- application compatibility issues [ODBC]
ms.assetid: d346a64e-a32c-4153-a40f-5b53c2f57ef2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 54056a6111924fb584ac35a65d6f74e8dab1ba6c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465550"
---
# <a name="types-of-applications"></a>Anwendungstypen
ODBC-Anwendungen können wie folgt klassifiziert werden:  
  
-   **Reines ODBC 2.**  
     ** _x_ -Anwendung** : eine 32-Bit-Anwendung, die Folgendes:  
  
    -   Ruft nur ODBC 2 auf. *x* -Funktionen (einschließlich der ODBC 1,0-Funktion **SQLSetParam**). Dies schließt ODBC 1 ein. *x* -Anwendungen, die in 32-Bit portiert wurden.  
  
    -   Erwartet ODBC 2. *x* -Verhalten für Funktionen, die über Verhaltensänderungen verfügen. (Weitere Informationen finden Sie unter [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md) .)  
  
    -   Wurde nicht mit ODBC 3,5-Headern neu kompiliert.  
  
-   **Reines ODBC 2.**  
     **_x_ rekompilierte Anwendung** ein reines ODBC 2. *x* -Anwendung, die mithilfe der ODBC 3,5-Header Dateien neu kompiliert wurde, durch Festlegen von ODBCVer = 0x0250.  
  
-   **Reines ODBC 2.**  
     **_x_ Unicode-Anwendung** ein reines ODBC 2. *neu* kompilierte Anwendung, die Unicode-kompatibel ist und den SQL_WCHAR-Datentyp verwendet.  
  
-   **Reine offene Gruppe und ISO** - **kompatible ODBC-Anwendung** Eine 32-Bit-Anwendung, die Folgendes hat:  
  
    -   Ruft Funktionen auf, die in den Standards Open Group oder ISO CLI definiert sind. (Diese Funktionen können als veraltet markierte 3,0-Funktionen enthalten.)  
  
    -   Die Unicode-Datentypen werden von nicht verwendet.  
  
    -   Erwartet das ODBC 3,0-Verhalten für Funktionen, die über Verhaltensänderungen verfügen.  
  
-   **Reine ODBC 3,0-Anwendung** Eine 32-Bit-Anwendung, die Folgendes hat:  
  
    -   Wird mit 3,0-Headern kompiliert.  
  
    -   Ruft jede ODBC 3,0-Funktion auf, einschließlich derjenigen, die veraltet sind.  
  
    -   Erwartet das ODBC 3,0-Verhalten für Funktionen, die über Verhaltensänderungen verfügen.  
  
-   **Reine ODBC 3,5-Anwendung** Eine 32-oder 64-Bit-Anwendung, die Folgendes hat:  
  
    -   Kann Unicode-Datentypen verwenden.  
  
    -   Ruft jede ODBC 3,5-Funktion auf, einschließlich derjenigen, die veraltet sind.  
  
    -   Erwartet das ODBC 3,5-Verhalten für Funktionen, die über Verhaltensänderungen verfügen.  
  
-   **Reine ODBC 3,8-Anwendung (oder höher)** Eine 32-Bit-oder 64-Bit-Anwendung, die Folgendes hat:  
  
    -   Kann Unicode-Datentypen verwenden.  
  
    -   Ruft jede ODBC 3,8-Funktion auf, einschließlich derjenigen, die veraltet sind.  
  
    -   Erwartet das ODBC 3,8-Verhalten für Funktionen, die über Verhaltensänderungen verfügen.  
  
-   **Ersetzte Anwendung** Eine 32-oder 64-Bit-Anwendung, die Folgendes hat:  
  
    -   Implementiert neues Verhalten für duplizierte Funktionen.  
  
    -   Verwendet alle neuen Features in einer neueren Version von ODBC nur innerhalb von bedingtem Code.  
  
    -   Weist eingeschränkten bedingten Code auf, um Verhaltensänderungen zu behandeln, oder hat sich als frühere Version der ODBC-Anwendung registriert.
