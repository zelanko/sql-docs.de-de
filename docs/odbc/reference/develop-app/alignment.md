---
title: Ausrichtung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- alignment issues [ODBC]
ms.assetid: 06a01e51-e7a5-495f-aa27-e304b0d005ff
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 205cc3ff95dd60db215150f46ae894fbb99bd9ff
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81288605"
---
# <a name="alignment"></a>Ausrichtung
Die Ausrichtungs Probleme in einer ODBC-Anwendung unterscheiden sich in der Regel nicht von anderen Anwendungen. Das heißt, die meisten ODBC-Anwendungen haben nur wenige oder keine Probleme mit der Ausrichtung. Die Gebühren für das nicht Ausrichten von Adressen variieren mit der Hardware und dem Betriebssystem und können so gering wie eine geringfügige Leistungs Einbuße oder ein schwerwiegender Fehler beim Ausführen eines schwerwiegenden Lauf zeitfehlers sein. Daher sollten ODBC-Anwendungen und insbesondere Portier Bare ODBC-Anwendungen darauf achten, Daten ordnungsgemäß auszurichten.  
  
 Ein Beispiel für den Fall, dass ODBC-Anwendungen Ausrichtungs Probleme stoßen, besteht darin, dass Sie einen großen Speicherblock zuordnen und verschiedene Teile dieses Speichers an die Spalten in einem Resultset binden. Dies tritt am wahrscheinlichsten auf, wenn eine generische Anwendung die Form eines Resultsets zur Laufzeit bestimmen und Arbeitsspeicher entsprechend zuordnen und binden muss.  
  
 Nehmen wir beispielsweise an, dass eine Anwendung eine vom Benutzer eingegebene **Select** -Anweisung ausführt und die Ergebnisse dieser Anweisung abruft. Da die Form dieses Resultsets beim Schreiben des Programms nicht bekannt ist, muss die Anwendung den Typ der einzelnen Spalten ermitteln, nachdem das Resultset erstellt wurde, und den Arbeitsspeicher entsprechend binden. Die einfachste Möglichkeit hierfür ist, einen großen Speicherblock zuzuordnen und verschiedene Adressen in diesem Block an jede Spalte zu binden. Um auf die Daten in einer Spalte zuzugreifen, wandelt die Anwendung den an diese Spalte gebundenen Speicher um.  
  
 Das folgende Diagramm zeigt ein Beispielresultset und wie ein Speicherblock an ihn gebunden werden kann. dazu wird der C-Standard Datentyp für jeden SQL-Datentyp verwendet. Jedes "X" stellt ein einzelnes Byte des Speichers dar. (In diesem Beispiel werden nur die Datenpuffer angezeigt, die an die Spalten gebunden sind. Dies erfolgt aus Gründen der Einfachheit. In tatsächlichem Code müssen die Längen-/Indikatorpuffer ebenfalls ausgerichtet werden.)  
  
 ![Standardmäßige Bindung von C-Datentypen an SQL-Datentypen](../../../odbc/reference/develop-app/media/pr24.gif "pr24")  
  
 Wenn die gebundenen Adressen im *Adress* Array gespeichert werden, verwendet die Anwendung die folgenden Ausdrücke, um auf den Speicher zuzugreifen, der an die einzelnen Spalten gebunden ist:  
  
```  
(SQLCHAR *)       Address[0]  
(SQLSMALLINT *)   Address[1]  
(SQLINTEGER *)    Address[2]  
```  
  
 Beachten Sie, dass die an die zweite und die dritte Spalte gebundenen Adressen bei ungeraden Bytes beginnen und dass die an die dritte Spalte gebundene Adresse nicht durch vier, d. h. die Größe eines sdworts, nicht teilbar ist. Auf einigen Computern ist dies kein Problem. bei anderen führt dies zu einer geringfügigen Leistungs Einbuße. bei anderen Personen führt dies zu einem schwerwiegenden Laufzeitfehler. Eine bessere Lösung besteht darin, jede gebundene Adresse an ihrer natürlichen Ausrichtungs Grenze auszurichten. Wenn dies der Fall ist, dass 1 für einen UCHAR, 2 für ein Schwert und 4 für ein SDWORD ist, würde dies das in der folgenden Abbildung dargestellte Ergebnis ergeben, wobei ein "X" ein Byte des verwendeten Speichers darstellt und ein "O" ein nicht verwendetes Byte des Speichers darstellt.  
  
 ![Bindung nach natürlichen Ausrichtungsgrenzen](../../../odbc/reference/develop-app/media/pr25.gif "pr25")  
  
 Obwohl bei dieser Lösung nicht der gesamte Arbeitsspeicher der Anwendung verwendet wird, sind keine Ausrichtungs Probleme aufgetreten. Leider benötigt Sie eine große Menge an Code, um diese Lösung zu implementieren, da jede Spalte entsprechend ihrem Typ einzeln ausgerichtet werden muss. Eine einfachere Lösung besteht darin, alle Spalten an der Größe der größten Ausrichtungs Grenze auszurichten. Dies ist 4 im Beispiel in der folgenden Abbildung dargestellt.  
  
 ![Bindung nach größten Ausrichtungsgrenzen](../../../odbc/reference/develop-app/media/pr26.gif "pr26")  
  
 Obwohl diese Lösung größere Lücken beibehält, ist der Code für die Implementierung relativ einfach und schnell. In den meisten Fällen wird dadurch die im nicht verwendeten Speicherkosten pflichtige Strafe versetzt. Ein Beispiel, in dem diese Methode verwendet wird, finden [Sie unter Verwenden von SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).
