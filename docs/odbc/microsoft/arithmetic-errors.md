---
title: Arithmetische Fehler | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ab1b472540d1978a6e7a06d94da7542cc641e999
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299900"
---
# <a name="arithmetic-errors"></a>Arithmetische Fehler
Der ODBC-Treiber wertet die WHERE-Klausel in einer SELECT-Anweisung aus, während jede Zeile abgerufen wird. Wenn eine Zeile einen Wert enthält, der einen arithmetischen Fehler verursacht, z. B. Divide-by-Null oder numerischer Überlauf, gibt der Treiber alle Zeilen zurück, gibt jedoch Fehler für Spalten mit arithmetischen Fehlern zurück. Beim Einfügen oder Aktualisieren beendet der ODBC-Treiber jedoch das Einfügen oder Aktualisieren von Daten, wenn der erste Arithmetikfehler auftritt.
