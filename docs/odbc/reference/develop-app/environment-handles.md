---
description: Umgebungshandles
title: Umgebungs Handles | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1aa22a89288f4dd5a8400484078f57b60fc135fb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461502"
---
# <a name="environment-handles"></a>Umgebungshandles
Eine *Umgebung* ist ein globaler Kontext, in dem auf Daten zugegriffen werden kann. mit einer Umgebung verknüpft sind alle Informationen, die Global sind, wie z. b.:  
  
-   Der Zustand der Umgebung  
  
-   Die aktuelle Diagnose auf Umgebungs Ebene  
  
-   Die Handles der derzeit in der Umgebung zugewiesenen Verbindungen  
  
-   Die aktuellen Einstellungen der einzelnen Umgebungs Attribute  
  
 Innerhalb eines Code Abschnitts, der ODBC (Treiber-Manager oder Treiber) implementiert, identifiziert ein Umgebungs Handle eine-Struktur, die diese Informationen enthält.  
  
 Umgebungs Handles werden in ODBC-Anwendungen nicht häufig verwendet. Sie werden immer in Aufrufen von **SQLDataSources** und **SQLDrivers** verwendet und manchmal in Aufrufen von **sqlfreichandle**, **SQLEndTran**, **SQLFreeHandle**, **SQLGetDiagField**und **SQLGetDiagRec**verwendet.  
  
 Jedes Code Element, das ODBC implementiert (Treiber-Manager oder Treiber) enthält mindestens ein Umgebungs Handle. Der Treiber-Manager verwaltet z. b. ein separates Umgebungs Handle für jede Anwendung, die mit ihm verbunden ist. Umgebungs Handles werden mit **sqlzuordchandle** zugeordnet und mit **SQLFreeHandle**freigegeben.
