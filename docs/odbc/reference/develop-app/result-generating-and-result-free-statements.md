---
title: Generiertem Ergebnis und ohne Ergebnis Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result-generating statements [ODBC]
- batches [ODBC], result-generating statements
- batches [ODBC], result-free statements
- SQL statements [ODBC], batches
- result-free statements [ODBC]
ms.assetid: 2f3475d1-3999-4dd8-aba2-a6e1299c95f8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f357576e9e7510ae581b41a50976a34981f35109
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861520"
---
# <a name="result-generating-and-result-free-statements"></a>Anweisungen mit generiertem Ergebnis und ohne Ergebnis
SQL-Anweisungen können lose in den folgenden fünf Kategorien unterteilt werden:  
  
-   **Führen Sie die Anweisungen Set generiert** Hierbei handelt es sich um SQL-Anweisungen, die ein Resultset generieren. Z. B. eine **wählen** Anweisung.  
  
-   **Row Count-generieren Anweisungen** Hierbei handelt es sich um SQL-Anweisungen, die Anzahl der betroffenen Zeilen zu generieren. Z. B. eine **UPDATE** oder **löschen** Anweisung.  
  
-   **Anweisungen der Data Definition Language (DDL)** Hierbei handelt es sich um SQL-Anweisungen, die die Struktur der Datenbank zu ändern. Z. B. **CREATE TABLE** oder **DROP INDEX**.  
  
-   **Ändern von Kontext Anweisungen** Hierbei handelt es sich um SQL-Anweisungen, die den Kontext einer Datenbank zu ändern. Z. B. die **verwenden** und **festgelegt** Anweisungen in SQL Server.  
  
-   **Verwaltungsanweisungen** Hierbei handelt es sich um SQL-Anweisungen, die für administrative Zwecke in einer Datenbank verwendet. Z. B. **GRANT** und **widerrufen**.  
  
 SQL-Anweisungen in den ersten beiden Kategorien werden zusammen als bezeichnet *Anweisungen mit generiertem*. SQL-Anweisungen in den letzten drei Kategorien werden zusammen als bezeichnet *Ergebnis kostenfreie Anweisungen*. ODBC definiert die Semantik des Batches, die nur aus dem Ergebnis generieren Anweisungen enthalten. Diese Semantik stark variieren und sind daher Daten datenquellenspezifische. Beispielsweise unterstützt der SQL Server-Treiber nicht, ein Objekt löschen und verweisen auf oder das gleiche Objekt im selben Batch neu zu erstellen. Daher der Begriff *Batch* als im bezieht sich dieses Handbuch nur für Batches von generiertem Anweisungen.
