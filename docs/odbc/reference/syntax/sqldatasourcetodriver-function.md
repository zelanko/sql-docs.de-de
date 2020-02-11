---
title: Sqldatasourceto Driver-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: ba5019b15fdbb8bce06f04d5109813b88c40647d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68104847"
---
# <a name="sqldatasourcetodriver-function"></a>SQLDataSourceToDriver-Funktion
**Sqldatasourceto Driver** supportstranslations für ODBC-Treiber. Diese Funktion wird nicht von ODBC-fähigen Anwendungen aufgerufen. Anwendungen fordern Übersetzungen über **SQLSetConnectAttr**an. Der Treiber, der dem in **SQLSetConnectAttr** angegebenen *connectionHandle* zugeordnet ist, ruft die angegebene DLL auf, um Übersetzungen für alle Daten zu übertragen, die von der Datenquelle an den Treiber fließen. In der ODBC-Initialisierungsdatei kann eine standardmäßige Übersetzungs-DLL angegeben werden.  
  
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
 Der Optionswert.  
  
 *Typ "f"*  
 Der Der SQL-Datentyp. Dieses Argument weist den Treiber an, wie *rgbvaluein* in ein von der Anwendung akzeptables Formular konvertiert werden kann. Eine Liste gültiger SQL-Datentypen finden Sie im Abschnitt [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen.  
  
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
 Der Treiber ruft **sqldatasourcetodriver** auf, um alldata (Resultsetdaten, Tabellennamen, Zeilen Anzahl, Fehlermeldungen usw.) zu übersetzen, die von der Datenquelle an den Treiber übergeben werden. Die Übersetzungs-DLL übersetzt möglicherweise einige Daten nicht, je nach Datentyp und Zweck der Übersetzungs-DLL. eine DLL, die Zeichendaten aus einer Codepage in eine andere übersetzt, ignoriert beispielsweise alle numerischen und binären Daten.  
  
 Der Wert von *fOption* wird auf den Wert von *vParam* festgelegt, der durch Aufrufen von **SQLSetConnectAttr** mit dem SQL_ATTR_TRANSLATE_OPTION-Attribut angegeben wird. Dabei handelt es sich um einen 32-Bit-Wert, der für eine bestimmte Übersetzungs-DLL eine bestimmte Bedeutung hat. Beispielsweise kann eine bestimmte Zeichensatz Übersetzung angegeben werden.  
  
 Wenn derselbe Puffer für *rgbvaluein* und *rgbvalueout*angegeben wird, wird die Übersetzung der Daten im Puffer direkt ausgeführt.  
  
 Obwohl *cbvaluein*, *cbvalueoutmax*und *pcbvalueout* den Typ SDWORD haben, unterstützt **sqldatasourcededriver** nicht notwendigerweise große Zeiger.  
  
 Wenn **sqldatasourcetdriver** false zurückgibt, ist möglicherweise während der Übersetzung ein Abschneiden der Daten aufgetreten. Wenn *pcbvalueout* (die Anzahl der verfügbaren Bytes im Ausgabepuffer) größer als *cbvalueoutmax* (die Länge des Ausgabepuffers) ist, ist ein Abschneiden aufgetreten. Der Treiber muss feststellen, ob das Abschneiden akzeptabel ist. Wenn keine abkürzen erfolgt ist, hat **sqldatasourceto Driver** aufgrund eines anderen Fehlers false zurückgegeben. In beiden Fällen wird eine bestimmte Fehlermeldung in *szErrorMsg*zurückgegeben.  
  
 Weitere Informationen zum Übersetzen von Daten finden Sie unter [Translation DLLs](../../../odbc/reference/develop-app/translation-dlls.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Übersetzen von Daten, die an die Datenquelle gesendet werden|[Sqldriverflidatasource](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|  
|Zurückgeben der Einstellung eines Verbindungs Attributs|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Festlegen eines Verbindungs Attributs|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
