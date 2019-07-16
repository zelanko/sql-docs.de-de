---
title: Abrufen der Werte in Deskriptorfeldern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 55d7017c659ca4d0b8094ed4a665d27c10b355f7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020451"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Abrufen der Werte in Deskriptorfeldern
Kann eine Anwendung aufrufen **SQLGetDescField** zum Abrufen eines einzelnen Felds aus einem anwendungsparameterdeskriptor-Datensatz. **SQLGetDescField** erhält die Anwendungszugriff, um alle deskriptorfelder, die in ODBC definiert und ebenfalls treiberdefinierten Felder.  
  
 **SQLGetDescRec** aufgerufen werden, um die Einstellungen des mehrere deskriptorfelder, die den Datentyp auswirken und Speicherung von Daten für Spalte oder Parameter abzurufen.
