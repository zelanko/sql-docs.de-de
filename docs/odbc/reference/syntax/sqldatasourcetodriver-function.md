---
title: SQLDataSourceToDriver-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 92df58b76a9a11d0d4ab9821756bff014ecae29a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301190"
---
# <a name="sqldatasourcetodriver-function"></a>SQLDataSourceToDriver-Funktion
**SQLDataSourceToDriver** unterstützt Übersetzungen für ODBC-Treiber. Diese Funktion wird nicht von ODBC-fähigen Anwendungen aufgerufen. Anwendungen fordern die Übersetzung über **SQLSetConnectAttr**an. Der dem ConnectionHandle zugeordnete *Treiber,* der in **SQLSetConnectAttr** angegeben ist, ruft die angegebene DLL auf, um Übersetzungen aller Daten durchzuführen, die von der Datenquelle an den Treiber fließen. Eine Standard-Übersetzungs-DLL kann in der ODBC-Initialisierungsdatei angegeben werden.  
  
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
 [Eingabe] Optionswert.  
  
 *fSqlType*  
 [Eingabe] Der SQL-Datentyp. Dieses Argument teilt dem Treiber mit, wie *rgbValueIn* in ein von der Anwendung akzeptables Formular konvertiert wird. Eine Liste gültiger SQL-Datentypen finden Sie im Abschnitt [SQL-Datentypen](../../../odbc/reference/appendixes/sql-data-types.md) in Anhang D: Datentypen.  
  
 *rgbValueIn*  
 [Eingabe] Wert zu übersetzen.  
  
 *cbValueIn*  
 [Eingabe] Länge von *rgbValueIn*.  
  
 *rgbValueOut*  
 [Ausgabe] Ergebnis der Übersetzung.  
  
> [!NOTE]  
>  Die Übersetzungs-DLL beendet diesen Wert nicht null.  
  
 *cbValueOutMax*  
 [Eingabe] Länge von *rgbValueOut*.  
  
 *pcbValueOut*  
 [Ausgabe] Die Gesamtzahl der Bytes (mit Ausnahme des Null-Beendigungsbytes), die in *rgbValueOut*zurückgegeben werden können.  
  
 Bei Zeichen- oder Binärdaten werden die Daten in *rgbValueOut* auf *cbValueOutMax-Bytes* abgeschnitten, wenn diese größer oder gleich *cbValueOutMax*sind.  
  
 Bei allen anderen Datentypen wird der Wert von *cbValueOutMax* ignoriert, und die Übersetzungs-DLL geht davon aus, dass die Größe von *rgbValueOut* die Größe des Standard-C-Datentyps des mit *fSqlType*angegebenen SQL-Datentyps ist.  
  
 Das *Argument pcbValueOut* kann ein Nullzeiger sein.  
  
 *szErrorMsg*  
 [Ausgabe] Zeiger auf den Speicher für eine Fehlermeldung. Dies ist eine leere Zeichenfolge, es sei denn, die Übersetzung ist fehlgeschlagen.  
  
 *cbErrorMsgMax*  
 [Eingabe] Länge von *szErrorMsg*.  
  
 *pcbErrorMsg*  
 [Ausgabe] Zeiger auf die Gesamtzahl der Bytes (mit Ausnahme des Null-Beendigungs-Bytes), die in *szErrorMsg*zurückgegeben werden können. Wenn dies größer oder gleich *cbErrorMsg*ist, werden die Daten in *szErrorMsg* auf *cbErrorMsgMax* abzüglich des Nullbeendigungszeichens abgeschnitten. Das Argument *pcbErrorMsg* kann ein Nullzeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 TRUE wenn die Übersetzung erfolgreich war, FALSE, wenn die Übersetzung fehlgeschlagen ist.  
  
## <a name="comments"></a>Kommentare  
 Der Treiber ruft **SQLDataSourceToDriver** auf, um alle Daten (Ergebnissatzdaten, Tabellennamen, Zeilenanzahlen, Fehlermeldungen usw.) zu übersetzen, die von der Datenquelle an den Treiber übergeben werden. Die Übersetzungs-DLL übersetzt möglicherweise einige Daten nicht, je nach Typ der Daten und dem Zweck der Übersetzungs-DLL; Beispielsweise ignoriert eine DLL, die Zeichendaten von einer Codepage in eine andere übersetzt, alle numerischen und binären Daten.  
  
 Der Wert von *fOption* wird auf den Wert von *vParam* festgelegt, der durch Aufrufen von **SQLSetConnectAttr** mit dem Attribut SQL_ATTR_TRANSLATE_OPTION angegeben wird. Es ist ein 32-Bit-Wert, der eine bestimmte Bedeutung für eine bestimmte Übersetzungs-DLL hat. Sie könnte z. B. eine bestimmte Zeichensatzübersetzung angeben.  
  
 Wenn derselbe Puffer für *rgbValueIn* und *rgbValueOut*angegeben ist, wird die Übersetzung der Daten im Puffer an Ort und Stelle durchgeführt.  
  
 Obwohl *cbValueIn*, *cbValueOutMax*und *pcbValueOut* vom Typ SDWORD sind, unterstützt **SQLDataSourceToDriver** nicht unbedingt große Zeiger.  
  
 Wenn **SQLDataSourceToDriver** FALSE zurückgibt, ist möglicherweise während der Übersetzung eine Datenkürzung aufgetreten. Wenn *pcbValueOut* (die Anzahl der Bytes, die im Ausgabepuffer zurückgegeben werden können) größer als *cbValueOutMax* (die Länge des Ausgabepuffers) ist, ist eine Abschneide erfolgt. Der Treiber muss feststellen, ob die Kürzung akzeptabel war. Wenn keine Abschneidung aufgetreten ist, hat **DER SQLDataSourceToDriver** FALSE aufgrund eines anderen Fehlers zurückgegeben. In beiden Fällen wird eine bestimmte Fehlermeldung in *szErrorMsg*zurückgegeben.  
  
 Weitere Informationen zum Übersetzen von Daten finden Sie unter [Übersetzungs-DLLs](../../../odbc/reference/develop-app/translation-dlls.md).  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Übersetzen von Daten, die an die Datenquelle gesendet werden|[SQLDriverToDataSource](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|  
|Zurückgeben der Einstellung eines Verbindungsattributs|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Festlegen eines Verbindungsattributs|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|
