---
title: Kopieren von Deskriptoren | Microsoft Docs
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
ms.openlocfilehash: 2e2e5897afc3673a21396e256df04d25008c8cdf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301669"
---
# <a name="copying-descriptors"></a>Kopieren von Deskriptoren
Die **SQLCopyDesc-Funktion** wird aufgerufen, um die Felder eines Deskriptors in einen anderen Deskriptor zu kopieren. Felder können nur in einen Anwendungsdeskriptor oder eine IPD kopiert werden, nicht jedoch in eine IRD. Felder können aus jedem Deskriptortyp kopiert werden. Es werden nur die Felder kopiert, die sowohl für die Quell- als auch für die Zieldeskriptoren definiert sind. **SQLCopyDesc** kopiert das Feld SQL_DESC_ALLOC_TYPE nicht, da der Zuordnungstyp eines Deskriptors nicht geändert werden kann. Kopierte Felder überschreiben die vorhandenen Felder.  
  
 Ein ARD-Anweisungshandle kann als APD für einen anderen Statement-Handle dienen. Dadurch kann eine Anwendung Zeilen zwischen Tabellen kopieren, ohne Daten auf Anwendungsebene zu kopieren. Zu diesem Tun wird ein Zeilendeskriptor, der eine abgerufene Zeile einer Tabelle beschreibt, als Parameterdeskriptor für einen Parameter in einer INSERT-Anweisung wiederverwendet. Der SQL_MAX_CONCURRENT_ACTIVITIES Informationstyp muss größer als 1 sein, damit dieser Vorgang erfolgreich ausgeführt werden kann.
