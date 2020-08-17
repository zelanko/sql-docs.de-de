---
description: SQLGetData (Desktop-Datenbanktreiber)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cfce744c3f4a2e0e4d9fcb054a8226538537bdcf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340227"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (Desktop-Datenbanktreiber)
Diese Funktion kann Daten aus beliebigen Spalten abrufen, unabhängig davon, ob es gebundene Spalten gibt, und zwar unabhängig von der Reihenfolge, in der die Spalten abgerufen werden.  
  
> [!NOTE]  
>  \*pcbValue in **SQLGetData** gibt möglicherweise doppelt so viele Zeichen zurück, wie es tatsächlich verfügbar ist, wenn die Bindung an ANSI-Daten in einer Jet 4,0-Datenbank mehr als 510 Zeichen beträgt. Bei Zeichen Werten von 510 oder weniger wird der tatsächliche cbValue-Wert zurückgegeben.
