---
description: Überprüfungen des Statusübergangs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 50a845f2b83ada7c9d4f03f252b6d2bc3d3eff3d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476372"
---
# <a name="state-transition-checks"></a>Überprüfungen des Statusübergangs
Der Treiber-Manager überprüft, ob der Zustand der Umgebung, der Verbindung oder der Anweisung für die aufgerufene Funktion geeignet ist. Beispielsweise muss sich eine Verbindung in einem zugewiesenen Zustand befinden, wenn **SQLCONNECT** aufgerufen wird. eine-Anweisung muss sich in einem vorbereiteten Zustand befinden, wenn **SQLExecute** aufgerufen wird. Der Treiber-Manager gibt SQL_ERROR für Zustands Übergangs Fehler zurück.
