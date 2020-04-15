---
title: Treiberspezifische Verbindungsinformationen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 16c8c5fc4fd3ac63aa3613b41e530446dffec118
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305791"
---
# <a name="driver-specific-connection-information"></a>Treiberspezifische Verbindungsinformationen
**SQLConnect** geht davon aus, dass ein Datenquellenname, eine Benutzer-ID und ein Kennwort ausreichen, um eine Verbindung mit einer Datenquelle herzustellen, und dass alle anderen Verbindungsinformationen auf dem System gespeichert werden können. Dies ist häufig nicht der Fall. Beispielsweise benötigt ein Treiber möglicherweise eine Benutzer-ID und ein Kennwort, um sich an einem Server anzumelden, und eine andere Benutzer-ID und ein anderes Kennwort, um sich an einem DBMS anzumelden. Da **SQLConnect** eine einzelne Benutzer-ID und ein Kennwort akzeptiert, bedeutet dies, dass die andere Benutzer-ID und das andere Kennwort zusammen mit den Datenquelleninformationen auf dem System gespeichert werden müssen, wenn **SQLConnect** verwendet werden soll. Dies stellt eine potenzielle Sicherheitsverletzung dar und sollte vermieden werden, es sei denn, das Kennwort ist verschlüsselt.  
  
 **SQLDriverConnect** ermöglicht es dem Treiber, eine beliebige Menge an Verbindungsinformationen in den Schlüsselwort-Wert-Paaren der Verbindungszeichenfolge zu definieren. Angenommen, ein Treiber benötigt einen Datenquellennamen, eine Benutzer-ID und ein Kennwort für den Server sowie eine Benutzer-ID und ein Kennwort für das DBMS. Ein benutzerdefiniertes Programm, das immer die XYZ Corp-Datenquelle verwendet, fordert den Benutzer möglicherweise zur Eingabe von IDs und Kennwörtern auf und erstellt den folgenden Satz von Schlüsselwort-Wert-Paaren oder *Verbindungszeichenfolgen,* um sie an **SQLDriverConnect**zu übergeben:  
  
> [!NOTE]  
>  Wenn Sie eine Verbindung zu einem Datenquellenanbieter herstellen, `Trusted_Connection=yes` der die Windows-Authentifizierung unterstützt, sollten Sie anstelle von Benutzer-ID- und Kennwortinformationen in der Verbindungszeichenfolge angeben.  
  
```  
DSN={MyDataSourceName};UID={MyUserID};PWD={MyServerPassword};UIDDBMS={MyDBMSUserID};PWDDBMS={MyDBMSUserPassword};  
```  
  
 Das **Schlüsselwort DSN** (Data Source Name) benennt die Datenquelle, die **Schlüsselwörter UID** und **PWD** geben die Benutzer-ID und das Kennwort für den Server an, und die Schlüsselwörter **UIDDBMS** und **PWDDBMS** geben die Benutzer-ID und das Kennwort für das DBMS an. Beachten Sie, dass das endgültige Semikolon optional ist. **SQLDriverConnect** analysiert diese Zeichenfolge. verwendet den Datenquellennamen XYZ Corp, um zusätzliche Verbindungsinformationen aus dem System abzurufen, z. B. die Serveradresse; und meldet sich mit den angegebenen Benutzer-IDs und Kennwörtern am Server und DBMS an.  
  
 Schlüsselwort-Wert-Paare in **SQLDriverConnect** müssen bestimmten Syntaxregeln folgen. Die Schlüsselwörter und ihre Werte sollten nicht die **[] (),;?{} \*=!** Zeichen. Der Wert des **DSN-Schlüsselworts** darf nicht nur aus Leerzeichen bestehen und sollte keine führenden Leerzeichen enthalten. Aufgrund der Registrierungsgrammatik dürfen Schlüsselwörter und Datenquellennamen nicht\\den umgekehrten Schrägstrich ( ) enthalten. Leerzeichen sind um das Gleichheitszeichen im Schlüsselwort-Wert-Paar nicht zulässig.  
  
 Das **FiledSN-Schlüsselwort** kann in einem Aufruf von **SQLDriverConnect** verwendet werden, um den Namen einer Datei anzugeben, die Datenquelleninformationen enthält (siehe [Verbinden mit Dateidatenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)weiter unten in diesem Abschnitt). Das **Schlüsselwort SAVEFILE** kann verwendet werden, um den Namen einer DSN-Datei anzugeben, in der die Schlüsselwort-Wert-Paare einer erfolgreichen Verbindung, die durch den Aufruf von **SQLDriverConnect** hergestellt wurde, gespeichert werden. Weitere Informationen zu Dateidatenquellen finden Sie in der [SQLDriverConnect-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqldriverconnect-function.md)
