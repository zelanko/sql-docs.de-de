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
manager: craigg
ms.openlocfilehash: 690acf80bfabdc04d5f70b780e41943337c18cb9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026610"
---
# <a name="comparing-bookmarks"></a>Vergleichen von Textmarken
Da Lesezeichen Byte vergleichbar sind, können sie für Gleichheit oder Ungleichheit verglichen werden. Zu diesem Zweck wird eine Anwendung jedes Lesezeichen als ein Array von Bytes behandelt und vergleicht zwei Lesezeichen Byte-pro-Byte. Da es sich bei Lesezeichen garantiert werden, nur innerhalb eines Resultsets unterscheiden, ist es nicht sinnvoll, Lesezeichen zu vergleichen, die aus den verschiedenen Resultsets abgerufen wurden.
