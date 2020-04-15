---
title: Umgebungsgriffe | Microsoft Docs
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
ms.openlocfilehash: b504995e99dfad032598485e370b4d5a6681ae81
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300440"
---
# <a name="environment-handles"></a>Umgebungshandles
Eine *Umgebung* ist ein globaler Kontext, in dem auf Daten zugreift. Einer Umgebung zugeordnet sind alle Informationen, die globaler Natur sind, z. B.:  
  
-   Der Zustand der Umwelt  
  
-   Die aktuelle Diagnose auf Umgebungsebene  
  
-   Die Handles von Verbindungen, die derzeit der Umgebung zugewiesen sind  
  
-   Die aktuellen Einstellungen der einzelnen Umgebungsattribute  
  
 Innerhalb eines Codes, der ODBC implementiert (treiber-Manager oder Treiber), identifiziert ein Umgebungshandle eine Struktur, die diese Informationen enthält.  
  
 Umgebungshandles werden nicht häufig in ODBC-Anwendungen verwendet. Sie werden immer in Aufrufen von **SQLDataSources** und **SQLDrivers** und manchmal in Aufrufen von **SQLAllocHandle**, **SQLEndTran**, **SQLFreeHandle**, **SQLGetDiagField**und **SQLGetDiagRec**verwendet.  
  
 Jeder Code, der ODBC implementiert (treiber-Manager oder Treiber), enthält ein oder mehrere Umgebungshandles. Beispielsweise verwaltet der Treiber-Manager für jede Mitdiesem-Anwendung ein separates Umgebungshandle. Umgebungshandles werden mit **SQLAllocHandle** zugewiesen und mit **SQLFreeHandle**freigegeben.
