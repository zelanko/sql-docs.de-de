---
title: Arithmetische Fehler | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0d957d6091dc5fa29ee8a0b707c0e7fe7dfc7c8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63302038"
---
# <a name="arithmetic-errors"></a>Arithmetische Fehler
Der ODBC-Treiber die WHERE-Klausel einer SELECT-Anweisung ausgewertet wird, wie jede Zeile abgerufen. Wenn eine Zeile einen Wert enthält, der einen arithmetischen Fehler wie z. B. aufgrund einer Division durch Null "oder" numeric "Überlauf", bewirkt, dass der Treiber gibt alle Zeilen zurück, gibt jedoch Fehler für Spalten mit arithmetischen Fehlern. Beim Einfügen oder aktualisieren, beendet jedoch der ODBC-Treiber, einfügen oder Aktualisieren von Daten, wenn die erste arithmetische Fehler aufgetreten ist.
