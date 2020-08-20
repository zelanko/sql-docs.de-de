---
description: Treiberfähiges Verbindungspooling
title: Treiber fähiges Verbindungs Pooling | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 53e7e3f7-edab-4d0b-8943-45442ba3ebc9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ed2fa29a68095be9cfcc7d4192c6dc2e15f3eac7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494658"
---
# <a name="driver-aware-connection-pooling"></a>Treiberfähiges Verbindungspooling
Treiber fähiges Verbindungspooling ist ein neues Feature des Treiber-Managers in Windows 8. Treiber fähiges Verbindungspooling ermöglicht es Treiber Entwicklern, das Verbindungspooling Verhalten in Ihrem ODBC-Treiber anzupassen.  
  
> [!NOTE]  
>  Treiber fähiges Verbindungspooling wird bei der Cursor Bibliothek nicht unterstützt. Eine Anwendung empfängt eine Fehlermeldung, wenn versucht wird, die Cursor Bibliothek über SQLSetConnectAttr zu aktivieren, wenn das Verbindungspooling für Treiber aktiviert ist.  
  
 Treiber fähiges Verbindungspooling behandelt die folgenden Probleme im Zusammenhang mit dem Treiber-Manager-Verbindungspooling:  
  
 **Pool Fragmentierung** Der Treiber-Manager gibt nur dann eine Verbindung aus dem Pool zurück, wenn es sich um eine genaue Entsprechung mit der Verbindungs Zeichenfolge einer neuen Verbindungsanforderung handelt.  Ein Grund dafür, dass der Treiber-Manager eine genaue Entsprechung erfordert, ist, dass der Treiber-Manager nicht alle treiberspezifischen Verbindungs Zeichenfolgen-Schlüsselwörter und deren Wert versteht.  Einige Schlüsselwort Werte für Verbindungs Zeichenfolgen (z. b. der Name der Datenbank) erfordern jedoch möglicherweise keine genaue Entsprechung, da der Treiber die Datenbank in weniger Zeit ändern kann, die zum Öffnen einer neuen Verbindung benötigt wird (der genaue Zeitunterschied hängt von der Datenquelle ab). Und Unterschiede in einigen Verbindungs Attributen (z. b. SQL_ATTR_CURRENT_CATALOG) können mehr Zeit in Anspruch nehmen als die Unterschiede in anderen Attributen (z. b. SQL_ATTR_LOGIN_TIMEOUT). Dies kann auch verhindern, dass der Treiber-Manager die kostengünstigste, wiederverwendbare Verbindung aus dem Pool verwendet. Wenn ein Treiber viele neue Verbindungen erstellen muss, kann die Leistung einer Anwendung verringert werden, und die Skalierbarkeit der Datenquelle kann abnehmen. Die Pool Fragmentierung kann mit dem Treiber fähigen Verbindungspooling reduziert werden, da ein Treiber die Kosten für die Wiederverwendung einer Verbindung im Pool für eine Verbindungsanforderung besser einschätzen kann.  
  
 **Keine Berücksichtigung der Anwendungs** Einstellung Einige Datenquellen können neue Verbindungen effizient öffnen (im Gegensatz zum Zurücksetzen einiger Attribute). Daher kann es sein, dass eine Anwendung eine neue Verbindung öffnet, anstatt zu versuchen, eine nicht übereinstimmende Verbindung aus dem Pool wiederzuverwenden und einige Werte zurückzusetzen (obwohl dies während der Initialisierungs Phrase des Verbindungspools langsamer sein kann). Bei einigen Anwendungen wird der Server jedoch möglicherweise kleiner, und es werden weniger Verbindungen geöffnet, obwohl es möglicherweise zu größeren Kosten kommt, um die Konflikte für das korrekte Verhalten zu beheben. Ohne Treiber fähiges Verbindungspooling können Sie diese Art von Vorgängen nicht effektiv angeben, da der Treiber-Manager nicht alle treiberspezifischen Verbindungs Attribute erkennt. Treiber fähiges Verbindungspooling ermöglicht einem Treiber das Abrufen der Benutzereinstellungen (mit einem treiberspezifischen Attribut von SQLSetConnectAttr), um die Kosten für die Wiederverwendung einer Verbindung aus dem Pool basierend auf der Benutzereinstellung besser einschätzen zu können.  
  
 Weitere Informationen zum Treiber fähigen Verbindungspooling finden Sie unter [entwickeln von Verbindungs Pool Informationen in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
## <a name="determining-driver-support"></a>Bestimmen der Treiberunterstützung  
 Treiber fähiges Verbindungspooling ist ein optionales Feature, das von einem Treiber möglicherweise nicht unterstützt wird. Verwenden Sie den SQL_DRIVER_AWARE_POOLING_SUPPORTED *InfoType* von [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), um zu bestimmen, ob er von einem Treiber unterstützt wird.  
  
## <a name="how-to-enable-driver-aware-connection-pooling"></a>Aktivieren von Treiber fähiger Verbindungs Pooling  
 Eine Anwendung kann die Verbindung mit dem Verbindungspooling eines Treibers verwenden, indem das SQL_ATTR_CONNECTION_POOLING-Attribut auf SQL_CP_DRIVER_AWARE mit [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)festgelegt wird. Wenn ein Treiber keine Informationen zum Verbindungspool unterstützt, wird das Verbindungspooling des Treiber-Managers verwendet (identisch mit der Angabe, ob SQL_CP_ONE_PER_HENV statt SQL_CP_DRIVER_AWARE). Diese Funktion kann von ODBC 2. x-und 3. x-Anwendungen aktiviert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Developing an ODBC Driver (Entwickeln eines ODBC-Treibers)](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
