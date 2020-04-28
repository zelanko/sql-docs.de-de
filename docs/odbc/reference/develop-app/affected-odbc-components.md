---
title: Betroffene ODBC-Komponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- upgrading applications [ODBC], affected components
- application upgrades [ODBC], affected components
- compatibility [ODBC], affected components
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], affected components
ms.assetid: 71fa6ea4-007c-4c2b-b5af-2cec6ea79b58
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8d9155fa1c9df5846f069e93a3db1b969e9219ed
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306474"
---
# <a name="affected-odbc-components"></a>Betroffene ODBC-Komponenten
Abwärtskompatibilität beschreibt, wie Anwendungen, Treiber-Manager und Treiber durch die Einführung einer neuen Version des Treiber-Managers beeinflusst werden. Dies wirkt sich auf Anwendungen und Treiber aus, wenn eine oder beide in der alten Version verbleiben. Daher sind drei Arten von Abwärtskompatibilität zu beachten, wie in der folgenden Tabelle dargestellt.  
  
|Typ|DM-Version|Version der Anwendung|Treiber Version|  
|----------|-------------------|----------------------------|-----------------------|  
|Abwärtskompatibilität des Treiber-Managers|*3.x*|*2.x*|*2.x*|  
|Abwärtskompatibilität des Treibers [1]|*3.x*|*2.x*|*3.x*|  
|Abwärtskompatibilität der Anwendung|*3.x*|*3.x*|*2.x*|  
  
 [1] die Abwärtskompatibilität von Treibern wird in erster Linie in Anhang G: Treiber Richtlinien für die Abwärtskompatibilität erläutert.  
  
> [!NOTE]
>  Eine mit Standards kompatible Anwendung, z. b. eine Anwendung, die in Übereinstimmung mit den Standards Open Group oder ISO CLI geschrieben wurde, funktioniert mit einem ODBC *3. x* -Treiber über den ODBC *3. x* -Treiber-Manager. Es wird davon ausgegangen, dass die von der Anwendung verwendete Funktionalität im Treiber verfügbar ist. Außerdem wird davon ausgegangen, dass die standardkonforme Anwendung mit den ODBC *3. x* -Header Dateien kompiliert wurde.
