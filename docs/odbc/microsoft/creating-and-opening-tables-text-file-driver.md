---
description: Erstellen und Öffnen von Tabellen (Textdateitreiber)
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
ms.openlocfilehash: c64f74270e8c2bbf4645f72406113e88948d0da9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340966"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Erstellen und Öffnen von Tabellen (Textdateitreiber)
Wenn der Text Treiber verwendet wird, wird eine neue Tabelle mit dem in Odbcinst.ini angegebenen Format erstellt. Wenn keine Angabe besteht, werden Tabellen im csvdelizierten Format erstellt. Standardmäßig werden ganzzahlige Spalten standardmäßig 11 Zeichen und float-Spalten standardmäßig 22 Zeichen lang angezeigt. Für Datums Spalten wird das Format yyyy-mm-dd verwendet. CHAR-und LONGCHAR-Spalten sind die in der CREATE-Anweisung angegebene Breite.
