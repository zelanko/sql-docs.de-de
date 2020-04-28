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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c28392c0d48984b4aaf8a8df442b6a4054a7eced
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307475"
---
# <a name="comparing-bookmarks"></a>Vergleichen von Textmarken
Da Lesezeichen Byte-vergleichbar sind, können Sie auf Gleichheit oder Ungleichheit verglichen werden. Zu diesem Zweck behandelt eine Anwendung jedes Lesezeichen als Bytearray und vergleicht zwei Lesezeichen Byte Weise. Da Lesezeichen garantiert nur innerhalb eines Resultsets eindeutig sind, ist es nicht sinnvoll, Lesezeichen zu vergleichen, die aus unterschiedlichen Resultsets abgerufen wurden.
