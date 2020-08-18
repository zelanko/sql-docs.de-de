---
description: Fehler des Treiber-Managers und Überprüfungen der Warnung
title: Fehler-und Warnungs Überprüfungen für Treiber-Manager | Microsoft-Dokumentation
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
ms.openlocfilehash: 99a99e1dfeb6cb6993a6967d5d93748afbd44b83
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483053"
---
# <a name="driver-manager-error-and-warning-checks"></a>Fehler des Treiber-Managers und Überprüfungen der Warnung
Der Treiber-Manager implementiert eine Reihe von Funktionen vollständig oder teilweise und überprüft daher alle oder einige der Fehler und Warnungen in diesen Funktionen.  
  
-   Der Treiber-Manager implementiert **SQLDataSources** und **SQLDrivers** und überprüft alle Fehler und Warnungen in diesen Funktionen.  
  
-   Der Treiber-Manager überprüft, ob ein Treiber **SQLGetFunctions**implementiert. Wenn der Treiber **SQLGetFunctions**nicht implementiert, implementiert der Treiber-Manager und überprüft alle Fehler und Warnungen darin.  
  
-   Der Treiber-Manager implementiert **sqlfreichandle**, **SQLCONNECT**, **SQLDriverConnect**, **sqlbrowseconnetct**, **SQLFreeHandle**, **SQLGetDiagRec**und **SQLGetDiagField** teilweise und prüft einige Fehler in diesen Funktionen. Sie gibt möglicherweise dieselben Fehler wie der Treiber für einige dieser Funktionen zurück, da beide ähnliche Vorgänge ausführen. Beispielsweise kann der Treiber-Manager oder Treiber SQLSTATE IM008 (Dialog Feld Fehler) zurückgeben, wenn eine der Anmelde Informationen für **SQLDriverConnect**nicht angezeigt werden kann.
