---
title: Interoperabilität | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 434b27bffe3b32aa9fa0c5c6fd3a7100e8c7ea8d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138855"
---
# <a name="interoperability"></a>Interoperabilität
*Interoperabilität* ist die Fähigkeit einer einzelnen Anwendung, mit vielen verschiedenen DBMSs zu arbeiten. Die Notwendigkeit, generische, interoperable Anwendungen zu schreiben, war einer der Hauptfaktoren, die zur Entwicklung von ODBC führten. Die Interoperabilität ist jedoch kein einfacher Pfad, gefolgt von "nicht interoperabel" zu "vollständig interoperabel". Der Pfad umfasst viele branches, und jeder erfordert Kompromisse zwischen Features, Geschwindigkeit, Codekomplexität und Entwicklungszeit.  
  
 Der Prozess zum Schreiben einer interoperablen Anwendung erfolgt in mehreren Schritten:  
  
1.  Entscheiden, ob die Anwendung ODBC verwendet.  
  
2.  Wählen Sie eine Ebene der Interoperabilität aus, und entscheiden Sie, welche Kompromisse erforderlich sind, um diese Ebene zu erreichen.  
  
3.  Schreiben von interoperablen Code und Testen des Codes so umfassend wie möglich.  
  
 Beachten Sie, dass die Interoperabilität in erster Linie die Domäne des anwendungswriter ist. Treiber sind so konzipiert, dass Sie mit einem einzelnen DBMS funktionieren und definitionsgemäß nicht interoperabel sind. Sie spielen eine Rolle in der Interoperabilität, indem ODBC ordnungsgemäß implementiert und über ein einzelnes DBMS verfügbar gemacht wird.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Ist ODBC die Antwort?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Auswählen einer Interoperabilitätsebene](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Ermitteln der Ziel-DBMS und Zieltreiber](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Erwägen der zu verwendenden Datenbankfunktionen](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Länge des Produktzyklus](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Schreiben einer interoperablen Anwendung](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Testen von interoperablen Anwendungen](../../../odbc/reference/develop-app/testing-interoperable-applications.md)
