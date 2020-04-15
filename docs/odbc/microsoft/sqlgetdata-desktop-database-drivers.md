---
title: SQLGetData (Desktop-Datenbanktreiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2b102d8435831d45aad3c2049581513e0493de9a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304121"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (Desktop-Datenbanktreiber)
Diese Funktion kann Daten aus jeder Spalte abrufen, unabhängig davon, ob es danach gebundene Spalten gibt und unabhängig von der Reihenfolge, in der die Spalten abgerufen werden.  
  
> [!NOTE]  
>  \*pcbValue in **SQLGetData** gibt möglicherweise doppelt so viele Zeichen zurück wie tatsächlich verfügbar, wenn an ANSI-Daten bindungen, die länger als 510 Zeichen in einer Jet 4.0-Datenbank sind. Zeichenwerte von 510 oder weniger geben den tatsächlichen cbValue zurück.
