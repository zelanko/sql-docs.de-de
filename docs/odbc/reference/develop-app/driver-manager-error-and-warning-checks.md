---
title: Fehler des Treiber-Managers und Überprüfungen der Warnung | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e00b6907d58cda1708cf61907d3c5ff6bf56edfa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47848978"
---
# <a name="driver-manager-error-and-warning-checks"></a>Fehler des Treiber-Managers und Überprüfungen der Warnung
Der Treiber-Manager vollständig oder teilweise implementiert eine Reihe von Funktionen und daher alle oder einige der Fehler und Warnungen in diesen Funktionen überprüft.  
  
-   Der Treiber-Manager implementiert **SQLDataSources** und **SQLDrivers** und überprüft es auf alle Fehler und Warnungen in diesen Funktionen.  
  
-   Der Treiber-Manager überprüft, ob ein Treiber implementiert **SQLGetFunctions**. Wenn der Treiber nicht implementiert **SQLGetFunctions**, des Treiber-Managers implementiert und überprüft, ob alle Fehler und Warnungen in es.  
  
-   Der Treiber-Manager teilweise implementiert **SQLAllocHandle**, **SQLConnect**, **SQLDriverConnect**, **SQLBrowseConnect**,  **SQLFreeHandle**, **SQLGetDiagRec**, und **SQLGetDiagField** und sucht nach einigen Fehlern in diesen Funktionen. Es kann die gleichen Fehler, da der Treiber für einige dieser Funktionen zurückgeben, da beide ähnliche Vorgänge ausführen. Z. B. der Treiber-Manager oder der Treiber möglicherweise zurück SQLSTATE IM008 (Dialogfehler) Wenn er kein Anmeldedialogfeld angezeigt **SQLDriverConnect**.
