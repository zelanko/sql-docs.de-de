---
title: Benutzerdefinierte Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], custom applications
- custom applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: f28178d9-ecd6-4e8c-9644-9bb624999dcb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df00a748ee4d5e3a63b32c95449417a1057b58e1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305281"
---
# <a name="custom-applications"></a>Benutzerdefinierte Anwendungen
Benutzerdefinierte Anwendungen führen in der Regel eine bestimmte Aufgabe für einige DBMSs aus. Beispielsweise kann eine Anwendung Daten aus einem einzelnen DBMS abrufen und einen Bericht generieren, oder Sie kann Daten zwischen mehreren DBMSs übertragen. Diese Anwendungen sind häufig vorhanden, da diese DBMSs bekannt sind, bevor die Anwendung geschrieben wird, und sich im Laufe der Lebensdauer der Anwendung wahrscheinlich nicht mehr ändern.  
  
 Die benutzerdefinierte Anwendung erfordert daher wenig oder keine Interoperabilität. Der Anwendungsentwickler kann einen einzelnen Treiber für jedes DBMS und jeden Code direkt für diese Treiber auswählen. Die Anwendung kann den treiberspezifischen Code sicher enthalten, um die Funktionen dieser Treiber auszunutzen, und kann sogar Aufrufe an die native Database-API durchführen, um Funktionen zu verwenden, die nicht von ODBC unterstützt werden.  
  
 Das wichtigste Interoperabilitäts Problem bei den meisten benutzerdefinierten Anwendungen ist, ob sich die Ziel-DBMSs in Zukunft ändern wird. Wenn dies der Fall ist, kann dieser Prozess durch Schreiben von interoperablen Code vereinfacht werden, um mit zu beginnen. Eine solche Änderung von DBMSs ist jedoch selten und umfasst im Allgemeinen eine große Menge an Arbeit. Daher entscheiden sich Entwickler von benutzerdefinierten Anwendungen selten dafür, die Interoperabilität auf Kosten der Funktionalität zu erhöhen. Diese Funktionen werden in der Regel bei der Änderung von DBMSs erneut verwendet.
