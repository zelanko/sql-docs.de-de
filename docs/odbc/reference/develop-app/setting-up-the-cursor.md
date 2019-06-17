---
title: Einrichten des Cursors | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: b80afb0e-ef2f-408f-86f5-a392edd99a56
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59ade343f282933e05619996b119bc08e2dfb2ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62445912"
---
# <a name="setting-up-the-cursor"></a>Einrichten des Cursors
Die Anwendung kann den Cursortyp angeben, vor dem Ausführen einer Anweisung, die ein Ergebnis erstellt. Dies wird mit dem SQL_ATTR_CURSOR_TYPE-Attribut-Anweisung. Wenn die Anwendung nicht explizit einen Typ angeben, wird ein Vorwärtscursor verwendet werden. Um einen gemischten Cursor zu erhalten, eine Anwendung gibt an, einen keysetgesteuerten Cursor deklariert jedoch eine Keysetgröße kleiner als die Größe des Resultsets.  
  
 Für keysetgesteuerte und gemischte Cursor kann die Anwendung auch die Keysetgröße angeben. Dies wird mit dem Attribut der SQL_ATTR_KEYSET_SIZE-Anweisung. Wenn die Keysetgröße auf 0 (null), die der Standardwert ist festgelegt ist, die Keysetgröße auf die Größe des Resultsets festgelegt ist, und ein keysetgesteuerten Cursors wird verwendet. Die Keysetgröße kann geändert werden, nachdem der Cursor geöffnet wurde.  
  
 Die Anwendung kann auch die Rowsetgröße festzulegen; Weitere Informationen finden Sie unter [Verwenden von Blockcursorn](../../../odbc/reference/develop-app/using-block-cursors.md)weiter oben in diesem Abschnitt.
