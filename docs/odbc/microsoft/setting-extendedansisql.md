---
title: Festlegen von ExtendedAnsiSQL | Microsoft Docs
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
ms.openlocfilehash: 6b5c2e4ed4d8bd64d02fb6a62861db832f6b0898
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300800"
---
# <a name="setting-extendedansisql"></a>Festlegen von ExtendedAnsiSQL
Das Attribut kann in der Verbindungszeichenfolge gesteuert werden, indem das ExtendedAnsiSQL-Attribut hinzugefügt wird:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|ExtendedAnsiSQL=0 (Standard)|Diese Einstellung aktiviert die neuen Features nicht.|  
|ExtendedAnsiSQL=1|Diese Einstellung aktiviert die neuen Funktionen.|  
  
 Das Attribut kann auch in einem DSN über das Dialogfeld **Erweiterte Optionen** festgelegt werden, wenn ein DSN über die Systemsteuerung konfiguriert wird.  
  
 Wenn Sie das Attribut auf 0 setzen, werden die neuen Features deaktiviert. Die Einstellung auf 1 ermöglicht die neuen Funktionen.  
  
 Das Attribut kann auch mit SQLSetConnectAttr() festgelegt werden. Der Attributwert ist 65501 und wird auf einen SQLINTEGER-Wert von 1 oder 0 festgelegt, wie in der vorherigen Tabelle dokumentiert. Es kann vor oder nach der Verbindung aufgerufen werden, aber es ist besser, es nach dem Herstellen einer Verbindung aufzurufen, da der Treiber zwischengespeicherte Verbindungsattribute und Verbindungszeichenfolgen verarbeitet.
