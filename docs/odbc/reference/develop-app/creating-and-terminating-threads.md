---
title: Erstellen und Beenden von Threads | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301691"
---
# <a name="creating-and-terminating-threads"></a>Erstellen und Beenden von Threads
Multithreadanwendungen, die ODBC verwenden, sollten die Funktionen Microsoft® Visual C++® Run-Time Library **aufrufen, _beginthread** und **_endthread** (oder **_beginthreadex** und **_endthreadex**) zum Erstellen und Beenden von Threads aufrufen, die den ODBC-Treiber-Manager aufrufen. Wenn Anwendungen stattdessen die Microsoft Windows NT®-Funktionen **CreateThread** und **EndThread** aufrufen, treten Speicherverluste auf, da der Treiber-Manager und einige ODBC-Treiber C-Laufzeitfunktionen aufrufen, die nicht auf einem Thread funktionieren, der durch den Aufruf von **CreateThread**erstellt wurde. Weitere Informationen finden Sie in der Microsoft Windows®-Dokumentation.
