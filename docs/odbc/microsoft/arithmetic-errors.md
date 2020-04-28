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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ab1b472540d1978a6e7a06d94da7542cc641e999
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299900"
---
# <a name="arithmetic-errors"></a>Arithmetische Fehler
Der ODBC-Treiber wertet die WHERE-Klausel in einer SELECT-Anweisung aus, während er jede Zeile abruft. Wenn eine Zeile einen Wert enthält, der einen arithmetischen Fehler verursacht, z. b. einen Division durch 0 (null) oder einen numerischen Überlauf, gibt der Treiber alle Zeilen zurück, gibt jedoch Fehler für Spalten mit arithmetischen Fehlern zurück. Beim Einfügen oder aktualisieren beendet der ODBC-Treiber jedoch das Einfügen oder Aktualisieren von Daten, wenn der erste arithmetische Fehler auftritt.
