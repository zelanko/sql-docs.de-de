---
title: Festlegen von extendedansisql | Microsoft-Dokumentation
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
ms.openlocfilehash: 330b55ef2d4fee090c453990d3fe75e6e2dacb6f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68063599"
---
# <a name="setting-extendedansisql"></a>Festlegen von ExtendedAnsiSQL
Das-Attribut kann in der Verbindungs Zeichenfolge durch Hinzufügen des extendedansisql-Attributs gesteuert werden:  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|Extendedansisql = 0 (Standard)|Diese Einstellung aktiviert nicht die neuen Funktionen.|  
|Extendedansisql = 1|Diese Einstellung aktiviert die neuen Funktionen.|  
  
 Das-Attribut kann auch im Dialogfeld **Erweiterte Optionen** in einem DSN festgelegt werden, wenn ein DSN über die Systemsteuerung konfiguriert wird.  
  
 Wenn Sie das-Attribut auf 0 festlegen, werden die neuen Funktionen deaktiviert. Wenn Sie auf 1 festlegen, werden die neuen Funktionen aktiviert.  
  
 Das-Attribut kann auch mithilfe von SQLSetConnectAttr () festgelegt werden. Der-Attribut Wert ist 65501, und wird auf einen SQLINTEGER-Wert von 1 oder 0 festgelegt, wie in der obigen Tabelle dokumentiert. Sie kann vor oder nach dem Herstellen der Verbindung aufgerufen werden, aber es ist besser, Sie nach dem Herstellen der Verbindung aufzurufen, da der Treiber zwischengespeicherte Verbindungs Attribute und Verbindungs Zeichenfolgen verarbeitet.
