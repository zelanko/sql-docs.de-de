---
description: Ist ODBC die Antwort?
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7a51c4248a041d65f00ec1846f60788cded68f7b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476602"
---
# <a name="is-odbc-the-answer"></a>Ist ODBC die Antwort?
Bevor Sie sich mit der Frage der Interoperabilität befassen, berücksichtigen Sie die folgende Frage: sollte die Anwendung ODBC überhaupt verwenden? Dies mag eine merkwürdige Frage in einem Leitfaden zu ODBC sein, aber es ist tatsächlich eine legitime Frage. ODBC wurde nicht zum vollständigen ersetzen der systemeigenen Datenbank-APIs entworfen, und wurde nicht für die Bereitstellung von Datenbankzugriff in allen Fällen konzipiert. Es wurde entwickelt, um eine gemeinsame Schnittstelle für Datenbanken bereitzustellen, die es den Anwendungs Programmierern erleichtern soll, sich über Links zu mehreren Datenbanken zu informieren und diese beizubehalten.  
  
 Benutzerdefinierte Anwendungen sind Hauptkandidaten für Native Datenbank-APIs. Der Hauptgrund ist, dass benutzerdefinierte Anwendungen häufig mit einem einzelnen DBMS funktionieren und nicht interoperabel sein müssen. Native Datenbank-APIs können besser funktionieren als ODBC, um die Funktionen eines bestimmten DBMS verfügbar zu machen, und möglicherweise Funktionen verfügbar machen, die nicht von ODBC verfügbar gemacht werden. Da die Entwickler von benutzerdefinierten Anwendungen in der Regel mit der systemeigenen Datenbank-API für Ihr DBMS vertraut sind, gibt es kaum einen Grund, ODBC zu erlernen. Es ist jedoch interessant zu beachten, dass bei einigen DBMSs ODBC die native Database-API ist.  
  
 Welche Anwendungen sind also Kandidaten für ODBC? Die besten Kandidaten sind Anwendungen, die mit mehr als einem DBMS funktionieren. Dies umfasst praktisch alle allgemeinen und vertikalen Anwendungen. Es umfasst auch eine Reihe von benutzerdefinierten Anwendungen. Beispielsweise sind benutzerdefinierte Anwendungen, die mehrere verschiedene DBMSs verwenden, viel einfacher und leichter mit ODBC zu schreiben als mit mehreren nativen APIs. Benutzerdefinierte Anwendungen, die mit ODBC geschrieben wurden, sind viel leichter zu migrieren, wenn ein Unternehmen von einem DBMS zu einem anderen wechselt oder die gleiche Anwendung für andere DBMSs bereitstellt.
