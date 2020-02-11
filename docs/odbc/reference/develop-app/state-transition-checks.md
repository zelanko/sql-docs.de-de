---
title: Status Übergangs Überprüfungen | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107282"
---
# <a name="state-transition-checks"></a>Überprüfungen des Statusübergangs
Der Treiber-Manager überprüft, ob der Zustand der Umgebung, der Verbindung oder der Anweisung für die aufgerufene Funktion geeignet ist. Beispielsweise muss sich eine Verbindung in einem zugewiesenen Zustand befinden, wenn **SQLCONNECT** aufgerufen wird. eine-Anweisung muss sich in einem vorbereiteten Zustand befinden, wenn **SQLExecute** aufgerufen wird. Der Treiber-Manager gibt SQL_ERROR für Zustands Übergangs Fehler zurück.
