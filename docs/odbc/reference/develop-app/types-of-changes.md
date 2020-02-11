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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5f43dbf75754a16b3163bbb8e268400f34d372b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087807"
---
# <a name="types-of-changes"></a>Änderungstypen
In ODBC *3. x* (und allen Versionen von ODBC) werden drei Typen von Änderungen vorgenommen. Jede dieser Auswirkungen wirkt sich auf die Abwärtskompatibilität anders aus und wird auf andere Weise behandelt. Diese Änderungen werden in der folgenden Tabelle beschrieben.  
  
|Änderungstyp|BESCHREIBUNG|  
|--------------------|-----------------|  
|Neue Funktionen|Dabei handelt es sich um Features, die neu in ODBC *3. x*sind, z. b. out-of-Line-Bindungen oder Deskriptoren. Diese werden nur implementiert, wenn die Anwendung und der Treiber sowie der Treiber-Manager Version *3. x*haben. Daher wird nicht versucht, diese Abwärtskompatibilität herzustellen.|  
|Doppelte Features|Dabei handelt es sich um Funktionen, die in ODBC *2. x* und ODBC *3. x* vorhanden sind, aber auf unterschiedliche Weise implementiert werden. Es handelt sich um ein Beispiel für die Funktionen **sqlzuweisung CHandle** und **sqlzuweisung** . Abwärts Kompatibilitätsprobleme bei diesen und anderen doppelten Features werden größtenteils durch Zuordnungen im Treiber-Manager behandelt.|  
|Verhaltensänderungen|Dabei handelt es sich um Funktionen, die in ODBC *2. x* und ODBC *3. x*anders behandelt werden. Ein DateTime- **#define** ist ein Beispiel. Diese Features werden vom ODBC *3. x* -Treiber basierend auf einer Umgebungs Attribut Einstellung behandelt. (Weitere Informationen finden Sie unter [Verhaltensänderungen](../../../odbc/reference/develop-app/behavioral-changes.md) .)|
