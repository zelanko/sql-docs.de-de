---
title: Kopieren von Deskriptoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], copying
- copying descriptors [ODBC]
ms.assetid: 949a860d-6579-4218-882e-8c061688dd87
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7d41cd744d39113c556c4ee8bc17411b7992e596
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68002142"
---
# <a name="copying-descriptors"></a>Kopieren von Deskriptoren
Die **sqlcopydebug** -Funktion wird aufgerufen, um die Felder von einem Deskriptor in einen anderen Deskriptor zu kopieren. Felder können nur in einen Anwendungs Deskriptor oder eine IPD, aber nicht in einen IRD kopiert werden. Felder können von jedem Deskriptortyp kopiert werden. Nur die Felder, die sowohl für die Quell-als auch die Ziel Deskriptoren definiert sind, werden kopiert. **SQLCopyDesc** kopiert das SQL_DESC_ALLOC_TYPE Feld nicht, da der Zuordnungstyp eines Deskriptors nicht geändert werden kann. Kopierte Felder überschreiben die vorhandenen Felder.  
  
 Ein ARD für ein Anweisungs Handle kann als APD für ein anderes Anweisungs Handle fungieren. Dies ermöglicht es einer Anwendung, Zeilen zwischen Tabellen zu kopieren, ohne Daten auf Anwendungsebene zu kopieren. Zu diesem Zweck wird ein Zeilen Deskriptor, der eine abgerufene Zeile einer Tabelle beschreibt, als Parameter Deskriptor für einen Parameter in einer INSERT-Anweisung wieder verwendet. Der SQL_MAX_CONCURRENT_ACTIVITIES Informationstyp muss größer als 1 sein, damit dieser Vorgang erfolgreich ausgeführt wird.
