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
manager: craigg
ms.openlocfilehash: da22ba86ea49532f460b081b13e18d6b7d95211c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63042756"
---
# <a name="copying-descriptors"></a>Kopieren von Deskriptoren
Die **SQLCopyDesc** Funktion wird aufgerufen, um die Felder der einen Deskriptor auf einem anderen Deskriptor zu kopieren. Felder können nur für einen Anwendungsdienst-Deskriptor oder einem IPD, aber nicht für eine IRD kopiert werden. Felder können von jeder Art von Deskriptor kopiert werden. Nur die Felder, die für die Quell- und Zieldateien Deskriptoren definiert sind, werden kopiert. **SQLCopyDesc** Feld SQL_DESC_ALLOC_TYPE wird nicht kopiert werden, da ein Deskriptor der Zuordnungstyp nicht geändert werden kann. Kopierte Felder überschreiben die vorhandenen Felder.  
  
 Ein ARD für ein Anweisungshandle kann als APD auf ein anderes Anweisungshandle dienen. Dies kann es sich um eine Anwendung, um Zeilen zwischen den Tabellen ohne Kopieren von Daten auf Anwendungsebene zu kopieren. Zu diesem Zweck wird ein Zeile Deskriptor, der eine abgerufene Zeile einer Tabelle wird beschrieben, wie ein Parameterdeskriptor für einen Parameter in einer INSERT-Anweisung wiederverwendet. Der Informationstyp SQL_MAX_CONCURRENT_ACTIVITIES muss größer als 1 für diesen Vorgang erfolgreich ausgeführt werden kann.
