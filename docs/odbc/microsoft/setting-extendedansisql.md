---
description: Festlegen von ExtendedAnsiSQL
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5a2d739a3093b0d1e806bc9aa3f8d136746954c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88412446"
---
# <a name="setting-extendedansisql"></a>Festlegen von ExtendedAnsiSQL
Das-Attribut kann in der Verbindungs Zeichenfolge durch Hinzufügen des extendedansisql-Attributs gesteuert werden:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|Extendedansisql = 0 (Standard)|Diese Einstellung aktiviert nicht die neuen Funktionen.|  
|Extendedansisql = 1|Diese Einstellung aktiviert die neuen Funktionen.|  
  
 Das-Attribut kann auch im Dialogfeld **Erweiterte Optionen** in einem DSN festgelegt werden, wenn ein DSN über die Systemsteuerung konfiguriert wird.  
  
 Wenn Sie das-Attribut auf 0 festlegen, werden die neuen Funktionen deaktiviert. Wenn Sie auf 1 festlegen, werden die neuen Funktionen aktiviert.  
  
 Das-Attribut kann auch mithilfe von SQLSetConnectAttr () festgelegt werden. Der-Attribut Wert ist 65501, und wird auf einen SQLINTEGER-Wert von 1 oder 0 festgelegt, wie in der obigen Tabelle dokumentiert. Sie kann vor oder nach dem Herstellen der Verbindung aufgerufen werden, aber es ist besser, Sie nach dem Herstellen der Verbindung aufzurufen, da der Treiber zwischengespeicherte Verbindungs Attribute und Verbindungs Zeichenfolgen verarbeitet.
