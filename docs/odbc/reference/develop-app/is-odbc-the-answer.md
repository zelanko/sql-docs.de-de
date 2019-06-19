---
title: Ist ODBC die Antwort? | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], ODBC
ms.assetid: bfa5e6ee-5979-42a9-be6f-a84d1ee7a54c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f90f2395eac5dce76848d7bc309f1a3d5ce289f9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63179891"
---
# <a name="is-odbc-the-answer"></a>Ist ODBC die Antwort?
Berücksichtigen Sie dabei die Frage, Interoperabilität, die folgende Frage: Sollte die Anwendung ODBC überhaupt verwenden? Dies mag eine seltsame Frage in eine Anleitung für ODBC, aber es ist tatsächlich eine rechtmäßige. ODBC OTKLoadr können keine systemeigenen Datenbank-APIs vollständig zu ersetzen, noch der Entwicklung von bieten Zugriff auf die Datenbank in allen Fällen. Es wurde entworfen, um eine allgemeine Schnittstelle für Datenbanken bereitstellen und freigeben Anwendungsprogrammierer zu lernen und Links zu mehreren Datenbanken verwalten soll.  
  
 Benutzerdefinierte Anwendungen sind ideale Kandidaten für die systemeigenen Datenbank-APIs. Der Hauptgrund ist, dass benutzerdefinierte Anwendungen häufig mit einem einzelnen DBMS zu arbeiten und nicht interoperabel müssen. Datenbank im einheitlichen APIs möglicherweise besser funktionieren als ODBC verfügbar zu machen die Funktionen der ein bestimmtes DBMS und verfügbar machen könnten-Funktionen, die nicht von ODBC verfügbar gemacht. Da die Entwickler benutzerdefinierter Anwendungen in der Regel mit der systemeigenen Datenbank-API für ihre DBMS vertraut sind, besteht außerdem wenig Grund zum Lernen von ODBC. Es ist jedoch zu beachten, dass für einige DBMS ODBC der systemeigenen Datenbank-API ist interessant.  
  
 Welche Anwendungen sind Kandidaten für ODBC? Die besten Kandidaten sind Anwendungen, die mit mehr als ein DBMS zu arbeiten. Dies schließt praktisch alle generische und vertikale Anwendungen. Darüber hinaus eine Reihe von benutzerdefinierten Anwendungen. Benutzerdefinierte Anwendungen, die mehrere unterschiedliche DBMS-Systeme sind beispielsweise viel einfacheren und saubereren, mit ODBC als mit mehreren nativen APIs zu schreiben. Und benutzerdefinierte Anwendungen, die mit ODBC geschrieben sind viel leichter zu migrieren, wie ein Unternehmen aus einem DBMS auf einen anderen verschiebt oder die gleiche Anwendung für unterschiedliche DBMS-Systeme bereitgestellt werden.
