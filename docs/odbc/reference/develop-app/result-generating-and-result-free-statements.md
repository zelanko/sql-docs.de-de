---
title: Ergebnis-Generierungs-und Ergebnis freie Anweisungen | Microsoft-Dokumentation
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
ms.openlocfilehash: 55b2ff4d428f02b59883b675fde95531366f0b4d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68020602"
---
# <a name="result-generating-and-result-free-statements"></a>Anweisungen mit generiertem Ergebnis und ohne Ergebnis
SQL-Anweisungen können lose in die folgenden fünf Kategorien unterteilt werden:  
  
-   **Resultset-generierende Anweisungen** Dies sind SQL-Anweisungen, die ein Resultset generieren. Beispielsweise eine **Select** -Anweisung.  
  
-   **Zeilen Anzahl-generierende Anweisungen** Dabei handelt es sich um SQL-Anweisungen, die die Anzahl der betroffenen Zeilen generieren. Beispielsweise eine **Update** -oder **Delete** -Anweisung.  
  
-   **DDL-Anweisungen (Data Definition Language)** Dabei handelt es sich um SQL-Anweisungen, die die Struktur der Datenbank ändern. Beispielsweise **CREATE TABLE** oder **Drop Index**.  
  
-   **Kontextwechsel Anweisungen** Dabei handelt es sich um SQL-Anweisungen, die den Kontext einer Datenbank ändern. Beispielsweise werden die **use** -Anweisung und die **set** -Anweisung in SQL Server.  
  
-   **Administrative Anweisungen** Dabei handelt es sich um SQL-Anweisungen, die zu Verwaltungszwecken in einer Datenbank verwendet werden Beispielsweise **Grant** und **Widerruf**.  
  
 SQL-Anweisungen in den ersten beiden Kategorien werden zusammen als *Ergebnis generierende Anweisungen*bezeichnet. SQL-Anweisungen in den letzten drei Kategorien werden zusammen als *Ergebnis freie Anweisungen*bezeichnet. ODBC definiert die Semantik von Batches, die nur Ergebnis generierende Anweisungen enthalten. Diese Semantik variiert stark und ist daher Datenquellen spezifisch. Beispielsweise unterstützt der SQL Server Treiber das Löschen eines Objekts und das anschließende verweisen auf das gleiche Objekt im gleichen Batch nicht. Daher bezieht sich der Begriff *Batch* , wie er in diesem manuellen verwendet wird, nur auf Batches von Ergebnis Generierungs Anweisungen.
