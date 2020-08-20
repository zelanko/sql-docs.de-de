---
description: Arithmetische Fehler
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
ms.openlocfilehash: 3e2fa142b43f1e96693390f777c90ea6f10705f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500403"
---
# <a name="arithmetic-errors"></a>Arithmetische Fehler
Der ODBC-Treiber wertet die WHERE-Klausel in einer SELECT-Anweisung aus, während er jede Zeile abruft. Wenn eine Zeile einen Wert enthält, der einen arithmetischen Fehler verursacht, z. b. einen Division durch 0 (null) oder einen numerischen Überlauf, gibt der Treiber alle Zeilen zurück, gibt jedoch Fehler für Spalten mit arithmetischen Fehlern zurück. Beim Einfügen oder aktualisieren beendet der ODBC-Treiber jedoch das Einfügen oder Aktualisieren von Daten, wenn der erste arithmetische Fehler auftritt.
