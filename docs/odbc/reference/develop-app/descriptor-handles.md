---
description: Deskriptorhandles
title: Deskriptorhandles | Microsoft-Dokumentation
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
ms.openlocfilehash: 859071eacbfa65f360965cf5c5df17d4fbf6361d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476722"
---
# <a name="descriptor-handles"></a>Deskriptorhandles
Ein *Deskriptor* ist eine Auflistung von Metadaten, die die Parameter einer SQL-Anweisung oder der Spalten eines Resultsets beschreiben, wie Sie von der Anwendung oder dem Treiber (auch als *Implementierung*bezeichnet) erkannt werden. Daher kann ein Deskriptor eine beliebige von vier Rollen ausfüllen:  
  
-   **Anwendungs Parameter Deskriptor (Application Parameter Descriptor, APD).** Enthält Informationen zu den Anwendungs Puffern, die an die Parameter in einer SQL-Anweisung gebunden sind, z. b. Adressen, Längen und C-Datentypen.  
  
-   **Implementierungs Parameter Deskriptor (IPD).** Enthält Informationen zu den Parametern in einer SQL-Anweisung, z. b. SQL-Datentypen, Längen und NULL-Zulässigkeit.  
  
-   **Anwendungs Zeilen Deskriptor (ARD).** Enthält Informationen zu den Anwendungs Puffern, die an die Spalten in einem Resultset gebunden sind, z. b. Adressen, Längen und C-Datentypen.  
  
-   **Implementierungs Zeilen Deskriptor (IRD).** Enthält Informationen über die Spalten in einem Resultset, z. b. SQL-Datentypen, Längen und NULL-Zulässigkeit.  
  
 Vier Deskriptoren (eine, die jede Rolle füllt) werden automatisch zugewiesen, wenn eine-Anweisung zugeordnet wird. Diese werden als *automatisch zugeordnete Deskriptoren* bezeichnet und sind immer dieser Anweisung zugeordnet. Anwendungen können mit **SQLAllocHandle**auch Deskriptoren zuordnen. Diese werden als *explizit zugeordnete Deskriptoren*bezeichnet. Sie werden in einer Verbindung zugeordnet und können mit einer oder mehreren Anweisungen in dieser Verbindung verknüpft werden, um die Rolle eines APD oder einer ARD für diese Anweisungen zu erfüllen.  
  
 Die meisten Vorgänge in ODBC können ohne explizite Verwendung von Deskriptoren durch die Anwendung ausgeführt werden. Deskriptoren stellen jedoch eine bequeme Verknüpfung für einige Vorgänge dar. Nehmen wir beispielsweise an, dass eine Anwendung Daten aus zwei unterschiedlichen Puffer Sätzen einfügen möchte. Um den ersten Puffer Satz zu verwenden, würde er wiederholt **SQLBindParameter** aufrufen, um Sie an die Parameter in einer **Insert** -Anweisung zu binden und dann die Anweisung auszuführen. Um den zweiten Puffer Satz zu verwenden, wird dieser Vorgang wiederholt. Sie können auch Bindungen zum ersten Puffer Satz in einem Deskriptor und zum zweiten Puffer Satz in einem anderen Deskriptor einrichten. Um zwischen den Bindungs Sätzen zu wechseln, würde die Anwendung einfach **SQLSetStmtAttr** aufrufen und der Anweisung den richtigen Deskriptor als APD zuordnen.  
  
 Weitere Informationen zu Deskriptoren finden Sie unter [Typen von Deskriptoren](../../../odbc/reference/develop-app/types-of-descriptors.md).
