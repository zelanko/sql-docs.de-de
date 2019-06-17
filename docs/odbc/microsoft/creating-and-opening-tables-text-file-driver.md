---
title: Erstellen und Öffnen von Tabellen (Textdateitreiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce901e6a8639c8a2caea6e55cbaa18fedb56f4a7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63132728"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Erstellen und Öffnen von Tabellen (Textdateitreiber)
Wenn der Text-Treiber verwendet wird, wird eine neue Tabelle mit dem angegebenen Format in "Odbcinst.ini" erstellt. Wenn nicht angegeben, werden die Tabellen im CSVDELIMITED Format erstellt. Standardmäßig Spalten standardmäßig auf 11 Zeichen und FLOAT-Spalten standardmäßig 22 Zeichen. DATE-Spalten verwenden Sie das Format JJJJ-MM-TT. CHAR und LONGCHAR Spalten sind die Breite in der CREATE-Anweisung angegeben.
