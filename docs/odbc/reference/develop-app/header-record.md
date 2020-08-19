---
description: Headerdatensatz
title: Header Daten Satz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- header records [ODBC]
- diagnostic records [ODBC]
ms.assetid: d0fff1ed-5616-422a-a394-7ea1d2486f89
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4de764381e54a0b3485130c1a3bdf25b2a9bf9fa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476642"
---
# <a name="header-record"></a>Headerdatensatz
Die Felder im Header Daten Satz enthalten allgemeine Informationen über die Ausführung einer Funktion, einschließlich des Rückgabecodes, der Zeilen Anzahl, der Anzahl von Statusdaten Sätzen und des Typs der ausgeführten Anweisung. Der Header Daten Satz wird immer erstellt, es sei denn, die Funktion gibt SQL_INVALID_HANDLE zurück. Eine komplette Liste der Felder im Header Daten Satz finden Sie in der Beschreibung der [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) -Funktion.
