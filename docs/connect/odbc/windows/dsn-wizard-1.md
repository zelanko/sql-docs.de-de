---
title: Datenquellen-Assistentenbildschirm 1 (ODBC-Treiber für SQLServer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f13746005f05d84bd8b987fe048baf392e81af3b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47641971"
---
# <a name="data-source-wizard-screen-1"></a>Datenquellen-Assistent (Bildschirm 1)

Geben Sie den Namen und die Beschreibung der Datenquelle und den Namen des Servers an, auf dem SQL Server ausgeführt wird und mit dem die Datenquelle eine Verbindung herstellen wird. 
    
## <a name="options"></a>Tastatur

### <a name="name"></a>Name

Der von einer ODBC-Anwendung verwendete Datenquellenname, wenn sie eine Verbindung mit der Datenquelle anfordert. Beispielsweise „Personal“. Der Name der Datenquelle wird im Dialogfeld ODBC-Datenquellen-Administrator angezeigt.

### <a name="description"></a>und Beschreibung

(Optional) Eine Beschreibung der Datenquelle. Zum Beispiel „Einstellungsdatum, Gehaltsverlauf und aktuelle Überprüfung aller Mitarbeiter“.

### <a name="select-or-enter-a-server-name"></a>Wählen Sie einen Servernamen aus, oder geben Sie ihn ein.

Der Name einer Instanz von SQL Server in Ihrem Netzwerk. Sie müssen im nächsten Eingabefeld einen Server angeben.

In den meisten Fällen kann der ODBC-Treiber eine Verbindung mit der Standardprotokollreihenfolge und dem in diesem Feld bereitgestellten Servernamen herstellen. Mit dem SQL Server-Konfigurations-Manager können Sie einen Alias für den Server erstellen oder Clientnetzwerkbibliotheken konfigurieren.

Sie können „(local)“ in das Serverfeld eingeben, wenn Sie den gleichen Computer wie SQL Server verwenden. Der Benutzer kann anschließend eine Verbindung mit der lokalen Instanz von SQL Server herstellen, selbst wenn eine nicht vernetzte Version von SQL Server ausgeführt wird. Es können mehrere Instanzen von SQL Server auf demselben Computer ausführen. Um eine benannte Instanz von SQL Server anzugeben, wird der Servername im Format _Servername_\\_Instanzname_ angegeben.

Weitere Informationen über Servernamen für andere Typen von Netzwerken finden Sie in der SQL Server-Installationsdokumentation in der SQL Server-Onlinedokumentation.

### <a name="finish"></a>Fertig stellen

Wenn über die auf diesem Bildschirm angegebenen Informationen hinaus keine weiteren Informationen zum Herstellen einer Verbindung mit SQL Server erforderlich sind, können Sie auf **Fertig stellen** klicken. Für alle auf anderen Bildschirmen des Assistenten angegebenen Attribute werden Standardwerte verwendet.

### <a name="next"></a>Weiter

Um zum nächsten Bildschirm des Assistenten fortzufahren, klicken Sie auf **Weiter**.

## <a name="next-steps"></a>Nächste Schritte

[Datenquellen-Assistent (Bildschirm 2)](../../../connect/odbc/windows/dsn-wizard-2.md)
