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
ms.openlocfilehash: b97f29ad06c4ed961f3cee571b0ca7b8d9c0b774
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002085"
---
# <a name="creating-and-terminating-threads"></a>Erstellen und Beenden von Threads
Multithread-Anwendungen, die ODBC verwenden, sollten die Microsoft® Visual Aufrufen C++®-Laufzeitbibliotheksfunktionen **_beginthread** und **_endthread** (oder **_beginthreadex**und **_endthreadex**) erstellen und Beenden von Threads, die den ODBC-Treiber-Manager aufrufen. Wenn Anwendungen die Microsoft Windows NT®-Funktionen aufrufen **CreateThread** und **EndThread** stattdessen Speicher Speicherverluste tritt auf, da der Treiber-Manager und einige ODBC-Treiber Aufrufen von C-Laufzeit-Funktionen, funktioniert nicht in einem Thread durch Aufrufen von erstellt **CreateThread**. Weitere Informationen finden Sie unter der Microsoft Windows®-Dokumentation.
