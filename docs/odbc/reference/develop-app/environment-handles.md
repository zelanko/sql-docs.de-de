---
title: Umgebungshandles | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a73ec4a842e220a16189f1390df167fe12bbab8a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62942993"
---
# <a name="environment-handles"></a>Umgebungshandles
Ein *Umgebung* wird von ein globaler Kontext, in denen auf Daten zugreifen, eine Umgebung zugeordnet ist, alle Informationen, die globaler Natur, z. B. ist:  
  
-   Status von der Umgebung  
  
-   Die aktuelle auf Umgebungsebene-Diagnose  
  
-   Die Ziehpunkte der Verbindungen, die derzeit in der Umgebung zugeordnet.  
  
-   Die aktuellen Einstellungen der einzelnen Attribute für die Umgebung  
  
 Innerhalb eines Codeabschnitts, die ODBC (des Treiber-Managers oder eines Treibers) implementiert, gibt ein Umgebungshandle eine Struktur, um diese Informationen enthalten.  
  
 Umgebungshandles werden in ODBC-Anwendungen nicht häufig verwendet werden. Sie werden immer verwendet, in Aufrufen von **SQLDataSources** und **SQLDrivers** und manchmal verwendet, in Aufrufen von **SQLAllocHandle**, **SQLEndTran**, **SQLFreeHandle**, **SQLGetDiagField**, und **SQLGetDiagRec**.  
  
 Jedes Datenelement Code zum Implementieren von ODBC (des Treiber-Managers oder eines Treibers) enthält eine oder mehrere Umgebungshandles. Der Treiber-Manager führt beispielsweise einen separate Umgebung-Handle für jede Anwendung, die mit ihm verbunden ist. Umgebungshandles zugeordnet sind **SQLAllocHandle** und mit freigegebenen **SQLFreeHandle**.
