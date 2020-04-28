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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d235146ffe1b4699f0064c5772407bcf40ae962
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306193"
---
# <a name="length-of-the-product-cycle"></a>Länge des Produktzyklus
Die letzte Frage zur Interoperabilität ist die Zeit. Die Entwicklung einer interoperablen Anwendung dauert in der Regel länger als die Entwicklung einer nicht interoperablen Anwendung. Der Grund hierfür ist, dass die Anwendung DBMS-Funktionen überprüfen muss, die gleichen Tasks für verschiedene DBMSs anders ausführen muss, um die von einigen DBMSs, aber nicht von anderen unterstützten Funktionen zu umgehen, usw.  
  
 Zusätzlich zur Entwicklungszeit muss die Produktlebensdauer berücksichtigt werden. Wenn die Anwendung einmal verwendet werden soll, z. b. eine Anwendung, die Daten bei der Migration von einem DBMS zu einem anderen überträgt, ist es nicht möglich, sie interoperabel zu gestalten. Die Anwendung wird einmalig verwendet und verworfen.  
  
 Wenn die Anwendung für einen längeren Zeitraum vorhanden ist, ist es möglicherweise einfacher, als interoperable Anwendung zu warten. Dies gilt auch für benutzerdefinierte Anwendungen, die ein einzelnes DBMS als Ziel haben. Der Grund hierfür ist, dass der interoperable Code eine begrenzte Teilmenge der Datenbankfunktionen verwendet. Der Treiber muss diese Features auch bei Änderungen am zugrunde liegenden DBMS verfügbar halten. Daher kann durch interoperablen Code die Last der Bewältigung von Änderungen am DBMS vom Anwendungsentwickler zum Treiber Entwickler verlagert werden.
