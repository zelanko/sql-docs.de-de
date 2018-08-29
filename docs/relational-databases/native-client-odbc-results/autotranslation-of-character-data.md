---
title: Automatische Übersetzung der Zeichendaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f63e52b0e5ec6c8e100878874321915da2f26ad3
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43094108"
---
# <a name="autotranslation-of-character-data"></a>Automatische Übersetzung der Zeichendaten
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Zeichendaten, wie z. B. ANSI-Zeichen mit SQL_C_CHAR deklarierte Variablen oder Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe der **Char**, **Varchar**, oder **Text** -Datentypen können Stellen Sie nur eine begrenzte Anzahl von Zeichen dar. Mit einem Byte pro Zeichen gespeicherte Zeichendaten können nur 256 Zeichen darstellen. Die in SQL_C_CHAR-Variablen gespeicherten Werte werden mithilfe der ANSI-Codepage (ACP) auf dem Clientcomputer interpretiert. Gespeicherte Werte **Char**, **Varchar**, oder **Text** Datentypen auf dem Server werden mithilfe der ACP des Servers ausgewertet.  
  
 Wenn sowohl die Server-als auch der, über die gleiche ACP verfügen, sie haben keine Probleme bei der Interpretation der in SQL_C_CHAR, gespeicherten Werte **Char**, **Varchar**, oder **Text** Objekte. SQL_C_CHAR-Daten vom Client können als ein anderes Zeichen auf dem Server interpretiert werden, wenn er in verwendet wird, wenn der Server und der Client über unterschiedliche ACP verfügen **Char**, **Varchar**, oder **Text** Spalten, Variablen oder Parameter. Beispielsweise ein Zeichen-Byte, die mit dem Wert 0xA5 als das Zeichen Ñ auf einem Computer mithilfe der Codepage 437 interpretiert wird und wie die Yen melden (¥) auf einem Computer mit der Codepage 1252 interpretiert.  
  
 Unicode-Daten werden mit zwei Bytes pro Zeichen gespeichert. Alle erweiterten Zeichen werden von der Unicode-Spezifikation abgedeckt, weshalb alle Unicode-Zeichen von allen Computern einheitlich interpretiert werden.  
  
 Die Funktion AutoTranslate des der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber versucht, die Probleme Verschieben von Daten zwischen einem Client und einem Server zu minimieren, die dieselbe Codepage haben. AutoTranslate kann festgelegt werden, in der Verbindungszeichenfolge der [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md), in der Konfigurationszeichenfolge von [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md), oder beim Konfigurieren von Datenquellen für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC Treiber, die mit ODBC-Administrator.  
  
 Wenn "autotranslate" auf "Nein" festgelegt ist, werden keine Konvertierungen ausgeführt, auf Daten, die zwischen SQL_C_CHAR-Variablen, auf dem Client verschoben und **Char**, **Varchar**, oder **Text** Spalten, Variablen oder Parameter in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank. Die Bitmuster werden auf dem Client- und dem Servercomputer möglicherweise unterschiedlich interpretiert, wenn die Daten erweiterte Zeichen enthalten und die beiden Computer unterschiedliche Codepages verwenden. Die Daten werden einheitlich interpretiert, wenn beide Computer die gleiche Codepage verwenden.  
  
 Wenn "autotranslate" festgelegt ist, auf "yes", die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber Unicode verwendet, um Daten zwischen SQL_C_CHAR-Variablen, auf dem Client verschoben zu konvertieren und **Char**, **Varchar**, oder **Text** Spalten, Variablen oder Parameter in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank:  
  
-   Beim Senden von einer SQL_C_CHAR-Variable auf dem Client eine **Char**, **Varchar**, oder **Text** Spalte, Variable oder Parameter in eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank, die ODBC Treiber konvertiert zuerst von SQL_C_CHAR in Unicode mithilfe der ACP des Clients aus Unicode wieder in Zeichen, die mithilfe der ACP des Servers.  
  
-   Beim Senden von einem **Char**, **Varchar**, oder **Text** Spalte, Variable oder Parameter in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank in eine SQL_C_CHAR-Variable auf dem Client die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber konvertiert zuerst von Zeichen in Unicode mithilfe der ACP des Servers, klicken Sie dann aus Unicode wieder zurück in SQL_C_CHAR, mithilfe der ACP des Clients.  
  
 Da alle diese Konvertierungen durch erfolgen die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber ausgeführt wird, auf dem Client die Server-ACP eine der auf dem Clientcomputer installierten Codepages sein muss.  
  
 Indem die Zeichenkonvertierung über Unicode durchgeführt wird, ist sichergestellt, dass alle Zeichen, die auf beiden Codepages enthalten sind, korrekt konvertiert werden. Wenn ein Zeichen jedoch nur auf einer der beiden Codepages aufgeführt ist, kann es auf der Zielcodepage nicht dargestellt werden. Zum Beispiel umfasst die Codepage 1252 das Symbol für eingetragene Marken (®), während das Symbol auf der Codepage 437 nicht enthalten ist.  
  
 Die AutoTranslate-Einstellung wirkt sich auf die folgenden Konvertierungen nicht aus:  
  
-   Verschieben von Daten zwischen SQL_C_CHAR-Clientvariablen Zeichen und Unicode- **Nchar**, **Nvarchar**, oder **Ntext** Spalten, Variablen oder Parameter in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken.  
  
-   Verschieben von Daten zwischen Unicode SQL_C_WCHAR-Clientvariablen und Zeichen **Char**, **Varchar**, oder **Text** Spalten, Variablen oder Parameter in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken.  
  
 Daten müssen immer konvertiert werden, wenn sie vom Zeichenformat in Unicode übertragen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Verarbeiten von Ergebnissen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)   
 [Sortierung und Unicode-Unterstützung](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  
