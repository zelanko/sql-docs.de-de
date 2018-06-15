---
title: Erstellen und Öffnen von Tabellen (Text-Datei-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], creating and opening tables
ms.assetid: e6a07dda-a665-4f5b-a8d6-9ff479700513
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b836fa5144ffb59a155eed150f3372385d808343
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32899625"
---
# <a name="creating-and-opening-tables-text-file-driver"></a>Erstellen und Öffnen von Tabellen (Text-Datei-Treiber)
Wenn der Text-Treiber verwendet wird, wird eine neue Tabelle erstellt, mit dem Format, das in "Odbcinst.ini" angegeben. Wenn nicht angegeben, werden die Tabellen in CSVDELIMITED Format erstellt. Standardmäßig Ganzzahlspalten standardmäßig 11 Zeichen und "float" Standardspalten bis 22 Zeichen. Datumsspalten verwenden Sie das Format JJJJ-MM-TT. CHAR und LONGCHAR Spalten sind die Breite, die in der CREATE-Anweisung angegeben.
