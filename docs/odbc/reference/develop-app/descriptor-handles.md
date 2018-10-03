---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3aa085cc0a098f557ca7a8cbddcd787a178b79d0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711608"
---
# <a name="descriptor-handles"></a>Deskriptorhandles
Ein *Deskriptor* ist eine Auflistung von Metadaten, die die Parameter der SQL-Anweisung oder die Spalten eines Resultsets zu beschreiben, wie von der Anwendung oder Treiber (auch bekannt als die *Implementierung*). Daher kann ein Deskriptor einer der vier Rollen ausfüllen:  
  
-   **Anwendungsparameterdeskriptor (APD).** Enthält Informationen über die Anwendungspuffer, der an die Parameter in einer SQL­Anweisung, wie ihre Adressen, die Länge und die C-Datentypen gebunden.  
  
-   **Implementation Parameter Descriptor (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor).** Enthält Informationen zu den Parametern in einer SQL­Anweisung, wie ihre SQL-Datentypen, Länge und NULL-Zulässigkeit an.  
  
-   **Zeile Anwendungsdeskriptor (ARD).** Enthält Informationen über die Anwendungspuffer, der an die Spalten in einem Resultset, wie ihre Adressen, die Länge und die C-Datentypen gebunden.  
  
-   **Implementierungszeilendeskriptors (IRD).** Enthält Informationen zu den Spalten in einem Resultset, wie ihre SQL-Datentypen, Länge und NULL-Zulässigkeit an.  
  
 Vier Deskriptoren (legt jede Rolle einem) werden automatisch zugeordnet werden, wenn eine Anweisung zugeordnet ist. Diese werden als bezeichnet *automatisch zugeordnet Deskriptoren* immer dieser Anweisung zugeordnet sind. Anwendungen können auch Deskriptoren mit zuordnen **SQLAllocHandle**. Diese werden als bezeichnet *explizit reserviert Deskriptoren*. Sie werden bei einer Verbindung zugeordnet und können eine oder mehrere Anweisungen für die Verbindung zum Erfüllen der Rolle eines APD oder ARD auf diese Anweisungen zugeordnet werden.  
  
 Die meisten Vorgänge in ODBC können ohne explizite Verwendung von Deskriptoren von der Anwendung ausgeführt werden. Deskriptoren bieten jedoch eine zweckmäßige Möglichkeit für einige Vorgänge an. Nehmen wir beispielsweise an, dass eine Anwendung Daten zum Einfügen von Daten aus zwei unterschiedlichen Gruppen von Puffern. Es würde wiederholt aufrufen, um den ersten Satz von Puffern zu verwenden, **SQLBindParameter** so binden Sie sie an die Parameter in einer **einfügen** Anweisung und die Anweisung anschließend auszuführen. Um den zweiten Satz von Puffern zu verwenden, würden sie diesen Vorgang wiederholen. Alternativ können sie Bindungen zu den ersten Satz von Puffern in einen Deskriptor und an den zweiten Satz von Puffern in einem anderen Deskriptor einrichten. Um zwischen den einzelnen Bindungen zu wechseln, die Anwendung einfach aufrufen würde **SQLSetStmtAttr** und ordnen Sie den richtigen Deskriptor der Anweisung als APD.  
  
 Weitere Informationen zu den sicherheitsbeschreibungen, finden Sie unter [Typen von Deskriptoren](../../../odbc/reference/develop-app/types-of-descriptors.md).
