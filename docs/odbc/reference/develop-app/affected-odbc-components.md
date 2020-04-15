---
title: Betroffene ODBC-Komponenten | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306474"
---
# <a name="affected-odbc-components"></a>Betroffene ODBC-Komponenten
Die Abwärtskompatibilität beschreibt, wie Anwendungen, der Treiber-Manager und Treiber durch die Einführung einer neuen Version des Treiber-Managers beeinflusst werden. Dies wirkt sich auf Anwendungen und Treiber aus, wenn eine oder beide in der alten Version verbleiben. Es gibt daher drei Arten von Abwärtskompatibilität zu berücksichtigen, wie in der folgenden Tabelle dargestellt.  
  
|type|Version von DM|Version der Anwendung|Version des Treibers|  
|----------|-------------------|----------------------------|-----------------------|  
|Abwärtskompatibilität des Treiber-Managers|*3.x*|*2.x*|*2.x*|  
|Abwärtskompatibilität des Treibers[1]|*3.x*|*2.x*|*3.x*|  
|Abwärtskompatibilität der Anwendung|*3.x*|*3.x*|*2.x*|  
  
 [1] Die Abwärtskompatibilität von Treibern wird in erster Linie in Anhang G: Treiberrichtlinien für die Abwärtskompatibilität erläutert.  
  
> [!NOTE]
>  Eine normkonforme Anwendung - z. B. eine Anwendung, die gemäß den Open Group- oder ISO CLI-Standards geschrieben wurde - funktioniert garantiert mit einem ODBC *3.x-Treiber* über den ODBC *3.x* Driver Manager. Es wird davon ausgegangen, dass die von der Anwendung verwendende Funktionalität im Treiber verfügbar ist. Es wird auch davon ausgegangen, dass die standardkonforme Anwendung mit den ODBC *3.x-Headerdateien* kompiliert wurde.
