---
title: Festlegen der Transaktions Isolationsstufe | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e59db823f8b84edfb5c92f2d142c8238449e3323
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107581"
---
# <a name="setting-the-transaction-isolation-level"></a>Festlegen der Transaktionsisolationsstufe
Zum Festlegen der Transaktions Isolationsstufe verwendet eine Anwendung das SQL_ATTR_TXN_ISOLATION-Verbindungs Attribut. Wenn die Datenquelle die angeforderte Isolationsstufe nicht unterstützt, kann der Treiber oder die Datenquelle eine höhere Ebene festlegen. Zum Ermitteln der Transaktions Isolations Stufen, die von einer Datenquelle unterstützt werden, und der Standard Isolationsstufe, ruft eine Anwendung **SQLGetInfo** mit den Optionen "SQL_TXN_ISOLATION_OPTION" und "SQL_DEFAULT_TXN_ISOLATION" auf.  
  
 Ein höheres Maß an Transaktions Isolation bietet den meisten Schutz für die Integrität von Datenbankdaten. Serialisierbare Transaktionen sind garantiert von anderen Transaktionen unberührt und gewährleisten daher die Datenbankintegrität.  
  
 Ein höheres Maß an Transaktions Isolation kann jedoch zu einer geringeren Leistung führen, da dadurch die Wahrscheinlichkeit erhöht wird, dass die Anwendung auf die Freigabe von Sperren von Daten wartet. Eine Anwendung kann eine niedrigere Isolationsstufe angeben, um die Leistung in den folgenden Fällen zu verbessern:  
  
-   Wenn gewährleistet werden kann, dass keine anderen Transaktionen vorhanden sind, die die Transaktionen einer Anwendung beeinträchtigen können. Diese Situation tritt nur in bestimmten Situationen auf, z. b. Wenn eine Person in einem kleinen Unternehmen dBASE-Dateien unterhält, die Personaldaten auf einem Computer enthalten und diese Dateien nicht gemeinsam nutzen.  
  
-   Wenn die Geschwindigkeit kritischer als die Genauigkeit ist und Fehler wahrscheinlich gering sind. Nehmen wir beispielsweise an, dass ein Unternehmen viele kleine Umsätze durchführt und dass große Umsätze selten sind. Eine Transaktion, die den Gesamtwert aller geöffneten Verkäufe schätzt, kann die Read-Isolationsstufe ohne Commit sicher verwenden. Obwohl die Transaktion Aufträge einschließen würde, die geöffnet oder geschlossen werden und anschließend ein Rollback durchgeführt wird, werden diese in der Regel gegenseitig abgebrochen, und die Transaktion wäre viel schneller, da Sie nicht jedes Mal blockiert wird, wenn eine solche Bestellung auftritt.  
  
 Weitere Informationen finden Sie unter [optimistische](../../../odbc/reference/develop-app/optimistic-concurrency.md)Parallelität.
