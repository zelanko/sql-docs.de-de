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
ms.openlocfilehash: 086c5381f1801baf919508525c17faab93746ca0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003355"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (Desktop-Datenbanktreiber)
Diese Funktion kann Daten aus einer beliebigen Spalte, abrufen, unabhängig davon, ob gebundene Spalten vorhanden sind, nachdem sie und unabhängig von der Reihenfolge, in der die Spalten abgerufen werden.  
  
> [!NOTE]  
>  \*PcbValue in **SQLGetData** möglicherweise doppelt so viele Zeichen zurückgeben als tatsächlich verfügbar sind beim Binden an die ANSI-Daten, die länger als 510 Zeichen in einer Jet 4.0-Datenbank. Zeichenwerten enthalten, die von 510 oder weniger werden der tatsächliche CbValue zurückgegeben.
