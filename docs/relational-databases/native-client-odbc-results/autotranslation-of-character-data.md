---
title: Automatische Übersetzung von Zeichendaten | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c08a0987e11f25c3f5b535d8d26526db5bb14a38
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73779172"
---
# <a name="autotranslation-of-character-data"></a>Automatische Übersetzung der Zeichendaten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Zeichendaten, wie z. b. ANSI-Zeichen Variablen, die mit SQL_C_CHAR oder in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherten Daten mit den Datentypen **char**, **varchar**oder **Text** deklariert werden, können nur eine begrenzte Anzahl von Zeichen darstellen. Mit einem Byte pro Zeichen gespeicherte Zeichendaten können nur 256 Zeichen darstellen. Die in SQL_C_CHAR-Variablen gespeicherten Werte werden mithilfe der ANSI-Codepage (ACP) auf dem Clientcomputer interpretiert. Die Werte, die mit den Datentypen **char**, **varchar**oder **Text** auf dem Server gespeichert werden, werden mithilfe der ACP des Servers ausgewertet.  
  
 Wenn sowohl der Server als auch der Client über dieselbe ACP verfügen, haben Sie keine Probleme bei der Interpretation der Werte, die in SQL_C_CHAR-, **char**-, **varchar**-oder **Text** -Objekten gespeichert werden. Wenn der Server und der Client über unterschiedliche ACPs verfügen, werden SQL_C_CHAR Daten vom Client möglicherweise als ein anderes Zeichen auf dem Server interpretiert, wenn Sie in **char**-, **varchar**-oder **Text** -Spalten,-Variablen oder-Parametern verwendet werden. Ein Zeichen Byte, das den Wert 0xA5 enthält, wird z. b. auf einem Computer mit der Codepage 437 als Zeichen Version interpretiert und als Yen-Zeichen (Yen Sign) auf einem Computer mit der Codepage 1252 interpretiert.  
  
 Unicode-Daten werden mit zwei Bytes pro Zeichen gespeichert. Alle erweiterten Zeichen werden von der Unicode-Spezifikation abgedeckt, weshalb alle Unicode-Zeichen von allen Computern einheitlich interpretiert werden.  
  
 Das Autotranslation-Feature des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treibers versucht, die Probleme beim Verschieben von Zeichendaten zwischen einem Client und einem Server mit unterschiedlichen Codepages zu minimieren. Autotranslation kann in der Verbindungs Zeichenfolge von [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md), in der Konfigurations Zeichenfolge von [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md)oder beim Konfigurieren von Datenquellen für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber mithilfe des ODBC-Administrators festgelegt werden.  
  
 Wenn AutoTranslate auf "No" festgelegt ist, werden keine Konvertierungen für Daten vorgenommen, die zwischen SQL_C_CHAR Variablen auf dem Client und **char**-, **varchar**-oder **Text** -Spalten,-Variablen oder-Parametern in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank verschoben werden. Die Bitmuster werden auf dem Client- und dem Servercomputer möglicherweise unterschiedlich interpretiert, wenn die Daten erweiterte Zeichen enthalten und die beiden Computer unterschiedliche Codepages verwenden. Die Daten werden einheitlich interpretiert, wenn beide Computer die gleiche Codepage verwenden.  
  
 Wenn AutoTranslate auf "yes" festgelegt ist, verwendet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber Unicode zum Konvertieren von Daten, die zwischen SQL_C_CHAR Variablen auf den Client-und **char**-, **varchar**-oder **Text** -Spalten,-Variablen oder-Parametern in einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindung  
  
-   Beim Senden von Daten aus einer SQL_C_CHAR Variablen auf dem Client an eine **char**-, **varchar**-oder **Text** -Spalte,-Variable oder einen-Parameter in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank wird der ODBC-Treiber zuerst mithilfe der ACP des Clients von SQL_C_CHAR in Unicode konvertiert. , dann mit der ACP des Servers von Unicode zurück zum Zeichen.  
  
-   Wenn Daten aus einer **char**-, **varchar**-oder **Text** -Spalte, einer Variablen oder einem Parameter in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank an eine SQL_C_CHAR Variable auf dem Client gesendet werden, konvertiert der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber zuerst mithilfe der ACP von Zeichen in Unicode. des Servers, dann von Unicode zurück zu SQL_C_CHAR mithilfe der ACP des Clients.  
  
 Da alle diese Konvertierungen vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber ausgeführt werden, der auf dem Client ausgeführt wird, muss die Server-ACP eine der auf dem Client Computer installierten Codepages sein.  
  
 Indem die Zeichenkonvertierung über Unicode durchgeführt wird, ist sichergestellt, dass alle Zeichen, die auf beiden Codepages enthalten sind, korrekt konvertiert werden. Wenn ein Zeichen jedoch nur auf einer der beiden Codepages aufgeführt ist, kann es auf der Zielcodepage nicht dargestellt werden. Zum Beispiel umfasst die Codepage 1252 das Symbol für eingetragene Marken (®), während das Symbol auf der Codepage 437 nicht enthalten ist.  
  
 Die AutoTranslate-Einstellung wirkt sich auf die folgenden Konvertierungen nicht aus:  
  
-   Verschieben von Daten zwischen Zeichen SQL_C_CHAR Client Variablen und Unicode- **NCHAR**-, **nvarchar**-oder **ntext** -Spalten,-Variablen oder-Parametern in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken.  
  
-   Verschieben von Daten zwischen Unicode-SQL_C_WCHAR Client Variablen und Zeichen **char**-, **varchar**-oder **Text** -Spalten,-Variablen oder-Parametern in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbanken.  
  
 Daten müssen immer konvertiert werden, wenn sie vom Zeichenformat in Unicode übertragen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Verarbeitungsergebnisse &#40;(ODBC&#41; ](../../relational-databases/native-client-odbc-results/processing-results-odbc.md) - )  
 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  
