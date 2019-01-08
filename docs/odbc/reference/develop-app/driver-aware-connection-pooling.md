---
title: Treiberfähiges Verbindungspooling | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 53e7e3f7-edab-4d0b-8943-45442ba3ebc9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ea4643354990ad416ac3975467c5991842adacc
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52390573"
---
# <a name="driver-aware-connection-pooling"></a>Treiberfähiges Verbindungspooling
Treiber bewusst Verbindungspooling ist eine neue Funktion des Treiber-Managers in Windows 8. Treiber bewusst Verbindungspooling kann Treiber Writer zum Anpassen der Verbindungspooling-Verhalten in ihren ODBC-Treiber.  
  
> [!NOTE]  
>  Beachten Sie Verbindungspooling der Treiber wird mit Cursorbibliothek nicht unterstützt. Eine Anwendung wird die Fehlermeldung angezeigt, wenn es versucht, Cursorbibliothek über SQLSetConnectAttr, aktivieren, wenn Treiber bewusst Verbindungspooling aktiviert ist.  
  
 Treiberfähigen Verbindungspoolings Treiber Adressen beziehen sich die folgenden Probleme auf Treibermanager-Verbindungspooling:  
  
 **Fragmentierung Pool** der Treiber-Manager wird nur eine Verbindung aus dem Pool eine genaue Übereinstimmung mit der Verbindungszeichenfolge eine neue verbindungsanforderung wird zurückgegeben.  Ein Grund für den Treiber-Manager, um eine genaue Übereinstimmung erforderlich ist, dass der Treiber-Manager alle Treiber-spezifische Schlüsselwort für Verbindungszeichenfolgen und dessen Wert nicht interpretieren kann.  Allerdings können einige Werte der Verbindungszeichenfolge-Schlüsselwort (z. B. den Namen der Datenbank) eine genaue Übereinstimmung, nicht erforderlich, da der Treiber die Datenbank in weniger als die zum Öffnen einer neuen Verbindung (der Unterschied für die genaue Zeit hängt von der Datenquelle) erforderliche Zeit ändern kann. Und Unterschiede in der einige Verbindungsattribute (z. B. SQL_ATTR_CURRENT_CATALOG) dauert länger als die Unterschiede bei den anderen Attributen (z. B. SQL_ATTR_LOGIN_TIMEOUT) ändern. Dies kann auch verhindern, dass der Treiber-Manager die niedrigsten Kosten, wieder verwendbare Verbindung aus dem Pool verwenden. Wenn ein Treiber besitzt viele neue Verbindungen zu erstellen, kann die Leistung einer Anwendung verringern und die Data-Source-Skalierbarkeit verringern kann. Poolfragmentierung kann reduziert werden, mit dem treiberfähiges Verbindungspooling, da der Treiber die Kosten für die Wiederverwendung von eine Verbindung im Pool eine verbindungsanforderung besser schätzen zu kann.  
  
 **Keine Berücksichtigung der anwendungseinstellung** einige Datenquellen können effizient neue Verbindungen (im Vergleich zum Zurücksetzen von einige Attribute), also öffnen, eine Anwendung bevorzugt Öffnen einer neuen Verbindung anstatt zu versuchen, eine etwas nicht übereinstimmende wiederverwenden die Verbindung aus dem Pool und einige Werte (obwohl dies langsamer während der Verbindung Pool Initialisierung Ausdruck sein kann) zurücksetzen. Aber einige Anwendungen möglicherweise behalten Sie die Serverlast kleinere und kleinere Anzahl von Verbindungen zu öffnen, es kann jedoch auch größere Kosten, die Konflikte für korrektes Verhalten zu beheben. Ohne treiberfähiges Verbindungspooling, können nicht Sie diese Art der Einstellung tatsächlich angeben, da der Treiber-Manager alle treiberspezifische Verbindungsattribute nicht erkannt wird. Treiberfähiges Verbindungspooling kann Treiber für die benutzereinstellung (mit Driver-spezifischen Attributen der SQLSetConnectAttr) zu erhalten, damit sie die Kosten für die Wiederverwendung von eine Verbindung aus dem Pool basierend auf den Einstellungen des Benutzers besser schätzen zu kann.  
  
 Weitere Informationen zum treiberfähiges Verbindungspooling finden Sie unter [Entwickeln von Verbindungspool Unterstützung in einem ODBC-Treiber](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
## <a name="determining-driver-support"></a>Bestimmen der Treiberunterstützung  
 Treiberfähiges Verbindungspooling ist ein optionales Feature, das ein Treiber nicht unterstützt. Um festzustellen, ob ein Treiber unterstützt, verwenden Sie die SQL_DRIVER_AWARE_POOLING_SUPPORTED *Informationsart* von [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
## <a name="how-to-enable-driver-aware-connection-pooling"></a>Treiberfähiges Verbindungspooling aktivieren  
 Eine Anwendung kann eine Fahrers Verbindungspooling Awareness verwenden, durch Festlegen der SQL_ATTR_CONNECTION_POOLING-Attributs auf SQL_CP_DRIVER_AWARE mit [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Wenn Sie ein Treiber Verbindungspool Unterstützung nicht unterstützt, Treibermanager-Verbindungspooling verwendet werden (als ob SQL_CP_ONE_PER_HENV wäre, statt SQL_CP_DRIVER_AWARE angegeben worden identisch). ODBC 2.x und 3.x-Anwendungen können diese Funktion aktivieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Developing an ODBC Driver (Entwickeln eines ODBC-Treibers)](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
