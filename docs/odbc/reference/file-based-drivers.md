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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 223bd838754f1d656ac71ae37926389097af3ea1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306663"
---
# <a name="file-based-drivers"></a>Dateibasierte Treiber
Dateibasierte Treiber werden mit Datenquellen wie dBase verwendet, die keine eigenständige Datenbank-Engine für den zu verwendenden Treiber bereitstellen. Diese Treiber greifen direkt auf die physischen Daten zu und müssen eine Datenbank-Engine implementieren, um SQL-Anweisungen verarbeiten zu können. Als Standardverfahren implementieren die Datenbank-Engines in dateibasierten Treibern die Teilmenge von ODBC SQL, die durch den minimalen SQL-Konformitäts Grad definiert ist. eine Liste der SQL-Anweisungen in dieser Konformitäts Ebene finden Sie in [Anhang C: SQL-Grammatik](../../odbc/reference/appendixes/appendix-c-sql-grammar.md).  
  
 Beim Vergleichen von dateibasierten und DBMS-basierten Treibern sind dateibasierte Treiber aufgrund der Datenbank-Engine-Komponente schwieriger zu konfigurieren, da keine Netzwerk Teile vorhanden sind und weniger leistungsfähig sind, da nur wenige Personen die Zeit haben, Datenbank-Engines so leistungsstark wie die von datenbankunternehmen erstellten Daten zu schreiben.  
  
 In der folgenden Abbildung sind zwei unterschiedliche Konfigurationen von dateibasierten Treibern dargestellt: eine, in der die Daten lokal gespeichert sind, und die andere, in der Sie sich auf einem Netzwerkdatei Server befindet.  
  
 ![Zwei Konfigurationen von Datei&#45;basierten Treibern](../../odbc/reference/media/pr06.gif "pr06")
