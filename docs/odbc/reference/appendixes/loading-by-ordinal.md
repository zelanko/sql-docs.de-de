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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fdc7728fe06df708efd973423f5c8c05333ce189
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041598"
---
# <a name="loading-by-ordinal"></a>Laden nach Ordnungszahl
In ODBC *2.x*, laden nach Ordnungszahl konnte zur Verbesserung der Leistung des Verbindungsprozesses ausgeführt werden. ODBC *2.x* Treiber exportiert eine dummy-Funktion mit der Ordnungszahl 199; Wenn der Treiber-Manager erkannt wird, löst er die Adressen der ODBC-Funktionen, anhand der Ordinalzahl, nicht anhand des Namens. Diese Funktion wird weiterhin für ODBC unterstützt *2.x* Treiber jedoch nicht für ODBC unterstützt *3.x* Treiber.
