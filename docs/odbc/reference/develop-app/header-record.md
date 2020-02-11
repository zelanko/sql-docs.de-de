---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7f5fe5cf6aae0d5953cc82b845396dd4164c7fa3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139016"
---
# <a name="header-record"></a>Headerdatensatz
Die Felder im Header Daten Satz enthalten allgemeine Informationen über die Ausführung einer Funktion, einschließlich des Rückgabecodes, der Zeilen Anzahl, der Anzahl von Statusdaten Sätzen und des Typs der ausgeführten Anweisung. Der Header Daten Satz wird immer erstellt, es sei denn, die Funktion gibt SQL_INVALID_HANDLE zurück. Eine komplette Liste der Felder im Header Daten Satz finden Sie in der Beschreibung der [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) -Funktion.
