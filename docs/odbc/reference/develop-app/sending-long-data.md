---
title: Senden von Long-Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- long data [ODBC]
- sending long data [ODBC]
ms.assetid: ea989084-a8e6-4737-892e-9ec99dd49caf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc7a140d7de8548f02fde6ab309823bbe1c9c656
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616088"
---
# <a name="sending-long-data"></a>Senden von Long-Daten
Definieren eines DBMS *long-Daten* als beliebiges Zeichen oder Binärdaten über eine bestimmte Größe, z. B. 254 Zeichen. Es eventuell nicht möglich, zum Speichern des gesamten Elements von long-Daten im Arbeitsspeicher, z. B. wenn das Element ein langer Text-Dokument oder eine Bitmap darstellt. Da diese Daten in einem einzigen Puffer gespeichert werden können, die Datenquelle wird an den Treiber in Teilen mit **SQLPutData** Wenn die Anweisung ausgeführt wird. Parameter für die Daten zum Zeitpunkt der Ausführung gesendet werden, werden als bezeichnet *Data-at-Execution-Parameter*.  
  
> [!NOTE]  
>  Eine Anwendung kann eigentlich jeden Datentyp zum Zeitpunkt der Ausführung mit senden **SQLPutData**, obwohl nur Zeichen- und Binärdaten in Teilen gesendet werden können. Wenn die Daten klein genug, um in einen einzelnen Puffer zu passen, gibt es ist jedoch im Allgemeinen kein Grund für die Verwendung **SQLPutData**. Es ist einfacher, den Puffer zu binden, und lassen den Treiber, die Abrufen der Daten aus dem Puffer.  
  
 Zum Senden von Daten zum Zeitpunkt der Ausführung führt die Anwendung die folgenden Aktionen aus:  
  
1.  Übergibt einen 32-Bit-Wert, den Parameter im identifiziert, die *ParameterValuePtr* -Argument in **SQLBindParameter** statt der Übergabe der Adresse eines Puffers. Dieser Wert wird vom Treiber nicht analysiert werden. Es wird an die Anwendung später zurückgegeben werden, damit es ähnelt der Anwendung bedeuten sollte. Beispielsweise kann es die Nummer des Parameters oder das Handle für eine Datei mit Daten sein.  
  
2.  Übergibt die Adresse ein Längen-/Indikatorpuffer in die *StrLen_or_IndPtr* Argument **SQLBindParameter**.  
  
3.  Speichert SQL_DATA_AT_EXEC oder das Ergebnis der SQL_LEN_DATA_AT_EXEC (*Länge*)-Makro in den Längen-/Indikatorpuffer. Beide dieser Werte angegeben werden, die der Treiber, der die Daten für den Parameter mit gesendet werden, **SQLPutData**. SQL_LEN_DATA_AT_EXEC (*Länge*) wird verwendet, wenn Sie long-Daten mit einer Datenquelle zu senden, die muss wissen, wie viele Bytes an Daten vom Typ long gesendet werden, damit es die Speicherplatz vorab zuweisen kann. Um zu bestimmen, wenn dieser Wert von eine Datenquelle erforderlich ist, wird die Anwendung ruft **SQLGetInfo** mit der Option SQL_NEED_LONG_DATA_LEN. Alle Treiber müssen dieses Makro unterstützen. Wenn die Bytelänge in die Datenquelle nicht erforderlich ist, können Sie durch der Treiber ignorieren.  
  
4.  Aufrufe **SQLExecute** oder **SQLExecDirect**. Der Treiber ermittelt, dass ein Längen-/Indikatorpuffer, den Wert SQL_DATA_AT_EXEC oder das Ergebnis der SQL_LEN_DATA_AT_EXEC enthält (*Länge*)-Makro aus und gibt SQL_NEED_DATA zurück, als der Rückgabewert der Funktion zurück.  
  
5.  Aufrufe **SQLParamData** Rückgabewert als Reaktion auf die SQL_NEED_DATA zurück. Wenn Sie long-Daten gesendet werden, müssen **SQLParamData** wird SQL_NEED_DATA zurückgegeben. In den Puffer, der auf die *ValuePtrPtr* -Argument, gibt der Treiber den Wert, der den Data-at-Execution-Parameter identifiziert. Wenn mehr als ein Data-at-Execution-Parameter vorhanden ist, muss die Anwendung diesen Wert verwenden, um zu bestimmen, welche Parameter zum Senden von Daten für; der Treiber ist nicht erforderlich, Anfordern von Daten für Data-at-Execution-Parameter in einer bestimmten Reihenfolge.  
  
6.  Aufrufe **SQLPutData** zum Senden der Parameterdaten an den Treiber. Wenn die Parameterdaten wie häufig der Fall mit langen Daten ist in einer einzelnen Puffer nicht passt, wird die Anwendung ruft **SQLPutData** wiederholt, um die Daten in Teile senden es obliegt dem Treiber und der Datenquelle, die Daten wieder zusammenzusetzen. Wenn die Anwendung Daten mit Null endende Zeichenfolge erfolgreich ist, muss die Treiber oder die Datenquelle die Null-Terminierungszeichen als Teil des Prozesses für die Reassemblierung entfernen.  
  
7.  Aufrufe **SQLParamData** erneut aus, um anzugeben, dass sie alle Daten für den Parameter gesendet hat. Wenn Data-at-Execution-Parameter für die Daten nicht der Treiber gibt SQL_NEED_DATA zurück, und der Wert gesendet wurde, der den nächsten Parameter identifiziert, vorhanden sind; Gibt zurück, die Anwendung mit Schritt 6 fort. Wenn die Daten für alle Data-at-Execution-Parameter gesendet wurde, wird die Anweisung ausgeführt. **SQLParamData** gibt SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO und kann zurückgeben, einen Rückgabewert oder Diagnose, die **SQLExecute** oder **SQLExecDirect** zurückgeben können.  
  
 Nach dem **SQLExecute** oder **SQLExecDirect** wird SQL_NEED_DATA zurückgegeben. und bevor die Daten vollständig für den letzten Data-at-Execution-Parameter gesendet wurde, wird die Anweisung in einem Zustand müssen Daten ist. Während eine Anweisung in einem Zustand der Daten erforderlich ist, kann nur die Anwendung aufrufen **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**, oder **SQLGetDiagRec**; alle anderen Funktionen zurückgeben SQLSTATE HY010 (Sequenzfehler funktionieren). Aufrufen von **SQLCancel** bricht die Ausführung der Anweisung ab und gibt sie an den ursprünglichen Zustand zurück. Weitere Informationen finden Sie unter [Anhang B: ODBC-Übergang-Statustabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Ein Beispiel für das Senden von Daten zum Zeitpunkt der Ausführung, finden Sie unter den [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md) funktionsbeschreibung.
