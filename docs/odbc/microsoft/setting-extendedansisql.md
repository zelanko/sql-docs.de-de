---
title: Festlegen von ExtendedAnsiSQL | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], setting
ms.assetid: 37b775d1-65ac-45ac-8572-454bc4e3c1a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c9b8999e229e8a6ed4804b2f06a4072d139ae93a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47818152"
---
# <a name="setting-extendedansisql"></a>Festlegen von ExtendedAnsiSQL
Das Attribut kann in der Verbindungszeichenfolge durch Hinzufügen des Attributs ExtendedAnsiSQL gesteuert werden:  
  
|value|Description|  
|-----------|-----------------|  
|ExtendedAnsiSQL = 0 (Standard)|Diese Einstellung wird die neuen Features nicht aktiviert.|  
|ExtendedAnsiSQL = 1|Diese Einstellung aktiviert, die neuen Features.|  
  
 Das Attribut kann auch festgelegt werden, in einem DSN, über die **erweiterte Optionen** im Dialogfeld, wenn Sie einen DSN über die Systemsteuerung zu konfigurieren.  
  
 Dem Attribut festlegen auf 0 deaktiviert die neuen Features; der Wert 1 aktiviert die neuen Features.  
  
 Das Attribut kann auch mithilfe von SQLSetConnectAttr() festgelegt werden. Den Wert des Attributs ist 65501 und eine SQLINTEGER-Wert von 1 oder 0 (null) festgelegt ist, wie in der obigen Tabelle beschrieben. Vor oder nach dem Herstellen einer Verbindung aufgerufen werden kann, aber es ist besser, rufen sie nach dem Herstellen einer Verbindung, da die Reihenfolge, in der die Treiber Prozesse-Verbindungsattributen und Verbindungszeichenfolgen zwischengespeichert.
