---
title: Verwalten von Text- und Image-Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- data types [ODBC], mapping
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 7b543556-ff36-4d35-ac08-de96223d92cd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a161b009239db3c17acb64f8d8eeaaa61321cd9f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48052034"
---
# <a name="managing-text-and-image-columns"></a>Verwalten von Text und Imagespalten
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text**, **Ntext**, und **Image** Daten (auch als long-Daten bezeichnet) sind Zeichen- oder binären Zeichenfolgen-Datentypen, Datenwerte zu groß für aufnehmen können **Char**, **Varchar**, **binäre**, oder **Varbinary** Spalten. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text** -Datentyp zugeordnet, der Datentyp SQL_LONGVARCHAR für ODBC **Ntext** SQL_WLONGVARCHAR zugeordnet und **Image** -Datentyp SQL_LONGVARBINARY. Einige Datenelemente, wie z. B. lange Dokumente oder große Bitmaps, sind möglicherweise zu groß, um im Speicher gespeichert zu werden. Zum Abrufen von long-Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in teilsequenzen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber ermöglicht einer Anwendung aufrufen, [SQLGetData](../native-client-odbc-api/sqlgetdata.md). Um lange Daten in teilsequenzen zu senden, die Anwendung aufrufen kann [SQLPutData](../native-client-odbc-api/sqlputdata.md). Parameter, für die Daten zur Ausführungszeit gesendet werden, werden als Data-at-Execution-Parameter bezeichnet.  
  
 Eine Anwendung kann tatsächlich schreiben oder rufen Sie alle Arten von Daten (nicht nur long-Daten) mit **SQLPutData** oder **SQLGetData**, obwohl nur **Zeichen** und  **binäre** Daten gesendet oder in Teilen abgerufen werden können. Wenn die Daten klein genug, um in einen einzelnen Puffer zu passen, gibt es ist jedoch im Allgemeinen kein Grund für die Verwendung **SQLPutData** oder **SQLGetData**. Es ist viel leichter, den einzelnen Puffer an den Parameter oder die Spalte zu binden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Gebundene im Vergleich zu ungebundenen Text- und Image-Spalten](bound-vs-unbound-text-and-image-columns.md)  
  
-   [Protokollierte im Vergleich zu nicht protokollierten Änderungen](logged-vs-unlogged-modifications.md)  
  
-   [Data-at-Execution und Text-, ntext- oder Imagespalten](data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
