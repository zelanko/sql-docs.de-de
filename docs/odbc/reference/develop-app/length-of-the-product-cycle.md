---
title: Länge des Produktzyklus | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306193"
---
# <a name="length-of-the-product-cycle"></a>Länge des Produktzyklus
Die letzte Frage zur Interoperabilität ist die Zeit. Die Entwicklung einer interoperablen Anwendung dauert in der Regel länger als die Entwicklung einer nicht interoperablen Anwendung. Der Grund dafür ist, dass die Anwendung DBMS-Funktionen überprüfen, die gleichen Aufgaben für verschiedene DBMS unterschiedlich ausführen, Funktionen umgehen muss, die von einigen DBMS unterstützt werden, aber nicht von anderen usw.  
  
 Neben der Entwicklungszeit muss die Produktlebensdauer berücksichtigt werden. Wenn die Anwendung so konzipiert ist, dass sie einmal verwendet wird, z. B. eine Anwendung, die Daten überträgt, wenn Sie von einem DBMS zu einem anderen migrieren, macht es keinen Sinn, sie interoperabel zu machen. Die Anwendung wird einmal verwendet und verworfen.  
  
 Wenn die Anwendung für eine lange Zeit vorhanden sein wird, ist es möglicherweise einfacher, sie als interoperable Anwendung zu verwalten. Dies gilt auch für benutzerdefinierte Anwendungen, die über ein einzelnes DBMS als Ziel verfügen. Der Grund dafür ist, dass interoperabler Code eine begrenzte Teilmenge von Datenbankfeatures verwendet. Der Treiber muss diese Funktionen auch bei Änderungen am zugrunde liegenden DBMS verfügbar halten. Daher kann interoperabler Code die Last der Bewältigung von Änderungen am DBMS vom Anwendungsentwickler zum Treiberentwickler verlagern.
