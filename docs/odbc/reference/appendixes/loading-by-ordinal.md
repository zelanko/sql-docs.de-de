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
manager: craigg
ms.openlocfilehash: 702e1fe58080cc370ab9a858c985a7744df85050
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845858"
---
# <a name="loading-by-ordinal"></a>Laden nach Ordnungszahl
In ODBC 2. *x*, laden nach Ordnungszahl konnte zur Verbesserung der Leistung des Verbindungsprozesses ausgeführt werden. Eine ODBC-2. *x* Treiber exportiert eine dummy-Funktion mit der Ordnungszahl 199; Wenn der Treiber-Manager erkannt wird, löst er die Adressen der ODBC-Funktionen, anhand der Ordinalzahl, nicht anhand des Namens. Diese Funktion wird weiterhin für ODBC 2 unterstützt. *x* Treiber für ODBC 3 nicht unterstützt wird, aber *.x* Treiber.
