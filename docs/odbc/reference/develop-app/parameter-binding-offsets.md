---
title: Parameter Bindungs Offsets | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d0dbddc71b0d647246d10dad16ad72d533df16de
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68023348"
---
# <a name="parameter-binding-offsets"></a>Offsets der Parameterbindung
Eine Anwendung kann angeben, dass ein Offset zu gebundenen Parameter Puffer Adressen und die entsprechenden Längen-/indikatorpufferadressen hinzugefügt werden, wenn **SQLExecDirect** oder **SQLExecute** aufgerufen wird. Das Ergebnis dieser Ergänzungen bestimmt die Adressen, die in diesen Vorgängen verwendet werden.  
  
 Bindungs Offsets ermöglichen es einer Anwendung, Bindungen zu ändern, ohne dass **SQLBindParameter** für zuvor gebundene Parameter aufgerufen wird. Durch einen **SQLBindParameter** -Befehl zum erneuten Binden eines Parameters werden die Puffer Adresse und der Längen-/indikatorenzeiger geändert. Durch die erneute Bindung mit einem Offset wird hingegen einfach der vorhandene gebundene Parameter Puffer Adresse und der Länge/Indikator-Puffer Adresse ein Offset hinzugefügt. Wenn Offsets verwendet werden, sind die Bindungen eine "Vorlage" für die Art und Weise, wie die Anwendungs Puffer angelegt werden, und die Anwendung kann diese "Vorlage" durch Ändern des Offsets in verschiedene Speicherbereiche verschieben. Ein neuer Offset kann jederzeit angegeben werden und wird immer den ursprünglich gebundenen Werten hinzugefügt.  
  
 Um einen Bindungs Offset anzugeben, legt die Anwendung das SQL_ATTR_PARAM_BIND_OFFSET_PTR Statement-Attribut auf die Adresse eines SQLINTEGER-Puffers fest. Bevor die Anwendung eine Funktion aufruft, die die Bindungen verwendet, platziert Sie einen Offset in Bytes in diesem Puffer, sofern weder die Parameter Puffer Adresse noch die Länge/Indikator-Puffer Adresse 0 ist und der gebundene Parameter in der SQL-Anweisung vorliegt. Die Summe der Adresse und des Offsets muss eine gültige Adresse sein. (Dies bedeutet, dass entweder der Offset und die Adresse, zu der der Offset hinzugefügt wird, ungültig sein können, solange die Summe eine gültige Adresse ist.)  
  
> [!NOTE]  
>  Bindungs Offsets werden von ODBC 2 nicht unterstützt. *x* -Treiber.
