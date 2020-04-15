---
title: Senden langer Daten | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aeeeb716aa2f9a72338f3aeb586dffce86f84069
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304181"
---
# <a name="sending-long-data"></a>Senden von Long-Daten
DBMS definieren *lange Daten* als beliebige Zeichen- oder Binärdaten über eine bestimmte Größe, z. B. 254 Zeichen. Es ist möglicherweise nicht möglich, ein ganzes Element langer Daten im Arbeitsspeicher zu speichern, z. B. wenn das Element ein langes Textdokument oder eine Bitmap darstellt. Da solche Daten nicht in einem einzelnen Puffer gespeichert werden können, sendet die Datenquelle sie in Teilen mit **SQLPutData** an den Treiber, wenn die Anweisung ausgeführt wird. Parameter, für die Daten zur Ausführungszeit gesendet werden, werden als *Data-at-Execution-Parameter*bezeichnet.  
  
> [!NOTE]  
>  Eine Anwendung kann tatsächlich jede Art von Daten zur Ausführungszeit mit **SQLPutData**senden, obwohl nur Zeichen- und Binärdaten in Teilen gesendet werden können. Wenn die Daten jedoch klein genug sind, um in einen einzelnen Puffer zu passen, gibt es im Allgemeinen keinen Grund, **SQLPutData**zu verwenden. Es ist viel einfacher, den Puffer zu binden und den Treiber die Daten aus dem Puffer abrufen zu lassen.  
  
 Um Daten zur Ausführungszeit zu senden, führt die Anwendung die folgenden Aktionen aus:  
  
1.  Übergibt einen 32-Bit-Wert, der den Parameter im *ParameterValuePtr-Argument* in **SQLBindParameter** identifiziert, anstatt die Adresse eines Puffers zu übergeben. Dieser Wert wird vom Treiber nicht analysiert. Sie wird später an die Anwendung zurückgegeben, daher sollte sie etwas für die Anwendung bedeuten. Es kann z. B. die Nummer des Parameters oder das Handle einer Datei sein, die Daten enthält.  
  
2.  Übergibt die Adresse eines Längen-/Indikatorpuffers im *StrLen_or_IndPtr-Argument* von **SQLBindParameter**.  
  
3.  Speichert SQL_DATA_AT_EXEC oder das Ergebnis des*SQL_LEN_DATA_AT_EXEC(Länge*) Makros im Längen-/Indikatorpuffer. Beide Werte zeigen dem Treiber an, dass die Daten für den Parameter mit **SQLPutData**gesendet werden. SQL_LEN_DATA_AT_EXEC(*Länge*) wird verwendet, wenn lange Daten an eine Datenquelle gesendet werden, die wissen muss, wie viele Bytes langer Daten gesendet werden, damit Speicherplatz vorab zugewiesen werden kann. Um zu ermitteln, ob eine Datenquelle diesen Wert erfordert, ruft die Anwendung **SQLGetInfo** mit der Option SQL_NEED_LONG_DATA_LEN auf. Alle Treiber müssen dieses Makro unterstützen. Wenn die Datenquelle die Bytelänge nicht benötigt, kann der Treiber sie ignorieren.  
  
4.  Ruft **SQLExecute** oder **SQLExecDirect**auf. Der Treiber stellt fest, dass ein Längen-/Indikatorpuffer den*length*Wert SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC-Makros enthält und gibt SQL_NEED_DATA als Rückgabewert der Funktion zurück.  
  
5.  Ruft **SQLParamData** als Antwort auf den SQL_NEED_DATA Rückgabewert auf. Wenn lange Daten gesendet werden müssen, gibt **SQLParamData** SQL_NEED_DATA zurück. Im Puffer, auf den das *ValuePtrPtr-Argument* zeigt, gibt der Treiber den Wert zurück, der den Parameter data-at-execution identifiziert. Wenn mehr als ein Data-at-Execution-Parameter vorhanden ist, muss die Anwendung diesen Wert verwenden, um zu bestimmen, für welchen Parameter Daten gesendet werden sollen. Der Treiber ist nicht verpflichtet, Daten für Daten-at-Execution-Parameter in einer bestimmten Reihenfolge anzufordern.  
  
6.  Ruft **SQLPutData** auf, um die Parameterdaten an den Treiber zu senden. Wenn die Parameterdaten nicht in einen einzelnen Puffer passen, wie dies bei langen Daten häufig der Fall ist, ruft die Anwendung **SQLPutData** wiederholt auf, um die Daten in Teilen zu senden. Es liegt an dem Treiber und der Datenquelle, die Daten wieder zusammenzusetzen. Wenn die Anwendung null-beendete Zeichenfolgendaten übergibt, muss der Treiber oder die Datenquelle das NULL-Beendigungszeichen als Teil des Reassembly-Prozesses entfernen.  
  
7.  Ruft **SQLParamData** erneut auf, um anzugeben, dass alle Daten für den Parameter gesendet wurden. Wenn Daten-at-Execution-Parameter vorhanden sind, für die keine Daten gesendet wurden, gibt der Treiber SQL_NEED_DATA und den Wert zurück, der den nächsten Parameter identifiziert. die Anwendung kehrt zu Schritt 6 zurück. Wenn Daten für alle Data-at-Execution-Parameter gesendet wurden, wird die Anweisung ausgeführt. **SQLParamData** gibt SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück und kann jeden Rückgabewert oder jede Diagnose zurückgeben, die **SQLExecute** oder **SQLExecDirect** zurückgeben kann.  
  
 Nachdem **SQLExecute** oder **SQLExecDirect** SQL_NEED_DATA zurückgegeben und bevor Daten vollständig für den letzten Data-at-Execution-Parameter gesendet wurden, befindet sich die Anweisung im Status Need Data. Während sich eine Anweisung im Status Need Data befindet, kann die Anwendung nur **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**oder **SQLGetDiagRec**aufrufen. Alle anderen Funktionen geben SQLSTATE HY010 (Funktionssequenzfehler) zurück. Durch Aufrufen von **SQLCancel** wird die Ausführung der Anweisung abgebrochen und in den vorherigen Zustand zurückgesendet. Weitere Informationen finden Sie in [Anhang B: ODBC-Zustandsübergangstabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Ein Beispiel für das Senden von Daten zur Ausführungszeit finden Sie in der [SQLPutData-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlputdata-function.md)
