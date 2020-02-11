---
title: Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6460410488186c94713d859bf2912f2844ca2736
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915429"
---
# <a name="drivers"></a>Treiber
*Treiber* sind Bibliotheken, die die Funktionen in der ODBC-API implementieren. Jede ist für ein bestimmtes DBMS spezifisch. Beispielsweise kann ein Treiber für Oracle nicht direkt auf Daten in einem Informix-DBMS zugreifen. Treiber machen die Funktionen der zugrunde liegenden DBMSs verfügbar. Sie sind nicht erforderlich, um Funktionen zu implementieren, die nicht vom DBMS unterstützt werden. Wenn das zugrunde liegende DBMS beispielsweise keine äußeren Joins unterstützt, sollte keiner der Treiber verwendet werden. Die einzige wesentliche Ausnahme besteht darin, dass Treiber für DBMSs, die keine eigenständigen Datenbank-Engines wie xbase aufweisen, eine Datenbank-Engine implementieren müssen, die zumindest eine minimale Menge an SQL unterstützt.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Treiberaufgaben](../../odbc/reference/driver-tasks.md)  
  
-   [Treiberarchitektur](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von Microsoft bereitgestellte ODBC-Treiber](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
