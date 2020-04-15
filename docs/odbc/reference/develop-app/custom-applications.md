---
title: Benutzerdefinierte Anwendungen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], custom applications
- custom applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: f28178d9-ecd6-4e8c-9644-9bb624999dcb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df00a748ee4d5e3a63b32c95449417a1057b58e1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305281"
---
# <a name="custom-applications"></a>Benutzerdefinierte Anwendungen
Benutzerdefinierte Anwendungen führen in der Regel eine bestimmte Aufgabe für einige DBMS aus. Beispielsweise kann eine Anwendung Daten von einem einzelnen DBMS abrufen und einen Bericht generieren oder Daten zwischen mehreren DBMS übertragen. Gemeinsam ist diesen Anwendungen, dass diese DBMS vor der Ablage bekannt sind und sich während der Lebensdauer der Anwendung wahrscheinlich nicht ändern werden.  
  
 Die benutzerdefinierte Anwendung erfordert daher wenig oder keine Interoperabilität. Der Anwendungsentwickler kann für jedes DBMS einen einzelnen Treiber auswählen und direkt für diese Treiber codeen. Die Anwendung kann sicher treiberspezifischen Code enthalten, um die Funktionen dieser Treiber auszunutzen, und sogar Aufrufe an die systemeigene Datenbank-API tätigen, um Funktionen zu verwenden, die von ODBC nicht unterstützt werden.  
  
 Das Hauptanliegen der meisten benutzerdefinierten Anwendungen ist, ob sich die Ziel-DBMS in Zukunft ändern werden. Wenn dies der Zuzug ist, kann dieser Prozess vereinfacht werden, indem zunächst mehr interoperabler Code geschrieben wird. Eine solche Veränderung der DBMS ist jedoch selten und erfordert in der Regel einen hohen Arbeitsaufwand. Aus diesem Grund entscheiden sich Entwickler von benutzerdefinierten Anwendungen selten dafür, die Interoperabilität auf Kosten der Funktionalität zu erhöhen. Sie entscheiden sich in der Regel dafür, diese Funktionalität neu zu codieren, wenn sie DBMS ändern.
