---
title: Offsets der parameterbindung | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: f1fd069336a52b0a27ae927880f749c02d2c1d43
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998922"
---
# <a name="parameter-binding-offsets"></a>Offsets der Parameterbindung
Einer Anwendung angegeben werden, dass ein Offset hinzugefügt wird, um die pufferadressen Parameter und den entsprechenden Längenindikator gebunden Puffer behandelt, wenn **SQLExecDirect** oder **SQLExecute** aufgerufen wird. Das Ergebnis dieser Ergänzungen bestimmt, die Adressen, die bei diesen Vorgängen verwendet wird.  
  
 BIND-Offsets können eine Anwendung so ändern Sie die Bindungen ohne **SQLBindParameter** für zuvor gebundene Parameter. Ein Aufruf von **SQLBindParameter** zum Binden der Parameter geändert wird, die Pufferadresse und den Längenindikator /-Zeiger. Das erneute Binden mit einem Offset, fügt auf der anderen Seite einfach einen Offset auf die vorhandenen Pufferadresse für gebundene Parameter und den Längenindikator/Pufferadresse. Wenn Offsets verwendet werden, die Bindungen sind eine "Vorlage" wie die Anwendungspuffer angeordnet werden, und der Anwendung kann auf unterschiedliche Bereiche des Arbeitsspeichers dieser "Template" verschieben, durch Ändern des Offsets. Ein neuer Offset kann zu einem beliebigen Zeitpunkt angegeben werden, und es wird immer hinzugefügt, die ursprünglich gebundenen Werte.  
  
 Um eine Bindung Offset anzugeben, legt die Anwendung das Anweisungsattribut SQL_ATTR_PARAM_BIND_OFFSET_PTR an die Adresse eines Puffers SQLINTEGER fest. Bevor die Anwendung eine Funktion, die die Bindungen verwendet aufruft, wird einen Offset in Bytes, die in diesen Puffer, solange weder die Pufferadresse für den Parameter als auch die Pufferadresse Längenindikator/0, und der gebundene Parameter in der SQL-Anweisung ist. Die Summe der Adresse und den Offset muss eine gültige Adresse sein. (Dies bedeutet, dass eine oder beide der Offset und die Adresse, die der Offset hinzugefügt wird, ungültig sein können, solange die Summe über eine gültige Adresse ist.)  
  
> [!NOTE]  
>  Bindung Offsets werden vom ODBC-2 nicht unterstützt. *x* Treiber.
