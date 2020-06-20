---
title: Verwalten von Text-und image-Spalten | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e9d7d5b0f48c68e8ac911f5e274c9afdb8cfe17d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85049695"
---
# <a name="managing-text-and-image-columns"></a>Verwalten von Text und Imagespalten
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**Text**- **, ntext**-und **Image** -Daten (auch als Long Data bezeichnet) sind Zeichen-oder Binär Zeichenfolgendatentypen, die Datenwerte enthalten können, die für die Spalten **char**, **varchar**, **Binary**oder **varbinary** zu groß sind. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Text** Datentyp wird dem ODBC-SQL_LONGVARCHAR-Datentyp zugeordnet. **ntext** wird SQL_WLONGVARCHAR zugeordnet. und **Image** wird SQL_LONGVARBINARY zugeordnet. Einige Datenelemente, wie z. B. lange Dokumente oder große Bitmaps, sind möglicherweise zu groß, um im Speicher gespeichert zu werden. Zum Abrufen von Long-Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sequenziellen Teilen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ermöglicht der Native Client ODBC-Treiber einer Anwendung das Aufrufen von [SQLGetData](../native-client-odbc-api/sqlgetdata.md). Um lange Daten in sequenziellen Teilen zu senden, kann die Anwendung [SQLPutData](../native-client-odbc-api/sqlputdata.md)abrufen. Parameter, für die Daten zur Ausführungszeit gesendet werden, werden als Data-at-Execution-Parameter bezeichnet.  
  
 Eine Anwendung kann mit **SQLPutData** oder **SQLGetData**tatsächlich beliebige Datentypen (nicht nur mit langen Daten) schreiben oder abrufen, obwohl nur **Zeichen** -und **Binär** Daten in Teilen gesendet oder abgerufen werden können. Wenn die Daten jedoch klein genug für einen einzelnen Puffer sind, gibt es im Allgemeinen keinen Grund, **SQLPutData** oder **SQLGetData**zu verwenden. Es ist viel leichter, den einzelnen Puffer an den Parameter oder die Spalte zu binden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Vergleich von gebundenen und ungebundenen Text- und Image-Spalten](bound-vs-unbound-text-and-image-columns.md)  
  
-   [Vergleich von protokollierten und nicht protokollierten Änderungen](logged-vs-unlogged-modifications.md)  
  
-   [Data-at-Execution und Text-, ntext- oder Imagespalten](data-at-execution-and-text-ntext-or-image-columns.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)  
  
  
