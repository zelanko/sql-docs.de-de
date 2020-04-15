---
title: Treiber-Manager-Fehler- und Warnungsprüfungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- driver manager [ODBC], error checking
ms.assetid: eeb5ab3f-987d-4f30-87d2-7425a81ad1d7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ee8a0f5ebfac8b6f87281806f07989f4980eb9b9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305782"
---
# <a name="driver-manager-error-and-warning-checks"></a>Fehler des Treiber-Managers und Überprüfungen der Warnung
Der Treiber-Manager implementiert eine Reihe von Funktionen ganz oder teilweise und überprüft daher alle oder einige Fehler und Warnungen in diesen Funktionen.  
  
-   Der Treiber-Manager implementiert **SQLDataSources** und **SQLDrivers** und sucht nach allen Fehlern und Warnungen in diesen Funktionen.  
  
-   Der Treiber-Manager prüft, ob ein Treiber **SQLGetFunctions**implementiert. Wenn der Treiber **SQLGetFunctions**nicht implementiert, implementiert und überprüft der Treiber-Manager alle darin enthaltenen Fehler und Warnungen.  
  
-   Der Treiber-Manager implementiert teilweise **SQLAllocHandle**, **SQLConnect**, **SQLDriverConnect**, **SQLBrowseConnect**, **SQLFreeHandle**, **SQLGetDiagRec**und **SQLGetDiagField** und sucht nach einigen Fehlern in diesen Funktionen. Es kann die gleichen Fehler wie der Treiber für einige dieser Funktionen zurückgeben, da beide ähnliche Vorgänge ausführen. Beispielsweise kann der Treiber-Manager oder -Treiber SQLSTATE IM008 (Dialog fehlgeschlagen) zurückgeben, wenn einer der beiden Nichtanzeigen eines Anmeldedialogfelds für **SQLDriverConnect**nicht anzeigen kann.
