---
title: Erstellen und Öffnen von Tabellen (Text Datei Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae13312299f131d1957557db28bbe4db0bf7b4c7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280920"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Erstellen und Öffnen von Tabellen (Textdateitreiber)
Wenn der Text Treiber verwendet wird, wird eine neue Tabelle mit dem in "Odbcinst. ini" angegebenen Format erstellt. Wenn keine Angabe besteht, werden Tabellen im csvdelizierten Format erstellt. Standardmäßig werden ganzzahlige Spalten standardmäßig 11 Zeichen und float-Spalten standardmäßig 22 Zeichen lang angezeigt. Für Datums Spalten wird das Format yyyy-mm-dd verwendet. CHAR-und LONGCHAR-Spalten sind die in der CREATE-Anweisung angegebene Breite.
