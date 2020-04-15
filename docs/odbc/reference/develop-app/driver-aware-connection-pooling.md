---
title: Treiber-Aware-Verbindungspooling | Microsoft Docs
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
ms.openlocfilehash: 70b70c841f37bd69179137c807c0dadcfd932d2b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287600"
---
# <a name="driver-aware-connection-pooling"></a>Treiberfähiges Verbindungspooling
Treiber-fähiges Verbindungspooling ist eine neue Funktion des Treiber-Managers in Windows 8. Das treiberbewusste Verbindungspooling ermöglicht es Treiberautoren, das Verbindungspoolverhalten in ihrem ODBC-Treiber anzupassen.  
  
> [!NOTE]  
>  Treiberfähiges Verbindungspooling wird mit der Cursorbibliothek nicht unterstützt. Eine Anwendung erhält eine Fehlermeldung, wenn sie versucht, die Cursorbibliothek über SQLSetConnectAttr zu aktivieren, wenn das treiberbewusste Verbindungspooling aktiviert ist.  
  
 Das treiberbewusste Verbindungspooling behebt die folgenden Probleme im Zusammenhang mit dem Treiber-Manager-Verbindungspooling:  
  
 **Poolfragmentierung** Der Treiber-Manager gibt eine Verbindung aus dem Pool nur dann zurück, wenn es sich um eine exakte Übereinstimmung mit der Verbindungszeichenfolge einer neuen Verbindungsanforderung handelt.  Ein Grund für den Treiber-Manager, eine genaue Übereinstimmung zu verlangen, ist, dass der Treiber-Manager nicht jedes treiberspezifische Verbindungszeichenfolgenschlüsselwort und seinen Wert versteht.  Einige Schlüsselwortwerte für Verbindungszeichenfolgen (z. B. der Name der Datenbank) erfordern jedoch möglicherweise keine genaue Übereinstimmung, da der Treiber die Datenbank in weniger als der Zeit ändern kann, die zum Öffnen einer neuen Verbindung erforderlich ist (die genaue Zeitdifferenz hängt von der Datenquelle ab). Und Unterschiede in einigen Verbindungsattributen (z. B. SQL_ATTR_CURRENT_CATALOG) können mehr Zeit in Anspruch nehmen, sich zu ändern, als Unterschiede in anderen Attributen (z. B. SQL_ATTR_LOGIN_TIMEOUT). Auch dies kann verhindern, dass der Treiber-Manager die kostengünstigste, wiederverwendbare Verbindung aus dem Pool verwendet. Wenn ein Treiber viele neue Verbindungen erstellen muss, kann die Leistung einer Anwendung und die Skalierbarkeit der Datenquelle verringern. Die Poolfragmentierung kann durch fahrerbewusstes Verbindungspooling reduziert werden, da ein Treiber die Kosten für die Wiederverwendung einer Verbindung im Pool für eine Verbindungsanforderung besser abschätzen kann.  
  
 **Keine Berücksichtigung der Anwendungspräferenz** Einige Datenquellen können effizient neue Verbindungen öffnen (im Vergleich zum Zurücksetzen einiger Attribute), daher kann es vorkommen, dass eine Anwendung eine neue Verbindung öffnet, anstatt zu versuchen, eine leicht übereinstimmende Verbindung aus dem Pool wiederzuverwenden und einige Werte zurückzusetzen (obwohl dies während der Initialisierungsphrase des Verbindungspools möglicherweise langsamer ist). Einige Anwendungen können jedoch die Serverlast kleiner halten und weniger Verbindungen öffnen, obwohl es möglicherweise höhere Kosten für die Behebung der Inkongruenzen für das korrekte Verhalten gibt. Ohne treiberorientiertes Verbindungspooling können Sie diese Art von Voreinstellung nicht effektiv angeben, da der Treiber-Manager nicht alle treiberspezifischen Verbindungsattribute erkennt. Das treiberorientierte Verbindungspooling ermöglicht es einem Treiber, die Benutzereinstellung (mit einem treiberspezifischen Attribut von SQLSetConnectAttr) abzuerhalten, sodass er die Kosten für die Wiederverwendung einer Verbindung aus dem Pool basierend auf den Einstellungen eines Benutzers besser abschätzen kann.  
  
 Weitere Informationen zum treiberbewussten Verbindungspooling finden Sie unter [Entwickeln von Verbindungspool-Awareness in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
## <a name="determining-driver-support"></a>Bestimmen der Treiberunterstützung  
 Treiber-fähiges Verbindungspooling ist eine optionale Funktion, die ein Treiber möglicherweise nicht unterstützt. Um zu ermitteln, ob ein Treiber dies unterstützt, verwenden Sie den SQL_DRIVER_AWARE_POOLING_SUPPORTED *InfoType* von [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
## <a name="how-to-enable-driver-aware-connection-pooling"></a>So aktivieren Sie das Pooling für treiberbewusste Verbindungen  
 Eine Anwendung kann die Verbindungspool-Awareness eines Treibers verwenden, indem sie das Attribut SQL_ATTR_CONNECTION_POOLING auf SQL_CP_DRIVER_AWARE mit [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Wenn ein Treiber die Bekanntheit des Verbindungspools nicht unterstützt, wird das Driver Manager-Verbindungspooling verwendet (so, als ob SQL_CP_ONE_PER_HENV angegeben wurde, anstatt SQL_CP_DRIVER_AWARE). ODBC 2.x- und 3.x-Anwendungen können diese Funktion aktivieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Developing an ODBC Driver (Entwickeln eines ODBC-Treibers)](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
