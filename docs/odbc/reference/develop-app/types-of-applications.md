---
title: Arten von Anwendungen | Microsoft Docs
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
ms.openlocfilehash: f14326c9cec1eb89e431154c91b680e4688fcdfa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305531"
---
# <a name="types-of-applications"></a>Anwendungstypen
ODBC-Anwendungen können wie folgt klassifiziert werden:  
  
-   **Reine ODBC 2.**  
     ** _x_ Anwendung** Eine 32-Bit-Anwendung, die:  
  
    -   Ruft nur ODBC 2 auf. *x-Funktionen* (einschließlich der ODBC 1.0-Funktion **SQLSetParam**). Dazu gehört ODBC 1. *x-Anwendungen,* die auf 32-Bit portiert wurden.  
  
    -   Erwartet ODBC 2. *x-Verhalten* für Features, die Verhaltensänderungen hatten. (Weitere Informationen finden Sie unter [Verhaltensänderungen.)](../../../odbc/reference/develop-app/behavioral-changes.md)  
  
    -   Wurde nicht mit ODBC 3.5-Headern neu kompiliert.  
  
-   **Reine ODBC 2.**  
     **_x_ Recompiled Application** A pure ODBC 2. *x-Anwendung,* die mit den ODBC 3.5-Headerdateien neu kompiliert wurde, indem ODBCVER=0x0250 gesetzt wird.  
  
-   **Reine ODBC 2.**  
     **_x_ Unicode-Anwendung** Eine reine ODBC 2. *x* neu kompilierte Anwendung, die Unicode-kompatibel ist und den SQL_WCHAR Datentyp verwendet.  
  
-   **Pure Open Group und**-**ISO-konforme ODBC-Anwendung** Eine 32-Bit-Anwendung, die:  
  
    -   Ruft Funktionen auf, die in den Open Group- oder ISO CLI-Standards definiert sind. (Diese Funktionen können veraltete 3.0-Funktionen enthalten.)  
  
    -   Verwendet die Unicode-Datentypen nicht.  
  
    -   Erwartet ODBC 3.0-Verhalten für Features, die Verhaltensänderungen hatten.  
  
-   **Pure ODBC 3.0 Anwendung** Eine 32-Bit-Anwendung, die:  
  
    -   Wird mit 3.0-Headern kompiliert.  
  
    -   Ruft jede ODBC 3.0-Funktion auf, möglicherweise einschließlich der veralteten.  
  
    -   Erwartet ODBC 3.0-Verhalten für Features, die Verhaltensänderungen hatten.  
  
-   **Pure ODBC 3.5 Anwendung** Eine 32- oder 64-Bit-Anwendung, die:  
  
    -   Kann Unicode-Datentypen verwenden.  
  
    -   Ruft jede ODBC 3.5-Funktion auf, möglicherweise einschließlich der veralteten.  
  
    -   Erwartet ODBC 3.5-Verhalten für Features, die Verhaltensänderungen vorgenommen haben.  
  
-   **Reine ODBC 3.8 (oder höher) Anwendung** Eine 32-Bit- oder 64-Bit-Anwendung, die:  
  
    -   Kann Unicode-Datentypen verwenden.  
  
    -   Ruft jede ODBC 3.8-Funktion auf, möglicherweise einschließlich der veralteten.  
  
    -   Erwartet ODBC 3.8-Verhalten für Features, die Verhaltensänderungen vorgenommen haben.  
  
-   **Ersetzte Anwendung** Eine 32- oder 64-Bit-Anwendung, die:  
  
    -   Implementiert neues Verhalten für duplizierte Funktionen.  
  
    -   Verwendet alle neuen Features in einer späteren Version von ODBC nur innerhalb bedingten Codes.  
  
    -   Hat bedingten Code, um Verhaltensänderungen zu behandeln, oder hat sich selbst als eine frühere Version der ODBC-Anwendung registriert.
