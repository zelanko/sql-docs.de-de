---
title: Automatische Übersetzung von Zeichendaten | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], autotranslating character data
- data types [ODBC], autotranslating character data
- ACPs
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- AutoTranslate feature
- ANSI code pages
- character data autotranslation [ODBC]
- autotranslating character data
- SQL Server Native Client ODBC driver, data types
- ODBC data types, autotranslating character data
ms.assetid: 86a8adda-c5ad-477f-870f-cb370c39ee13
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2a8672f748af8d643fa39038be030efa5d434dc8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297880"
---
# <a name="autotranslation-of-character-data"></a>Automatische Übersetzung der Zeichendaten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Zeichendaten, z. B. ANSI-Zeichenvariablen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die mit SQL_C_CHAR deklariert wurden, oder Daten, die in den Datentypen **char**, **varchar**oder **text** gespeichert sind, können nur eine begrenzte Anzahl von Zeichen darstellen. Mit einem Byte pro Zeichen gespeicherte Zeichendaten können nur 256 Zeichen darstellen. Die in SQL_C_CHAR-Variablen gespeicherten Werte werden mithilfe der ANSI-Codepage (ACP) auf dem Clientcomputer interpretiert. Die Werte, die mit **char**, **varchar**oder **text** datentypen auf dem Server gespeichert werden, werden mit dem ACP des Servers ausgewertet.  
  
 Wenn sowohl der Server als auch der Client denselben ACP haben, haben sie keine Probleme beim Interpretieren der in SQL_C_CHAR, **char**, **varchar**oder **text** objekte gespeicherten Werte. Wenn Server und Client unterschiedliche ACPs haben, können SQL_C_CHAR Daten vom Client als ein anderes Zeichen auf dem Server interpretiert werden, wenn er in **char,** **varchar**oder **Textspalten,** Variablen oder Parametern verwendet wird. Beispielsweise wird ein Zeichenbyte, das den Wert 0xA5 enthält, auf einem Computer mit Derkofeldein2 als Zeichenzeichen interpretiert und als Yen-Zeichen () auf einem Computer interpretiert, auf dem Diecodeseite 1252 ausgeführt wird.  
  
 Unicode-Daten werden mit zwei Bytes pro Zeichen gespeichert. Alle erweiterten Zeichen werden von der Unicode-Spezifikation abgedeckt, weshalb alle Unicode-Zeichen von allen Computern einheitlich interpretiert werden.  
  
 Die AutoTranslate-Funktion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des nativen Client-ODBC-Treibers versucht, die Probleme beim Verschieben von Zeichendaten zwischen einem Client und einem Server mit unterschiedlichen Codepages zu minimieren. AutoTranslate kann in der Verbindungszeichenfolge von [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md), in der Konfigurationszeichenfolge von [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)oder beim Konfigurieren von Datenquellen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nativen Client-ODBC-Treiber mit ODBC-Administrator festgelegt werden.  
  
 Wenn AutoTranslate auf "nein" festgelegt ist, werden keine Konvertierungen für Daten durchgeführt, die zwischen SQL_C_CHAR Variablen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem Client und **char**, **varchar**oder **Textspalten,** Variablen oder Parametern in einer Datenbank verschoben werden. Die Bitmuster werden auf dem Client- und dem Servercomputer möglicherweise unterschiedlich interpretiert, wenn die Daten erweiterte Zeichen enthalten und die beiden Computer unterschiedliche Codepages verwenden. Die Daten werden einheitlich interpretiert, wenn beide Computer die gleiche Codepage verwenden.  
  
 Wenn AutoTranslate auf "yes" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] festgelegt ist, verwendet der native Client ODBC-Treiber Unicode, um Daten zu konvertieren, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zwischen SQL_C_CHAR Variablen auf dem Client und **char**, **varchar**oder **Textspalten,** Variablen oder Parametern in einer Datenbank verschoben wurden:  
  
-   Wenn Daten von einer SQL_C_CHAR-Variablen auf dem Client an eine **char-,** **varchar-** oder **Textspalte,** -Variable oder einen Parameter in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank gesendet werden, konvertiert der ODBC-Treiber zuerst von SQL_C_CHAR in Unicode mit der ACP des Clients und dann von Unicode zurück in das Zeichen mit der ACP des Servers.  
  
-   Wenn Daten von einer **char**- **varchar**oder **Textspalte,** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Variablen oder einem Parameter in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einer Datenbank an eine SQL_C_CHAR-Variable auf dem Client gesendet werden, konvertiert der Native Client ODBC-Treiber zuerst von Zeichen in Unicode mit dem ACP des Servers, dann von Unicode zurück in SQL_C_CHAR mit dem ACP des Clients.  
  
 Da alle diese Konvertierungen vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber durchgeführt werden, der auf dem Client ausgeführt wird, muss der Server ACP eine der auf dem Clientcomputer installierten Codepages sein.  
  
 Indem die Zeichenkonvertierung über Unicode durchgeführt wird, ist sichergestellt, dass alle Zeichen, die auf beiden Codepages enthalten sind, korrekt konvertiert werden. Wenn ein Zeichen jedoch nur auf einer der beiden Codepages aufgeführt ist, kann es auf der Zielcodepage nicht dargestellt werden. Zum Beispiel umfasst die Codepage 1252 das Symbol für eingetragene Marken (®), während das Symbol auf der Codepage 437 nicht enthalten ist.  
  
 Die AutoTranslate-Einstellung wirkt sich auf die folgenden Konvertierungen nicht aus:  
  
-   Verschieben von Daten zwischen ZeichenSQL_C_CHAR Clientvariablen und Unicode **nchar**, **nvarchar**oder **ntext** Spalten, Variablen oder Parametern in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken.  
  
-   Verschieben von Daten zwischen Unicode-SQL_C_WCHAR Clientvariablen und Zeichen **zeichen**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **varchar**oder **Textspalten,** Variablen oder Parametern in Datenbanken.  
  
 Daten müssen immer konvertiert werden, wenn sie vom Zeichenformat in Unicode übertragen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verarbeitungsergebnisse &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)   
 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  
