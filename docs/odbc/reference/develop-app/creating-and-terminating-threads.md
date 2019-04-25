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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9d6d15c449d88043e844addd12ac10a98d5c4a0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62470868"
---
# <a name="creating-and-terminating-threads"></a>Erstellen und Beenden von Threads
Multithread-Anwendungen, die ODBC verwenden, sollten die Microsoft® Visual Aufrufen C++®-Laufzeitbibliotheksfunktionen **_beginthread** und **_endthread** (oder **_beginthreadex**und **_endthreadex**) erstellen und Beenden von Threads, die den ODBC-Treiber-Manager aufrufen. Wenn Anwendungen die Microsoft Windows NT®-Funktionen aufrufen **CreateThread** und **EndThread** stattdessen Speicher Speicherverluste tritt auf, da der Treiber-Manager und einige ODBC-Treiber Aufrufen von C-Laufzeit-Funktionen, funktioniert nicht in einem Thread durch Aufrufen von erstellt **CreateThread**. Weitere Informationen finden Sie unter der Microsoft Windows®-Dokumentation.
