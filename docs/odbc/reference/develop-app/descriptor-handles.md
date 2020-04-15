---
title: Deskriptor-Griffe | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application parameter descriptor [ODBC]
- automatically allocated descriptors [ODBC]
- implementation row descriptor [ODBC]
- descriptor handles [ODBC]
- handles [ODBC], descriptor
- implementation parameter descriptor [ODBC]
- apd [ODBC]
- ard [ODBC]
- explicitly allocated descriptors [ODBC]
- ipd [ODBC]
- ird [ODBC]
- application row descriptor [ODBC]
ms.assetid: 7741035c-f3e7-4c89-901e-fe528392f67d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ed0595c97f3f4ad92d976c89327a01e25cb5b753
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305911"
---
# <a name="descriptor-handles"></a>Deskriptorhandles
Ein *Deskriptor* ist eine Sammlung von Metadaten, die die Parameter einer SQL-Anweisung oder die Spalten eines Resultsets beschreibt, wie von der Anwendung oder dem Treiber (auch als *Implementierung*bezeichnet) angezeigt wird. Somit kann ein Deskriptor eine der vier Rollen ausfüllen:  
  
-   **Anwendungsparameterdeskriptor (APD).** Enthält Informationen zu den Anwendungspuffern, die an die Parameter in einer SQL-Anweisung gebunden sind, z. B. deren Adressen, Längen und C-Datentypen.  
  
-   **Implementierungsparameterdeskriptor (IPD).** Enthält Informationen zu den Parametern in einer SQL-Anweisung, z. B. ihre SQL-Datentypen, -Längen und NULL-Werte.  
  
-   **Application Row Descriptor (ARD).** Enthält Informationen zu den Anwendungspuffern, die an die Spalten in einer Resultmenge gebunden sind, z. B. deren Adressen, Längen und C-Datentypen.  
  
-   **Implementierungszeilendeskriptor (IRD).** Enthält Informationen zu den Spalten in einem Resultset, z. B. IHRE SQL-Datentypen, -Längen und NULL-Zulässigkeit.  
  
 Vier Deskriptoren (eine füllt jede Rolle aus) werden automatisch zugewiesen, wenn eine Anweisung zugewiesen wird. Diese werden als *automatisch zugewiesene Deskriptoren* bezeichnet und sind dieser Anweisung immer zugeordnet. Anwendungen können auch Deskriptoren mit **SQLAllocHandle**zuweisen. Diese werden als *explizit zugewiesene Deskriptoren*bezeichnet. Sie werden auf einer Verbindung zugeordnet und können mit einer oder mehreren Aussagen zu diesem Zusammenhang in Verbindung gebracht werden, um die Rolle einer APD oder ARD zu diesen Aussagen zu erfüllen.  
  
 Die meisten Operationen in ODBC können ohne explizite Verwendung von Deskriptoren durch die Anwendung ausgeführt werden. Deskriptoren stellen jedoch eine praktische Verknüpfung für einige Vorgänge bereit. Angenommen, eine Anwendung möchte Daten aus zwei verschiedenen Puffersätzen einfügen. Um den ersten Satz von Puffern zu verwenden, würde es wiederholt **SQLBindParameter** aufrufen, um sie an die Parameter in einer **INSERT-Anweisung** zu binden und dann die Anweisung auszuführen. Um den zweiten Satz von Puffern zu verwenden, würde dieser Vorgang wiederholt. Alternativ können Bindungen für den ersten Satz von Puffern in einem Deskriptor und für den zweiten Satz von Puffern in einem anderen Deskriptor eingerichtet werden. Um zwischen den Bindungssätzen zu wechseln, würde die Anwendung einfach **SQLSetStmtAttr** aufrufen und die richtige Deskriptorin der Anweisung als APD zuordnen.  
  
 Weitere Informationen zu Deskriptoren finden Sie unter [Deskriptorentypen](../../../odbc/reference/develop-app/types-of-descriptors.md).
