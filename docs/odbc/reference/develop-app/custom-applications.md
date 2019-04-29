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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ab470951162b5e4035c1253ed4ce425356ad8ec
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63042526"
---
# <a name="custom-applications"></a>Benutzerdefinierte Anwendungen
Benutzerdefinierte Anwendungen werden in der Regel eine bestimmte Aufgabe ausführen, für einige DBMS. Z. B. eine Anwendung möglicherweise Abrufen von Daten aus einer einzelnen DBMS und einen Bericht generieren, oder es kann Daten zwischen mehreren DBMS-Systeme übertragen. Was diese Anwendungen gemeinsam haben ist, dass diese DBMS bekannt sind, bevor die Anwendung geschrieben wird und es unwahrscheinlich, dass während der Lebensdauer der Anwendung ändern.  
  
 Die benutzerdefinierte Anwendung erfordert daher nur wenig oder keine Interoperabilität. Der Anwendungsentwickler kann nur einen Treiber für die einzelnen DBMS und den Code direkt mit dem diese Treiber auswählen. Die Anwendung kann sicher Driver-spezifischen Code aus, um die Funktionen der Treiber exploit enthält, und möglicherweise sogar Aufrufe der systemeigenen Datenbank-API-Funktionen von ODBC nicht unterstützt.  
  
 Die wichtigsten Interoperabilität der meisten benutzerdefinierten Anwendungen spielt, ob das Ziel-DBMS-Systeme in der Zukunft ändern wird. Wenn dies der Fall ist, kann dieser Prozess vereinfacht werden, durch Schreiben von Interoperabilität Code für den Einstieg. Eine solche Änderung des DBMS ist jedoch selten und in der Regel umfasst eine große Menge an Arbeit. Aus diesem Grund entscheiden sich Entwickler benutzerdefinierter Anwendungen selten um Interoperabilität zu Lasten der Funktionalität zu erhöhen; in der Regel möchten sie diese Funktionalität zu codieren, wenn sie Datenbank-Managementsysteme ändern.
