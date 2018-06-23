---
title: Verwalten von Text- und Image-Spalten | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1316f093ac0d1f79c5155ae1be88df98f091bd8f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160904"
---
# <a name="managing-text-and-image-columns"></a>Verwalten von Text und Imagespalten
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text**, **Ntext**, und **Image** Daten (auch als long-Daten bezeichnet) sind Zeichen- oder binären Zeichenfolgen-Datentypen, die Datenwerte zu groß für aufnehmen können **Char**, **Varchar**, **binäre**, oder **Varbinary** Spalten. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text** -Datentyp mit der ODBC SQL_LONGVARCHAR-Datentyp; **Ntext** ordnet SQL_WLONGVARCHAR und **Image** -Datentyp SQL_LONGVARBINARY. Einige Datenelemente, wie z. B. lange Dokumente oder große Bitmaps, sind möglicherweise zu groß, um im Speicher gespeichert zu werden. Zum Abrufen von long-Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in teilsequenzen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber ermöglicht einer Anwendung aufrufen [SQLGetData](../native-client-odbc-api/sqlgetdata.md). Um lange Daten in teilsequenzen zu senden, kann die Anwendung aufrufen [SQLPutData](../native-client-odbc-api/sqlputdata.md). Parameter, für die Daten zur Ausführungszeit gesendet werden, werden als Data-at-Execution-Parameter bezeichnet.  
  
 Tatsächlich eine Anwendung schreiben bzw. jeden Datentyp (nicht nur long-Daten) mit abrufen **SQLPutData** oder **SQLGetData**, obwohl nur **Zeichen** und  **binäre** Daten gesendet oder in Teilen abgerufen werden können. Wenn die Daten klein genug, um einen einzelnen Puffer zu groß ist, besteht jedoch im Allgemeinen kein Grund zur Verwendung **SQLPutData** oder **SQLGetData**. Es ist viel leichter, den einzelnen Puffer an den Parameter oder die Spalte zu binden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Gebundene im Vergleich zu ungebundenen Text- und Image-Spalten](bound-vs-unbound-text-and-image-columns.md)  
  
-   [Protokollierte im Vergleich zu nicht protokollierten Änderungen](logged-vs-unlogged-modifications.md)  
  
-   [Data-at-Execution und Text-, ntext- oder Imagespalten](data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  