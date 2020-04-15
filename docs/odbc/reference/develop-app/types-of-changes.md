---
title: Arten von Änderungen | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301605"
---
# <a name="types-of-changes"></a>Änderungstypen
In ODBC *3.x* (und jeder Version von ODBC) werden drei Arten von Änderungen vorgenommen. Jeder von ihnen wirkt sich auf die Abwärtskompatibilität unterschiedlich aus und wird auf andere Weise behandelt. Diese Änderungen werden in der folgenden Tabelle beschrieben.  
  
|Art der Änderung|Beschreibung|  
|--------------------|-----------------|  
|Neue Funktionen|Dies sind Features, die für ODBC *3.x*neu sind, z. B. Out-of-Line-Bindung oder Deskriptoren. Diese werden nur implementiert, wenn die Anwendung und der Treiber sowie der Treiber-Manager der Version *3.x*sind, sodass kein Versuch unternommen wird, diese abwärtskompatibel zu machen.|  
|Duplizierte Funktionen|Dies sind Features, die in ODBC *2.x* und ODBC *3.x* vorhanden sind, aber jeweils auf unterschiedliche Weise implementiert sind. Die Funktionen **SQLAllocHandle** und **SQLAllocStmt** sind ein Beispiel. Abwärtskompatibilitätsprobleme für diese und andere duplizierte Features werden meist durch Zuordnungen im Treiber-Manager behandelt.|  
|Verhaltensänderungen|Dies sind Features, die in ODBC *2.x* und ODBC *3.x*unterschiedlich behandelt werden. Ein **Datetime-#define** ist ein Beispiel. Diese Funktionen werden vom ODBC *3.x-Treiber* basierend auf einer Umgebungsattributeinstellung verarbeitet. (Weitere Informationen finden Sie unter [Verhaltensänderungen.)](../../../odbc/reference/develop-app/behavioral-changes.md)|
