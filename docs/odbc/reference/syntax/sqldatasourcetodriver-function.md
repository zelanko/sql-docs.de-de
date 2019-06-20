---
title: SQLDataSourceToDriver-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDataSourceToDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDataSourceToDriver
helpviewer_keywords:
- SQLDataSourceToDriver function [ODBC]
ms.assetid: 0d87fcac-30a0-4303-ad8f-a5b53f4b428d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 022387847cb1371af13465cee7a9e3e1c21e5749
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537655"
---
# <a name="sqldatasourcetodriver-function"></a>SQLDataSourceToDriver-Funktion
**SQLDataSourceToDriver** Supportstranslations für ODBC-Treiber. Diese Funktion wird nicht von ODBC-fähigen Anwendungen aufgerufen werden; Anwendungen fordern Übersetzung über **SQLSetConnectAttr**. Die zugeordneten Treibers Untersuchen der *ConnectionHandle* im angegebenen **SQLSetConnectAttr** Ruft die angegebene DLL um Übersetzungen für den Treiber alle Datenflüsse aus der Datenquelle auszuführen. Eine Standard-Konvertierungs-DLL kann in der ODBC-Initialisierungsdatei angegeben werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLDataSourceToDriver(  
     UDWORD     fOption,  
     SWORD      fSqlType,  
     PTR        rgbValueIn,  
     SDWORD     cbValueIn,  
     PTR        rgbValueOut,  
     SDWORD     cbValueOutMax,  
     SDWORD *   pcbValueOut,  
     UCHAR *    szErrorMsg,  
     SWORD      cbErrorMsgMax,  
     SWORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>Argumente  
 *fOption*  
 [Eingabe] Der Wert.  
  
 *fSqlType*  
 [Eingabe] Der SQL-Datentyp. Dieses Argument weist den Treiber konvertieren *RgbValueIn* in ein Format, die von der Anwendung akzeptabel. Eine Liste der gültigen SQL-Datentypen, finden Sie unter den [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) Abschnitt in Anhang D: Datentypen.  
  
 *rgbValueIn*  
 [Eingabe] Zu übersetzender Wert.  
  
 *cbValueIn*  
 [Eingabe] Länge der *RgbValueIn*.  
  
 *rgbValueOut*  
 [Ausgabe] Ergebnis der Übersetzung.  
  
> [!NOTE]  
>  Der Konvertierungs-DLL ist nicht Null-dieser Wert beendet werden.  
  
 *cbValueOutMax*  
 [Eingabe] Länge der *RgbValueOut*.  
  
 *pcbValueOut*  
 [Ausgabe] Die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierung Byte) zur Verfügung, die in zurückgegeben *RgbValueOut*.  
  
 Für Zeichen- oder Binärdaten, ist dies größer als oder gleich *CbValueOutMax*, die Daten in *RgbValueOut* auf abgeschnitten *CbValueOutMax* Bytes.  
  
 Für alle anderen Datentypen den Wert der *CbValueOutMax* wird ignoriert, und der Konvertierungs-DLL wird vorausgesetzt, dass die Größe des *RgbValueOut* ist die Größe der Standard-C-Datentyp des SQL-Datentyps mit angegeben*fSqlType*.  
  
 Die *PcbValueOut* Argument kann ein null-Zeiger sein.  
  
 *szErrorMsg*  
 [Ausgabe] Zeiger auf Speicher für eine Fehlermeldung angezeigt. Dies ist eine leere Zeichenfolge, es sei denn, die Übersetzung Fehler.  
  
 *cbErrorMsgMax*  
 [Eingabe] Länge der *von SQLDiagRec()*.  
  
 *pcbErrorMsg*  
 [Ausgabe] Zeiger auf die Gesamtzahl der Bytes, die (mit Ausnahme der Null-Terminierung Byte) zur Verfügung, die in zurückgegeben *von SQLDiagRec()*. Wenn dieser größer als oder gleich ist *CbErrorMsg*, die Daten in *von SQLDiagRec()* auf abgeschnitten *CbErrorMsgMax* minus der Null-Terminierungszeichen. Die *PcbErrorMsg* Argument kann ein null-Zeiger sein.  
  
## <a name="returns"></a>Rückgabewert  
 TRUE, wenn die Verschiebung erfolgreich "false" war, wenn die Übersetzung fehlgeschlagen ist.  
  
## <a name="comments"></a>Kommentare  
 Der Treiber ruft **SQLDataSourceToDriver** Alldata (Resultsetdaten, Tabellennamen, Zeilenanzahl, Fehlermeldungen usw.) zu übersetzen Quellcode-übergeben von Daten an den Treiber. Einige Daten, je nach der Typ der Daten und den Zweck des Konvertierungs-DLL kann von den Konvertierungs-DLL nicht übersetzt werden; Beispielsweise wird eine DLL, die Zeichendaten, die von einer Codeseite in eine andere übersetzt alle numeric- und binary-ignoriert.  
  
 Der Wert des *fOption* festgelegt ist, auf den Wert der *vParam* angegeben, indem **SQLSetConnectAttr** mit dem SQL_ATTR_TRANSLATE_OPTION-Attribut. Es ist eine 32-Bit-Wert, der für einen bestimmten Konvertierungs-DLL eine besondere Bedeutung hat. Beispielsweise können sie angeben, dass ein bestimmtes Zeichen Übersetzung festgelegt.  
  
 Wenn im gleiche Puffer für angegeben wird *RgbValueIn* und *RgbValueOut*, erfolgt die Übersetzung von Daten in den Puffer vorhanden.  
  
 Obwohl *CbValueIn*, *CbValueOutMax*, und *PcbValueOut* sind vom Typ SDWORD, **SQLDataSourceToDriver** werden nicht unbedingt unterstützen Sie große Zeiger.  
  
 Wenn **SQLDataSourceToDriver** gibt FALSE zurück, Abschneiden von Daten kann während der Übersetzung aufgetreten sind. Wenn *PcbValueOut* (die Anzahl der zurückzugebenden im Ausgabepuffer verfügbaren Bytes) ist größer als *CbValueOutMax* (die Länge des Ausgabepuffers), und klicken Sie dann die Daten abgeschnitten wurden. Der Treiber muss bestimmen, ob das Abschneiden akzeptabel war. Wenn nicht abgeschnitten, die **SQLDataSourceToDriver** "false" aufgrund von Fehler ein anderer Fehler zurückgegeben. In beiden Fällen wird eine bestimmte Fehlermeldung zurückgegeben, *von SQLDiagRec()*.  
  
 Weitere Informationen zum Übersetzen von Daten, finden Sie unter [Konvertierungs-DLLs](../../../odbc/reference/develop-app/translation-dlls.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Übersetzen von Daten an die Datenquelle gesendet werden|[SQLDriverToDataSource](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|  
|Die Einstellung ein Verbindungsattribut zurückgeben|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Ein Verbindungsattribut festlegen|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
