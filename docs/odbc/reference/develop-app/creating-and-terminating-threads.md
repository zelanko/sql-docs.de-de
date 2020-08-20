---
description: Erstellen und Beenden von Threads
title: Erstellen und Beenden von Threads | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- terminating threads [ODBC]
- threads [ODBC]
- multithreaded applications [ODBC]
ms.assetid: a2cf98ef-1c71-4742-8ee2-b53fd8e04333
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c0100b85bc596149d809dee7e6c4cb3547dbd081
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465852"
---
# <a name="creating-and-terminating-threads"></a>Erstellen und Beenden von Threads
Multithread-Anwendungen, die ODBC verwenden, sollten die Microsoft® Visual C++®-Lauf Zeit Bibliotheksfunktionen **_beginthread** und **_endthread** (oder **_beginthreadex** und **_endthreadex**) zum Erstellen und Beenden von Threads, die den ODBC-Treiber-Manager anrufen, verwenden. Wenn Anwendungen die Microsoft Windows NT-® Funktionen **CreateThread** und **endthread** aufrufen, treten Speicher Verluste auf, da der Treiber-Manager und einige ODBC-Treiber C-Lauf Zeitfunktionen aufrufen, die nicht in einem durch den Aufruf von **CreateThread**erstellten Thread funktionieren. Weitere Informationen finden Sie in der Dokumentation zu Microsoft Windows®.
