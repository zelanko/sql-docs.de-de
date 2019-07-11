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
ms.openlocfilehash: ca1b0fc2f7a1a74e1b9ab9a85baba945e4edf491
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792951"
---
# <a name="types-of-changes"></a>Änderungstypen
Drei Arten von Änderungen werden vorgenommen, in ODBC *3.x* (und alle ODBC-Version). Jeder dieser wirkt sich unterschiedlich auf Abwärtskompatibilität und in eine andere Weise behandelt wird. Diese Änderungen werden in der folgenden Tabelle beschrieben.  
  
|Typ der Änderung|Beschreibung|  
|--------------------|-----------------|  
|Neue Funktionen|Hierbei handelt es sich um neue Funktionen zu ODBC *3.x*, z. B. Out-of-Line-Bindung oder Deskriptoren. Diese implementiert werden, nur, wenn die Anwendung und Treiber als auch der Treiber-Manager, Version sind *3.x*, es gibt also keinen Versuch, diese abwärts kompatibel zu machen.|  
|Doppelte Funktionen|Hierbei handelt es sich um Funktionen, die in ODBC vorhanden *2.x* und ODBC *3.x* jedoch auf unterschiedliche Weise in den einzelnen implementiert werden. Die Funktionen **SQLAllocHandle** und **SQLAllocStmt** sind ein Beispiel. Abwärtskompatibilität für diese Probleme und andere doppelten Funktionen werden hauptsächlich von Zuordnungen im Treiber-Manager verarbeitet.|  
|Verhaltensänderungen|Hierbei handelt es sich um Funktionen, die in ODBC anders behandelt werden *2.x* und ODBC *3.x*. Ein DateTime-Wert **#define** ist ein Beispiel. Diese Funktionen werden von der ODBC behandelt *3.x* Treiber auf der Grundlage von einer umgebungseinstellung-Attribut. (Finden Sie unter [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md) für Weitere Informationen.)|
