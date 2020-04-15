---
title: Beladen von Ordinal | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288720"
---
# <a name="loading-by-ordinal"></a>Laden nach Ordnungszahl
In ODBC *2.x*kann das Laden durch Ordinal durchgeführt werden, um die Leistung des Verbindungsprozesses zu verbessern. Ein ODBC *2.x-Treiber* exportiert eine Dummy-Funktion mit dem Ordinal 199; Wenn der Treiber-Manager es erkennt, werden die Adressen der ODBC-Funktionen durch Ordinal aufgelöst, nicht durch Namen. Diese Funktionalität wird weiterhin für ODBC *2.x-Treiber* unterstützt, aber nicht für ODBC *3.x-Treiber.*
