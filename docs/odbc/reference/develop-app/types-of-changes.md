---
title: Typen von Änderungen | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f44adb59aa9b0f25475a76a97fe3670de0228c08
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301605"
---
# <a name="types-of-changes"></a>Änderungstypen
In ODBC *3. x* (und allen Versionen von ODBC) werden drei Typen von Änderungen vorgenommen. Jede dieser Auswirkungen wirkt sich auf die Abwärtskompatibilität anders aus und wird auf andere Weise behandelt. Diese Änderungen werden in der folgenden Tabelle beschrieben.  
  
|Änderungstyp|BESCHREIBUNG|  
|--------------------|-----------------|  
|Neue Funktionen|Dabei handelt es sich um Features, die neu in ODBC *3. x*sind, z. b. out-of-Line-Bindungen oder Deskriptoren. Diese werden nur implementiert, wenn die Anwendung und der Treiber sowie der Treiber-Manager Version *3. x*haben. Daher wird nicht versucht, diese Abwärtskompatibilität herzustellen.|  
|Doppelte Features|Dabei handelt es sich um Funktionen, die in ODBC *2. x* und ODBC *3. x* vorhanden sind, aber auf unterschiedliche Weise implementiert werden. Es handelt sich um ein Beispiel für die Funktionen **sqlzuweisung CHandle** und **sqlzuweisung** . Abwärts Kompatibilitätsprobleme bei diesen und anderen doppelten Features werden größtenteils durch Zuordnungen im Treiber-Manager behandelt.|  
|Verhaltensänderungen|Dabei handelt es sich um Funktionen, die in ODBC *2. x* und ODBC *3. x*anders behandelt werden. Ein DateTime- **#define** ist ein Beispiel. Diese Features werden vom ODBC *3. x* -Treiber basierend auf einer Umgebungs Attribut Einstellung behandelt. (Weitere Informationen finden Sie unter [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md) .)|
