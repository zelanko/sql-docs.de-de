---
title: Fehlermeldungen (Visual FoxPro ODBC-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], error messages
- SQLSTATE [ODBC]
- FoxPro ODBC driver [ODBC], error messages
ms.assetid: 58ea9734-4edf-44da-ba80-938aa7b340e4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31f894e58da93fe6091dba306f8b765d14bac2cb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286400"
---
# <a name="error-messages-visual-foxpro-odbc-driver"></a>Fehlermeldungen (Visual FoxPro-ODBC-Treiber)
Wenn ein Fehler auftritt, gibt der Visual FoxPro-Treiber die folgenden Informationen zurück:  
  
-   Die systemeigene Fehlernummer und der Fehlermeldungstext  
  
-   Der SQLSTATE (ein ODBC-Fehlercode) und der Fehlermeldungstext  
  
 Sie greifen auf diese Fehlerinformationen zu, indem Sie [SQLError](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md)aufrufen.  
  
## <a name="native-errors"></a>Systemeigene Fehler  
 Bei Fehlern, die in der Datenquelle auftreten, gibt der Visual FoxPro-Treiber die systemeigene Fehlernummer und den Fehlermeldungstext zurück. Eine Liste der systemeigenen Fehlernummern finden Sie unter [Visual FoxPro ODBC Driver Native Error Messages](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md).  
  
## <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (ODBC-Fehlercodes)  
 Bei Fehlern, die vom Visual FoxPro-Treiber erkannt und zurückgegeben werden, ordnet der Treiber die zurückgegebene systemeigene Fehlernummer der entsprechenden SQLSTATE zu. Wenn eine systemeigene Fehlernummer nicht über einen ODBC-Fehlercode verfügt, dem zugeordnet werden kann, gibt der Visual FoxPro-Treiber SQLSTATE S1000 (Allgemeiner Fehler) zurück.  
  
 Eine Liste der SQLSTATE-Werte, die vom Visual FoxPro ODBC-Treiber für entsprechende Visual FoxPro-Fehler generiert werden, finden Sie unter [ODBC-Fehlercodes](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).  
  
## <a name="syntax"></a>Syntax  
 Fehlermeldungen haben das folgende Format:  
  
 **[** *Anbieter* **][** *ODBC_component* **]** *error_message*  
  
 Die Präfixe in Klammern ([ ]) identifizieren die Ursache des Fehlers, wie in der folgenden Tabelle definiert.  
  
|Datenquelle|Präfix|Wert|  
|-----------------|------------|-----------|  
|Treiber-Manager|[Lieferant]<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[ODBC-Treiber-Manager]<br />Nicht zutreffend|  
|Visual FoxPro-Treiber|Anbieter]<br />[ODBC_component]<br />[data_source]|[Microsoft]<br />[ODBC Visual FoxPro-Treiber]<br />Nicht zutreffend|  
  
 Wenn der Visual FoxPro ODBC-Treiber z. B. die Datei employee.dbf nicht finden konnte, wird möglicherweise die folgende Fehlermeldung zurückgegeben:  
  
 "[*Microsoft*][*ODBC Visual FoxPro Driver*]Datei 'employee.dbf' ist nicht vorhanden"
