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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72e004e6fd41ee74643fc05ec9020e6ac1933e09
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63186256"
---
# <a name="affected-odbc-components"></a>Betroffene ODBC-Komponenten
Abwärtskompatibilität wird beschrieben, wie Anwendungen, Treiber-Manager und Treiber durch die Einführung einer neuen Version des Treiber-Managers betroffen sind. Dies wirkt sich auf Anwendungen und Treiber, wenn eine oder beide Angaben in der alten Version bleiben. Es gibt daher drei Arten von Abwärtskompatibilität berücksichtigt werden, wie in der folgenden Tabelle gezeigt.  
  
|Typ|DM-Version|Version der Anwendung|Version des Treibers|  
|----------|-------------------|----------------------------|-----------------------|  
|Abwärtskompatibilität des Treiber-Managers|3 *.x*|2.*x*|2.*x*|  
|Abwärtskompatibilität von Treiber [1]|3 *.x*|2.*x*|3.*x*|  
|Abwärtskompatibilität der Anwendung|3.*x*|3.*x*|2.*x*|  
  
 [1] die Abwärtskompatibilität der Treiber wird in erster Linie in Anhang G: erläutert. Treiber-Richtlinien für die Abwärtskompatibilität zu gewährleisten.  
  
> [!NOTE]
>  Eine Standards kompatible Anwendung – z. B. eine Anwendung, die gemäß den Standards Open Group oder ISO-CLI - geschrieben wurde ist garantiert zum Arbeiten mit einer ODBC-3 *.x* Treiber über die ODBC 3.*.x*-Treiber-Manager. Es wird vorausgesetzt, dass die Funktionalität, die die Anwendung im Treiber verfügbar ist. Außerdem wird vorausgesetzt, dass die ODBC 3. die Standards kompatible Anwendung kompiliert wurde *.x* Headerdateien.
