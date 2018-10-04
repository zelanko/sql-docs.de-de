---
title: Festlegen der Transaktionsisolation | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 37b575f9e208b5a1b7fa03b170b74633da149c67
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750618"
---
# <a name="setting-the-transaction-isolation-level"></a>Festlegen der Transaktionsisolationsstufe
Zum Festlegen der Isolationsstufe für Transaktionen verwendet eine Anwendung das Verbindungsattribut SQL_ATTR_TXN_ISOLATION. Wenn die Datenquelle die angeforderte Isolationsstufe nicht unterstützt, kann die Treiber oder die Datenquelle eine höhere Ebene festlegen. Um zu bestimmen, welche Transaktionsisolationsstufen wird eine Datenquelle unterstützt, und welche die Standardisolationsstufe ist, eine Anwendung ruft **SQLGetInfo** mit den Optionen dem SQL_TXN_ISOLATION_OPTION und SQL_DEFAULT_TXN_ISOLATION bzw.  
  
 Höhere Stufen der Transaktionsisolation bieten die größtmöglichen Schutz für die Integrität von Datenbankdaten. Serializable-Transaktionen sind immer durch andere Transaktionen nicht betroffen, und daher unbedingt die Datenbankintegrität zu verwalten.  
  
 Allerdings kann ein höheres Maß an Isolation jeder Transaktion Leistungseinbußen führen, da die Wahrscheinlichkeit erhöht, die die Anwendung auf Daten freigegeben werden Sperren gewartet wird. Eine Anwendung kann auf eine niedrigere Ebene der Isolation zum Erhöhen der Leistung in den folgenden Fällen angeben:  
  
-   Wenn garantiert werden kann, dass, die keine anderen Transaktionen vorhanden sind kann Transaktionen von einer Anwendung beeinträchtigen. Diese Situation tritt nur unter bestimmten Umständen, z. B. wenn eine Person in einem kleinen Unternehmen dBASE-Dateien verwaltet, die persönliche Daten auf einem Computer enthalten und diese Dateien wird nicht freigegeben.  
  
-   Wenn Geschwindigkeit ist wichtiger als die Genauigkeit und ggf. aufgetretenen Fehlern wahrscheinlich klein sein werden. Nehmen wir beispielsweise an, dass ein Unternehmen viele kleine Verkäufe macht und große Sales selten sind. Eine Transaktion, die den Gesamtwert aller geöffneten Sales schätzt können problemlos die Isolationsstufe Read Uncommitted. Obwohl die Transaktion Bestellungen enthalten würde, die geöffnet oder geschlossen und anschließend werden ein Rollback diese würden in der Regel heben sich gegenseitig und die Transaktion wäre viel schneller, weil er nicht blockiert wird, jedes Mal, wenn die It solche eine Bestellung auftritt.  
  
 Weitere Informationen finden Sie unter [optimistische Parallelität](../../../odbc/reference/develop-app/optimistic-concurrency.md).
