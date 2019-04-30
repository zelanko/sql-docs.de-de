---
title: SQLGetData (Desktop-Datenbanktreiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f362d725f8b734ab9ecdbdc79c268af08a495b4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63313143"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (Desktop-Datenbanktreiber)
Diese Funktion kann Daten aus einer beliebigen Spalte, abrufen, unabhängig davon, ob gebundene Spalten vorhanden sind, nachdem sie und unabhängig von der Reihenfolge, in der die Spalten abgerufen werden.  
  
> [!NOTE]  
>  \*PcbValue in **SQLGetData** möglicherweise doppelt so viele Zeichen zurückgeben als tatsächlich verfügbar sind beim Binden an die ANSI-Daten, die länger als 510 Zeichen in einer Jet 4.0-Datenbank. Zeichenwerten enthalten, die von 510 oder weniger werden der tatsächliche CbValue zurückgegeben.
