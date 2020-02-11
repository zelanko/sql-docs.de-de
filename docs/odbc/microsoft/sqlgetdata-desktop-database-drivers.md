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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68003355"
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (Desktop-Datenbanktreiber)
Diese Funktion kann Daten aus beliebigen Spalten abrufen, unabhängig davon, ob es gebundene Spalten gibt, und zwar unabhängig von der Reihenfolge, in der die Spalten abgerufen werden.  
  
> [!NOTE]  
>  \*pcbValue in **SQLGetData** gibt möglicherweise doppelt so viele Zeichen zurück, wie es tatsächlich verfügbar ist, wenn die Bindung an ANSI-Daten in einer Jet 4,0-Datenbank mehr als 510 Zeichen beträgt. Bei Zeichen Werten von 510 oder weniger wird der tatsächliche cbValue-Wert zurückgegeben.
