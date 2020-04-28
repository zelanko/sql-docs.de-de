---
title: Transaktionsunterstützung | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81297978"
---
# <a name="transaction-support"></a>Transaktionsunterstützung
Der Grad der Unterstützung für Transaktionen ist Treiber definiert. ODBC ist für die Implementierung in einer Einzelbenutzer-oder Desktop Datenbank konzipiert, die nicht mehrere Datenaktualisierungen verwalten muss. Darüber hinaus tun einige Datenbanken, die Transaktionen unterstützen, dies nur für die DML-Anweisungen (Data Manipulation Language, Daten Bearbeitungs Sprache) von SQL. Es gibt Einschränkungen oder eine spezielle Transaktions Semantik in Bezug auf die Verwendung der DDL (Data Definition Language), wenn eine Transaktion aktiv ist. Das heißt, es gibt möglicherweise Transaktionsunterstützung für mehrere gleichzeitige Aktualisierungen von Tabellen, jedoch nicht zum Ändern der Anzahl und Definition von Tabellen während einer Transaktion.  
  
 Eine Anwendung bestimmt, ob Transaktionen unterstützt werden, ob DDL in eine Transaktion eingeschlossen werden kann, und alle besonderen Auswirkungen der Einbeziehung von DDL in eine Transaktion, indem **SQLGetInfo** mit der Option SQL_TXN_CAPABLE aufgerufen wird. Weitere Informationen finden Sie in der Beschreibung der [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) -Funktion.  
  
 Wenn der Treiber keine Transaktionen unterstützt, aber die Anwendung (mit einer anderen API als ODBC) zum Sperren und Entsperren von Daten verwendet werden kann, können Anwendungen Transaktionsunterstützung erzielen, indem Sie Datensätze und Tabellen nach Bedarf Sperren und entsperren. Um das Beispiel für die Konto Übertragung zu implementieren, sperrt die Anwendung die Datensätze für beide Konten, kopiert die aktuellen Werte, gibt das erste Konto aus, Gutschriften das zweite Konto und entsperrt die Datensätze. Wenn ein Fehler aufgetreten ist, würde die Anwendung die Konten mithilfe der Kopien zurücksetzen.  
  
 Sogar Datenquellen, die Transaktionen unterstützen, können in einer bestimmten Umgebung möglicherweise höchstens eine Transaktion gleichzeitig unterstützen. Anwendungen aufrufen **SQLGetInfo** mit der SQL_MULTIPLE_ACTIVE_TXN-Option, um zu bestimmen, ob eine Datenquelle gleichzeitige aktive Transaktionen für mehr als eine Verbindung in derselben Umgebung unterstützen kann. Da pro Verbindung eine Transaktion vorhanden ist, ist dies nur für Anwendungen interessant, die über mehrere Verbindungen mit derselben Datenquelle verfügen.
