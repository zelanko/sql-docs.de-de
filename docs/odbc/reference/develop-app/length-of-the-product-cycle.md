---
title: Die Länge des Produktzyklus | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100455"
---
# <a name="length-of-the-product-cycle"></a>Länge des Produktzyklus
Die letzte Frage zur Interoperabilität ist Zeit. Entwickeln Sie in der Regel von einer interoperablen Anwendung dauert länger als die Entwicklung einer noninteroperable. Der Grund ist, dass die Anwendung muss überprüfen Sie die Funktionen des DBMS, die gleichen Aufgaben anders für die verschiedenen DBMS, von einigen DBMS-Systeme, aber in anderen unterstützten Funktionen zu umgehen, usw. an.  
  
 Zusätzlich zur Entwicklungszeit muss Produktlebenszyklus berücksichtigt werden. Wenn die Anwendung konzipiert ist, einmal, z. B. eine Anwendung verwendet werden, die Datenübertragung bei der Migration von einem DBMS in eine andere besteht keinen Sinn machen es interoperabel. Die Anwendung wird einmal verwendet und verworfen werden.  
  
 Wenn die Anwendung einen längeren Zeitraum vorhanden ist, kann es einfacher, als einer interoperablen Anwendung zu verwalten sein. Dies gilt auch für benutzerdefinierte Anwendungen, die eine einzelne DBMS als Ziel haben. Der Grund ist, dass interoperable Code eine begrenzte Teilmenge der Funktionen der Datenbank verwendet. Der Treiber ist erforderlich, um diese Features verfügbar, auch bei Änderungen an das zugrunde liegende DBMS zu halten. Daher kann interoperable Code Druck mit Änderungen die Last für das DBMS seitens des Entwicklers der Anwendung für den Treiber Entwickler verlagern.
