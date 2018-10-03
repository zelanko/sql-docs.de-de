---
title: Dateibasierte Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 45d9203a08b9c70809e81fb3d9cf84a521017068
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47722958"
---
# <a name="file-based-drivers"></a>Dateibasierte Treiber
Dateibasierte Treiber werden mit Datenquellen wie z. B. dBASE verwendet, die keine eigenständige Datenbank-Engine für den Treiber bieten verwenden. Diese Treiber greifen Sie direkt auf die physischen Daten, und implementieren Sie eine Datenbank-Engine, SQL-Anweisungen verarbeiten müssen. Als Standardverfahren empfohlen implementieren die Datenbank-Engine in einem dateibasierten Treibern die Teilmenge von ODBC-SQL, die durch die minimale SQL-Konformitätsgrad definiert; eine Liste der SQL-Anweisungen in diesem Konformitätsgrad, finden Sie unter [Anhang C: SQL-Grammatik](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 In Vergleich von dateibasierten und DBMS-basierten Treibern sind dateibasierten Treibern zu schreiben, die aufgrund der Datenbank-Engine-Komponente, die weniger kompliziert zu konfigurieren, da es keine Netzwerk sind, und weniger leistungsfähig, da nur wenige Benutzer die Datenbank schreiben können die Module ist so leistungsfähig wie die von Datenbank-Unternehmen.  
  
 Die folgende Abbildung zeigt zwei unterschiedliche Konfigurationen von dateibasierten Treibern, 1, in dem die Daten lokal vorliegen, und die andere, in dem er sich befindet, auf einem Netzwerkserver für die Datei.  
  
 ![Zwei Konfigurationen von Datei&#45;basierte Treiber](../../odbc/reference/media/pr06.gif "pr06")
