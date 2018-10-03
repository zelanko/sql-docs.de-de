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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722378"
---
# <a name="creating-and-terminating-threads"></a>Erstellen und Beenden von Threads
Multithread-Anwendungen, die ODBC verwenden, sollten die Funktionen von Microsoft® Visual C++® Laufzeit-Bibliothek aufrufen **_beginthread** und **_endthread** (oder **_beginthreadex** und **_endthreadex**) erstellen und Beenden von Threads, die den ODBC-Treiber-Manager aufrufen. Wenn Anwendungen die Microsoft Windows NT®-Funktionen aufrufen **CreateThread** und **EndThread** stattdessen Speicher Speicherverluste tritt auf, da der Treiber-Manager und einige ODBC-Treiber Aufrufen von C-Laufzeit-Funktionen, funktioniert nicht in einem Thread durch Aufrufen von erstellt **CreateThread**. Weitere Informationen finden Sie unter der Microsoft Windows®-Dokumentation.
