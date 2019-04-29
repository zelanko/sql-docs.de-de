---
title: Status-Übergang-Überprüfungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- state transition checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0706db7d-e125-4845-a13a-7fe4308f7360
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dcfefffb167b97ace09bfa358296d886265a987f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149061"
---
# <a name="state-transition-checks"></a>Überprüfungen des Statusübergangs
Der Treiber-Manager überprüft, dass der Status der Umgebung, die Verbindungs-und die Anweisung für die aufgerufene Funktion geeignet ist. Beispielsweise muss eine Verbindung in einer zugeordneten Zustand über, wenn **SQLConnect** aufgerufen wird; eine Anweisung muss in mindestens eine vorbereitete Zustand über, wenn **SQLExecute** aufgerufen wird. Der Treiber-Manager gibt SQL_ERROR zurück, für die Status-Übergang-Fehler.
