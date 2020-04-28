---
title: Laden nach Ordnungszahl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 64bff8dcdd3802f75dc402c9ada60f82580aca5c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81288720"
---
# <a name="loading-by-ordinal"></a>Laden nach Ordnungszahl
In ODBC *2. x*kann das Laden nach Ordnungszahl durchgeführt werden, um die Leistung des Verbindungs Vorgangs zu verbessern. Ein ODBC *2. x* -Treiber exportiert eine Dummy-Funktion mit der Ordinalzahl 199; Wenn Sie vom Treiber-Manager erkannt wird, werden die Adressen der ODBC-Funktionen nach Ordinalzahl, nicht nach Name aufgelöst. Diese Funktion wird weiterhin für ODBC *2. x* -Treiber unterstützt, wird aber nicht für ODBC *3. x* -Treiber unterstützt.
