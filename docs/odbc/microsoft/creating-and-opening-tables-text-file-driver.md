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
ms.openlocfilehash: b36c02d772682088a799cfca66f5bbf3e169a67f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096544"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Erstellen und Öffnen von Tabellen (Textdateitreiber)
Wenn der Text-Treiber verwendet wird, wird eine neue Tabelle mit dem angegebenen Format in "Odbcinst.ini" erstellt. Wenn nicht angegeben, werden die Tabellen im CSVDELIMITED Format erstellt. Standardmäßig Spalten standardmäßig auf 11 Zeichen und FLOAT-Spalten standardmäßig 22 Zeichen. DATE-Spalten verwenden Sie das Format JJJJ-MM-TT. CHAR und LONGCHAR Spalten sind die Breite in der CREATE-Anweisung angegeben.
