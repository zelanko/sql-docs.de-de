---
title: Einrichten des Cursors | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 805d8076c853513d86f9a3a92d9342d1224226c9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299800"
---
# <a name="setting-up-the-cursor"></a>Einrichten des Cursors
Die Anwendung kann den Cursortyp angeben, bevor sie eine Anweisung ausführt, die eine Resultmenge erstellt. Dies geschieht mit dem Attribut SQL_ATTR_CURSOR_TYPE.- Wenn die Anwendung keinen Typ explizit angibt, wird ein Vorwärtscursor verwendet. Um einen gemischten Cursor zu erhalten, gibt eine Anwendung einen mit Keyset gesteuerten Cursor an, deklariert jedoch eine Keysetgröße, die kleiner als die Größe des Resultsets ist.  
  
 Bei Keyset-gesteuerten und gemischten Cursorn kann die Anwendung auch die Keysetgröße angeben. Dies geschieht mit dem Attribut SQL_ATTR_KEYSET_SIZE.- Wenn die Keysetgröße auf 0 festgelegt ist, was der Standardwert ist, wird die Keysetgröße auf die Größe des Resultsets festgelegt, und es wird ein Keyset-gesteuerter Cursor verwendet. Die Größe des Keysets kann geändert werden, nachdem der Cursor geöffnet wurde.  
  
 Die Anwendung kann auch die Rowsetgröße festlegen. Weitere Informationen finden Sie unter [Verwenden von Blockcursors](../../../odbc/reference/develop-app/using-block-cursors.md)weiter oben in diesem Abschnitt.
