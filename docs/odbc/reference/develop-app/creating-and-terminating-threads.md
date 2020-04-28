---
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
ms.openlocfilehash: 3536deef604d7dbf645903e7d171a58cd9fec96a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301691"
---
# <a name="creating-and-terminating-threads"></a>Erstellen und Beenden von Threads
Multithread-Anwendungen, die ODBC verwenden, sollten die Microsoft® Visual C++®-Lauf Zeit Bibliotheksfunktionen **_beginthread** und **_endthread** (oder **_beginthreadex** und **_endthreadex**) zum Erstellen und Beenden von Threads, die den ODBC-Treiber-Manager anrufen, verwenden. Wenn Anwendungen die Microsoft Windows NT-® Funktionen **CreateThread** und **endthread** aufrufen, treten Speicher Verluste auf, da der Treiber-Manager und einige ODBC-Treiber C-Lauf Zeitfunktionen aufrufen, die nicht in einem durch den Aufruf von **CreateThread**erstellten Thread funktionieren. Weitere Informationen finden Sie in der Dokumentation zu Microsoft Windows®.
