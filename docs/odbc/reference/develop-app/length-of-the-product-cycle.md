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
manager: craigg
ms.openlocfilehash: 2c8a5b88f3fdca03be7740ba086e7ff61edbf684
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656148"
---
# <a name="length-of-the-product-cycle"></a>Länge des Produktzyklus
Die letzte Frage zur Interoperabilität ist Zeit. Entwickeln Sie in der Regel von einer interoperablen Anwendung dauert länger als die Entwicklung einer noninteroperable. Der Grund ist, dass die Anwendung muss überprüfen Sie die Funktionen des DBMS, die gleichen Aufgaben anders für die verschiedenen DBMS, von einigen DBMS-Systeme, aber in anderen unterstützten Funktionen zu umgehen, usw. an.  
  
 Zusätzlich zur Entwicklungszeit muss Produktlebenszyklus berücksichtigt werden. Wenn die Anwendung konzipiert ist, einmal, z. B. eine Anwendung verwendet werden, die Datenübertragung bei der Migration von einem DBMS in eine andere besteht keinen Sinn machen es interoperabel. Die Anwendung wird einmal verwendet und verworfen werden.  
  
 Wenn die Anwendung einen längeren Zeitraum vorhanden ist, kann es einfacher, als einer interoperablen Anwendung zu verwalten sein. Dies gilt auch für benutzerdefinierte Anwendungen, die eine einzelne DBMS als Ziel haben. Der Grund ist, dass interoperable Code eine begrenzte Teilmenge der Funktionen der Datenbank verwendet. Der Treiber ist erforderlich, um diese Features verfügbar, auch bei Änderungen an das zugrunde liegende DBMS zu halten. Daher kann interoperable Code Druck mit Änderungen die Last für das DBMS seitens des Entwicklers der Anwendung für den Treiber Entwickler verlagern.
