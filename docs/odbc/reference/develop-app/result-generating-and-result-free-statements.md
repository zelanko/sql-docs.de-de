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
ms.openlocfilehash: e38e17ac469ec0685f11d7dfde587f36073fb970
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706908"
---
# <a name="result-generating-and-result-free-statements"></a>Anweisungen mit generiertem Ergebnis und ohne Ergebnis
SQL-Anweisungen können lose in den folgenden fünf Kategorien unterteilt werden:  
  
-   **Führen Sie die Anweisungen Set generiert** Hierbei handelt es sich um SQL-Anweisungen, die ein Resultset generieren. Z. B. eine **wählen** Anweisung.  
  
-   **Row Count-generieren Anweisungen** Hierbei handelt es sich um SQL-Anweisungen, die Anzahl der betroffenen Zeilen zu generieren. Z. B. eine **UPDATE** oder **löschen** Anweisung.  
  
-   **Anweisungen der Data Definition Language (DDL)** Hierbei handelt es sich um SQL-Anweisungen, die die Struktur der Datenbank zu ändern. Z. B. **CREATE TABLE** oder **DROP INDEX**.  
  
-   **Ändern von Kontext Anweisungen** Hierbei handelt es sich um SQL-Anweisungen, die den Kontext einer Datenbank zu ändern. Z. B. die **verwenden** und **festgelegt** Anweisungen in SQL Server.  
  
-   **Verwaltungsanweisungen** Hierbei handelt es sich um SQL-Anweisungen, die für administrative Zwecke in einer Datenbank verwendet. Z. B. **GRANT** und **widerrufen**.  
  
 SQL-Anweisungen in den ersten beiden Kategorien werden zusammen als bezeichnet *Anweisungen mit generiertem*. SQL-Anweisungen in den letzten drei Kategorien werden zusammen als bezeichnet *Ergebnis kostenfreie Anweisungen*. ODBC definiert die Semantik des Batches, die nur aus dem Ergebnis generieren Anweisungen enthalten. Diese Semantik stark variieren und sind daher Daten datenquellenspezifischen. Beispielsweise unterstützt der SQL Server-Treiber nicht, ein Objekt löschen und verweisen auf oder das gleiche Objekt im selben Batch neu zu erstellen. Daher der Begriff *Batch* als im bezieht sich dieses Handbuch nur für Batches von generiertem Anweisungen.
