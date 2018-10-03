---
title: WIE Prädikat Einschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8035eed9e0aaff1f914f386b6d4bc9f2d65f9a0f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47652974"
---
# <a name="like-predicate-limitations"></a>Einschränkungen des LIKE-Prädikats
Wenn Daten in einer Spalte mehr als 255 Zeichen ist, wird der Vergleich mit LIKE nur auf die ersten 255 Zeichen basieren.  
  
 Eine ähnliche verwendet wird, eine Prozedur wird nur mit Konstantenmuster unterstützt. Die Desktop-Datenbanktreiber unterstützt SQL-92 wie Mustervergleich.  
  
 Verwenden einer Escape-Klausel in einer LIKE-Prädikat wird nicht unterstützt.  
  
 Ein Vergleich mit LIKE sollte nicht für eine Spalte mit Daten eines Datentyps der numerischen oder "float" ausgeführt werden. Die Ergebnisse möglicherweise nicht vorhersehbar sein. Weitere Informationen finden Sie unter den *Microsoft Jet-Datenbank-Engine Handbuch für Programmierer*.
