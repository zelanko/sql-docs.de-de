---
title: Scrollbare Cursor und Transaktionsisolation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- isolation levels [ODBC]
- scrollable cursors [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: f0216f4a-46e3-48ae-be0a-e2625e8403a6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5510eb58315f70195eb40390edec1766c350fb6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47662348"
---
# <a name="scrollable-cursors-and-transaction-isolation"></a>Scrollbare Cursor und Transaktionsisolation
In der folgende Tabelle sind die Faktoren aufgeführt, die die Sichtbarkeit der Änderungen.  
  
|Änderungen durch:|Sichtbarkeit hängt:|  
|----------------------|----------------------------|  
|Cursor|Cursortyp, Cursor-Implementierung|  
|Andere Anweisungen in derselben Transaktion|Cursortyp|  
|Anweisungen in anderen Transaktionen|Cursortyp, die Isolationsstufe für Transaktionen|  
  
 Diese Faktoren werden in der folgenden Abbildung angezeigt.  
  
 ![Faktoren, die die Sichtbarkeit der Änderungen](../../../odbc/reference/develop-app/media/pr23.gif "pr23")  
  
 Die folgende Tabelle enthält die Fähigkeit der einzelnen Cursor zum Erkennen von Änderungen, die sich durch andere Vorgänge in einer eigenen Transaktion und von anderen Transaktionen vorgenommen werden. Die Sichtbarkeit der letzten Änderungen hängt davon ab, der Cursortyp und die Isolationsstufe der Transaktion, die den Cursor enthält.  
  
|Cursor type\action|Self-Service|Besitzer<br /><br /> Transaktionsvorgänge|Adresszuweisungen<br /><br /> Transaktionsvorgänge<br /><br /> (RU[a])|Adresszuweisungen<br /><br /> Transaktionsvorgänge<br /><br /> (RC[a])|Adresszuweisungen<br /><br /> Transaktionsvorgänge<br /><br /> (RR[a])|Adresszuweisungen<br /><br /> Transaktionsvorgänge<br /><br /> (S[a])|  
|-------------------------|----------|-----------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|  
|STATIC-Cursor|||||||  
|Insert|Vielleicht [b]|nein|nein|nein|nein|nein|  
|Update|Vielleicht [b]|nein|nein|nein|nein|nein|  
|DELETE|Vielleicht [b]|nein|nein|nein|nein|nein|  
|Keysetgesteuerte|||||||  
|Insert|Vielleicht [b]|nein|nein|nein|nein|nein|  
|Update|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein|  
|DELETE|Vielleicht [b]|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein|  
|Dynamic|||||||  
|Insert|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|Update|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein|  
|DELETE|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein|  
  
 [a] der Buchstaben in Klammern geben die Isolationsstufe der Transaktion, die mit dem Cursor; die Isolationsstufe der anderen Transaktion (in dem die Änderung vorgenommen wurde) ist nicht relevant.  
  
 RU: Read uncommitted  
  
 RC: Lesen zugesichert  
  
 RR: Wiederholbarer Lesevorgang  
  
 S: serialisierbar  
  
 [b] hängt wie der Cursor implementiert wird. Gibt an, ob der Cursor für solche Änderungen erkennen, kann werden gemeldet, über die Feedbackoption im SQL_STATIC_SENSITIVITY in **SQLGetInfo**.
