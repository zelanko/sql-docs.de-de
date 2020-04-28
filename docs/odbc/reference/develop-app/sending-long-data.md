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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aeeeb716aa2f9a72338f3aeb586dffce86f84069
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304181"
---
# <a name="sending-long-data"></a>Senden von Long-Daten
DBMSs definiert *lange Daten* als beliebige Zeichen oder Binärdaten über eine bestimmte Größe, z. b. 254 Zeichen. Möglicherweise ist es nicht möglich, ein gesamtes Element mit langen Daten im Arbeitsspeicher zu speichern, z. b. wenn das Element ein langes Textdokument oder eine Bitmap darstellt. Da solche Daten nicht in einem einzelnen Puffer gespeichert werden können, sendet die Datenquelle Sie an den Treiber in Teilen mit **SQLPutData** , wenn die Anweisung ausgeführt wird. Parameter, für die Daten zur Ausführungszeit gesendet werden, werden als *Data-at-Execution-Parameter*bezeichnet.  
  
> [!NOTE]  
>  Eine Anwendung kann tatsächlich beliebige Datentypen zur Ausführungszeit mit **SQLPutData**senden, obwohl nur Zeichen-und Binärdaten in Teilen gesendet werden können. Wenn die Daten jedoch klein genug sind, um in einen einzelnen Puffer zu passen, gibt es in der Regel keinen Grund, **SQLPutData**zu verwenden. Es ist viel einfacher, den Puffer zu binden, sodass der Treiber die Daten aus dem Puffer abrufen kann.  
  
 Zum Senden von Daten zur Ausführungszeit führt die Anwendung die folgenden Aktionen aus:  
  
1.  Übergibt einen 32-Bit-Wert, der den-Parameter im *ParameterValuePtr* -Argument in **SQLBindParameter** identifiziert, anstatt die Adresse eines Puffers zu übergeben. Dieser Wert wird vom Treiber nicht analysiert. Er wird später an die Anwendung zurückgegeben und sollte daher etwas für die Anwendung bedeuten. Dies kann z. b. die Nummer des-Parameters oder das Handle einer Datei sein, die Daten enthält.  
  
2.  Übergibt die Adresse eines Längen-/Indikatorpuffers im *StrLen_or_IndPtr* -Argument von **SQLBindParameter**.  
  
3.  Speichert SQL_DATA_AT_EXEC oder das Ergebnis des Makros SQL_LEN_DATA_AT_EXEC (*length*) im Längen-/Indikatorpuffer. Beide Werte geben dem Treiber an, dass die Daten für den Parameter mit **SQLPutData**gesendet werden. SQL_LEN_DATA_AT_EXEC (*Länge*) wird verwendet, wenn lange Daten an eine Datenquelle gesendet werden, die wissen müssen, wie viele Bytes von langen Daten gesendet werden, damit der Speicherplatz vorab zugeordnet werden kann. Um zu ermitteln, ob eine Datenquelle diesen Wert erfordert, ruft die Anwendung **SQLGetInfo** mit der SQL_NEED_LONG_DATA_LEN-Option auf. Dieses Makro muss von allen Treibern unterstützt werden. Wenn die Datenquelle die Byte Länge nicht benötigt, kann Sie vom Treiber ignoriert werden.  
  
4.  Ruft **SQLExecute** oder **SQLExecDirect**auf. Der Treiber ermittelt, dass ein Längen-/Indikatorpuffer den Wert SQL_DATA_AT_EXEC oder das Ergebnis des SQL_LEN_DATA_AT_EXEC (*length*)-Makros enthält und SQL_NEED_DATA als Rückgabewert der Funktion zurückgibt.  
  
5.  Ruft **SQLParamData** als Reaktion auf den SQL_NEED_DATA Rückgabewert auf. Wenn Long-Daten gesendet werden müssen, gibt **SQLParamData** SQL_NEED_DATA zurück. Im Puffer, auf den das *ValuePtrPtr* -Argument zeigt, gibt der Treiber den Wert zurück, der den Data-at-Execution-Parameter identifiziert. Wenn mehr als ein Data-at-Execution-Parameter vorhanden ist, muss die Anwendung diesen Wert verwenden, um zu bestimmen, für welchen Parameterdaten gesendet werden sollen. der Treiber muss keine Daten für Data-at-Execution-Parameter in einer bestimmten Reihenfolge anfordern.  
  
6.  Ruft **SQLPutData** auf, um die Parameterdaten an den Treiber zu senden. Wenn die Parameterdaten nicht in einen einzelnen Puffer passen, wie es häufig bei langen Daten der Fall ist, ruft die Anwendung **SQLPutData** wiederholt auf, um die Daten in Teilen zu senden. der Treiber und die Datenquelle müssen die Daten neu zuweisen. Wenn die Anwendung auf NULL endenden Zeichen folgen Daten übergibt, muss der Treiber oder die Datenquelle das NULL-Beendigungs Zeichen als Teil des neuzuordnungs Prozesses entfernen.  
  
7.  Ruft **SQLParamData** erneut auf, um anzugeben, dass alle Daten für den Parameter gesendet wurden. Wenn Data-at-Execution-Parameter vorhanden sind, für die keine Daten gesendet wurden, gibt der Treiber SQL_NEED_DATA und den Wert zurück, der den nächsten Parameter identifiziert. die Anwendung kehrt zu Schritt 6 zurück. Wenn Daten für alle Data-at-Execution-Parameter gesendet wurden, wird die-Anweisung ausgeführt. **SQLParamData** gibt SQL_SUCCESS oder SQL_SUCCESS_WITH_INFO zurück und kann beliebige Rückgabewerte oder Diagnosen zurückgeben, die von **SQLExecute** oder **SQLExecDirect** zurückgegeben werden können.  
  
 Nach dem Zurückgeben von **SQLExecute** oder **SQLExecDirect** SQL_NEED_DATA und bevor Daten vollständig für den letzten Data-at-Execution-Parameter gesendet wurden, befindet sich die-Anweisung in einem Daten Zustands Bedarf. Während sich eine-Anweisung in einem benötigten Daten Zustand befindet, kann die Anwendung nur **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**oder **SQLGetDiagRec**aufrufen. alle anderen Funktionen geben SQLSTATE HY010 (Funktions Sequenz Fehler) zurück. Durch den Aufruf von **SQLCancel** wird die Ausführung der-Anweisung abgebrochen und in den vorherigen Zustand zurückversetzt. Weitere Informationen finden Sie unter [Anhang B: ODBC-Status Übergangs Tabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Ein Beispiel für das Senden von Daten zur Ausführungszeit finden Sie in der Beschreibung der [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md) -Funktion.
