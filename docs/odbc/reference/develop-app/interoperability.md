---
title: Interoperabilität | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31b20a696c601ff91c591e4c717f468beca34e36
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306221"
---
# <a name="interoperability"></a>Interoperabilität
*Interoperabilität* ist die Fähigkeit einer einzelnen Anwendung, mit vielen verschiedenen DBMS zu arbeiten. Die Notwendigkeit, generische, interoperable Anwendungen zu schreiben, war einer der Hauptfaktoren, die zur Entwicklung von ODBC führten. Interoperabilität ist jedoch kein einfacher Weg, der von "nicht interoperabel" bis "vollständig interoperabel" geht. Der Pfad hat viele Zweige, und jeder erfordert Kompromisse zwischen Features, Geschwindigkeit, Codekomplexität und Entwicklungszeit.  
  
 Der Prozess des Schreibens einer interoperablen Anwendung folgt mehreren Schritten:  
  
1.  Entscheiden, ob die Anwendung ODBC verwendet.  
  
2.  Die Wahl eines Interoperabilitätsniveaus und die Entscheidung, welche Kompromisse erforderlich sind, um dieses Niveau zu erreichen.  
  
3.  Interoperablen Code schreiben und so vollständig wie möglich testen.  
  
 Es sollte beachtet werden, dass die Interoperabilität in erster Linie die Domäne des Anwendungsschreibers ist. Treiber sind so konzipiert, dass sie mit einem einzelnen DBMS arbeiten und sind per definitionem nicht interoperabel. Sie spielen eine Rolle in der Interoperabilität, indem sie ODBC korrekt über ein einzelnes DBMS implementieren und freilegen.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Ist ODBC die Antwort?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Auswählen einer Interoperabilitätsebene](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Ermitteln der Ziel-DBMS und Zieltreiber](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Erwägen der zu verwendenden Datenbankfunktionen](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Länge des Produktzyklus](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Schreiben einer interoperablen Anwendung](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Testen von interoperablen Anwendungen](../../../odbc/reference/develop-app/testing-interoperable-applications.md)
