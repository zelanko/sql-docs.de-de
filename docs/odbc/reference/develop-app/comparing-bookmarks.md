---
description: Vergleichen von Textmarken
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 939c3780fc9c6738a307e9a969a346951cfac5e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476782"
---
# <a name="comparing-bookmarks"></a>Vergleichen von Textmarken
Da Lesezeichen Byte-vergleichbar sind, können Sie auf Gleichheit oder Ungleichheit verglichen werden. Zu diesem Zweck behandelt eine Anwendung jedes Lesezeichen als Bytearray und vergleicht zwei Lesezeichen Byte Weise. Da Lesezeichen garantiert nur innerhalb eines Resultsets eindeutig sind, ist es nicht sinnvoll, Lesezeichen zu vergleichen, die aus unterschiedlichen Resultsets abgerufen wurden.
