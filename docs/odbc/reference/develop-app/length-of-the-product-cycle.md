---
title: Länge des Produktzyklen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], product cycle
- length of the product cycle [ODBC]
ms.assetid: 4d08d886-6d8b-40fd-8544-13032f4bf6c7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 203ad92dd6abfc71b0fdeddc466752612e666cee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68100455"
---
# <a name="length-of-the-product-cycle"></a>Länge des Produktzyklus
Die letzte Frage zur Interoperabilität ist die Zeit. Die Entwicklung einer interoperablen Anwendung dauert in der Regel länger als die Entwicklung einer nicht interoperablen Anwendung. Der Grund hierfür ist, dass die Anwendung DBMS-Funktionen überprüfen muss, die gleichen Tasks für verschiedene DBMSs anders ausführen muss, um die von einigen DBMSs, aber nicht von anderen unterstützten Funktionen zu umgehen, usw.  
  
 Zusätzlich zur Entwicklungszeit muss die Produktlebensdauer berücksichtigt werden. Wenn die Anwendung einmal verwendet werden soll, z. b. eine Anwendung, die Daten bei der Migration von einem DBMS zu einem anderen überträgt, ist es nicht möglich, sie interoperabel zu gestalten. Die Anwendung wird einmalig verwendet und verworfen.  
  
 Wenn die Anwendung für einen längeren Zeitraum vorhanden ist, ist es möglicherweise einfacher, als interoperable Anwendung zu warten. Dies gilt auch für benutzerdefinierte Anwendungen, die ein einzelnes DBMS als Ziel haben. Der Grund hierfür ist, dass der interoperable Code eine begrenzte Teilmenge der Datenbankfunktionen verwendet. Der Treiber muss diese Features auch bei Änderungen am zugrunde liegenden DBMS verfügbar halten. Daher kann durch interoperablen Code die Last der Bewältigung von Änderungen am DBMS vom Anwendungsentwickler zum Treiber Entwickler verlagert werden.
