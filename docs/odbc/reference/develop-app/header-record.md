---
title: Header-Datensatz | Microsoft Docs
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
ms.openlocfilehash: 372185966cc1644147feb2683177ae3a5b69e788
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300180"
---
# <a name="header-record"></a>Headerdatensatz
Die Felder im Kopfdatensatz enthalten allgemeine Informationen über die Ausführung einer Funktion, einschließlich des Rückgabecodes, der Zeilenanzahl, der Anzahl der Statusdatensätze und des Typs der ausgeführten Anweisung. Der Headerdatensatz wird immer erstellt, es sei denn, die Funktion gibt SQL_INVALID_HANDLE zurück. Eine vollständige Liste der Felder im Headerdatensatz finden Sie in der [SQLGetDiagField-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)
