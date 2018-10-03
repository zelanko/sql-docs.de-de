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
manager: craigg
ms.openlocfilehash: 2e3996aafa0e4f5b389e4f46d5df3b22632daad9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47710038"
---
# <a name="drivers"></a>Treiber
*Treiber* sind Bibliotheken, die die Funktionen der ODBC-API zu implementieren. Jeder kann nur für ein bestimmtes DBMS. Beispielsweise kann nicht in ein Treiber für Oracle Daten in eine Informix DBMS direkt zugreifen. Treiber verfügbar machen, die Funktionen von der zugrunde liegenden DBMS. Sie sind nicht erforderlich, zum Implementieren von Funktionen, die nicht vom DBMS unterstützt. Sollten Sie den Treiber z. B. wenn das zugrunde liegende DBMS äußere Joins, und klicken Sie dann keine nicht unterstützt. Die einzige große Ausnahme hierbei ist, dass die Treiber für DBMS-Systeme, denen keine eigenständige Datenbank-Engines wie Xbase, eine Datenbank-Engine implementieren müssen, die mindestens eine minimale Menge von SQL unterstützt.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Treiber-Aufgaben](../../odbc/reference/driver-tasks.md)  
  
-   [Treiberarchitektur](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Von Microsoft gelieferte ODBC-Treiber](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
