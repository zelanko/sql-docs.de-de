---
title: Transaktionsunterstützung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], degree of support
ms.assetid: d56e1458-8da2-4d73-a777-09e045c30a33
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5b9d731d12329a4ef663b1ea66cdc59a0b153fa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297978"
---
# <a name="transaction-support"></a>Transaktionsunterstützung
Der Grad der Unterstützung für Transaktionen ist treiberdefiniert. ODBC wurde für die Implementierung in einer Einzelbenutzer- oder Desktopdatenbank entwickelt, die nicht mehrere Aktualisierungen ihrer Daten verwalten muss. Darüber hinaus tun einige Datenbanken, die Transaktionen unterstützen, dies nur für die DML-Anweisungen (Data Manipulation Language) von SQL. Es gibt Einschränkungen oder spezielle Transaktionssemantik in Bezug auf die Verwendung von Data Definition Language (DDL), wenn eine Transaktion aktiv ist. Das heißt, es kann Transaktionsunterstützung für mehrere gleichzeitige Aktualisierungen von Tabellen geben, aber nicht für die Änderung der Anzahl und Definition von Tabellen während einer Transaktion.  
  
 Eine Anwendung bestimmt, ob Transaktionen unterstützt werden, ob DDL in eine Transaktion einbezogen werden kann, und welche Spezialeffekte die Einbeziehung von DDL in eine Transaktion mit der Option **SQLGetInfo** mit der Option SQL_TXN_CAPABLE. Weitere Informationen finden Sie in der [SQLGetInfo-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
 Wenn der Treiber keine Transaktionen unterstützt, die Anwendung jedoch (mit einer anderen API als ODBC) Daten sperren und entsperren kann, können Anwendungen Transaktionsunterstützung erzielen, indem sie Datensätze und Tabellen bei Bedarf sperren und entsperren. Um das Kontoübertragungsbeispiel zu implementieren, sperrt die Anwendung die Datensätze für beide Konten, kopiert die aktuellen Werte, belastet das erste Konto, gutgeschrieben das zweite Konto und entsperrt die Datensätze. Wenn Schritte fehlgeschlagen sind, setzt die Anwendung die Konten mithilfe der Kopien zurück.  
  
 Selbst Datenquellen, die Transaktionen unterstützen, können möglicherweise nicht mehr als eine Transaktion gleichzeitig in einer bestimmten Umgebung unterstützen. Anwendungen rufen **SQLGetInfo** mit der Option SQL_MULTIPLE_ACTIVE_TXN auf, um zu bestimmen, ob eine Datenquelle gleichzeitig aktive Transaktionen für mehr als eine Verbindung in derselben Umgebung unterstützen kann. Da es eine Transaktion pro Verbindung gibt, ist dies nur für Anwendungen interessant, die mehrere Verbindungen mit derselben Datenquelle haben.
