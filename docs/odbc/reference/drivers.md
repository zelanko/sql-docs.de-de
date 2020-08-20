---
description: Treiber
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 81e8989fc178728e687baa13b37e6055692d9413
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494593"
---
# <a name="drivers"></a>Treiber
*Treiber* sind Bibliotheken, die die Funktionen in der ODBC-API implementieren. Jede ist für ein bestimmtes DBMS spezifisch. Beispielsweise kann ein Treiber für Oracle nicht direkt auf Daten in einem Informix-DBMS zugreifen. Treiber machen die Funktionen der zugrunde liegenden DBMSs verfügbar. Sie sind nicht erforderlich, um Funktionen zu implementieren, die nicht vom DBMS unterstützt werden. Wenn das zugrunde liegende DBMS beispielsweise keine äußeren Joins unterstützt, sollte keiner der Treiber verwendet werden. Die einzige wesentliche Ausnahme besteht darin, dass Treiber für DBMSs, die keine eigenständigen Datenbank-Engines wie xbase aufweisen, eine Datenbank-Engine implementieren müssen, die zumindest eine minimale Menge an SQL unterstützt.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Treiberaufgaben](../../odbc/reference/driver-tasks.md)  
  
-   [Treiberarchitektur](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Von Microsoft gelieferte ODBC-Treiber](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
