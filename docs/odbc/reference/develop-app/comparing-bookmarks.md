---
title: Vergleichen von Lesezeichen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 44da652ad1e52934fa48f32b1b2f88b30212ad3b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083305"
---
# <a name="comparing-bookmarks"></a>Vergleichen von Textmarken
Da Lesezeichen Byte vergleichbar sind, können sie für Gleichheit oder Ungleichheit verglichen werden. Zu diesem Zweck wird eine Anwendung jedes Lesezeichen als ein Array von Bytes behandelt und vergleicht zwei Lesezeichen Byte-pro-Byte. Da es sich bei Lesezeichen garantiert werden, nur innerhalb eines Resultsets unterscheiden, ist es nicht sinnvoll, Lesezeichen zu vergleichen, die aus den verschiedenen Resultsets abgerufen wurden.
