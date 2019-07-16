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
ms.openlocfilehash: 08997f610b00f22d436a5c91d34beb2a8fc2cc1d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67944853"
---
# <a name="affected-odbc-components"></a>Betroffene ODBC-Komponenten
Abwärtskompatibilität wird beschrieben, wie Anwendungen, Treiber-Manager und Treiber durch die Einführung einer neuen Version des Treiber-Managers betroffen sind. Dies wirkt sich auf Anwendungen und Treiber, wenn eine oder beide Angaben in der alten Version bleiben. Es gibt daher drei Arten von Abwärtskompatibilität berücksichtigt werden, wie in der folgenden Tabelle gezeigt.  
  
|Typ|DM-Version|Version der Anwendung|Version des Treibers|  
|----------|-------------------|----------------------------|-----------------------|  
|Abwärtskompatibilität des Treiber-Managers|*3.x*|*2.x*|*2.x*|  
|Abwärtskompatibilität von Treiber [1]|*3.x*|*2.x*|*3.x*|  
|Abwärtskompatibilität der Anwendung|*3.x*|*3.x*|*2.x*|  
  
 [1] die Abwärtskompatibilität der Treiber wird in erster Linie in Anhang G: erläutert. Treiber-Richtlinien für die Abwärtskompatibilität zu gewährleisten.  
  
> [!NOTE]
>  Eine Standards kompatible Anwendung – z. B. eine Anwendung, die gemäß den Standards Open Group oder ISO-CLI - geschrieben wurde mit einer ODBC-funktioniert Sicherheit *3.x* Treiber über die ODBC *3.x*-Treiber-Manager. Es wird vorausgesetzt, dass die Funktionalität, die die Anwendung im Treiber verfügbar ist. Außerdem wird vorausgesetzt, dass es sich bei der Kompilierung der Standards kompatible Anwendung mit der ODBC *3.x* Headerdateien.
