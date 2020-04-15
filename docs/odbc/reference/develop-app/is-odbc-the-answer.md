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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f3716acbcc1b8ea648b5edc03e277983936da557
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288091"
---
# <a name="is-odbc-the-answer"></a>Ist ODBC die Antwort?
Bevor Sie sich mit der Frage der Interoperabilität befassen, sollten Sie die folgende Frage berücksichtigen: Sollte die Anwendung ODBC überhaupt verwenden? Dies mag eine seltsame Frage in einem Leitfaden zu ODBC zu stellen scheinen, aber es ist in der Tat eine legitime. ODBC wurde nicht entwickelt, um systemeigene Datenbank-APIs vollständig zu ersetzen, noch wurde es entwickelt, um Datenbankzugriff unter allen Umständen bereitzustellen. Es wurde entwickelt, um eine gemeinsame Schnittstelle zu Datenbanken zu bieten und sollte Anwendungsprogrammierer davon befreien, Links zu mehreren Datenbanken zu erfahren und zu pflegen.  
  
 Benutzerdefinierte Anwendungen sind die besten Kandidaten für systemeigene Datenbank-APIs. Der Hauptgrund dafür ist, dass benutzerdefinierte Anwendungen häufig mit einem einzelnen DBMS arbeiten und nicht interoperabel sein müssen. Native Datenbank-APIs können einen besseren Job als ODBC leisten, um die Funktionen eines bestimmten DBMS verfügbar zu machen, und möglicherweise Funktionen verfügbar machen, die nicht von ODBC verfügbar gemacht werden. Da die Entwickler von benutzerdefinierten Anwendungen in der Regel mit der nativen Datenbank-API für ihr DBMS vertraut sind, gibt es wenig Grund, ODBC zu lernen. Es ist jedoch interessant festzustellen, dass ODBC für einige DBMS die native Datenbank-API ist.  
  
 Welche Bewerbungen sind also Kandidaten für ODBC? Die besten Kandidaten sind Bewerbungen, die mit mehr als einem DBMS arbeiten. Dies umfasst praktisch alle generischen und vertikalen Anwendungen. Es enthält auch eine Reihe von benutzerdefinierten Anwendungen. Beispielsweise sind benutzerdefinierte Anwendungen, die mehrere verschiedene DBMS verwenden, viel einfacher und einfacher mit ODBC zu schreiben als mit mehreren systemeigenen APIs. Und benutzerdefinierte Anwendungen, die mit ODBC geschrieben wurden, sind viel einfacher zu migrieren, wenn ein Unternehmen von einem DBMS zu einem anderen wechselt oder dieselbe Anwendung für verschiedene DBMS bereitstellt.
