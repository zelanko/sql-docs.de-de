---
title: Parameterbindungsversätze | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- offsets of parameters [ODBC]
- binding offsets of parameters [ODBC]
ms.assetid: 309339e9-9ccd-4a58-8aa4-b6dc88f4eb7c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: de67b230883f3cf8a582e73ce82e8c4bd7d21ad0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282490"
---
# <a name="parameter-binding-offsets"></a>Offsets der Parameterbindung
Eine Anwendung kann angeben, dass ein Offset zu gebundenen Parameterpufferadressen und den entsprechenden Längen-/Indikatorpufferadressen hinzugefügt wird, wenn **SQLExecDirect** oder **SQLExecute** aufgerufen wird. Das Ergebnis dieser Ergänzungen bestimmt die Adressen, die in diesen Vorgängen verwendet werden.  
  
 Bindungsoffsets ermöglichen es einer Anwendung, Bindungen zu ändern, ohne **SQLBindParameter** für zuvor gebundene Parameter aufzurufen. Ein Aufruf von **SQLBindParameter** zum erneuten Binden eines Parameters ändert die Pufferadresse und den Längen-/Indikatorzeiger. Die Neubindung mit einem Offset hingegen fügt der vorhandenen gebundenen Parameterpufferadresse und Längen-/Indikatorpufferadresse einfach einen Offset hinzu. Wenn Offsets verwendet werden, sind die Bindungen eine "Vorlage" dafür, wie die Anwendungspuffer angeordnet sind, und die Anwendung kann diese "Vorlage" in verschiedene Speicherbereiche verschieben, indem sie den Offset ändert. Ein neuer Offset kann jederzeit angegeben werden und wird immer zu den ursprünglich gebundenen Werten hinzugefügt.  
  
 Um einen Bindungsoffset anzugeben, legt die Anwendung das SQL_ATTR_PARAM_BIND_OFFSET_PTR-Anweisungsattribut auf die Adresse eines SQLINTEGER-Puffers fest. Bevor die Anwendung eine Funktion aufruft, die die Bindungen verwendet, platziert sie einen Offset in Bytes in diesem Puffer, solange weder die Parameterpufferadresse noch die Length/Indicator-Pufferadresse 0 ist und der gebundene Parameter in der SQL-Anweisung liegt. Die Summe der Adresse und des Offsets muss eine gültige Adresse sein. (Dies bedeutet, dass entweder der Offset oder die Adresse, der der Offset hinzugefügt wird, ungültig sein kann, solange ihre Summe eine gültige Adresse ist.)  
  
> [!NOTE]  
>  Bindungsoffsets werden von ODBC 2 nicht unterstützt. *x-Treiber.*
