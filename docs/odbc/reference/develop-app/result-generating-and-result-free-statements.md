---
title: Ergebnisgenerierende und ergebnisfreie Aussagen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fc94aabd7982fba5879519573980db03b1857ef6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300090"
---
# <a name="result-generating-and-result-free-statements"></a>Anweisungen mit generiertem Ergebnis und ohne Ergebnis
SQL-Anweisungen können lose in die folgenden fünf Kategorien unterteilt werden:  
  
-   **Ergebnis-Set-Generierende Anweisungen** Dies sind SQL-Anweisungen, die ein Resultset generieren. Zum Beispiel **SELECT** eine SELECT-Anweisung.  
  
-   **Zeilenanzahlgenerierende Anweisungen** Dies sind SQL-Anweisungen, die eine Anzahl betroffener Zeilen generieren. Beispiel: eine **UPDATE-** oder **DELETE-Anweisung.**  
  
-   **DDL-Anweisungen (Data Definition Language)** Dies sind SQL-Anweisungen, die die Struktur der Datenbank ändern. Beispiel: **CREATE TABLE** oder **DROP INDEX**.  
  
-   **Kontextändernde Anweisungen** Dies sind SQL-Anweisungen, die den Kontext einer Datenbank ändern. Beispiel: **USE-** und **SET-Anweisungen** in SQL Server.  
  
-   **Administrative Erklärungen** Dies sind SQL-Anweisungen, die für administrative Zwecke in einer Datenbank verwendet werden. Beispiel: **GRANT** und **REVOKE**.  
  
 SQL-Anweisungen in den ersten beiden Kategorien werden zusammen als *ergebnisgenerierende Anweisungen*bezeichnet. SQL-Anweisungen in den letzten drei Kategorien werden kollektiv als *ergebnisfreie Anweisungen*bezeichnet. ODBC definiert die Semantik von Batches, die nur ergebnisgenerierende Anweisungen enthalten. Diese Semantik ist sehr unterschiedlich und daher datenquellenspezifisch. Der SQL Server-Treiber unterstützt z. B. das Löschen eines Objekts und das verweisen auf dasselbe Objekt oder das neu erstellen dein Objekt im gleichen Batch. Daher bezieht sich der in diesem Handbuch verwendete Begriff *Batch* nur auf Chargen von ergebnisgenerierenden Anweisungen.
