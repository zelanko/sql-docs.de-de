---
description: Laden nach Ordnungszahl
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
ms.openlocfilehash: eb8929962e97e7560f50117218f621cd21846fc4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429632"
---
# <a name="loading-by-ordinal"></a>Laden nach Ordnungszahl
In ODBC *2. x*kann das Laden nach Ordnungszahl durchgeführt werden, um die Leistung des Verbindungs Vorgangs zu verbessern. Ein ODBC *2. x* -Treiber exportiert eine Dummy-Funktion mit der Ordinalzahl 199; Wenn Sie vom Treiber-Manager erkannt wird, werden die Adressen der ODBC-Funktionen nach Ordinalzahl, nicht nach Name aufgelöst. Diese Funktion wird weiterhin für ODBC *2. x* -Treiber unterstützt, wird aber nicht für ODBC *3. x* -Treiber unterstützt.
