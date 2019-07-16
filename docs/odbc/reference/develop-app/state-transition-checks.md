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
ms.openlocfilehash: b337d317092ad6ae20cc91236d69c1314de96bce
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68107282"
---
# <a name="state-transition-checks"></a>Überprüfungen des Statusübergangs
Der Treiber-Manager überprüft, dass der Status der Umgebung, die Verbindungs-und die Anweisung für die aufgerufene Funktion geeignet ist. Beispielsweise muss eine Verbindung in einer zugeordneten Zustand über, wenn **SQLConnect** aufgerufen wird; eine Anweisung muss in mindestens eine vorbereitete Zustand über, wenn **SQLExecute** aufgerufen wird. Der Treiber-Manager gibt SQL_ERROR zurück, für die Status-Übergang-Fehler.
