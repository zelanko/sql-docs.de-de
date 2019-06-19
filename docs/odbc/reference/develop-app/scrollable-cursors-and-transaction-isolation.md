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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62468592"
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
  
|Cursor type\action|Self-Service|Besitzer<br /><br /> Txn|Adresszuweisungen<br /><br /> Txn<br /><br /> (RU[a])|Adresszuweisungen<br /><br /> Txn<br /><br /> (RC[a])|Adresszuweisungen<br /><br /> Txn<br /><br /> (RR[a])|Adresszuweisungen<br /><br /> Txn<br /><br /> (S[a])|  
|-------------------------|----------|-----------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|  
|Statisch|||||||  
|Insert|Maybe[b]|Nein|Nein|Nein|Nein|Nein|  
|Update|Maybe[b]|Nein|Nein|Nein|Nein|Nein|  
|DELETE|Maybe[b]|Nein|Nein|Nein|Nein|Nein|  
|Keysetgesteuerte|||||||  
|Insert|Maybe[b]|Nein|Nein|Nein|Nein|Nein|  
|Update|Ja|Ja|Ja|Ja|Nein|Nein|  
|DELETE|Maybe[b]|Ja|Ja|Ja|Nein|Nein|  
|Dynamic|||||||  
|Insert|Ja|Ja|Ja|Ja|Ja|Nein|  
|Update|Ja|Ja|Ja|Ja|Nein|Nein|  
|DELETE|Ja|Ja|Ja|Ja|Nein|Nein|  
  
 [a] der Buchstaben in Klammern geben die Isolationsstufe der Transaktion, die mit dem Cursor; die Isolationsstufe der anderen Transaktion (in dem die Änderung vorgenommen wurde) ist nicht relevant.  
  
 RU: Read Uncommitted  
  
 RC: Read Committed  
  
 RR: Repeatable Read  
  
 S:  Serializable  
  
 [b] hängt wie der Cursor implementiert wird. Gibt an, ob der Cursor für solche Änderungen erkennen, kann werden gemeldet, über die Feedbackoption im SQL_STATIC_SENSITIVITY in **SQLGetInfo**.
