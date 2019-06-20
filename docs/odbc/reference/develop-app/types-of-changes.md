---
title: Arten von Änderungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], types of changes
- backward compatibility [ODBC], types of changes
ms.assetid: 6a7db81a-20aa-4915-aed8-429711a36f49
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac92c6d40ea9ead6b8875e3338bb740b4bdf8523
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63473173"
---
# <a name="types-of-changes"></a>Änderungstypen
Drei Arten von Änderungen werden in ODBC 3. vorgenommen. *x* (und alle ODBC-Version). Jeder dieser wirkt sich unterschiedlich auf Abwärtskompatibilität und in eine andere Weise behandelt wird. Diese Änderungen werden in der folgenden Tabelle beschrieben.  
  
|Typ der Änderung|Beschreibung|  
|--------------------|-----------------|  
|Neue Funktionen|Hierbei handelt es sich um Funktionen, die mit ODBC 3. nicht vertraut sind. *x*, z. B. Out-of-Line-Bindung oder Deskriptoren. Diese implementiert werden, nur, wenn die Anwendung und Treiber als auch der Treiber-Manager, Version 3 sind *.x*, es gibt also keinen Versuch, diese abwärts kompatibel zu machen.|  
|Doppelte Funktionen|Hierbei handelt es sich um Funktionen, die in ODBC 2. vorhanden *.x* während ODBC 3.. *X* jedoch auf unterschiedliche Weise in den einzelnen implementiert werden. Die Funktionen **SQLAllocHandle** und **SQLAllocStmt** sind ein Beispiel. Abwärtskompatibilität für diese Probleme und andere doppelten Funktionen werden hauptsächlich von Zuordnungen im Treiber-Manager verarbeitet.|  
|Verhaltensänderungen|Hierbei handelt es sich um Funktionen, die in ODBC 2. anders behandelt werden *.x* während ODBC 3.. *X*. Ein DateTime-Wert **#define** ist ein Beispiel. Diese Funktionen werden durch die ODBC 3. verarbeitet. *x* Treiber auf der Grundlage von einer umgebungseinstellung-Attribut. (Finden Sie unter [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md) für Weitere Informationen.)|
