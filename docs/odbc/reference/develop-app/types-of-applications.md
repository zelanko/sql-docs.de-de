---
title: Anwendungstypen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d835e7d541f69c6a84129d3d6c1c8128f748a23
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52541906"
---
# <a name="types-of-applications"></a>Anwendungstypen
ODBC-Anwendungen können wie folgt klassifiziert werden:  
  
-   **Reine ODBC 2.**  
     ***X* Anwendung** ein 32-Bit-Anwendung, die:  
  
    -   Ruft nur ODBC 2. *x* Funktionen (einschließlich der ODBC-1.0-Funktion **SQLSetParam**). Dazu gehören die ODBC-1. *x* Anwendungen, die auf 32 Bits portiert haben.  
  
    -   Erwartet, dass ODBC 2. *x* -Verhalten für Funktionen, die Änderungen am Verhalten aufweisen. (Finden Sie unter [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md) für Weitere Informationen.)  
  
    -   Nicht mit ODBC 3.5-Headern neu kompiliert wurde.  
  
-   **Reine ODBC 2.**  
     ***X* Anwendung neu kompiliert** eine reine ODBC 2. *X* -Anwendung, die neu kompiliert wurde mithilfe der ODBC 3.5-Header-Dateien, durch Festlegen von ODBCVER = 0x0250.  
  
-   **Reine ODBC 2.**  
     ***X* Unicode-Anwendung** eine reine ODBC 2. *X* neu kompiliert die Anwendung, die Unicode-kompatibel ist und verwendet den SQL_WCHAR-Datentyp.  
  
-   **Reine Open Group und ISO**-**kompatible ODBC-Anwendung** ein 32-Bit-Anwendung, die:  
  
    -   Ruft die Funktionen, die in den Open Group oder ISO-CLI-Standards definiert. (Diese Funktionen möglicherweise veraltete 3.0-Funktionen enthalten.)  
  
    -   Verwendet nicht die Unicode-Datentypen.  
  
    -   Erwartet, dass ODBC 3.0-Verhalten für Funktionen, die Änderungen am Verhalten aufweisen.  
  
-   **Reine ODBC 3.0-Anwendung** ein 32-Bit-Anwendung, die:  
  
    -   Mit 3.0-Header wird kompiliert werden.  
  
    -   Ruft alle ODBC 3.0-Funktion, die möglicherweise auch solche, die als veraltet markiert werden.  
  
    -   Erwartet, dass ODBC 3.0-Verhalten für Funktionen, die Änderungen am Verhalten aufweisen.  
  
-   **Reine ODBC 3.5-Anwendung** ein 32 oder 64-Bit-Anwendung, die:  
  
    -   Sie können Unicode-Datentypen.  
  
    -   Ruft beliebige ODBC 3.5-Funktionen, die möglicherweise auch solche, die als veraltet markiert werden.  
  
    -   Erwartet, dass ODBC 3.5-Verhalten für Funktionen, die Änderungen am Verhalten aufweisen.  
  
-   **Reine ODBC 3.8 (oder höher)-Anwendung** ein 32-Bit oder 64-Bit-Anwendung, die:  
  
    -   Sie können Unicode-Datentypen.  
  
    -   Ruft beliebige ODBC 3.8-Funktionen, die möglicherweise auch solche, die als veraltet markiert werden.  
  
    -   Erwartet, dass ODBC 3.8-Verhalten für Funktionen, die Änderungen am Verhalten aufweisen.  
  
-   **Ersetzt die Anwendung** ein 32 oder 64-Bit-Anwendung, die:  
  
    -   Implementiert die neue Verhalten für die duplizierte Funktionalität.  
  
    -   Verwendet keine neuen Features in einer späteren Version von ODBC nur innerhalb der bedingten Code.  
  
    -   Bietet eine eingeschränkte bedingten Code zum Verarbeiten von Änderungen am Verhalten, oder sich werden von einer früheren Version von ODBC-Anwendung registriert hat.
