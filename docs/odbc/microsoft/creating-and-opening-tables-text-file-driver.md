---
title: Erstellen und Öffnen von Tabellen (Textdateitreiber) | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280920"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Erstellen und Öffnen von Tabellen (Textdateitreiber)
Wenn der Texttreiber verwendet wird, wird eine neue Tabelle mit dem in Odbcinst.ini angegebenen Format erstellt. Wenn nicht angegeben, werden Tabellen im CSVDELIMITED-Format erstellt. Standardmäßig werden INTEGER-Spalten standardmäßig auf 11 Zeichen und FLOAT-Spalten standardmäßig auf 22 Zeichen. DATE-Spalten verwenden das YYYY-MM-DD-Format. CHAR- und LONGCHAR-Spalten sind die in der CREATE-Anweisung angegebene Breite.
