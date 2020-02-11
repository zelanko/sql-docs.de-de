---
title: Treiber spezifische Verbindungsinformationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConnect function [ODBC], driver-specific connection information
- connecting to driver [ODBC], SQLConnect
- SQLDriverConnect function [ODBC], driver specific connection information
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], SQLConnect
- connecting to driver [ODBC], driver-specific information
ms.assetid: 3748758a-f16a-4f3b-9c40-06f2e300704e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 69f2c98678739a8b7879e152e13546f2bf9b9cc1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046932"
---
# <a name="driver-specific-connection-information"></a>Treiberspezifische Verbindungsinformationen
**SQLCONNECT** geht davon aus, dass ein Datenquellen Name, eine Benutzer-ID und ein Kennwort zum Herstellen einer Verbindung mit einer Datenquelle ausreichen und alle anderen Verbindungsinformationen auf dem System gespeichert werden können. Dies ist häufig nicht der Fall. Beispielsweise kann ein Treiber eine Benutzer-ID und ein Kennwort für die Anmeldung an einem Server und eine andere Benutzer-ID und ein anderes Kennwort für die Anmeldung bei einem DBMS benötigen. Da **SQLCONNECT** eine einzelne Benutzer-ID und ein Kennwort akzeptiert, bedeutet dies, dass die andere Benutzer-ID und das Kennwort mit den Datenquellen Informationen im System gespeichert werden müssen, wenn **SQLCONNECT** verwendet werden soll. Dies ist eine potenzielle Sicherheitsverletzung und sollte vermieden werden, es sei denn, das Kennwort ist verschlüsselt.  
  
 **SQLDriverConnect** ermöglicht es dem Treiber, eine beliebige Menge an Verbindungsinformationen in den Schlüsselwort-Wert-Paaren der Verbindungs Zeichenfolge zu definieren. Nehmen wir beispielsweise an, dass ein Treiber einen Datenquellen Namen, eine Benutzer-ID und ein Kennwort für den Server sowie eine Benutzer-ID und ein Kennwort für das DBMS benötigt. Ein benutzerdefiniertes Programm, das immer die XYZ Corp-Datenquelle verwendet, kann den Benutzer zur Eingabe von IDs und Kenn Wörtern auffordern und den folgenden Satz von Schlüsselwort-Wert-Paaren oder *Verbindungs Zeichenfolge erstellen,* um Sie an **SQLDriverConnect**zu übergeben:  
  
> [!NOTE]  
>  Wenn Sie eine Verbindung mit einem Datenquellen Anbieter herstellen, der die Windows-Authentifizierung unter `Trusted_Connection=yes` stützt, sollten Sie anstelle von Benutzer-ID-und Kenn Wort Informationen in der Verbindungs Zeichenfolge angeben.  
  
```  
DSN={MyDataSourceName};UID={MyUserID};PWD={MyServerPassword};UIDDBMS={MyDBMSUserID};PWDDBMS={MyDBMSUserPassword};  
```  
  
 Das **DSN** -Schlüsselwort (Datenquellen Name) benennt die Datenquelle, die Schlüsselwörter **UID** und **pwd** geben die Benutzer-ID und das Kennwort für den Server an, und die Schlüsselwörter **uiddbms** und **pwddbms** geben die Benutzer-ID und das Kennwort für das DBMS an. Beachten Sie, dass das abschließende Semikolon optional ist. **SQLDriverConnect** analysiert diese Zeichenfolge. verwendet den XYZ Corp Corp-Datenquellen Namen, um zusätzliche Verbindungsinformationen aus dem System abzurufen, z. b. die Server Adresse; und anmelden sich beim Server und DBMS mithilfe der angegebenen Benutzer-IDs und Kenn Wörter.  
  
 Schlüsselwort-Wert-Paare in **SQLDriverConnect** müssen bestimmten Syntax Regeln folgen. Die Schlüsselwörter und ihre Werte dürfen nicht **[]{}(),;? enthalten. = \*! @** Zeichen. Der Wert des **DSN** -Schlüssel Worts darf nicht nur aus Leerzeichen bestehen und darf keine führenden Leerzeichen enthalten. Aufgrund der Registrierungs Grammatik dürfen Schlüsselwörter und Datenquellen Namen keinen umgekehrten Schrägstrich (\\) enthalten. Leerzeichen sind um das Gleichheitszeichen im Schlüsselwort-Wert-Paar nicht zulässig.  
  
 Das **FILEDSN** -Schlüsselwort kann in einem **SQLDriverConnect** -Befehl verwendet werden, um den Namen einer Datei anzugeben, die Datenquellen Informationen enthält (siehe [Herstellen einer Verbindung mithilfe von Datei Datenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)weiter unten in diesem Abschnitt). Das **SaveFile** -Schlüsselwort kann verwendet werden, um den Namen einer DSN-Datei anzugeben, in der die Schlüsselwort-Wert-Paare einer erfolgreichen Verbindung, die durch den **SQLDriverConnect** -Befehl erstellt wird, gespeichert werden. Weitere Informationen zu Datei Datenquellen finden Sie in der Beschreibung der [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) -Funktion.
