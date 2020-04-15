---
title: Festlegen der Transaktionsisolationsstufe | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- isolation levels [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: 64a037f0-5065-4f45-9669-6710404a540c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 80401b276355a47469355cb6921d768d168398ae
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299810"
---
# <a name="setting-the-transaction-isolation-level"></a>Festlegen der Transaktionsisolationsstufe
Zum Festlegen der Transaktionsisolationsstufe verwendet eine Anwendung das SQL_ATTR_TXN_ISOLATION Verbindungsattribut. Wenn die Datenquelle die angeforderte Isolationsstufe nicht unterstützt, kann der Treiber oder die Datenquelle eine höhere Ebene festlegen. Um zu bestimmen, welche Transaktionsisolationsstufen eine Datenquelle unterstützt und welche Standardisolationsstufe die sorgsam ist, ruft eine Anwendung **SQLGetInfo** mit den Optionen SQL_TXN_ISOLATION_OPTION bzw. SQL_DEFAULT_TXN_ISOLATION auf.  
  
 Höhere Ebenen der Transaktionsisolation bieten den größten Schutz für die Integrität von Datenbankdaten. Serialisierbare Transaktionen werden garantiert von anderen Transaktionen nicht beeinflusst und somit garantiert die Datenbankintegrität aufrechterhalten.  
  
 Eine höhere Transaktionsisolation kann jedoch zu einer langsameren Leistung führen, da sie die Wahrscheinlichkeit erhöht, dass die Anwendung auf die Freigabe von Sperren für Daten warten muss. Eine Anwendung kann eine niedrigere Isolationsstufe angeben, um die Leistung in den folgenden Fällen zu erhöhen:  
  
-   Wenn sichergestellt werden kann, dass keine anderen Transaktionen vorhanden sind, die die Transaktionen einer Anwendung beeinträchtigen könnten. Diese Situation tritt nur unter begrenzten Umständen auf, z. B. wenn eine Person in einem kleinen Unternehmen dBASE-Dateien verwaltet, die Personaldaten auf einem Computer enthalten, und diese Dateien nicht gemeinsam mit ihnen teilt.  
  
-   Wenn Geschwindigkeit wichtiger als Genauigkeit ist und Fehler wahrscheinlich klein sind. Angenommen, ein Unternehmen macht viele kleine Umsätze und große Verkäufe sind selten. Eine Transaktion, die den Gesamtwert aller offenen Verkäufe schätzt, kann die Isolationsstufe "Nicht festschreiben" sicher verwenden. Obwohl die Transaktion Aufträge enthalten würde, die geöffnet oder geschlossen werden und anschließend zurückgesetzt werden, würden diese sich in der Regel gegenseitig abbrechen, und die Transaktion wäre viel schneller, da sie nicht jedes Mal blockiert wird, wenn sie auf einen solchen Auftrag trifft.  
  
 Weitere Informationen finden Sie unter [Optimistische Parallelität](../../../odbc/reference/develop-app/optimistic-concurrency.md).
