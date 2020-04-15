---
title: Dateibasierte Treiber | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 223bd838754f1d656ac71ae37926389097af3ea1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306663"
---
# <a name="file-based-drivers"></a>Dateibasierte Treiber
Dateibasierte Treiber werden mit Datenquellen wie dBASE verwendet, die kein eigenständiges Datenbankmodul für den treiberischen Treiber bereitstellen. Diese Treiber greifen direkt auf die physischen Daten zu und müssen ein Datenbankmodul implementieren, um SQL-Anweisungen zu verarbeiten. Standardmäßig implementieren die Datenbankmodule in dateibasierten Treibern die Teilmenge von ODBC SQL, die durch die Mindestsql-Konformitätsstufe definiert ist. Eine Liste der SQL-Anweisungen in dieser Konformitätsebene finden Sie unter [Anhang C: SQL Grammar](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Beim Vergleich dateibasierter und DBMS-basierter Treiber sind dateibasierte Treiber aufgrund der Datenbankmodulkomponente schwieriger zu schreiben, weniger kompliziert zu konfigurieren, da keine Netzwerkteile vorhanden sind, und weniger leistungsfähig, da nur wenige Benutzer die Zeit haben, Datenbankmodule so leistungsfähig zu schreiben wie die von Datenbankunternehmen produzierten.  
  
 Die folgende Abbildung zeigt zwei verschiedene Konfigurationen dateibasierter Treiber, eine, in der sich die Daten lokal befinden, und die andere, in der sie sich auf einem Netzwerkdateiserver befinden.  
  
 ![Zwei Konfigurationen von dateibasierten&#45;-basierten Treibern](../../odbc/reference/media/pr06.gif "pr06")
