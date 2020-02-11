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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041598"
---
# <a name="loading-by-ordinal"></a>Laden nach Ordnungszahl
In ODBC *2. x*kann das Laden nach Ordnungszahl durchgeführt werden, um die Leistung des Verbindungs Vorgangs zu verbessern. Ein ODBC *2. x* -Treiber exportiert eine Dummy-Funktion mit der Ordinalzahl 199; Wenn Sie vom Treiber-Manager erkannt wird, werden die Adressen der ODBC-Funktionen nach Ordinalzahl, nicht nach Name aufgelöst. Diese Funktion wird weiterhin für ODBC *2. x* -Treiber unterstützt, wird aber nicht für ODBC *3. x* -Treiber unterstützt.
