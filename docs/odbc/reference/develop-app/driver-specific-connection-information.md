---
title: Treiberspezifische Verbindungsinformationen | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: e3852e713e517828e83e74bf7fb291ef20865532
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63238702"
---
# <a name="driver-specific-connection-information"></a>Treiberspezifische Verbindungsinformationen
**SQLConnect** wird davon ausgegangen, dass eine ODBC-Datenquellenname, Benutzer-ID und Kennwort für die Verbindung mit einer Datenquelle ausreichen und alle anderen Verbindungsinformationen auf dem System gespeichert werden kann. Dies ist häufig nicht der Fall. Ein Treiber möglicherweise z. B. eine Benutzer-ID und Kennwort zum Anmelden bei einem Server und einen anderen Benutzer-ID und ein Kennwort zum Anmelden ein DBMS. Da **SQLConnect** akzeptiert einen einzelnen Benutzer-ID und ein Kennwort, das bedeutet, dass andere Benutzer-ID und Kennwort mit Informationen für die Datenquelle auf dem System bei gespeichert werden müssen **SQLConnect** verwendet werden soll. Dies ist eine potenzielle Sicherheitslücke und sollte vermieden werden, es sei denn, das Kennwort verschlüsselt wird.  
  
 **SQLDriverConnect** ermöglicht es dem Treiber auf eine beliebige Anzahl von Verbindungsinformationen in der Verbindungszeichenfolge der-Wert-Paare zu definieren. Nehmen wir beispielsweise an, dass ein Treiber Datenquellenname, Benutzer-ID und Kennwort für den Server, und Benutzer-ID und Kennwort für das DBMS erforderlich ist. Ein benutzerdefiniertes Programm, das die XYZ Corp-Datenquelle immer verwendet kann der Benutzer aufgefordert, IDs und Kennwörtern, und erstellen Sie den folgenden Satz von Schlüsselwort-Wert-Paare oder *Verbindungszeichenfolge* Übergabe an **SQLDriverConnect**:  
  
> [!NOTE]  
>  Wenn Sie für einen Datenanbieter der Datenquelle, der Windows-Authentifizierung unterstützt herstellen, sollten Sie angeben `Trusted_Connection=yes` anstelle von Benutzer-ID und Kennwort-Informationen in der Verbindungszeichenfolge.  
  
```  
DSN={MyDataSourceName};UID={MyUserID};PWD={MyServerPassword};UIDDBMS={MyDBMSUserID};PWDDBMS={MyDBMSUserPassword};  
```  
  
 Die **DSN** (Data Source Name)-Schlüsselwort Namen die Datenquelle, die **UID** und **PWD** Schlüsselwörter angeben, die Benutzer-ID und das Kennwort für den Server, und die **UIDDBMS**  und **PWDDBMS** Schlüsselwörter geben Sie den Benutzer-ID und das Kennwort für das DBMS. Beachten Sie, dass das endgültige Semikolon optional ist. **SQLDriverConnect** analysiert diese Zeichenfolge; der Name der Datenquelle XYZ Corp verwendet, um zusätzliche Verbindungsinformationen aus dem System, z. B. die Adresse des Servers, zu abzurufen, und meldet sich an den Server und ein DBMS, die mit dem angegebenen Benutzer-IDs und Kennwörter.  
  
 Schlüsselwort-Wert-Paare in **SQLDriverConnect** müssen bestimmte Syntaxregeln entsprechen. Die Schlüsselwörter und deren Werte sollten keine der **[]{}();? \*=! @** Zeichen. Der Wert des der **DSN** -Schlüsselwort darf nicht ausschließlich aus Leerzeichen bestehen und darf keine führende Leerzeichen enthalten. Aufgrund der Grammatik Registrierung darf keine Schlüsselwörter und Namen von Datenquellen enthalten, den umgekehrten Schrägstrich (\\) Zeichen. Leerzeichen sind vor und hinter dem Gleichzeichen im Schlüsselwort-Wert-Paar nicht zulässig.  
  
 Die **FILEDSN** -Schlüsselwort kann verwendet werden, in einem Aufruf von **SQLDriverConnect** an den Namen einer Datei, die Informationen der Datenquelle enthält (finden Sie unter [Herstellen einer Verbindung mithilfe von Dateidatenquellen](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)weiter unten in diesem Abschnitt). Die **SAVEFILE** -Schlüsselwort können Sie den Namen des DSN-Datei angeben, in dem die Schlüsselwort-Wert-Paare einer erfolgreichen Verbindung verwendet werden, durch den Aufruf von **SQLDriverConnect** gespeichert werden sollen. Weitere Informationen zu Datei-Datenquellen, finden Sie unter den [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) funktionsbeschreibung.
