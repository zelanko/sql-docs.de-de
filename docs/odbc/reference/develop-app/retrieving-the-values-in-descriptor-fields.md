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
manager: craigg
ms.openlocfilehash: ae95160a11a965e47845726748c2b9449a819e8a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63284963"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Abrufen der Werte in Deskriptorfeldern
Kann eine Anwendung aufrufen **SQLGetDescField** zum Abrufen eines einzelnen Felds aus einem anwendungsparameterdeskriptor-Datensatz. **SQLGetDescField** erhält die Anwendungszugriff, um alle deskriptorfelder, die in ODBC definiert und ebenfalls treiberdefinierten Felder.  
  
 **SQLGetDescRec** aufgerufen werden, um die Einstellungen des mehrere deskriptorfelder, die den Datentyp auswirken und Speicherung von Daten für Spalte oder Parameter abzurufen.
