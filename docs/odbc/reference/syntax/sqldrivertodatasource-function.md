---
title: Sqldriverflidatasource-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDriverToDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDriverToDataSource
helpviewer_keywords:
- SQLDriverToDataSource function [ODBC]
ms.assetid: 0de28eb5-8aa9-43e4-a87f-7dbcafe800dc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89e7db7e4b20a35e047dca94cb72d8a6888fb670
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302751"
---
# <a name="sqldrivertodatasource-function"></a>SQLDriverToDataSource-Funktion
**Sqldriverumdatasource** unterstützt Übersetzungen für ODBC-Treiber. Diese Funktion wird nicht von ODBC-fähigen Anwendungen aufgerufen. Anwendungen fordern Übersetzungen über **SQLSetConnectAttr**an. Der Treiber, der dem in **SQLSetConnectAttr** angegebenen *connectionHandle* zugeordnet ist, ruft die angegebene DLL auf, um Übersetzungen für alle Daten zu übertragen, die vom Treiber an die Datenquelle übertragen werden. In der ODBC-Initialisierungsdatei kann eine standardmäßige Übersetzungs-DLL angegeben werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLDriverToDataSource(  
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
 Der Optionswert.  
  
 *Typ "f"*  
 Der Der ODBC SQL-Datentyp. Dieses Argument weist den Treiber an, wie *rgbvaluein* in ein von der Datenquelle akzeptables Formular konvertiert werden kann. Eine Liste gültiger SQL-Datentypen finden Sie unter [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md).  
  
 *rgbvaluein*  
 Der Zu übersetzender Wert.  
  
 *cbvaluein*  
 Der Länge von *rgbvaluein*.  
  
 *rgbvalueout*  
 Ausgeben Ergebnis der Übersetzung.  
  
> [!NOTE]  
>  Dieser Wert wird von der Übersetzungs-DLL nicht Null beendet.  
  
 *cbvalueoutmax*  
 Der Länge von *rgbvalueout*.  
  
 *pcbvalueout*  
 Ausgeben Die Gesamtanzahl der Bytes (mit Ausnahme des NULL-Beendigungs Byte), die in *rgbvalueout*zurückgegeben werden können.  
  
 Für Zeichen-oder Binärdaten, wenn diese größer oder gleich *cbvalueoutmax*ist, werden die Daten in *rgbvalueout* auf *cbvalueoutmax* Bytes gekürzt.  
  
 Für alle anderen Datentypen wird der Wert von *cbvalueoutmax* ignoriert, und die Übersetzungs-DLL geht davon aus, dass die Größe von *rgbvalueout* die Größe des Standard-C-Datentyps des SQL-Datentyps ist, der mit " *ssqltype*" angegeben wird.  
  
 Das *pcbvalueout* -Argument kann ein NULL-Zeiger sein.  
  
 *szErrorMsg*  
 Ausgeben Zeiger auf den Speicher für eine Fehlermeldung. Dies ist eine leere Zeichenfolge, es sei denn, bei der Übersetzung  
  
 *cberrormsgmax*  
 Der Länge von *szErrorMsg*.  
  
 *pcberrormsg*  
 Ausgeben Ein Zeiger auf die Gesamtzahl der Bytes (mit Ausnahme des NULL-Beendigungs Byte), die in *szErrorMsg*zurückgegeben werden können. Wenn dieser Wert größer oder gleich *cberrormsg*ist, werden die Daten in *szErrorMsg* auf *cberrormsgmax* abzüglich des NULL-Beendigungs Zeichens gekürzt. Das *pcberrormsg* -Argument kann ein NULL-Zeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 TRUE, wenn die Übersetzung erfolgreich war, false, wenn die Übersetzung fehlgeschlagen ist.  
  
## <a name="comments"></a>Kommentare  
 Der Treiber ruft **sqldrivertodatasource** auf, um alle Daten (SQL-Anweisungen, Parameter usw.) zu übersetzen, die vom Treiber an die Datenquelle übergeben werden. Die Übersetzungs-DLL übersetzt möglicherweise einige Daten nicht, je nach Datentyp und Zweck der Übersetzungs-DLL. Eine DLL, die Zeichendaten aus einer Codepage in eine andere übersetzt, ignoriert beispielsweise alle numerischen und binären Daten.  
  
 Der Wert von *fOption* wird auf den Wert von *vParam* festgelegt, der durch Aufrufen von **SQLSetConnectAttr** mit dem SQL_ATTR_TRANSLATE_OPTION-Attribut angegeben wird. Dabei handelt es sich um einen 32-Bit-Wert, der für eine bestimmte Übersetzungs-DLL eine bestimmte Bedeutung hat. Beispielsweise kann eine bestimmte Zeichensatz Übersetzung angegeben werden.  
  
 Wenn derselbe Puffer für *rgbvaluein* und *rgbvalueout*angegeben wird, wird die Übersetzung der Daten im Puffer direkt ausgeführt.  
  
 Obwohl *cbvaluein*, *cbvalueoutmax*und *pcbvalueout* den Typ SDWORD aufweisen, unterstützt **sqldriverydatasource** nicht notwendigerweise große Zeiger.  
  
 Wenn **sqldriverumdatasource** den Wert false zurückgibt, ist möglicherweise während der Übersetzung ein Abschneiden der Daten aufgetreten. Wenn *pcbvalueout* (die Anzahl der verfügbaren Bytes im Ausgabepuffer) größer als *cbvalueoutmax* (die Länge des Ausgabepuffers) ist, ist ein Abschneiden aufgetreten. Der Treiber muss feststellen, ob das Abschneiden akzeptabel ist. Wenn keine abkürzen erfolgt ist, hat **sqldrivergedatasource** aufgrund eines anderen Fehlers false zurückgegeben. In beiden Fällen wird eine bestimmte Fehlermeldung in *szErrorMsg*zurückgegeben.  
  
 Weitere Informationen zum Übersetzen von Daten finden Sie unter [Translation DLLs](../../../odbc/reference/develop-app/translation-dlls.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Konvertieren von Daten, die von der Datenquelle zurückgegeben werden|[Sqldatasourceto Driver](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|  
|Zurückgeben der Einstellung eines Verbindungs Attributs|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Festlegen eines Verbindungs Attributs|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
