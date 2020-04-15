---
title: Treiber | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c8b40641be3db34fc6929edecdd5dd923700957
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294183"
---
# <a name="drivers"></a>Treiber
*Treiber* sind Bibliotheken, die die Funktionen in der ODBC-API implementieren. Jedes ist spezifisch für ein bestimmtes DBMS. Beispielsweise kann ein Treiber für Oracle nicht direkt auf Daten in einem Informix DBMS zugreifen. Treiber machen die Funktionen der zugrunde liegenden DBMS verfügbar. Sie sind nicht erforderlich, um Funktionen zu implementieren, die vom DBMS nicht unterstützt werden. Wenn z. B. das zugrunde liegende DBMS keine äußeren Verknüpfungen unterstützt, sollte der Treiber auch nicht. Die einzige wichtige Ausnahme besteht darin, dass Treiber für DBMS, die nicht über eigenständige Datenbankmodule verfügen, wie z. B. Xbase, ein Datenbankmodul implementieren müssen, das zumindest eine minimale Menge an SQL unterstützt.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Treiberaufgaben](../../odbc/reference/driver-tasks.md)  
  
-   [Treiberarchitektur](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von Microsoft gelieferte ODBC-Treiber](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
