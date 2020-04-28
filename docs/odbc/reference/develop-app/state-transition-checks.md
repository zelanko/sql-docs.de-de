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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7dc1ddc126a2d652dfdb038cbb0e510f9735d7b0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299705"
---
# <a name="state-transition-checks"></a>Überprüfungen des Statusübergangs
Der Treiber-Manager überprüft, ob der Zustand der Umgebung, der Verbindung oder der Anweisung für die aufgerufene Funktion geeignet ist. Beispielsweise muss sich eine Verbindung in einem zugewiesenen Zustand befinden, wenn **SQLCONNECT** aufgerufen wird. eine-Anweisung muss sich in einem vorbereiteten Zustand befinden, wenn **SQLExecute** aufgerufen wird. Der Treiber-Manager gibt SQL_ERROR für Zustands Übergangs Fehler zurück.
