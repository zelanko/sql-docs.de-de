---
description: Kopieren von Deskriptoren
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90f3acb5ccb479ba5c1d1eb4c405a486f7032f3f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465866"
---
# <a name="copying-descriptors"></a>Kopieren von Deskriptoren
Die **sqlcopydebug** -Funktion wird aufgerufen, um die Felder von einem Deskriptor in einen anderen Deskriptor zu kopieren. Felder können nur in einen Anwendungs Deskriptor oder eine IPD, aber nicht in einen IRD kopiert werden. Felder können von jedem Deskriptortyp kopiert werden. Nur die Felder, die sowohl für die Quell-als auch die Ziel Deskriptoren definiert sind, werden kopiert. **SQLCopyDesc** kopiert das SQL_DESC_ALLOC_TYPE Feld nicht, da der Zuordnungstyp eines Deskriptors nicht geändert werden kann. Kopierte Felder überschreiben die vorhandenen Felder.  
  
 Ein ARD für ein Anweisungs Handle kann als APD für ein anderes Anweisungs Handle fungieren. Dies ermöglicht es einer Anwendung, Zeilen zwischen Tabellen zu kopieren, ohne Daten auf Anwendungsebene zu kopieren. Zu diesem Zweck wird ein Zeilen Deskriptor, der eine abgerufene Zeile einer Tabelle beschreibt, als Parameter Deskriptor für einen Parameter in einer INSERT-Anweisung wieder verwendet. Der SQL_MAX_CONCURRENT_ACTIVITIES Informationstyp muss größer als 1 sein, damit dieser Vorgang erfolgreich ausgeführt wird.
