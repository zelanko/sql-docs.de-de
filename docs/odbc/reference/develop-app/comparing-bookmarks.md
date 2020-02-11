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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083305"
---
# <a name="comparing-bookmarks"></a>Vergleichen von Textmarken
Da Lesezeichen Byte-vergleichbar sind, können Sie auf Gleichheit oder Ungleichheit verglichen werden. Zu diesem Zweck behandelt eine Anwendung jedes Lesezeichen als Bytearray und vergleicht zwei Lesezeichen Byte Weise. Da Lesezeichen garantiert nur innerhalb eines Resultsets eindeutig sind, ist es nicht sinnvoll, Lesezeichen zu vergleichen, die aus unterschiedlichen Resultsets abgerufen wurden.
