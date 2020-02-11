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
ms.openlocfilehash: 2e0880e1746b4b65070fb28bf8d83aadec301aa4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138178"
---
# <a name="arithmetic-errors"></a>Arithmetische Fehler
Der ODBC-Treiber wertet die WHERE-Klausel in einer SELECT-Anweisung aus, während er jede Zeile abruft. Wenn eine Zeile einen Wert enthält, der einen arithmetischen Fehler verursacht, z. b. einen Division durch 0 (null) oder einen numerischen Überlauf, gibt der Treiber alle Zeilen zurück, gibt jedoch Fehler für Spalten mit arithmetischen Fehlern zurück. Beim Einfügen oder aktualisieren beendet der ODBC-Treiber jedoch das Einfügen oder Aktualisieren von Daten, wenn der erste arithmetische Fehler auftritt.
